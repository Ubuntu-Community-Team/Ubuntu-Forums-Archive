---
title: "Virtual box installation"
date: 2009-01-27
forum: New to Ubuntu
---

### Post by deondebbie on 2009-01-27
Hi All

Im having major problems installing virtualbox-2.1_2.1.2-41885_ubuntu_intrepid_i138.deb,
Im being honest to say that i dont know what commands or what to do to make or compile and extract the files,alot of help will be great,Im using Ubuntu 8.1 intrepid,also i dont have a internet connection for linux,because i cant get my iburst wireless desktop modem to work,The error is 

Error Dependency is not satisfiable:Libqt4-core

Thanxs

---

### Post by halovivek on 2009-01-27
what is the error message you get while installing the program, could you please post it?

---

### Post by Drakkor on 2009-01-27
Why don't you just get the .deb ?
A new version of VirtualBox has been released! Version 2.1.2 is available at virtualbox.org.
You can download this version from this direct link:
[http://download.virtualbox.org/virtualbox/2.1.2/virtualbox-2.1_2.1.2-41885_Ubuntu_intrepid_i386.deb](http://download.virtualbox.org/virtualbox/2.1.2/virtualbox-2.1_2.1.2-41885_Ubuntu_intrepid_i386.deb)

You just  download it to your desktop,and double-click it for the installer

---

### Post by Tek-E on 2009-01-27
> **deondebbie said:**
> Hi All

Im having major problems installing virtualbox-2.1_2.1.2-41885_ubuntu_intrepid_i138.deb,
Im being honest to say that i dont know what commands or what to do to make or compile and extract the files,alot of help will be great,Im using Ubuntu 8.1 intrepid,also i dont have a internet connection for linux,because i cant get my iburst wireless desktop modem to work

Thanxs

Well...If I read what your message said correctly all you should have to do is type.
```

cd /path/to/deb/file/
dpkg -i virtualbox-2.1_2.1.2-41885_ubuntu_intrepid_i138.deb

```
And that should be it....
Or did I read your message incorrectly?

---

### Post by Tek-E on 2009-01-27
Didnt he say that he already has the .deb file?

---

### Post by GirionSoft on 2009-01-27
Add the repo so you can get updates.
deb [http://download.virtualbox.org/virtualbox/debian](http://download.virtualbox.org/virtualbox/debian) intrepid non-free
[http://download.virtualbox.org/virtualbox/debian/sun_vbox.asc](http://download.virtualbox.org/virtualbox/debian/sun_vbox.asc)

If you just install the package next time you do a kernel upgrade vbox will break and you will be right back where you started.

---

### Post by Drakkor on 2009-01-27
Yeah, I guess he does,but you don't make or compile a deb fie,you just open it, and there's the package installer . :p

---

### Post by GirionSoft on 2009-01-27
oops missed the no internet connection part

---

### Post by Tek-E on 2009-01-27
True.  oddly though......I never even thought to use the package installer :P

I have alwayse used dpkg......Brain Fart!

---

### Post by deondebbie on 2009-01-27
The error is as follows

Error Dependency is not satisfiable:Libqt4-core

---

### Post by boof1988 on 2009-01-27
> **deondebbie said:**
> The error is as follows

Error Dependency is not satisfiable:Libqt4-core


*Libqt4-core* is in the repositories (I just looked).  But I don't know how to get it without an internet connection on your computer.  Maybe use synaptic (or other) to generate the download script and then run the download script on a machine that has an internet connection.

I have attached a screen shot showing where the "generate download script" menu item is located (I have shown Synaptic Package Manager, but there are other methods to generate the script).  Of course you will need to select (if you do it this way) the *Libqt4-core* package by clicking on the check-box (mine is already installed, that's why it is green).

HTH some and maybe someone else can give more help then I can.

---

### Post by Tek-E on 2009-01-27
Sadly with ubuntu being an internet based os, if your installing from a .deb you tend to run into alot of problems.  Try finding all the dependencys you need first. Install them. And then try to install vitrual box.

---

