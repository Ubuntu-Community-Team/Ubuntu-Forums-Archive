---
title: "Begining help with getting WiFi working"
date: 2008-04-29
forum: Networking &amp; Wireless
---

### Post by redpete on 2008-04-29
:confused:Hello,

This is my first time with Ubuntu. I installed 8.04 just fine. I'd like to get my wifi working on my laptop. But when I press the button it wont switch on. I pressume that my wifi card isn't being "see" under Ubuntu or I'm missing a driver or something (it's just fine under Windows XP though). I looked at the list of supported drivers under the sticky and find it listed but no driver?

So what do I need to get this up and running. Remember I'm new to this so be gentle with me and start at the beginning! I'd prefer to configure it under the gUI if possible until I get the hang of things

Thanks Pete

Hardy 8.04
PC Compaq presario M2000
Wifi card: Broadcom BCM9 4318 (rev4)

---

### Post by Ek0nomik on 2008-04-29
I'd suggest you look at this thread:

[http://ubuntuforums.org/showthread.php?t=197102&highlight=ndiswrapper+howto](http://ubuntuforums.org/showthread.php?t=197102&highlight=ndiswrapper+howto)

If you run into problems you can post for help in that thread or here, as I have some WiFi experience on Linux myself.

Additional Information:
[http://ubuntuforums.org/showthread.php?t=188290](http://ubuntuforums.org/showthread.php?t=188290)
[http://kevinsbest.blogspot.com/2006/04/got-it-broadcom-4318-wireless.html](http://kevinsbest.blogspot.com/2006/04/got-it-broadcom-4318-wireless.html)

I'd suggest looking at the first link first.

---

### Post by redpete on 2008-05-04
Hi,

Well I looked in System/admin/hardware drivers and it's not listed. The first link you posted seemed to imply (?) that it was included on the install CD but I dont see it. So I presume I need to download it. Where do I find it? and how do I install it? given I'll have to download it in windows. 

And then there's these logs people post. I'm totally new to this (but a quick learner) so if you tell me to do this please tell me where to go to do it! Many thanks!

---

### Post by redpete on 2008-05-04
Oh and am I going to ned to download ndiswrapper first to get this to work?

---

### Post by redpete on 2008-05-05
OK now I'm confused :confused:

[https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Hardy](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Hardy)

says 

"Broadcom Wireless in Ubuntu 8.04 (Hardy)

The bcm43xx driver (via manual install) is now considered to be deprecated as it is now included in Ubuntu 8.04 and all Linux kernel versions 2.6.24 and later."

So where is it? or am I being really stupid here?

---

### Post by Ayuthia on 2008-05-05
bcm43xx has been depreciated.  However, they have created a new module called b43.  It is used in kernels 2.6.24 (which is in Hardy) and greater.

You can install b43-fwcutter from the LiveCD.  It will ask you if you want it to find the firmware for you.  You will need an internet connection in order for it to look for you.  So if you do, say yes, otherwise say no/cancel.  You will then need to download the following files and put them in your home directory:
[http://downloads.openwrt.org/sources/wl_apsta-3.130.20.0.o](http://downloads.openwrt.org/sources/wl_apsta-3.130.20.0.o)
[http://downloads.openwrt.org/sources/broadcom-wl-4.80.53.0.tar.bz2](http://downloads.openwrt.org/sources/broadcom-wl-4.80.53.0.tar.bz2)

You can then do the following from the terminal:
```
cd
sudo b43-fwcutter -w /lib/firmware wl_apsta-3.130.20.0.o
tar xfvj broadcom-wl-4.80.53.0.tar.bz2
sudo b43-fwcutter --unsupported -w /lib/firmware broadcom-wl-4.80.53.0/kmod/wl_apsta_mimo.o
sudo chmod o+rx /lib/firmware/b43 /lib/firmware/b43legacy
sudo ifconfig wlan0 up
```
That should get you up and running.

If for some reason, this doesn't work for you, you can try the NDISwrapper route.  I prefer that people try the b43 driver first before going the NDISwrapper route because it is easier to go from b43 to NDISwrapper than it is to go from NDISwrapper to b43.

EDIT: I forgot to mention that Ek0nomik's first link does show how to install the b43 firmware the GUI way.  That is the easiest way to do it.

---

### Post by redpete on 2008-05-06
Thanks Ayuthia.

OK do I actually need a an online connect when in Hardy to make this work? Right now I only have one in Windows. I'm using a shared wireless connection and have no option for a wired link.

I downloaded the other two files from Windows 
broadcom-wl-4.80.53.0.tar
wl_apsta-3.130.20.0.o
and saved them in my data partition. Can I then copy them over from Ubuntu?

I booted from the Live CD, went to System/admin/hardwaredrivers and found the B43 driver. Clicked on enable and it started Configuring b43-fwcutter, then clicked "fetch and extract firmware" 

Then got error message "b43-fwcutter: subprocess post-installation script returned error exit status 1"

So I suspect it's looking for the files online. Can I get it to fine them in my Home partition?

Pete

---

### Post by christianxxx on 2008-05-06
Does the fwcutter in hardy limit the bandwith as it did in Gutsy?
As far as i can remember, fwcutter didn't support bandwith > 11Mbs... 

If this is no longer an issue, fwcutter seems like a good solution. But if not, ndiswrapper is not that hard to install.

---

### Post by Ayuthia on 2008-05-06
> **redpete said:**
> Thanks Ayuthia.

OK do I actually need a an online connect when in Hardy to make this work? Right now I only have one in Windows. I'm using a shared wireless connection and have no option for a wired link.

I downloaded the other two files from Windows 
broadcom-wl-4.80.53.0.tar
wl_apsta-3.130.20.0.o
and saved them in my data partition. Can I then copy them over from Ubuntu?

I booted from the Live CD, went to System/admin/hardwaredrivers and found the B43 driver. Clicked on enable and it started Configuring b43-fwcutter, then clicked "fetch and extract firmware" 

Then got error message "b43-fwcutter: subprocess post-installation script returned error exit status 1"

So I suspect it's looking for the files online. Can I get it to fine them in my Home partition?

Pete

You are correct.  It is trying to look for it online.  You should be able to go to the Terminal and do what I listed in post #6.

---

### Post by Ayuthia on 2008-05-06
> **christianxxx said:**
> Does the fwcutter in hardy limit the bandwith as it did in Gutsy?
As far as i can remember, fwcutter didn't support bandwith > 11Mbs... 

If this is no longer an issue, fwcutter seems like a good solution. But if not, ndiswrapper is not that hard to install.That is still a debatable topic.  I have a 4311 rev 01 card that had that issue with the old driver.  The new driver does not have that limitation.  However, there are people who still feel that the driver is slower than NDISwrapper.

I have tested both b43 and NDISwrapper on my card passing files to my server and I received the same speeds on both.

My suggestion is to try b43 first because if you don't like it, you can go to NDISwrapper without having to do any additional steps.  However, if you start with NDISwrapper and want to go to b43, you will have to back out the steps that you did in NDISwrapper to make b43 work.

---

