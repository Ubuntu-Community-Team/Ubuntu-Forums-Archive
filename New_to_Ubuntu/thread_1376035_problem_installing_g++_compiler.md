---
title: "problem installing g++ compiler"
date: 2010-01-08
forum: New to Ubuntu
---

### Post by glahr32 on 2010-01-08
In a nutshell, my reason for wanting ubuntu is to be able to write fairly simple c++ programs that I can carry around with me on my usb to use anywhere.
 
**What I have done that works:**
 
I created a live usb of ubuntu 9.10 and from that I was able to install it onto my sandisk 8gb usb (formatted with the u3 software removed). Both the live usb and my 'installed' sandisk work fine and I can boot from either.
 
**The issue:** 
 
From the live usb, I try to compile a program and get this message.
 
*ubuntu@ubuntu:~/Documents$ g++ someprogram.cc*
*The program 'g++' can be found in the following packages:*
** g++*
** pentium-builder (You will have to enable component called 'universe')*
*Try: sudo apt-get install <selected package>*
*g++: command not found*
 
So I type in the command "sudo apt-get install g++", it loads the compiler, and everything works fine. I can compile programs and run them without issue.
 
BUT, when I try the same thing from my 'installed' sandisk usb, it doesn't seem to want to load the compiler. Here is the message I get:
 
*garrett@garrett-laptop:~/Documents$ g++ someprogram.cc*
*The program 'g++' can be found in the following packages:*
** g++*
** pentium-builder*
*Try: sudo apt-get install <selected package>*
*g++: command not found*
 
***this is the same message as before, so I type in the same command and this is what i get***
 
*garrett@garrett-laptop:~/Documents$ sudo apt-get install g++*
*[sudo] password for garrett: *
*Reading package lists... Done*
*Building dependency tree *
*Reading state information... Done*
*E: Couldn't find package g*
 
 
So, does anyone know why it works to load the compiler on the live usb but not on the 'installed' usb? Hopefully it isn't too technical of a fix because I am fairly new to this whole linux thing.
 
The reason I want to work from the 'installed' usb and not just the live usb is because I want to be able to save the programs on there. That way if I want to run it on a friend's computer, I only need the one usb and there I have ubuntu and my programs. Thanks in advance for the help!!

---

### Post by DGortze380 on 2010-01-08
the package you want is:

build-essential

---

### Post by glahr32 on 2010-01-08
Ok, I got it to work using that.  Thanks! :)

---

