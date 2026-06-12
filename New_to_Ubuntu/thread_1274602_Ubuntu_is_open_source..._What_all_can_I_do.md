---
title: "Ubuntu is open source... What all can I do?"
date: 2009-09-24
forum: New to Ubuntu
---

### Post by Mimz on 2009-09-24
Okay so I know that ubuntu is an open source operating system, but what exactly can I modify?
Can I change how much battery the computer uses?
Can I change icons?
Can I change Strings?
Can I change the overall look of my desktop?

Just what exactly is there to do? And where can I go to find out more about this wonderful operating system?

P.S To the guys that made the Ubuntu forums... I love the Eric Clapton looking smiley :guitar:

---

### Post by earthpigg on 2009-09-24
to all questions, yes.

> And where can I go to find out more about this wonderful operating system?

ubuntuforums.org is a great place to start.

this website is made by one of our ubuntuforums.org community members, and is outstanding:

[http://www.psychocats.net/ubuntu/](http://www.psychocats.net/ubuntu/)

---

### Post by Mimz on 2009-09-24
Sweet dude. Thanks for the link but I meant like what folders can I go rummaging through to learn more about ubuntu. Like in Windows, I would go through the C:\ drive and look through System32 files etc. What is ubuntu's equivalent of the System32 folder?

But still thanks for your answer I'll check that link out

---

### Post by stlsaint on 2009-09-24
there not the same but what your looking for my be your filesystem folders...there not a all in one folder setup and its not recommended to go "rumaging" :) thru them so be careful.

---

### Post by scorp123 on 2009-09-24
> **Mimz said:**
>  Just what exactly is there to do?  Enjoy and use it.

The rest will come auto-magically. If you force and rush things you might be frustrated soon. Just take it easy. Like that guitar player :D

To really make use of Ubuntu's (or any other GNU/Linux distribution's) open source nature you'd have to be fluent in C and C++

Most of the kernel and the GNU tools is written in C. Most of the GUI stuff is either written in C or in C++. Some programs are written in other languages such as Python ...

If all that sounds Greek and Chinese to you then I fear you will have to learn those programming languages first. I use Linux since 1996 and I never bothered to learn them. I learned shell scripting though. Different than the "cmd" shell in Windows which is dumb and stupid like a brick the Linux command line is extremely powerful and can do tons of things. So if learning programming languages such as C and C++ is not your thing then you won't be able to change so many things but then again with shell scripting you can still force your computer to do whatever you want.

The example you mentioned ... 

"Can I change how much battery the computer uses?" ==> easily. You don't need to be a C programmer to achieve that.

"Can I change icons?" ==> point and click. Done. No programming skills needed here.

"Can I change Strings?" ==> That's a bit more complicated. Some programs place their strings in external config files, so in those cases it will be enough to edit that file. Voila, done. Other programs may require you to download their C source code and then edit the file, and then re-compile it again.

"Can I change the overall look of my desktop?" ==> Point and click. No extra programming skills needed for that. There are tons of themes and wallpapers out there.

GNOME themes:
[http://www.gnome-look.org/](http://www.gnome-look.org/)

Wallpapers:
[http://interfacelift.com/wallpaper_beta/downloads/date/any](http://interfacelift.com/wallpaper_beta/downloads/date/any)
[http://www.caedes.net](http://www.caedes.net)


Have fun. But remember: Linux is not Windows! ;)
[http://linux.oneandoneis2.org/LNW.htm](http://linux.oneandoneis2.org/LNW.htm)

---

### Post by Mimz on 2009-09-24
Yeah I found the Filesystem folder... but I cant view any of the files with gedit, what program can I use to view these files?

Also I didnt see scorps post... I'm fairly good with Java, I know basic C and basic C++ so I'll definantly look into more C++ and C programming so I can modify stuff but thanks for the links dude.

---

### Post by scorp123 on 2009-09-24
> **Mimz said:**
> Yeah I found the Filesystem folder... but I cant view any of the files with gedit, what program can I use to view these files? Before you delete something important I'd say you better get familiar with the filesystem layout first, OK?

Here a posting in response to a user who was confused by Linux's filesystem layout:
[http://ubuntuforums.org/showpost.php?p=4897193&postcount=19](http://ubuntuforums.org/showpost.php?p=4897193&postcount=19)

And last but not least: Wikipedia.
[http://en.wikipedia.org/wiki/Filesystem_Hierarchy_Standard](http://en.wikipedia.org/wiki/Filesystem_Hierarchy_Standard)

---

### Post by scragar on 2009-09-24
> **Mimz said:**
> Yeah I found the Filesystem folder... but I cant view any of the files with gedit, what program can I use to view these files?I'm assuming those files are binaries, in which case looking at them is useless unless you understand assembly.
> **Mimz said:**
> Also I didnt see scorps post... I'm fairly good with Java, I know basic C and basic C++ so I'll definantly look into more C++ and C programming so I can modify stuff but thanks for the links dude.

You can download the source for almost anything: [http://packages.ubuntu.com](http://packages.ubuntu.com) just type the package name, and choose source on the right hand side, much easier than searching on google or something, provided you know the package name anyway(lot's of things come under core-utils).

---

### Post by jerrrys on 2009-09-24
here's a good pdf

[http://www.ubuntupocketguide.com/index_main.html](http://www.ubuntupocketguide.com/index_main.html)

---

### Post by scorp123 on 2009-09-24
> **scragar said:**
>  You can download the source for almost anything: [http://packages.ubuntu.com](http://packages.ubuntu.com) just type the package name, and choose source on the right hand side  What's wrong with using apt? :D
```
sudo apt-get source nameOfpackage
```

---

### Post by bboston7 on 2009-09-24
You can change anything you want, but you probably want to learn some C.

---

### Post by Mimz on 2009-09-24
Well actually I'm learning binary and hexidecimal in my computer class ;)

But I thanks to both of you for answering my questions. Ubuntu is a lot different from Windows... 
But I do have one more question,

Is Ubuntu virus-free?

---

### Post by scragar on 2009-09-24
> **scorp123 said:**
> What's wrong with using apt? :D
```
sudo apt-get source nameOfpackage
```

Apt doesn't tell you where it's downloading the source to meaning you need to search for it afterwards or do some searching anyway.


> **Mimz said:**
> Is Ubuntu virus-free?
Pretty much, it's almost impossible to get a virus or malware unless you actually search for it.

---

### Post by jakupl on 2009-09-24
> **Mimz said:**
> Well actually I'm learning binary and hexidecimal in my computer class ;)

But I thanks to both of you for answering my questions. Ubuntu is a lot different from Windows... 
But I do have one more question,

Is Ubuntu virus-free?

There have been made some proof-of-concept viruses, but they will never survive in the wild.
So far, yes.

---

### Post by blur xc on 2009-09-24
As far as the appearance of your desktop goes- [http://ubuntuforums.org/showthread.php?t=1254939](http://ubuntuforums.org/showthread.php?t=1254939)

You can make it look just about like anything you want.

BM

---

### Post by earthpigg on 2009-09-24
if you want to rummage without risking breaking your system, you can play around with the hidden files and folders in your home folder.

if, in your rummaging, you break something.... go ahead and delete the file/folder you changed. next time you start that program, it will just start with default settings.

---

### Post by Mimz on 2009-09-24
Thanks but really all I want to do is just view the source code..

---

### Post by scorp123 on 2009-09-24
> **Mimz said:**
>  Is Ubuntu virus-free? What's a virus? :D

---

### Post by juancarlospaco on 2009-09-24
***The limit is your imagination...***

---

### Post by bruno9779 on 2009-09-24
> **earthpigg said:**
> if you want to rummage without risking breaking your system, you can play around with the hidden files and folders in your home folder.

if, in your rummaging, you break something.... go ahead and delete the file/folder you changed. next time you start that program, it will just start with default settings.

It doesn't apply to stuff like wine, where in ~/.wine i have my win games installed

---

### Post by bruno9779 on 2009-09-24
Everything bad that will happen to your ubuntu install, will be your fault.

No viruses to blame I am afraid.... :)


And if you want to see some code, there is plenty of FOSS code to download, just google for app name + source, or go to sites like [sourceforge]("http://sourceforge.net/")  where you can download the latest versions

---

### Post by scorp123 on 2009-09-24
> **scragar said:**
> Apt doesn't tell you where it's downloading the source to. Usually right into your home folder or where ever you just happened to be when you execute that command.


```
> sudo apt-get source htop

Reading package lists... Done
Building dependency tree       
Reading state information... Done
Need to get 425kB of source archives.
Get: 1 http://ch.archive.ubuntu.com jaunty/universe htop 0.8.1-4ubuntu1 (dsc) [1149B]
Get: 2 http://ch.archive.ubuntu.com jaunty/universe htop 0.8.1-4ubuntu1 (tar) [415kB]
Get: 3 http://ch.archive.ubuntu.com jaunty/universe htop 0.8.1-4ubuntu1 (diff) [9039B]
Fetched 425kB in 0s (673kB/s)
dpkg-source: extracting htop in htop-0.8.1
dpkg-source: info: unpacking htop_0.8.1.orig.tar.gz
dpkg-source: info: applying htop_0.8.1-4ubuntu1.diff.gz


> pwd
/home/sysadm

> ls -al | grep htop
drwxr-xr-x   5 root root  4096 2009-09-25 01:33 htop-0.8.1
-rw-r--r--   1 root root       9039 2009-03-09 22:05 htop_0.8.1-4ubuntu1.diff.gz
-rw-r--r--   1 root root       1149 2009-03-09 22:05 htop_0.8.1-4ubuntu1.dsc
-rw-r--r--   1 root root     414870 2008-11-14 09:04 htop_0.8.1.orig.tar.gz
```

Voila, the sources of the "htop" program right in my $HOME ...


EDIT:

The Debian manual explains it too. You don't even need "root" powers to get the sources:
[http://www.debian.org/doc/manuals/apt-howto/ch-sourcehandling.en.html](http://www.debian.org/doc/manuals/apt-howto/ch-sourcehandling.en.html)
.
.
.

---

### Post by Mimz on 2009-09-24
cool dude I just really wanna know more about the operating system that I use. I'm a java programmer and I'm getting more into C++ before I go to college so yeah is ubuntu good for programming?

---

### Post by Diabolis on 2009-09-24
Ubuntu is GREAT for programming, most of the tools that you'll need are already in the repository. (java, ant, junit, svn, cvs, g++, mono, etc.) Unless you are working with visualbasic :biggrin:

As everyone here has answered, you can do whatever you want with the OS. I strongly recommend you to not start looking around the "system files" and changing files here and there.

Ask yourself what do you really need to change and come back to the forums for help.

In my case I don't like that much Gnome, so sometimes I use Fluxbox which is configured entirely through the files stored in **~/.fluxbox**. I hope that in the near future I'll try **Awesome**.
> It is primarly targeted at power users, developers and any people dealing with every day computing tasks and who want to have fine-grained control on theirs graphical environment.

You can even make your Linux box look as if it were running Vista :lolflag:

---

### Post by scorp123 on 2009-09-25
> **Diabolis said:**
>  You can even make your Linux box look as if it were running Vista :lolflag: Why would you want to do *that* ??? #-o

I don't know about you but really the last thing I want on my desktop is anything that looks like it has been produced by that stupid company in Redmond.

---

### Post by directhex on 2009-09-25
> **Diabolis said:**
> Ubuntu is GREAT for programming, most of the tools that you'll need are already in the repository. (java, ant, junit, svn, cvs, g++, mono, etc.) Unless you are working with visualbasic :biggrin:

[mono-vbnc](apt:mono-vbnc)

---

### Post by Peterfc on 2009-09-25
Hi Guys

Forgive me for jumping in. 

There is one change i would like to make and it's how do i move the bar that has Application, Places, System from the top of my screen to the bottom? i would like everything on the bottom of the screen.

Peter

---

### Post by scragar on 2009-09-25
> **Peterfc said:**
> Hi Guys

Forgive me for jumping in. 

There is one change i would like to make and it's how do i move the bar that has Application, Places, System from the top of my screen to the bottom? i would like everything on the bottom of the screen.

Peter

Right click, unlock, drag and drop, right click again to lock it back in place.

---

