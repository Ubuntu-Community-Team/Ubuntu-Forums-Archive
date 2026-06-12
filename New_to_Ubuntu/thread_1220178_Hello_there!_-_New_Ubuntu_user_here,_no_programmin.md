---
title: "Hello there! - New Ubuntu user here, no programming exp. etc"
date: 2009-07-22
forum: New to Ubuntu
---

### Post by Uboy on 2009-07-22
Hey there, I've recently just un-installed Vista and installed Ubuntu on my vaio notebook. I've installed Skype and need some assitance from an expert on how to get it to work correctly. I've installed, but I'm getting the cliche Linux message about how it can't "detect my audio output". I read up on ways to fix it, so I went and downloaded AlsaMixer, having a tough time getting it installed. When I cop/pastey "sudo apt-get install alsamixer" in the terminal I get "sudo apt-get install terminal.app
bash: Terminal: command not found
robert@PCG-6Q1L:~$ sudo apt-get install alsamixer
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package alsamixer" as the message, can someone please assist me? It would be greatly appreciated.

---

### Post by bacil on 2009-07-22
try 

```
sudo apt-get install alsa-utils
```and for future reference install apt-file and use it to search for packages you need 

so to get it

```
sudo apt-get install apt-file
```and then fter you update it with

```
apt-file update
```you can search eg.

```
apt-file search alsamixer
```you can replace alsamixer with waht you need :-)))

---

### Post by Uboy on 2009-07-22
robert@PCG-6Q1L:~$ sudo apt-get install alsa-utils
Reading package lists... Done
Building dependency tree       
Reading state information... Done
alsa-utils is already the newest version.
The following packages were automatically installed and are no longer required:
  linux-headers-2.6.28-11 linux-headers-2.6.28-11-generic
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.


that's the message I received, and from there?:)

---

### Post by achase79 on 2009-07-22
you successfully installed alsa-utils which includes alsamixer

---

### Post by bacil on 2009-07-22
well from there you got your alsamixer :-)

system suggest you to clean up ```
sudo apt-get autoremove
```

then you can install apt-file as suggested in my previous answer

---

### Post by Uboy on 2009-07-22
How would I access it exactly? It isn't showing up in my add/remove programs panel or my sound-applications?

---

### Post by Bölvaður on 2009-07-22
when you dont see a launcher for a program you can always write down the name of the program/package name into the terminal.

```
alsamixer 

```

*edit*
but Im not really sure that is what you are looking for.
Try pulse audio and install the pulse audo device manager

by clicking this link []("apt:pavucontrol")

---

