---
title: "Linksys WMP11"
date: 2005-08-31
forum: Networking &amp; Wireless
---

### Post by Runding on 2005-08-31
Hey All,

Just tried Ubuntu out and I'm lovin' it.  The only problem I've had so far is my Linksys WMP11...

I installed Ubuntu, then looking through the Device Manager I noticed that the only Unkown recognized on my system is the Linksys card.  So it doesn't recognize it as a network adapter, or even a specific type of card.  I've got ndiswrapper and the drivers; I just need Ubuntu to recognize the card as a network adapter, and that it's wifi.  

If you guys could please help me out, that would be really really awesome.  Thanks a lot!

Runding

---

### Post by bionnaki on 2005-09-01
so, you've installed ndiswrapper + drivers?

---

### Post by Runding on 2005-09-03
Indeed, yes I have installed both the drivers and ndiswrapper.  The main problem I'm thinking is that it lists the card as an Unknown, and it only says that Linksys manufactured it.  Is there a package that detects Unknowns?  It's kind of a strange situation, I've never encountered this before. 

Any other ideas?

Thanks for your help :)

---

### Post by 0vermind on 2005-09-03
Well, it is going to be uphill from here!! I'll try to help you out the best I can. First you need to install/configure ndiswrapper (if you've already done so then skip this step).

_--Installing Ndiswrapper--_
```
sudo apt-get install ndiswrapper-utils
```

_--Installing WMP11 drivers--_
First, besure you either have the drivers from the linksys website or you have the CD (I perfer the CD). If you perfer to use the CD type in the following:

```
cd /media/cdrom0
```

Now, lets get to installing the drivers.

```

sudo ndiswrapper -i LSIPND.inf
sudo ndiswapper -l

```

[if it replies somthing like DRIVERS AND HARDWARE INSTALLED then your good, continue on. Otherwise you've got a bad problem, and don't continue!!]

```

sudo modprobe ndiswarpper
sudo ndiswrapper -m

```

Now you've got two choices you can either configure the card through the terminal or the UI way of doing it.

**--In Terminal--**
```

iwconfig wlan0

```

**--Configuring out side the terminal--**
If the try config instead of admin if the networking is no in admin.

System-->Admin/Config-->Network

There you go your all set (it should work but it may not, Linksys doesn't support Linux drivers yet so this is the best alternitive)

Mike

---

### Post by apps4apps on 2007-04-07
Hi everyone, 

Sorry for bumping an old thread but I seem to be having a similar problem and was wondering if someone could please give suggestions for a fix for getting this card to work on Ubuntu 6.10 (desktop). 

I have a Linksys WMP11 v4 card installed and it is listed in device manager but the Device Type and Capabilities are listed as Unknown. I have installed ndiswrapper using apt-get and installed the driver from the Linksys website using the instructions from Overmind above. ndiswrapper says that the driver is present and that the hardware is present but Device manager still says unknown and the card is not listed in Networking or Network Tools and I haven't been able to figure out how to get past this point yet (yes, I'm a bit of a newb when it comes to installing drivers in Linux). 

When following the instructions I get the following error message when trying the following line:

```
sudo modprobe ndiswrapper
```
```
FATAL: Error inserting ndiswrapper (/lib/modules/2.6.17-11-generic/kernel/drivers/net/ndiswrapper/ndiswrapper.ko): Invalid argument

```

Could someone please give a suggestion?

---

### Post by apps4apps on 2007-04-07
I seem to have resolved part of the issue after reading the post [here](http://ubuntuforums.org/showthread.php?t=403093&highlight=Error+inserting+ndiswrapper) by installing ndiswrapper using the following:```
sudo apt-get install ndiswrapper-utils-1.8
```

Now I just need to figure out how to configure the card. Just supplying the name of the network and WEP key doesn't seem to work. I have verified that the card itself works ok by installing and using it in Vista...

---

