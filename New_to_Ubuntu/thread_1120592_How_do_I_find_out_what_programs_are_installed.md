---
title: "How do I find out what programs are installed?"
date: 2009-04-09
forum: New to Ubuntu
---

### Post by frOOgz on 2009-04-09
Hello,

I would like to find out what programs I have installed on ubuntu 8.10.  I can look through the applications menu to find out the ones with a GUI.  All programs have been installed via sudo apt-get install or the package manager.

Is there an easy way to find out the others like LAMP stack, cups-pdf. Which directories should I look in.

I have been happily using a wubi install for a couple of months.  I would like to install 9.04 on a partition on my new machine when it arrives.  Hence the need to find all the programs that I have installed.

---

### Post by kiridude on 2009-04-09
Through the GUI you can go to Administration - Synaptic package manager. Once in there, you can scroll down and all the programs marked with green are installed.

---

### Post by Jakey_TheSnake on 2009-04-09
Or you can open Synaptic, press the "Status" tab in the bottom left, then select "Installed". 

Also, why would you need to check your packages? You can upgrade from Intrepid to Jaunty, without having to reinstall and lose your settings etc.

edit: System > Administration > Synaptic Package Manager

---

### Post by stumbleUpon on 2009-04-09
dpkg --get-selections > installed-software

dumps the list of all the installed programs into the file 'installed-software'

---

### Post by frOOgz on 2009-04-09
Thanks for the tips.

I like dpkg --get-selections > installed-software

---

### Post by darksideforge on 2009-04-17
Ok, so here's a silly question: how do I "run" dpkg? I understand that it's part of the APT system; does that mean that running dpkg is the same as running sudo/apt/get/install ?

Specifically, I'd like to view a list of installed software so that I can either print it out and compare installed programs on two different computers, or so that I might be able to save the list, put it in an editor and run diff comparing two system's installed software.

Is that making sense to anyone?

Two Ubuntu computers: laptop at home, desktop at work. If I dl something and install it at home on the lappy and then go to work, how do I look at a printed list of my installed software so I can cross check it with the desktop at work?

Edit: I should probably say that I just need the list...I don't need to manipulate the programs in any way...although it would be nice to be able to copy the .deb file and put it on a flash and then take it into work and install it using gdebi.

---

### Post by HeirPixel on 2009-04-17
> **Jakey_TheSnake said:**
> Also, why would you need to check your packages? You can upgrade from Intrepid to Jaunty, without having to reinstall and lose your settings etc.

It seems our friend is more interested in a Jaunty partition on a *new* system. In this case I've often just used **Applications > Add/Remove** with **Show > Installed Applications Only** for an easy reference if I don't want to see all of my libraries/codecs/etc. Just personal preference really.

---

### Post by cariboo on 2009-04-17
> I like dpkg --get-selections > installed-software

The above command has to be run as root eg:

```
sudo dpkg --get-selections > installed
```

what the above command does is lists the installed packages and pipes them to a file called installed in your home directory. You should be able to open it with the text editor and peruse it at your leisure.

Jim

---

### Post by darksideforge on 2009-04-18
> **cariboo907 said:**
> The above command has to be run as root eg:

```
sudo dpkg --get-selections > installed
```

what the above command does is lists the installed packages and pipes them to a file called installed in your home directory. You should be able to open it with the text editor and peruse it at your leisure.

Jim

Jim, You are THE MAN!!!!!!!!!!!!!!!!!:popcorn::KS:popcorn:

---

### Post by darksideforge on 2009-08-19
> **cariboo907 said:**
> The above command has to be run as root eg:

```
sudo dpkg --get-selections > installed
```

what the above command does is lists the installed packages and pipes them to a file called installed in your home directory. You should be able to open it with the text editor and peruse it at your leisure.

Jim


Jim,
I keep coming back to this post over and over again and can't thank you enough for sharing almost a year ago. I wonder...with all of the programs I have installed in my 9.04DTE, is there a way to make more of them show up in a/my GUI menu? If I'm not seeing them, does that mean that they don't have a GUI front-end and are required to be run from the console, or is it possible that some of the things I have downloaded require support files from the KDE-DTE maybe?  Every once in a while I'll run across a program, download it, back it up with rsync or .tar it and then I'll go back at a later date & time and install it...and then never end up using it because I don't ever see it in my drop-down menus. I realize that this is the epitome of laziness and p-poor personal computing/resource wasting, but do you have any suggestions on it? I'm currently running 9.04 and am trying to make it last until it's time to ixnay it and go to 9.10.
Thanks,
Clint

---

### Post by philinux on 2009-08-19
Yes. Each time you install an app with no gui make sure you create a menu item to launch it. Simple ;)

---

### Post by isee on 2009-08-19
Well, I have 1608 packages installed, very few of which are actual programs per se.  I only download .deb programs, which uses the Debian Package Installer.  I've never seen one not appear in my applications.  Most packages seem to be composed of a lot of lib files.

---

### Post by wizard10000 on 2009-08-19
> **cariboo907 said:**
> The above command has to be run as root eg:

```
sudo dpkg --get-selections > installed
```

Nitpicking, but I don't believe it does have to be run as root.  I've got it running as a daily cron job under my normal user account.

---

### Post by jacksaff on 2009-08-19
> **isee said:**
> Well, I have 1608 packages installed, very few of which are actual programs per se.  I only download .deb programs, which uses the Debian Package Installer.  I've never seen one not appear in my applications.  Most packages seem to be composed of a lot of lib files.

Well you probably have far more programs than packages. I have well over 2000 files in /usr/bin alone, nearly all of which are binaries or scripts.
I think you mean only programs which have a gui which is a very small subset of the number of actual programs you have installed. You really don't want all of your programs in your menus!

---

### Post by darksideforge on 2009-08-19
> **philinux said:**
> Yes. Each time you install an app with no gui make sure you create a menu item to launch it. Simple ;)

Phil, how do I go about creating a menu-item to launch the program?
Thanx

---

