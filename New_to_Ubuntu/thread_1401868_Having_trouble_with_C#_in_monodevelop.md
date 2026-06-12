---
title: "Having trouble with C# in monodevelop"
date: 2010-02-08
forum: New to Ubuntu
---

### Post by mcbagpipe89 on 2010-02-08
When I try to run the following code, it doesn't prompt me for input.  Is there something I am missing in monodevelop, or is my code flawed?  also, is there an alternative IDE I could use for C#?  I tried to install a plugin for eclipse, but it was buggy, and didn't work properly.

```

 using System;
 using System.Collections.Generic;
 using System.Linq;
 using System.Text;

namespace testingRunning
{
    class Program
    {
	    static void Main( string[] args )
        {
		decimal[] inputNums = new decimal[10];
		int count = 0;
		decimal total = 0;
		decimal avg = 0;
		decimal difference = 0;
		
			Console.WriteLine("Enter 10 numbers");
			while(count < 10) 
			{
				Console.WriteLine("Enter number {0}", count + 1);
				inputNums[count] = Convert.ToDecimal (Console.ReadLine());
				total = total + inputNums[count];
				count = count + 1;
						                               
			}
		}
	}
}

```

---

### Post by argor on 2010-02-08
> **mcbagpipe89 said:**
> When I try to run the following code, it doesn't prompt me for input.  Is there something I am missing in monodevelop, or is my code flawed?  also, is there an alternative IDE I could use for C#?  I tried to install a plugin for eclipse, but it was buggy, and didn't work properly.

```

 using System;
 using System.Collections.Generic;
 using System.Linq;
 using System.Text;

namespace testingRunning
{
    class Program
    {
	    static void Main( string[] args )
        {
		decimal[] inputNums = new decimal[10];
		int count = 0;
		decimal total = 0;
		decimal avg = 0;
		decimal difference = 0;
		
			Console.WriteLine("Enter 10 numbers");
			while(count < 10) 
			{
				Console.WriteLine("Enter number {0}", count + 1);
				inputNums[count] = Convert.ToDecimal (Console.ReadLine());
				total = total + inputNums[count];
				count = count + 1;
						                               
			}
		}
	}
}

```
it should be Console.Write instead of Console.WriteLine
Console.Write  write and then  waits for input 
vile  Console.WriteLine only writes a line

---

### Post by doas777 on 2010-02-08
are you hitting enter after every number?

---

