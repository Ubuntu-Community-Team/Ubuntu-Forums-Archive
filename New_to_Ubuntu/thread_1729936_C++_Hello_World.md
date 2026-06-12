---
title: "C++ Hello World"
date: 2011-04-15
forum: New to Ubuntu
---

### Post by Ali.TK on 2011-04-15
Hey everyone, I'm new to ubuntu (using 10.10)

I've been trying to write a program in c++, and I have installed many programs like Anjuta, KDdevelop, Code::Blocks, but still I can't make a simple Hello World Program.

Please help me out with the easiest way to make run this code.

Any help would be appreciated.

---

### Post by sanderd17 on 2011-04-15
before you use an IDE, I would start with a plain text editor (like gedit).

Just make a .c file and follow the commands like they do it here: [http://www.network-theory.co.uk/docs/gccintro/gccintro_9.html](http://www.network-theory.co.uk/docs/gccintro/gccintro_9.html)

---

### Post by josephmills on 2011-04-15
[http://www.thenewboston.com/?cat=21&pOpen=tutorial](http://www.thenewboston.com/?cat=21&pOpen=tutorial)  hope that this helps

---

### Post by hakermania on 2011-04-15
I would suggest QtCreator (you can find it at the Ubuntu Software Center) which has gcc as backend.
So, run apt-get install g++ as well if needed.
When install give Ctrl+N, choose terminal project, give name etc., double-click on main.cpp and your code goes there normally!```

#include <iostream>

int main(){
std::cout << "Hello world!\n";
return 0;
}
```

---

### Post by vivek.pandey on 2011-04-15
i guess you should try this too
[http://ubuntuforums.org/showthread.php?t=1711697](http://ubuntuforums.org/showthread.php?t=1711697)

---

### Post by seawolf167 on 2011-04-16
Came in to say I really like Geany when coding.

```
sudo apt-get install geany
```You can just follow the hello world instructions then compile/build/run with a click without having to manually use g++ (even though its easy)

Make sure that you don't use Windows specific commands though as a lot of instructions on line are written with Windows users in mind. A good example (of a horrible Windows specific command) is

```
system("pause");
```use

```
cin.get();
```instead

---

### Post by wep940 on 2011-04-17
Geany is in synaptic package manager, and you are always encouraged to use the package manager in place of apt-get when ever possible.  why?  the package manager also installs all of the dependencies for the package you install.  Apt-get doesn't, and sometimes you can end up in a real mess.

---

### Post by seawolf167 on 2011-04-17
> **wep940 said:**
> Geany is in synaptic package manager, and you are always encouraged to use the package manager in place of apt-get when ever possible.  why?  the package manager also installs all of the dependencies for the package you install.  Apt-get doesn't, and sometimes you can end up in a real mess.

This is entirely false - please don't say things like this - they mislead new people and spread wrong information.

*apt-get* most definitely does install dependencies. The Synaptic Package Manager is a GUI front-end tool for *apt*. Even using *aptitude* vs. *apt-get* is essentially irrelevant in the current iteration.

---

### Post by wep940 on 2011-04-18
Well, I don't know what to say.  This is what I was taught on the forum - and hence why the man page for apt-get includes:

       build-dep
           build-dep causes apt-get to install/remove packages in an attempt to satisfy the build dependencies for a  source package.

I have run into this in the past when someone or some post said to download this package and all that happened was that it came up with all kinds of "dependency not met" messages throughout the install.

Is it a problem every time?  No.  Should we be pointing people in the direction of using the package manger? Yes.  It will guarantee the dependencies are met.

---

### Post by seawolf167 on 2011-04-18
I suggest you read the [Synaptic Package Manager ]("https://help.ubuntu.com/community/SynapticHowto")& [APT ]("https://help.ubuntu.com/community/AptGet/Howto")pages to familiarize yourself with how the Package Manager is an APT front-end, and the capabilities of APT.

The quick down-and-dirty differences between APT & Aptitude is that Aptitude is newer and supports dependencies better (especially removal of when uninstalling a package).

Note that you should not use aptitude & apt-get interchangeably as they function a little differently and you could run into problems installing/uninstalling with both (so just stick to one or the other).

---

### Post by sanderd17 on 2011-04-18
> **seawolf167 said:**
> I suggest you read the [Synaptic Package Manager ]("https://help.ubuntu.com/community/SynapticHowto")& [APT ]("https://help.ubuntu.com/community/AptGet/Howto")pages to familiarize yourself with how the Package Manager is an APT front-end, and the capabilities of APT.

The quick down-and-dirty differences between APT & Aptitude is that Aptitude is newer and supports dependencies better (especially removal of when uninstalling a package).

Note that you should not use aptitude & apt-get interchangeably as they function a little differently and you could run into problems installing/uninstalling with both (so just stick to one or the other).

Debian made aptitude the default after various dependancy problems with apt-get. But the guys behind apt-get did great work and solved all problems. This is why apt-get is once again the default in debian and Ubuntu.

So aptitude was newer about a year ago, but now, apt-get is better again. I always believe debian when it comes to stability.

[http://www.debian.org/doc/manuals/debian-reference/ch02.en.html#_literal_apt_get_literal_literal_apt_cache_literal_vs_literal_aptitude_literal](http://www.debian.org/doc/manuals/debian-reference/ch02.en.html#_literal_apt_get_literal_literal_apt_cache_literal_vs_literal_aptitude_literal) (read the note)

@OP: use whaterever you want: apt-get, aptitude, synaptic or the USC. They all work for the basic things and you can even mix them.

---

### Post by seawolf167 on 2011-04-18
Cool, thanks for the link Sanderd17 - though I'm still going to suggest picking one or the other and staying with it :P

---

### Post by wep940 on 2011-04-18
So why have I had problems in the past with downloading a package with apt-get, only to have the install spit out many "Dependency not met" messages, and why does apt-get have the build-dep option?  This is what I have used in the past when I used apt-get.
 
I don't mean to be a butt-head, nor am I arguing.  What I'm trying to find out is what makes my experience with apt-get (these things really did happen to me) different from what you are saying?  Did I omit something?  Did I do something wrong?  I'd like to know so that when I use apt-get in the future I don't mess things up.

---

### Post by wep940 on 2011-04-18
Seriously, I'm not arguing, etc., at all.  I have a TON and then some to learn.  It's just I had this as personal experience a couple of years ago (had a different forum id then, but lost all the information to it when my computer crashed, so I had to set up a new one).  Apt-get gave me tons of the dependency not met messages.  I asked on the forum and they said do apt-get build-dep to pick them up (which it did) and was told to use synaptic package manager instead of apt-get.  That's all I've ever gone by.  So, I really do want to learn, so if you could tell me (1) why this happened to me - did I omit something, etc. and (2) what is the recommended way to install packages by the Ubuntu developers, etc.?
 
I really just want to learn and understand!

---

### Post by wep940 on 2011-04-20
So I guess what you're saying is apt USED to have dependency problems like I had, but it has been updated so that problem has disapeared?  I'm only trying to learn, and I'd prefer not to have to go through what I had to a few years ago with the apt-get and not picking up dependencies (you know, x depends on y, y depends on z, etc.).

---

