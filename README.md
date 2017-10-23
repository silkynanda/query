# Query Pattern

Package that provides the foundation to implement the Query Pattern

![Build Status](https://chr.visualstudio.com/_apis/public/build/definitions/2d33193a-77fd-4ddc-be87-12c73bc5ff99/20/badge)

## How to install
`Install-Package Chroomsoft.Queries`

[NuGet.org](https://www.nuget.org/packages/Chroomsoft.Queries/)

## How to use
- Create a (.NET Core) console application
- Install the `Chroomsoft.Queries` package
- Pasted the following code:

```csharp
public class SumQuery : IQuery<int>
    {
        public int A { get; set; }
        public int B { get; set; }
    }

    public class SumQueryHandler : IQueryHandler<SumQuery, int>
    {
        public int Handle(SumQuery query)
        {
            return query.A + query.B;
        }
    }

    class Program
    {
        static void Main(string[] args)
        {
            // Setup classes
            IQueryHandlerRegister register = new QueryHandlerRegister();
            register.Register(new SumQueryHandler());

            // Construct Query
            var query = new SumQuery { A = 5, B = 2 };

            // Handle query
            var result = register.Handle(query);

            Console.WriteLine(result);
            Console.ReadKey();
        }
    }
```
