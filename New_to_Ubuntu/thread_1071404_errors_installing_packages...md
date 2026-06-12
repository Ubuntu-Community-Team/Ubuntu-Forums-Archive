---
title: "errors installing packages..?"
date: 2009-02-16
forum: New to Ubuntu
---

### Post by cosmicappuccino on 2009-02-16
I'm trying to install libc6-dev, and I can't because

> Error: Dependency is not satisfiable: libc6

But I definitely have libc6 installed - I can see it in Synaptic!

Am I misunderstanding something? Any suggestions on how to get it to work please?

NB I don't have internet at the moment, so am downloading packages from another computer which does have internet, and transferring them on a memory stick to the computer running Ubuntu...

---

### Post by halovivek on 2009-02-16
Upgrade the Synaptic manager.

code
sudo apt-get update 

and try to install again.

---

### Post by RomeReactor on 2009-02-16
Hi. Which version of libc6 do you have installed?
```
aptitude show libc6
```
And which version did you download?

---

### Post by cosmicappuccino on 2009-02-16
> **halovivek said:**
> Upgrade the Synaptic manager.

code
sudo apt-get update 

and try to install again.

Doesn't that require the internet? I tried it, and there are lots of lines of output starting **W: failed to fetch **and then some URL. :/ I don't have an internet connection at the moment so would there be another way?

---

### Post by RomeReactor on 2009-02-16
> **cosmicappuccino said:**
> Doesn't that require the internet? I tried it, and there are lots of lines of output starting **W: failed to fetch **and then some URL. :/ I don't have an internet connection at the moment so would there be another way?

Yes, that needs a connection. Since you don't have internet at the moment, apt/Synaptic can't verify the package version for you.

---

### Post by cosmicappuccino on 2009-02-16
> **RomeReactor said:**
> Hi. Which version of libc6 do you have installed?
```
aptitude show libc6
```
And which version did you download?

The output from that code is:

> Package: libc6
State: installed
Automatically installed: yes
Version: 2.7-10ubuntu4
Priority: required
Section: libs
Maintainer: Ubuntu Core developers <ubuntu-devel-discuss@lists.ubuntu.com>
Uncompressed Size: 10.7M
Depends: libgcc1
Suggests: locales, glibc-doc, libc6-i686
Conflicts: libterm-readline-gnu-perl (< 1.15-2), tzdata (<2007k-1)
Provides: glibc-2.7-1
Description: GNU C Library: Shared libraries
Contains the standard libraries that are used by nearly all programs on the system. This package includes shared versions of the standard C library and the standard math library, as well as many others.

Any insights? Thanks for your replies...

---

### Post by RomeReactor on 2009-02-16
libc6-dev has to be the same version as libc6; You can get the package [here]("http://packages.ubuntu.com/hardy-updates/libc6-dev").

---

### Post by sahabcse on 2009-02-16
Hi

Check your system wheather the packages build-essential and g++ are installed. If is is not means pls try to install those packages. It should solve package installation issues.

---

### Post by cosmicappuccino on 2009-02-16
Thanks for all your helpful replies!

@RomeReactor: That explains a lot - your link worked, thank you!

---

### Post by cosmicappuccino on 2009-02-16
Another similar problem :( ...

I am trying to install g++ (g++_4.2_4.2.4-1ubuntu3), and I am getting a message saying:

> Error: Dependency is not satisfiable: libstdc++6-4.2-dev

So, I downloaded libstdc++6-4.2-dev_4.2.4-1ubuntu3, but when I try to install that, I get a message saying:

> Error: Dependency is not satisfiable: g++-4.2

Are they cross-referenced?! How does that work?

Any thoughts, please?

---

### Post by RomeReactor on 2009-02-16
Even though it doesn't have an internet connection, try opening Synaptic on your Ubuntu machine, search for g++, mark it for installation, and (still in Synaptic) go to 'File->Generate package download script'. Save the file, and move it to the computer with access to the internet. If this other machine has Linux, open a terminal, drop the file there and press ENTER; it should download the packages necessary for installation, including all needed dependencies.

If the other machine has windows, open the file in notepad. You should see something like this:
```
#!/bin/sh
wget -c http://archive.ubuntu.com/ubuntu/pool/main/g/glibc/libc6-dev-i386_2.8~20080505-0ubuntu9_amd64.deb
wget -c http://archive.ubuntu.com/ubuntu/pool/main/g/gcc-4.3/lib32gomp1_4.3.2-1ubuntu12_amd64.deb
```
The links you need begin with **http** and end with **.deb**, so in this example the links are:
```
http://archive.ubuntu.com/ubuntu/pool/main/g/glibc/libc6-dev-i386_2.8~20080505-0ubuntu9_amd64.deb
http://archive.ubuntu.com/ubuntu/pool/main/g/gcc-4.3/lib32gomp1_4.3.2-1ubuntu12_amd64.deb
```
Copy those to Firefox or whichever browser the machine has, and download the packages.

Once you have them, move them to the Ubuntu machine, open Synaptic again, and go to 'File->Add downloaded packages'. You should be able to use Synaptic to install the packages then.

---

### Post by cosmicappuccino on 2009-02-16
Thanks so much for all your help, RomeReactor!

I have actually installed the packages now (but I didn't get around to updating this thread because I found the forums were down!)...

Cheers!

---

