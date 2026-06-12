---
title: "tomboy 1.15.1"
date: 2009-06-17
forum: New to Ubuntu
---

### Post by Knacker on 2009-06-17
Hi, 
I'm wondering if anyone has successfully installed the latest development version of tomboy (1.15.1) on Jaunty. 

[http://projects.gnome.org/tomboy/download.html](http://projects.gnome.org/tomboy/download.html)

I tried to build it from the tarball on the website, but got two too many errors with dependencies (i think: initools(?) and gmcs (?)) to continue and gave up. 

Can't find any information on how to make this work or whether it does...the new version has a "preview" of their new web-based sync tool ("Snowy") that looks amazing.

Anybody know anything about this? 

Thanks!

(oops: should be "tomboy 0.15.1")

---

### Post by Ms_Angel_D on 2009-06-17
I don't know about the development version but after some digging I found the latest version in .deb here: [https://launchpad.net/~futurepilot/+archive/ppa](https://launchpad.net/~futurepilot/+archive/ppa)

I'm posting it in case it helps somebody else.

Good Luck with getting the dev version going.

---

### Post by chrisod on 2009-06-17
Did you see these instructions for building Tomboy from source?
[http://live.gnome.org/Tomboy/Developers](http://live.gnome.org/Tomboy/Developers)

---

### Post by chrisod on 2009-06-17
Yeah - I'm looking forward to that too! In the meantime, if you just want to back up your Tomboy notes online you can use grsync and a free Backpack account. It's not the prettiest solution, but it works as a backup and read-only web access to your notes.

---

### Post by meditatingfrog on 2009-06-17
Is the new version of tomboy supposed to be faster?  On my system, tomboy was so slow I decided to just use gedit for making notes.

I have a Toshiba Laptop U305-S7448.  It has a 1.47Ghz Intel DUO core, 2GB of ram, onboard Intel GM965/GL960 graphics, and a 120GB HD.

---

### Post by Knacker on 2009-06-17
thanks for all the replies to this! 

i did look at the instructions for building the development version from source...but i ran into so many errors and missing packages when i tried to even begin (./configure) that I stopped in fear of screwing something up. i guess i was wondering if anyone (with more know-how) had done this successfully and can say it works okay...?

will look into a grsync and backpack account...but really want a native/simple/built-in solution...especially seeing as it's on its way anyhow.  

a .deb for 0.15.1 would be amazing. anyone?

thanks again!

---

### Post by Mark20 on 2009-06-18
I'm also trying to get a new version of Tomboy.  My current version is fine...but I'm bored and I want to get the install to work :)

I first grabbed the tar file here:
[http://download.gnome.org/sources/tomboy/0.14/tomboy-0.14.2.tar.gz]("http://download.gnome.org/sources/tomboy/0.14/tomboy-0.14.2.tar.gz"), obviously in the OP's case version 0.15.1 can be downloaded instead.

I got past all the dependency issues by doing this:
```
sudo apt-get build-dep tomboy
```

I then did a ```
./configure
``` which worked no problem.  I then tried to do a ```
make
``` but it failed with this info:
```
mark@mark-work:~/src/tomboy/tomboy-0.14.2$ make
make  all-recursive
make[1]: Entering directory `/home/mark/src/tomboy/tomboy-0.14.2'
Making all in data
make[2]: Entering directory `/home/mark/src/tomboy/tomboy-0.14.2/data'
Making all in icons
make[3]: Entering directory `/home/mark/src/tomboy/tomboy-0.14.2/data/icons'
make[3]: Nothing to be done for `all'.
make[3]: Leaving directory `/home/mark/src/tomboy/tomboy-0.14.2/data/icons'
make[3]: Entering directory `/home/mark/src/tomboy/tomboy-0.14.2/data'
make[3]: Nothing to be done for `all-am'.
make[3]: Leaving directory `/home/mark/src/tomboy/tomboy-0.14.2/data'
make[2]: Leaving directory `/home/mark/src/tomboy/tomboy-0.14.2/data'
Making all in libtomboy
make[2]: Entering directory `/home/mark/src/tomboy/tomboy-0.14.2/libtomboy'
make[2]: Nothing to be done for `all'.
make[2]: Leaving directory `/home/mark/src/tomboy/tomboy-0.14.2/libtomboy'
Making all in Tomboy
make[2]: Entering directory `/home/mark/src/tomboy/tomboy-0.14.2/Tomboy'
Making all in .
make[3]: Entering directory `/home/mark/src/tomboy/tomboy-0.14.2/Tomboy'
make[3]: *** No rule to make target `panelapplet/*.cs', needed by `Tomboy.exe'.  Stop.
make[3]: Leaving directory `/home/mark/src/tomboy/tomboy-0.14.2/Tomboy'
make[2]: *** [all-recursive] Error 1
make[2]: Leaving directory `/home/mark/src/tomboy/tomboy-0.14.2/Tomboy'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/mark/src/tomboy/tomboy-0.14.2'
make: *** [all] Error 2

```

It seems like make might be trying to build the Windows version since it's crashing when trying to build 'Tomboy.exe'.

I tried the TomBoy Wiki, but it did not help at all.
Anyone know what's going on?

Mark

---

### Post by Mark20 on 2009-06-19
Hi all,

The build issue was a PR which has now been fixed, if you git clone the latest code you will not see this issue.  

```
git clone git://git.gnome.org/tomboy
```

Hope that helps,
Mark

---

### Post by Knacker on 2009-06-20
hrm...when i type:

sudo apt-get build-dep tomboy

i get:

E: You must put some 'source' URIs in your sources.list

am i missing a repository? which one(s)? really want to get this to work. could someone please help me understand what i'm doing wrong? would be grateful for any help. 

thanks again!

---

### Post by Mark20 on 2009-06-20
Hi Knacker,

I've built Tomboy 0.15.3 on my Intel x86-64 machine running Jaunty, and I've uploaded the Tomboy binaries [here]("http://sites.google.com/site/mmwakim/Home/tomboy-jaunty-0.15.3.tar.gz").  

You should be able to solve your repository issues by adding the following to your /etc/apt/sources.list file:
```

deb http://archive.ubuntu.com/ubuntu/ jaunty main restricted universe multiverse
deb-src http://archive.ubuntu.com/ubuntu/ jaunty main restricted universe multiverse
deb http://archive.ubuntu.com/ubuntu/ jaunty-updates main restricted universe multiverse
deb-src http://archive.ubuntu.com/ubuntu/ jaunty-updates main restricted universe multiverse
deb http://security.ubuntu.com/ubuntu jaunty-security main restricted universe multiverse
deb-src http://security.ubuntu.com/ubuntu jaunty-security main restricted universe multiverse

```
I was able to get the dependencies with an unmodified sources.list file so it shouldn't be too difficult to get the repositories sorted out...

Mark

---

