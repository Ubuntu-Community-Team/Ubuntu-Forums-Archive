---
title: "HTML Tidy"
date: 2010-09-11
forum: New to Ubuntu
---

### Post by mörgæs on 2010-09-11
Hi, do anybody know where to download Tidy? 

I am searching for Tidy as one binary file that I can use where I am (and upload to a server), not an installation dependent on libraries.

---

### Post by llamabr on 2010-09-11
[https://launchpad.net/ubuntu/maverick/+source/tidy](https://launchpad.net/ubuntu/maverick/+source/tidy)

---

### Post by mörgæs on 2010-09-11
Thanks, but this seems to give me the option of compiling tidy and libtidy into the system, like if I used Synaptic. 

I want something which compares to a stand-alone .exe-file in Windows.

---

### Post by llamabr on 2010-09-11
This is the source code.  I'm not sure exactly what you're asking for, then.

How do you want to use it?  Over a server?  It requires a local installation.  Are you saying you want to put it, say, on a thumb drive, and run it from there on any machine you want?  It would still require all dependencies be satisfied.  

But in that case, what you want is the source, which you'd compile right in your thumb drive.

---

### Post by Chesamo on 2010-09-11
Installations of any program in Ubuntu are dependent on libraries. What you're looking for doesn't exist.

---

### Post by mörgæs on 2010-09-12
I was hoping for something that I could just put in /home and run from there. A binary that will only depend on the libraries in a standard Ubuntu.

I am working on a project that everybody should be able to use with normal user rights, no matter if the administrator has installed additional libraries or not.

If you tale a look at 
[http://tidy.sourceforge.net/#binaries](http://tidy.sourceforge.net/#binaries)
you will see a similar binary for MkLinux, but I didn't manage to find anything for Ubuntu.

---

### Post by JohnHeikkila on 2010-09-12
[http://packages.debian.org/lenny/tidy](http://packages.debian.org/lenny/tidy)
[http://packages.debian.org/lenny/libtidy-0.99-0](http://packages.debian.org/lenny/libtidy-0.99-0)
[http://packages.debian.org/lenny/libc6.1](http://packages.debian.org/lenny/libc6.1)
[http://packages.debian.org/lenny/libgcc1](http://packages.debian.org/lenny/libgcc1)
[http://packages.debian.org/lenny/gcc-4.3-base](http://packages.debian.org/lenny/gcc-4.3-base)


As long as I'm concerned, those are the required packages you need for Tidy and it's dependencies.

---

