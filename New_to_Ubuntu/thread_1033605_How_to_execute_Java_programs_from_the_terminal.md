---
title: "How to execute Java programs from the terminal?"
date: 2009-01-07
forum: New to Ubuntu
---

### Post by ItecKid on 2009-01-07
Hello,

I have the following Java program:

```

public class hello
{
	public static void main(String args[])
	{
		System.out.println("Hello, world!");
	}
}
```

When I try to execute it with 

```
javac hello.java
```

The system doesn't output anything.

Thoughts?

---

### Post by andamaru on 2009-01-07
javac is the "compiler" for java. There should be a file called hello.class

To run that class file you just created you type
java hello

Instructions
javac nameOfFile.java //creates class files of all your classes
java nameOfFile //nameOfFile should be the class that has main in it

---

