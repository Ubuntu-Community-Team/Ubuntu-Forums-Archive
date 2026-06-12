---
title: "tar.gz"
date: 2011-05-02
forum: New to Ubuntu
---

### Post by Kaladin72 on 2011-05-02
What IS tar.gz? Is it like a .rar or zipped file on Windows?

---

### Post by cobolt01 on 2011-05-02
Yes a tar.gz file is an archive like .zip

If you're trying to install a program you should try the Ubuntu software center or download the .deb file instead of compiling from source, it's a lot easier. (source files are normally downloaded in .tar.gz format)

Hope that helps.

---

### Post by Kaladin72 on 2011-05-02
Ahh, yes it is... But how do I install programs?? I cannot even run .exes. I'm trying to download Winrar for my gzip needs and cannot do it. What is up with .exes?

---

### Post by Carborundum on 2011-05-02
.exe-files are executables in Windows. Linux does not use them. Gzip archives are supported by default by the Archive Manager included in Ubuntu, so there should be no need to install additional software.

---

### Post by Kaladin72 on 2011-05-02
Ahh, I see now... Gah, this is all so crazy. I've used Windows all my life and I want to try something new and this stuff is definitely gonna need some getting used to.

---

### Post by cobolt01 on 2011-05-02
Ubuntu does not natively support windows programs. If you want to use windows programs you will have to install wine first.
In the terminal type:
```
sudo apt-get install wine unrar gzip
```

What version of Ubuntu do you have installed?

---

### Post by Carborundum on 2011-05-02
> **Kaladin72 said:**
> Ahh, I see now... Gah, this is all so crazy.  I've used Windows all my life and I want to try something new and this  stuff is definitely gonna need some getting used to.
Yeah, I was in the same situation a few years back. Hang in there, it will only get easier from here. :)

---

### Post by cobolt01 on 2011-05-02
Ah didn't see your post there Carborundum. Sorry for repeating.
Stick with it Kaladin72 you're going to love Ubuntu!

---

### Post by Kaladin72 on 2011-05-02
Is Crossover the same thing as Wine?

---

### Post by cobolt01 on 2011-05-02
Its based on wine

---

### Post by kaldor on 2011-05-02
I hope you're not trying to use Crossover/WINE just so you can run .exes and such on Linux all the time :)

I really recommend using Linux software unless you absolutely need a Windows program.

---

### Post by K_45 on 2011-05-02
> **kaldor said:**
> I hope you're not trying to use Crossover/WINE just so you can run .exes and such on Linux all the time :)

I really recommend using Linux software unless you absolutely need a Windows program.

I'd agree, and I'd also add that you should carefully make sure the software you choose to install comes from the right repository or PPA.

---

### Post by Hatsune Miku on 2011-05-02
> **Kaladin72 said:**
> Ahh, yes it is... But how do I install programs?? I cannot even run .exes. I'm trying to download Winrar for my gzip needs and cannot do it. What is up with .exes?

**_To give you a little more understanding of the Linux system vs a Windows system._**

Windows uses a .exe on any file that executes code; Linux does not it will just say the name of the file (Ex. Program). To see if it executes you need to check the permission on it (Google FileSystem permissions to understand)

Linux has compiled/script executables, Compiled is a program that is made from a compiled programing language (Like C, C++). A script executable is a interpreted programming language, it reads the file for command and executes them; Perl, Python, and UNIX shell are the most commonly used.

Linux compiled format is called an ELF compared to windows as a exe

So to put it simply Linux/UNIX system can turn/run anything into a program with the execution permission (Assuming you have what you need to run the file).

Hoped this cleared away some DERP for you.

---

