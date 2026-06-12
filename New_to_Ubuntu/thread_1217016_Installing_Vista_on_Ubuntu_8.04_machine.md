---
title: "Installing Vista on Ubuntu 8.04 machine"
date: 2009-07-19
forum: New to Ubuntu
---

### Post by briananderson28 on 2009-07-19
I could really use some help!  I'm attempting what appears to be quite difficult.... I'm trying to install Vista on a Dell PowerEdge, writing over my Ubuntu 8.04 installation.  I'm not an Ubuntu expert by any means, so could use some guidance.  The plan is for me to get Windows running for my younger children to use this machine.

I currently have Ubuntu 8.04 installed - command line only.  I've tried to get Gnome running, but seem to continually get an error when X Windows trys to start.  

Vista -- I have purchased a full version today, which of course is on DVD.  


The problem -- my machine has a CD drive, but no DVD.  

So far....I've tried using a portable harddrive (USB) to boot from, but no luck.  It doesn't recognize it.  

Any help is GREATLY appreciated....as my daughter/son have been asking me for days when I'm going to figure it out :)

Thanks alot,

Brian

---

### Post by winjeel on 2009-07-19
Good luck, with it. The only thing I can offer is Virtual Box, see this message, [reply #5 (and screen shot)]("http://ubuntuforums.org/showthread.php?t=1212550"). But I don't know how it'll be different if running from command line.

---

### Post by cosine352 on 2009-07-19
If only the X windows is your problem why don't you try ubuntu 8.10 or 9.04. See if that works. I know this is not what you wanted. 
I did not understand how booting from an external hard drive will help you.

---

### Post by briananderson28 on 2009-07-19
Hi Cosine,

I was thinking if I could boot the Vista install which I put on an external USB HD, I could then install it over my Ubuntu installation.  I've been trying to get the GUI working, so perhaps I can leverage that to get Vista installed.  Very frustrating process!

At this point...I have a DVD with about 2.8 GB's of Vista.... I have a Dell with only a CD drive and USB ports -- no DVD.  

The challenge - how to get Vista onto the machine>!?


Brian

---

### Post by cosine352 on 2009-07-19
I would guess you can follow this tutorial for the vista too. 
[https://help.ubuntu.com/community/Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick)

this will make your usb bootable.

---

### Post by bodhi.zazen on 2009-07-19
Borrow an external DVD from a friend ?

If all else fails you should be able to get a cheap internal DVD drive from somewhere (EBAY ? ) for less then it cost to purchase Vista and, depending on your time, the effort to convert that DVD.

---

### Post by lisati on 2009-07-19
> **briananderson28 said:**
> The problem -- my machine has a CD drive, but no DVD.  

That might be problematical. DVDs generally don't work on CD drives.
> **bodhi.zazen said:**
> Borrow an external DVD from a friend ?
My thoughts exactly: borrow or purchase a DVD drive.

---

### Post by powel212 on 2009-07-19
Without a dvd Drive you will continue to have a lot of walls standing in front of you.

But if you want to get the machine running for the kids and yourself.

Plug in your LAN cable, (you must be connected to an open internet connection), then re-install the gnome windows manager from the command line like this;

```
sudo apt-get -y install gnome-core gdm network-manager-gnome fast-user-switch-applet \
human-theme x11-xserver-utils tangerine-icon-theme gnome-themes-ubuntu ubuntu-artwork \
jockey-gtk gnome-screensaver gnome-utils

```

restart

Then you can at least use the Ubuntu that is already installed until you find a DVD Drive.

I hope that helps

Powel

---

### Post by ufolx on 2009-07-19
Vista is just a SCAM!!
I used Vista just for 2 day (1 day only for updates and updates of updates).Just drive me crazy.
I never get my money back that I paid for this s***
If I will ever met Bill I'll put that Vista DVD in his A**
Hope the best for you

---

### Post by lkraemer on 2009-07-19
Brian,
Why don't you download the LiveCD of Ubuntu 9.04 and see if it will
boot and run from the LiveCD.  (Other Distro's you might want to
try could be CrunchBang 9.04.1, PCLinuxOS 2009.2, or Ubuntu 8.04.3 LTS)

One of these should install and work fine, and it's time your children
experience something other than the OS on the DVD!  ENJOY!  After a year
or two they won't regret the change.

lkraemer

---

### Post by LewRockwell on 2009-07-19
> **briananderson28 said:**
> I could really use some help!  I'm attempting what appears to be quite difficult.... I'm trying to install Vista on a Dell PowerEdge, writing over my Ubuntu 8.04 installation.  I'm not an Ubuntu expert by any means, so could use some guidance.  The plan is for me to get Windows running for my younger children to use this machine.

I currently have Ubuntu 8.04 installed - command line only.  I've tried to get Gnome running, but seem to continually get an error when X Windows trys to start.  

Vista -- I have purchased a full version today, which of course is on DVD.  


The problem -- my machine has a CD drive, but no DVD.  

So far....I've tried using a portable harddrive (USB) to boot from, but no luck.  It doesn't recognize it.  

Any help is GREATLY appreciated....as my daughter/son have been asking me for days when I'm going to figure it out :)

Thanks alot,

Brian

Hi Brian,
I wanted to gather more information before replying to you and your trouble-call so I used the only information you provided on your equipment and went here([http://www.dell.com/poweredge](http://www.dell.com/poweredge)). Of course, that wasn't much help to me, but let's assume you have a desktop as opposed to a laptop.

dvd-rom drives are dime-a-dozen nowadays and surely if you can afford to spend a few bucks with Bill Gates you can pick up an optical drive somewhere

if you've got a laptop then you can pick up the same drive and just purchase one of these([http://www.newegg.com/Product/Product.aspx?Item=N82E16812104062](http://www.newegg.com/Product/Product.aspx?Item=N82E16812104062))

then you should git-r-done quite nicely!

.

---

### Post by bodhi.zazen on 2009-07-19
I am closing this thread now. The question is asked and answered. 

This is a Linux support forums and the responses are getting off topic.

---

