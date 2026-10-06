using System;
using System.Collections.Generic;

interface IShape
{
    double CalculateArea();
    double CalculatePerimeter();
}

class Circle : IShape
{
    public double Radius;

    public Circle(double radius)
    {
        Radius = radius;
    }

    public double CalculateArea()
    {
        return Math.PI * Radius * Radius;
    }

    public double CalculatePerimeter()
    {
        return 2 * Math.PI * Radius;
    }
}

class Rectangle : IShape
{
    public double Width;
    public double Height;

    public Rectangle(double width, double height)
    {
        Width = width;
        Height = height;
    }

    public double CalculateArea()
    {
        return Width * Height;
    }

    public double CalculatePerimeter()
    {
        return 2 * (Width + Height);
    }
}

class Triangle : IShape
{
    public double A;
    public double B;
    public double C;

    public Triangle(double a, double b, double c)
    {
        A = a;
        B = b;
        C = c;
    }

    public double CalculateArea()
    {
        double s = (A + B + C) / 2;
        return Math.Sqrt(s * (s - A) * (s - B) * (s - C));
    }

    public double CalculatePerimeter()
    {
        return A + B + C;
    }
}

class ShapeHelper
{
    public double CalculateArea(double radius)
    {
        return Math.PI * radius * radius;
    }

    public double CalculateArea(double width, double height)
    {
        return width * height;
    }
}

class Program
{
    static void Main()
    {
        List<IShape> shapes = new List<IShape>();

        shapes.Add(new Circle(5));
        shapes.Add(new Rectangle(4, 6));
        shapes.Add(new Triangle(3, 4, 5));

        foreach (IShape shape in shapes)
        {
            Console.WriteLine("Sahe: " + shape.CalculateArea());
            Console.WriteLine("Perimetr: " + shape.CalculatePerimeter());
            Console.WriteLine();
        }

        ShapeHelper helper = new ShapeHelper();

        Console.WriteLine("Circle sahesi: " + helper.CalculateArea(5));
        Console.WriteLine("Rectangle sahesi: " + helper.CalculateArea(4, 6));
    }
}
