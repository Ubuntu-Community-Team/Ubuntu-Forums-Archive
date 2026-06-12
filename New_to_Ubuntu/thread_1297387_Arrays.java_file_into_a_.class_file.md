---
title: "Arrays.java file into a .class file?"
date: 2009-10-21
forum: New to Ubuntu
---

### Post by Lil Josh on 2009-10-21
How would I turn Arrays.java file into an Arrays.class file with terminal? I've tried:

```

cd ~/home/gabe/Desktop/javac Arrays.java

```

Would that be right? If not, then how would I do it? If it is right, then it said,

```

gabe@gabe:~$ cd ~/home/gabe/Desktop/javac Arrays.java
bash: cd: /home/gabe/home/gabe/Desktop/javac: No such file or directory

```

Also, is, "/home/gabe/home/gabe/" supposed to be coming up twice? I've been noticing that and was wondering if something was wrong.

Thanks in advance.

---

### Post by issih on 2009-10-21
~ is a shortcut to your home directory so you should be using either:

```
~/Desktop/
```

or

```
/home/gabe/Desktop/
```

as ~ will for your user gabe point to /home/gabe...

That is why you are not finding the file, because you are passing it wrong information.

Secondarily..in a normal java install I don't think the compiler would be sat in your home directory, and further still it would normally be somewhere already in the system path. Entering the full path should not be necessary (you can just use javac filename.java) unless you have a specific version of the compiler you keep in your home directory for whatever reason.

Hope that helps

---

### Post by Lil Josh on 2009-10-21
I did:

```
gabe@gabe:~$ ~/Desktop/javac Arrays.java
```And got:

```
bash: /home/gabe/Desktop/javac: No such file or directory
```When trying it.

Then, I did:

```
gabe@gabe:~$ cd ~/Desktop/javac Arrays.java
```And got:

```
bash: cd: /home/gabe/Desktop/javac: No such file or directory
```When trying to use the, "cd" in front of it. Any help?

When doing:

```
gabe@gabe:~$ javac Arrays.java
```

I got:

```
bash: javac: command not found
```

Does that mean I have to download/install JDK?

---

### Post by falconindy on 2009-10-21
You seem to be confused about how the terminal operates. The command 'cd' changes your working directory. javac is a separate program which is located in /usr/bin/javac. javac accepts an argument in its execution which is a java source code file. The resulting output is bytecode. What you want is the following:
```
javac ~/Desktop/Arrays.java
```
However, once you get the resulting bytecode, it would be easier to 'cd' into the directory where its located in order to execute it as:
```
java Arrays
```
Notice that despite the bytecode file having the .class extension, I haven't included it in the execution. That's intentional. Now, I'm not sure if that will cause an error, but it may. The name 'Arrays' is already the name of a class that is included with the JRE -- it provides some extra functionality for working with arrays.

Executing java from a directory other than your current working directory can be problematic. I'm not going to explain why.

---

### Post by Lil Josh on 2009-10-21
> **falconindy said:**
> 
However, once you get the resulting bytecode, it would be easier to 'cd' into the directory where its located in order to execute it as:
```
java Arrays
```Notice that despite the bytecode file having the .class extension, I haven't included it in the execution. That's intentional. Now, I'm not sure if that will cause an error, but it may. The name 'Arrays' is already the name of a class that is included with the JRE -- it provides some extra functionality for working with arrays.

Thanks, but it came out with this:

```
gabe@gabe:~$ java Arrays
Exception in thread "main" java.lang.NoClassDefFoundError: Arrays
Caused by: java.lang.ClassNotFoundException: Arrays
    at java.net.URLClassLoader$1.run(URLClassLoader.java:200)
    at java.security.AccessController.doPrivileged(Native Method)
    at java.net.URLClassLoader.findClass(URLClassLoader.java:188)
    at java.lang.ClassLoader.loadClass(ClassLoader.java:306)
    at sun.misc.Launcher$AppClassLoader.loadClass(Launcher.java:276)
    at java.lang.ClassLoader.loadClass(ClassLoader.java:251)
    at java.lang.ClassLoader.loadClassInternal(ClassLoader.java:319)
```I was wondering if something was wrong with the file? Or is there something else wrong? Sorry, but I'm not too good at this. Ubuntu was never my thing, but I'm willing to keep on going with it. Works very well.

I also did this:

```

gabe@gabe:~$ javac Arrays.java
error: cannot read: Arrays.java
1 error

```

Anyone know what the error would be? In the file or in the code for javac?

---

### Post by falconindy on 2009-10-21
You haven't compiled the source code yet. Assuming the source file is still on your desktop(~/Desktop), you tried to compile (and execute) it from your home directory (~/).

---

### Post by Lil Josh on 2009-10-21
> **falconindy said:**
> You haven't compiled the source code yet. Assuming the source file is still on your desktop(~/Desktop), you tried to compile (and execute) it from your home directory (~/).

This is what happened when I did:

```

gabe@gabe:~$ ~/Desktop/javac Hello.java
bash: /home/gabe/Desktop/javac: No such file or directory

```

It's on the Desktop, so I wouldn't know why it says, "No such file or directory".

Any help? Thanks in advance.

---

### Post by falconindy on 2009-10-21
Once again, your source code is on your desktop, **NOT** javac. javac is a program in /usr/bin which can be called from anywhere because its path of your $PATH. You need to re-read my previous post. I gave you the correct execution and you're still doing it wrong.

```
cd ~/Desktop
javac Arrays.java
java Arrays
```

---

### Post by Lil Josh on 2009-10-21
Oh.. Sorry, still new at terminal. Thanks, it worked.

I'm also getting this problem for creating a class called, "Loops.java".

Code for Loops.java:

```

public class Loops
{
   public static void main(String[] args)
   {
      int i = 1;
      do
      {
         System.out.println("Hello");
         i++;
      }
      while (i <= 10)
   }
}

```

And then it comes up as the error:

```

gabe@gabe:~/Desktop$ javac Loops.java
Loops.java:14: ';' expected
   }
   ^
1 error

```

Any help? Thanks in advance.

---

### Post by igknighted on 2009-10-22
It's been a while since i've played with java, but should there be a ';' after the while statement?

---

### Post by Lil Josh on 2009-10-22
> **igknighted said:**
> It's been a while since i've played with java, but should there be a ';' after the while statement?

Yeah, just did it like a minute before you answered my thread. When I was doing it, I was wondering why it wasn't compiling right, so I knew there had to be a, ";" after it because it stops the while statement or else it'll think to on with it. I got it, thanks anyway.

New problem now. This came up. Everything was working fine for the Person3.java file except it didn't turn into a .class file. Here's the code I put into the terminal:

```

gabe@gabe:~/Desktop$ javac Person3.java
gabe@gabe:~/Desktop$ java Person3
Exception in thread "main" java.lang.NoClassDefFoundError: Person3
Caused by: java.lang.ClassNotFoundException: Person3
    at java.net.URLClassLoader$1.run(URLClassLoader.java:200)
    at java.security.AccessController.doPrivileged(Native Method)
    at java.net.URLClassLoader.findClass(URLClassLoader.java:188)
    at java.lang.ClassLoader.loadClass(ClassLoader.java:306)
    at sun.misc.Launcher$AppClassLoader.loadClass(Launcher.java:276)
    at java.lang.ClassLoader.loadClass(ClassLoader.java:251)
    at java.lang.ClassLoader.loadClassInternal(ClassLoader.java:319)

```

Works fine after javac Person3.java, but it won't make a .class file. Here's the code for the Person3.java:

```

interface Person
{
   public void setName(String n);
   public String getName();
}
 
class Student implements Person
{
   private String stuNum;
   private String name;
 
   public void setStuNum(String sn)
   {
      stuNum = sn;
   }
 
   public String getStuNum()
   {
      return stuNum;
   }
 
   public void setName(String n)
   {
      name = n;
   }
 
   public String getName()
   {
      return name;
   }
}

```

Is the name of the file wrong at all? The code? Thanks in advance.

---

### Post by falconindy on 2009-10-22
Your source file needs to have the same name as your class. Rename the file Student.java.

---

### Post by Lil Josh on 2009-10-22
Oh, yeah. Thanks. Now I have everything ready for what I wanted to do.

---

