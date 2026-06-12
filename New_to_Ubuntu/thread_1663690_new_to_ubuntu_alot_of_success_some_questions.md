---
title: "new to ubuntu alot of success some questions"
date: 2011-01-10
forum: New to Ubuntu
---

### Post by krismx6920 on 2011-01-10
I wanted a winter time computer project and came across a gateway laptop that had the hard drive ripped out and damage to the mobo.. $30 later and i was on my way to ubuntu...  managed to burn a cd from other laptop and did install on a 4 gig flash drive and it is purring away..  I found alot of help and finally got java 6u23 up and running.  When i started playing pogo my laptop would overheat and shut off 85c warning.  i figured out how to run sensors, but i couldn't get fan speeds.. just temp.  I gave up and got a $15 cooling pad and run a constant 35c now..  I would like to have a better idea of stats tried to run lm-sensors or sensor detect but got no where..  how exactly do i get to root in terminal?  I think i'm going to upgrade from 1 to 2 gig memory I assuming linux should have a vast improvement in speed?  I have a dual core t2050 should i consider upgrading to the 64 bit version or will i have more problems than its worth?  I do have to say i think i am done with windows.  Any thoughts ideas thanks...

---

### Post by krismx6920 on 2011-01-10
I forgot a few things..  i got java to work with firefox but not with chromium..  can't figure out the plug in..  Also when screen goes darkish does that mean memory is running swapfile?

---

### Post by pbpersson on 2011-01-10
Do not go to the 32-bit version, you will not see a huge improvement in speed in most cases.  It sounds like you have enough challenges now.

When the screen goes gray it means that application is temporarily frozen or busy. 

When you are in a terminal session to run any command as root you preface it with sudo

I believe that if you type "sudo -i" it means your entire terminal session will be as root.

---

### Post by lykeion on 2011-01-10
> **krismx6920 said:**
> I forgot a few things..  i got java to work with firefox but not with chromium..  can't figure out the plug in..  Also when screen goes darkish does that mean memory is running swapfile?
I think chromium may have a problem with the default installed java browser plugin (IcedTea). 
You can try to replace IcedTea with Sun Java browser plugin. In Lucid and later you do this:
1. Start a terminal (Applications > Accessories > Terminal)
2. Remove IcedTea:```
sudo apt-get remove icedtea6-plugin
```
3. Enable Partner repository (NOTE: replace lucid below with maverick if that's your Ubuntu version): ```
sudo add-apt-repository "deb http://archive.canonical.com/ lucid partner"
```
4. Update repositories:```
sudo apt-get update
```
5. Install Sun Java browser plugin:```
sudo apt-get install sun-java6-plugin
```
6. Restart your browser and you can go to [http://javatester.org](http://javatester.org) to see your current Java browser plugin version.

---

### Post by Bucky Ball on 2011-01-10
> **pbpersson said:**
> 
When you are in a terminal session to run any command as root you preface it with sudo

I believe that if you type "sudo -i" it means your entire terminal session will be as root.

This works to:

```
sudo su
```Open Synaptics Package Manager (System >Admin), search for and install 'ubuntu-restricted-extras'. That will install java and a whole lot of other goodies properly. You shouldn't need to install much manually at all nowadays.

The cooling pad is a stop gap measure. The machine shouldn't be that hot without one. Have a read of this page and check if your machine has the problem:

Go to the section marked:** Now to determine whether you actually suffer from this problem**

[http://ubuntuforums.org/showthread.php?p=5031046](http://ubuntuforums.org/showthread.php?p=5031046)

Welcome and glad you're enjoying your new OS. Lot of us here sure do! (Obviously!)

---

