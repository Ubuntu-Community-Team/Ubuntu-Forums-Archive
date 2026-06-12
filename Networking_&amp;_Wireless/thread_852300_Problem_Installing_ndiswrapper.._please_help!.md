---
title: "Problem Installing ndiswrapper.. please help!"
date: 2008-07-07
forum: Networking &amp; Wireless
---

### Post by gabriella on 2008-07-07
Hi,

I'm trying to get my wireless card to work BCM4318 rev2. I was recomended to try the insrtuctions using this link [https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff)

The problem is that in after Step 1 I get the following error:

sudo apt-get install ndiswrapper-utils-1.9
E: couldn't find package ndiswrapper-utils-1.9

So what am I doing wrong? I am using a wired connection for now and have the install CD as well

Gabriella

Compaq presario M2000 notebook
Hardy 8.04
BCM4318 rev 2

---

### Post by chalewa on 2008-07-07
you are using a guide for fiesty...

im guessing that the ndiswrapper release number is different. i don't know what it is off the top of my head, but a simple search within synaptic for ndiswrapper should install it for you.


[https://help.ubuntu.com/8.04/internet/C/ndiswrapper.html](https://help.ubuntu.com/8.04/internet/C/ndiswrapper.html)

there are the basic instructions for how to install a graphical frontend for ndiswrapper (which will also trigger the ndiswrapper-utils install.)

---

### Post by Ayuthia on 2008-07-07
The title says it is for Feisty, but the instructions does still apply to Hardy.

If you have not added the CD to the list of repositories yet (by going through Synaptic and adding it through Manage Repositories), you can also add it by going through the Terminal:
```
sudo apt-cdrom add
```Put in your CD when it asks and then when it is complete:
```
sudo apt-get update
sudo apt-get install ndiswrapper-utils-1.9
```It should be able to find it after that.

---

### Post by gabriella on 2008-07-07
Yes I've now resolved this by going to Synaptic package manager and installed both ndiswrapper and cabextract that way. Whats more I downloaded the driver files too and then nothing. See my other post, this is where I'm stuck at now! :
[http://ubuntuforums.org/showthread.php?t=825746&page=2](http://ubuntuforums.org/showthread.php?t=825746&page=2)

thanks everybody

---

### Post by freackout on 2009-01-21
> **gabriella said:**
> Hi,

I'm trying to get my wireless card to work BCM4318 rev2. I was recomended to try the insrtuctions using this link [https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff)

The problem is that in after Step 1 I get the following error:

sudo apt-get install ndiswrapper-utils-1.9
E: couldn't find package ndiswrapper-utils-1.9

So what am I doing wrong? I am using a wired connection for now and have the install CD as well

Gabriella

Compaq presario M2000 notebook
Hardy 8.04
BCM4318 rev 2

Hi i have exactly same model and found a few answers too more than half a dozen ways to do this with or without ndiswapper ect.. final solution for me after many tiny niggles with SOME thing not quite right in ubuntu i stumbled upon mint6 it is essentially ubuntu made easy certanly for this model (compac presario m2000) just brilliant sets everything up (apart from lights on the sound buttons however they do work) mostly everything is point and click it's amazing stable enough with virtual/ wine/mozilla firefox all codecs ect graphics TOTALY BLOWN AWAY WITH THIS thanks to the ubuntu team and mint linux 6.. thats all i can say. ps all ubuntu repos at a click here or there. + more 26000+ programmes

---

