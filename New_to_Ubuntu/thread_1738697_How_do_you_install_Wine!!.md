---
title: "How do you install Wine?!?!"
date: 2011-04-25
forum: New to Ubuntu
---

### Post by darkgame on 2011-04-25
Wine! Yes I have used it in Lucid Puppy, but HEY! This is ubuntu, and it cant install wine!
I went to winehq and added the repo. And I searched WINE in the software centre. But... HEY! MISSING DEPENDENCIES! I thought this is solved by the software centre itself?!?!
This is DarkGame, currently using Ubuntu 10.04 Lucid Live-CD.

---

### Post by flyingAnt on 2011-04-25
Most modern distro's have WineHQ in the repo. Just open up the package manager, enter the root password and search for 'wine'.
 
If you don't know how to do this, or it doesn't work, or you can't find it, please specify *which distro*  you are running. I never found it remotely difficult to install wine on  any of the distro's, but the exact way how to do this is (unfortunately  for you) one of the Big Differences between the various distro's. 
 
Think of it this way, every city has a railway station, but if you ask  the address of the railway station then we need to know in which city  you are [IMG]http://www.linuxforums.org/forum/images/smilies/icon_wink.gif[/IMG]

---

### Post by darkgame on 2011-04-25
im on 10.04 ubuntu. I will try again tommorrow
root password? Mine didnt ask for it!

---

### Post by grahammechanical on 2011-04-25
Excuse me for asking but, is it wine that is not installing correctly or is it some Windows program that is not installing correctly through wine?

I have used wine on Ubuntu for about two years. It was easy to install from Synaptic and the Software Centre. Installing the one Windows program that I wanted to use was another matter.

Adding the wine repository or PPA to software sources is a good idea because you always have the latest version of wine. The version in the software centre is older but perhaps more stable. 

If you are having a problem running a program, try to load it from the terminal. Then you will see error messages that might explain why the program is failing to run. Installers sometimes put files in the wrong or different folders to where they need to go. This is what happen to the program that I wanted to run.

Regards.

---

### Post by yetiman64 on 2011-04-25
> **darkgame said:**
> im on 10.04 ubuntu. I will try again tommorrow
root password? Mine didnt ask for it!

If you are asked for the "root" password in Ubuntu just input your user password (if your account is the original account set up at install time - that is the admin account) as your account is in the sudoers file. 

Also for your info, the root account is disabled by default in Ubuntu and no password is set on it. If you need more information / explanation link #4 in my sig has the Rootsudo Community Documentation to read about it.

The "software center" is a front end for Synaptic and sometimes when it can't successfully install a package, Synaptic can. Have a look in System > Administration > Synaptic Package Manager, to check it out. A tip is to update the system before trying to install a package "sudo apt-get update" in a terminal or the "reload" button in Synaptic. One last check is to ensure you have the "universe" repository enabled in System > Administration > Software Sources.  Good luck.

---

### Post by gandaran on 2011-04-25
> **darkgame said:**
> Wine! Yes I have used it in Lucid Puppy, but HEY! This is ubuntu, and it cant install wine!
I went to winehq and added the repo. And I searched WINE in the software centre. But... HEY! MISSING DEPENDENCIES! I thought this is solved by the software centre itself?!?!
This is DarkGame, currently using Ubuntu 10.04 Lucid Live-CD.
you have to update the software package list first to get the missing dependencies.
```
sudo apt-get update
```

---

### Post by gandaran on 2011-04-25
> **darkgame said:**
> im on 10.04 ubuntu. I will try again tommorrow
root password? Mine didnt ask for it!
it wont if you are using the live cd like you mentioned in the first post.

---

### Post by darkgame on 2011-04-25
> **gandaran said:**
> it wont if you are using the live cd like you mentioned in the first post.

ok. . .
Will it in a persistent live-usb?
Well downloading ubuntu is a pain (700mb)
wine is a pain to install, lol
but im not giving up, windows sux

well, i thought ubuntu software centre will auto update for dependcy? Or i m taking things for granted?

---

### Post by cottfcfan on 2011-04-25
if you haven't got Ubuntu installed on your hard drive you will run into problems. The live cd/usb is designed just to check out the distro. If you want to start updating and installing software, you're best installing the system.
Wine then installs simply.
What exactly are you trying to do?

---

### Post by Slidemansailor on 2011-04-25
I am just learning Ubuntu. My Windows XP died once again and I decided to quit investing time and money in it.  My retraining is going okay for an old guy, but I cannot get Open Office spreadsheet or Gnumeric spreadsheet to open THE BIG ONE that I built in Quattro Pro that has my whole financial life built into it.  Gnumeric opens smaller ones and I can see the light at the end of the tunnel where it will do what I need.

I tried to get Wine to run my Quattro Pro, but it won't recognize it as executable.  I have the Quattro Pro installation disc, but can't seem to get it recognized as executable either.

What's the trick?

---

### Post by Mark Phelps on 2011-04-25
See the page link below regarding Quattro and Wine:

[http://appdb.winehq.org/objectManager.php?sClass=application&iId=534]("http://appdb.winehq.org/objectManager.php?sClass=application&iId=534")

If you're trying to install version 13, you're out of luck.

---

### Post by darkgame on 2011-04-25
> **cottfcfan said:**
> if you haven't got Ubuntu installed on your hard drive you will run into problems. The live cd/usb is designed just to check out the distro. If you want to start updating and installing software, you're best installing the system.
Wine then installs simply.
What exactly are you trying to do?
im trying to use ubuntu to carry all my games with me when i go somewhere in a usb stick

---

### Post by Mark Phelps on 2011-04-26
> **darkgame said:**
> im trying to use ubuntu to carry all my games with me when i go somewhere in a usb stick

If these are Windows games, you're results are going to range from poor to abysmal doing this!  

Why?

Because the performance of Windows games depends critically on the video cards in use and then, on the drivers in use -- and with this being moved from machine to machine, you'll most likely be using the open-source drivers by default.

And while those work fine for standard graphics work, they will not support graphics-intensive games.

---

