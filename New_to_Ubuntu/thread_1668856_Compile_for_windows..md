---
title: "Compile for windows."
date: 2011-01-16
forum: New to Ubuntu
---

### Post by guilleme on 2011-01-16
Hello everyone, Well, I have a question, (if I hadn't, I wouldn't be here...), so, the thing is that I am somewhat a programmer, (or at least a wannabi), but, I'm not sure if it is possible to compile a C program for running on windows with ubuntu, is there a way to make ".exe" binaries with, say, codeblocks as IDE and GCC? Is there any other way to get exe's?
Thanks very much to everyone!!!

---

### Post by NightwishFan on 2011-01-16
Not sure if this is what you need but you might look at one of these two projects. Someone better qualified can help you if this isn’t what you need.
[http://en.wikipedia.org/wiki/Mono_programming_language](http://en.wikipedia.org/wiki/Mono_programming_language)
[http://en.wikipedia.org/wiki/Wine_software](http://en.wikipedia.org/wiki/Wine_software)

---

### Post by 123456789123456789123456 on 2011-01-16
recompiling a program can be difficult since the coding for linux and windows are very different.  The easiest way to run pc programs (exe) files is to use either wine or crossover(or both), to emulate windows to run the programs.

---

### Post by srs5694 on 2011-01-16
> **guilleme said:**
> Hello everyone, Well, I have a question, (if I hadn't, I wouldn't be here...), so, the thing is that I am somewhat a programmer, (or at least a wannabi), but, I'm not sure if it is possible to compile a C program for running on windows with ubuntu, is there a way to make ".exe" binaries with, say, codeblocks as IDE and GCC? Is there any other way to get exe's?

What you're describing is known as a cross-compiler. The one I know of to do this under Linux is called [MinGW.](http://www.mingw.org) (There's also a native Windows version.) It works fine, in my limited experience. I sometimes use it to compile the Windows version of my [GPT fdisk (gdisk)](http://www.rodsbooks.com/gdisk/) program.

Note that to test the binaries you create you'll need (in decreasing order of desirability) a separate Windows computer, Windows running in a virtual machine, or [WINE](http://www.winehq.org) (a set of Windows compatibility libraries and tools for Linux).

Another option is to run a Windows-native compiler, such as Microsoft Visual C, in a virtual machine or under WINE. According to the WINE application database, [Visual C works well under WINE;](http://appdb.winehq.org/objectManager.php?sClass=application&iId=53) however, I've not tested it myself, so I can't comment from personal experience.

---

### Post by HermanAB on 2011-01-17
Howdy,

This is what virtual machines are for.

Create a Virtualbox VM with Windows and compile your program with one of the free compilers, for example Pelles or LCC:
[http://www.smorgasbordet.com/pellesc/](http://www.smorgasbordet.com/pellesc/)

---

### Post by wep940 on 2011-01-17
+1 on Mingw in Windows.  I have some apps written in C, using GTK for the GUI.  Just a couple of ifdef's solved any mismatch between Linux and Windows.  I use normal gcc to compile in Linux.  In Windows, I have Mingw and GTK For Windows installed.  Via Mingw, it's the same gcc statement to compile, with pointers for the GTK libs.  So, you can develop SOURCE in C which can compile on Windows or Linux.  To actually create a Windows executable in Linux would involve a cross-compiler and I'm not familiar with any for Linux.

---

### Post by guilleme on 2011-01-17
Thanks everyone! now I know that what I needed was a cross-compiler. Thanks to everyone who sent an answer to this, were all very useful, and that's it, I'm really grateful to everybody who sent this in for helping, happy compiling:).

---

### Post by wep940 on 2011-01-17
Keep Mingw in mind - you can make it compile Windows apps:
 
[http://silmor.de/39](http://silmor.de/39)
 
In addition, if you do a web search with "linux to windows cross compiler" you'll get a lot of information.

---

