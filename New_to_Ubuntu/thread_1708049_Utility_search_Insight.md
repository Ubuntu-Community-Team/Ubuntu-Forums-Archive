---
title: "Utility search: Insight"
date: 2011-03-16
forum: New to Ubuntu
---

### Post by tekal on 2011-03-16
Hey there,
I'm reading a book on programming and i was advised to start "insight" from the Terminal, but it doesn't seem to be installed. Neither the Ubuntu Software Center nor the Terminal prompt apt-get know this program. Google search is useless, it thinks that, i'm searching for INSIGHTS into Ubuntu! Where can i find this program?

P.S.: I found an installation package for Ubuntu here. [http://packages.ubuntu.com/karmic/i386/insight/download](http://packages.ubuntu.com/karmic/i386/insight/download)

But after installation (no errors) it wont start properly from the Terminal. This error occurs:

------tekal@ubuntu:~/asmwork/asmsbs3e/chapter5$ insight eatsyscall
insight-bin: error while loading shared libraries: libitcl3.2.so.1: cannot open shared object file: No such file or directory------

Need instructions on how to get it working!

---

### Post by ikt on 2011-03-16
> **tekal said:**
> Need instructions on how to get it working!

The problem is that the program hasn't been updated in a few years now, and appears to be dead and after some research it seems here is why:

It looks like insight isn't special;

> Insight is a graphical user interface to GDB, the GNU Debugger

[http://sources.redhat.com/insight/aboutus.php](http://sources.redhat.com/insight/aboutus.php)

> Here's a partial list of front ends using GDB. If you know of others, please add a link.

Using GDB/MI:

BVRDE
CGDB
Eclipse CDT
KDevelop
NetBeans
Nemiver
WinGDB
CodeLite
Qt Creator
GNU Emacs
SlickEdit

[http://sourceware.org/gdb/wiki/GDB%20Front%20Ends](http://sourceware.org/gdb/wiki/GDB%20Front%20Ends)

A few of those I know work on ubuntu natively and are in the ubuntu software centre right now :)

---

### Post by tekal on 2011-03-16
> **ikt said:**
> The problem is that the program hasn't been updated in a few years now, and appears to be dead and after some research it seems here is why:

It looks like insight isn't special;



[http://sources.redhat.com/insight/aboutus.php](http://sources.redhat.com/insight/aboutus.php)



[http://sourceware.org/gdb/wiki/GDB%20Front%20Ends](http://sourceware.org/gdb/wiki/GDB%20Front%20Ends)

A few of those I know work on ubuntu natively and are in the ubuntu software centre right now :)

Thanks, im going to de-install it again, and will try to follow the books central theme on debugging code with the help of some of these listed tools!

---

