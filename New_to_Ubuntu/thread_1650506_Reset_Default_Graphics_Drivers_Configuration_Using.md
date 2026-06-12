---
title: "Reset Default Graphics Drivers Configuration Using Live CD"
date: 2010-12-21
forum: New to Ubuntu
---

### Post by AlphaTwentyEight on 2010-12-21
Thanks for having me.  

Ubuntu 10.10 /Radeon 7000 VE.  Boots up to the purple screen with no login prompt.  Using Live CD to access the HD with the goobed installation.    

Last night I installed a bunch of drivers from xorg, I am pretty sure that is what is causing my troubles.  System worked this morning.  I uninstalled some of the drivers that were not supported by my hardware.  System locked, did the REISUB to reboot.  Upon reboot Can't get in.

What I want to do is, copy the default files from the live cd and paste / replace goobed files onto / from the HD.

What I think I need to know is.  Which files need to be replaced to reset to the default settings?

I am thinking this should be straightforward and easy.  I don't know where drivers are stored, enabled.  

My home folder is encrypted.  Which is why I am weary of doing a reinstall.  I would prefer to default.


Any advice?

---

### Post by bwhite82 on 2010-12-21
Basically all you need to do is remove xorg.conf.

In the live CD after you've mounted your partition open a terminal.

```
cd /media/YOURDISKNAME/etc/X11
```

```
sudo mv xorg.conf xorg.conf.old
```

```
sudo reboot
```

That will take you back to default graphics setup (no xorg.conf). Really, it doesn't matter how many drivers you have installed, only which is listed in the xorg.conf. If you don't have an xorg.conf, it defaults to basic driver.

---

### Post by AlphaTwentyEight on 2010-12-21
Thank you sir for the timely response.  

I get the Ubuntu 10.10 screen which Is cool, that's progress man. 

But now it is spinning tires at the Ubuntu 10.10 with the 4 alternating white and red dots.

It must not be exclusively an xorg.conf issue.

Strong work, thanks

---

### Post by bwhite82 on 2010-12-21
> **AlphaTwentyEight said:**
> Thank you sir for the timely response.  

I get the Ubuntu 10.10 screen which Is cool, that's progress man. 

But now it is spinning tires at the Ubuntu 10.10 with the 4 alternating white and red dots.

It must not be exclusively an xorg.conf issue.

Strong work, thanks

Wow, so even the default driver isn't working for you. OK, this solution should be fool-proof.

Lets copy that xorg.conf.old back (again mount your partition from the live cd):

```
cd /media/YOURDISKNAME/etc/X11

```
```
sudo mv xorg.conf.old xorg.conf

```
```
sudo nano xorg.conf

```
Find the line:

Driver    "xxxx"

Change whatever the xxxx's are (doesn't matter what you have between those quotes) change it to:

Driver    "vesa"

```
sudo reboot
```

Edit to add: This will get you logged into Ubuntu. From here you can remove any unneeded drivers via Synaptic and follow the instructions in the wiki for getting your card to work.

---

### Post by AlphaTwentyEight on 2010-12-21
O.k. I did everything up to: sudo reboot

How do I apply the changes to xorg.conf in nano? 

 I changed the driver to "vesa".

---

### Post by AlphaTwentyEight on 2010-12-21
ctrl + o

---

### Post by AlphaTwentyEight on 2010-12-21
Ok very cool, I am logged in using the failsafe graphics mode.  

You do excellent work SoldierBoy.  Hell of a fine job.


A28

---

### Post by bwhite82 on 2010-12-22
> **AlphaTwentyEight said:**
> Ok very cool, I am logged in using the failsafe graphics mode.  

You do excellent work SoldierBoy.  Hell of a fine job.


A28

Thanks for the compliments and glad you've gotten a little further in your quest.

---

