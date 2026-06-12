---
title: "Beginner ubuntu Programmer"
date: 2011-03-17
forum: New to Ubuntu
---

### Post by sangsterthegangster on 2011-03-17
Hello, just installed ubuntu and love it lol. I am a student programmer on windows and I'm trying to figure out how to make linux executibles (NOT MS-DOS) but I cant really seem to find much online. I installed monodevelop and made a small console app, but its compiling it as a MS-DOS .exe file. How do I make a real linux(ubuntu) Application?

---

### Post by wojox on 2011-03-17
You installed:

```
sudo apt-get update; sudo apt-get install build-essential
```

Open a text file:

```
#include <iostream>
using namespace std;

int main() {
 cout << "Hello sangsterthegangster!" << endl;
 return 0;
}

```

Save as hello.cpp

```
g++ hello.cpp -o hello
```

```
./hello
```

---

### Post by sangsterthegangster on 2011-03-17
Well I have played with that before on another computer with ubuntu but its missing some libs from what i recall that are important to what I am messing around with at the moment. MonoDevelops C# has the tools I need and creating the user interface seems to be easier. So is there any way to make real linux apps with mono? And if not does anyone know how most people/Companies make real linux executables for ubuntu?

---

### Post by wojox on 2011-03-17
Oh, I thought you wanted something different. Have you looked at [Gtk#]("http://www.mono-project.com/GtkSharp"). 

I'm not a big fan of C# but I do like it better than Java. :P

---

### Post by fcomstoc on 2011-03-17
> **wojox said:**
> Oh, I thought you wanted something different. Have you looked at [Gtk#]("http://www.mono-project.com/GtkSharp"). 

I'm not a big fan of C# but I do like it better than Java. :P


I am also a programming student I am currently taking Java, C#, and Visual Basic, I love linux but the best tool out there, that I have found anyway,  for C# and VB is visual studio (as much as I hate to admit this.)  :(

I have tried to use monodevelop and it is a painful setup process and the truth is visual studio is better.

---

### Post by wojox on 2011-03-17
> **fcomstoc said:**
> I am also a programming student I am currently taking Java, C#, and Visual Basic, I love linux but the best tool out there, that I have found anyway,  for C# and VB is visual studio (as much as I hate to admit this.)  :(

No need to hate. I've used Visual C/C++, VB, Visual J++. We didn't have Visual Studio when I was in college. Of course their going to be easier under the platform they were developed for. :P

---

### Post by fcomstoc on 2011-03-17
> **wojox said:**
> No need to hate. I've used Visual C/C++, VB, Visual J++. We didn't have Visual Studio when I was in college. Of course their going to be easier under the platform they were developed for. :P

yeah I would agree with you on that one, So, although I love Linux I use windows on virtual box for visual studio 2010. (at least until there is a Linux tool that is comparable).

---

### Post by directhex on 2011-03-17
> **sangsterthegangster said:**
> Hello, just installed ubuntu and love it lol. I am a student programmer on windows and I'm trying to figure out how to make linux executibles (NOT MS-DOS) but I cant really seem to find much online. I installed monodevelop and made a small console app, but its compiling it as a MS-DOS .exe file. How do I make a real linux(ubuntu) Application?

You're not making MS-DOS executables.

For idiotic reasons of their own, when Microsoft designed .NET, they made .NET assemblies re-use the same file extension as MS-DOS executables (.exe), and re-use the header from MS-DOS executables (PE format) - however, the contents of the file are most decidedly NOT MS-DOS executables any more than a .class file or .jar file.

.NET executables, despite the .exe extension and what "file" reports, are true cross-platform bytecode. On your system, gBrainy, Tomboy, and MonoDevelop itself, are made from a selection of .NET assemblies (that is to say, .exe and .dll files). Because the apps use GTK# and are aimed at the Linux desktop, you can't actually tell without looking.

---

### Post by Thund3rstruck on 2011-03-17
> **wojox said:**
> I'm not a big fan of C# but I do like it better than Java. :P

I absolutely love C#, much more so than C/C++, Java, or any other language. Unfortunately mono just can't compare to Win32 .NET dev, especially if you like to develop on the cutting edge (Linq, Entity Framework, WPF/WCF, etc). I just can't recommend .NET/Mono personally on Linux; it's just too lacking and buggy for real enterprise solutions.

---

### Post by directhex on 2011-03-17
> **Thund3rstruck said:**
> I absolutely love C#, much more so than C/C++, Java, or any other language. Unfortunately mono just can't compare to Win32 .NET dev, especially if you like to develop on the cutting edge (Linq, Entity Framework, WPF/WCF, etc). I just can't recommend .NET/Mono personally on Linux; it's just too lacking and buggy for real enterprise solutions.

Your app doesn't suddenly become Enterprise(tm) because you're using WPF.

Plenty of people use Mono in production for Enterprise(tm) tasks. Especially ASP.NET type stuff.

---

### Post by sangsterthegangster on 2011-03-17
> **directhex said:**
> You're not making MS-DOS executables.

For idiotic reasons of their own, when Microsoft designed .NET, they made .NET assemblies re-use the same file extension as MS-DOS executables (.exe), and re-use the header from MS-DOS executables (PE format) - however, the contents of the file are most decidedly NOT MS-DOS executables any more than a .class file or .jar file.

.NET executables, despite the .exe extension and what "file" reports, are true cross-platform bytecode. On your system, gBrainy, Tomboy, and MonoDevelop itself, are made from a selection of .NET assemblies (that is to say, .exe and .dll files). Because the apps use GTK# and are aimed at the Linux desktop, you can't actually tell without looking.


Ok I'm acually using GTK# on mono. So if .NET apps are Cross-Platform how do I make them Runable on linux whithout running them from the terminal or a shellscript file? (like an executable made using g++)

---

### Post by directhex on 2011-03-17
> **sangsterthegangster said:**
> Ok I'm acually using GTK# on mono. So if .NET apps are Cross-Platform how do I make them Runable on linux whithout running them from the terminal or a shellscript file? (like an executable made using g++)

There's nothing wrong with a startup script - an app written in Java or many other languages would need one.

But if you insist, install the binfmt-support package.

```
directhex@dream:/tmp$ gmcs hello.cs 
directhex@dream:/tmp$ ./hello.exe 
Hello, World!
directhex@dream:/tmp$ 

```

---

### Post by Thund3rstruck on 2011-03-17
> **directhex said:**
> Your app doesn't suddenly become Enterprise(tm) because you're using WPF.

No, it becomes enterprise when it runs reliably across the enterprise on all target platforms without crashing or interrupting the other processes executing. No one's saying it can't be done, I'm just suggesting that its not worth the trouble (right tool for the job and .NET is not the right tool in nearly all circumstances in Linux).

---

### Post by sangsterthegangster on 2011-03-17
Ok well I already know how to run .exe files from the terminal like that, but how do people make apps like eclipse that are able to start up with a linux executible an no startup script?

---

### Post by directhex on 2011-03-17
> **sangsterthegangster said:**
> Ok well I already know how to run .exe files from the terminal like that, but how do people make apps like eclipse that are able to start up with a linux executible an no startup script?

Sigh.

mkbundle.

But it's a horrible solution. It is never the right solution.

---

### Post by sangsterthegangster on 2011-03-17
ok ill try it. But just wondering, in your opinion what are the best ways to make ubuntu and Linux applications?

---

### Post by directhex on 2011-03-17
> **sangsterthegangster said:**
> ok ill try it. But just wondering, in your opinion what are the best ways to make ubuntu and Linux applications?

Me? I like C#. I've written apps before with C#, and hacked on others.

---

### Post by sangsterthegangster on 2011-03-17
> **directhex said:**
> Me? I like C#. I've written apps before with C#, and hacked on others.


oh ok, so a shell script would be the best way to run an application made in C#?

---

### Post by directhex on 2011-03-17
> **sangsterthegangster said:**
> oh ok, so a shell script would be the best way to run an application made in C#?

Typically you write a startup script (it can be simple, like gbrainy, or complicated like banshee), and you point to the startup script with a .desktop file.

---

### Post by sangsterthegangster on 2011-03-18
Ok well i made a TCP chat app in mono using the console as the interface in like 5mins. No prob, mono works just as good as visual as far as when ur coding. But I started messing around with gtk and its kinda difficult to use, so is there anyway I can make Linux apps in visual?

---

### Post by directhex on 2011-03-18
> **sangsterthegangster said:**
> Ok well i made a TCP chat app in mono using the console as the interface in like 5mins. No prob, mono works just as good as visual as far as when ur coding. But I started messing around with gtk and its kinda difficult to use, so is there anyway I can make Linux apps in visual?

You can do WinForms apps. Which will look like complete ****. Or there's some GTK# design stuff for Visual Studio, and I have *no* idea what state they're in.

---

### Post by sangsterthegangster on 2011-03-18
Ok lol all my questions have been answered. Thank you everyone who posted.

---

