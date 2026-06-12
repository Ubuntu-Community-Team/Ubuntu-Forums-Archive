---
title: "Need wifi help!!"
date: 2011-05-14
forum: New to Ubuntu
---

### Post by ohmy28 on 2011-05-14
Hey guy/gals! I'm brand new to Ubuntu and I tried connecting my laptop to my wifi but no luck it says my card is off. Yet my wired connections works perfectly. I'm using an Hp Pavilion zd8000 if that makes a difference.

---

### Post by RedRat on 2011-05-14
Check your instruction manual. You may have to turn on the wifi by using the function buttons. Also, if you have the wired connection going, it may just turn off the wifi connection. Check that out.

---

### Post by ohmy28 on 2011-05-14
I've tried pressing my wifi button but nothing so i switched to wired to do some research to find the problem but no luck so far...

---

### Post by RBLevin on 2011-05-14
Also, if your WiFi has a physical on-off switch, make sure it is set to on.

Lastly, if you're on 10.x, right click the wireless icon, and make sure "Enable wireless" is checked. If you're on 11.04, click the wireless icon and check to see that wireless is enabled.

---

### Post by ohmy28 on 2011-05-14
It has a physical button but it wont turn on or right clicking the enable wireless is unclickable.:(

---

### Post by RedRat on 2011-05-14
In another post, someone mentioned that your wired connection may be favored by Network Manager and so turns off the wireless. Might try rebooting without being hard wired to the network. Also make sure that somehow your router is not blocking your particular card in the address permission table. Strange things do happen.

---

### Post by ManualSparrow on 2011-05-14
Open a terminal and type ```
ifconfig
``` and see if a wlan0 connection is being shown. Type ```
lspci
``` to see what your network adapter is called (it will spit out a list of all your hardware). You may need to download drivers or enable them if you haven't already. 

On the other hand you may just want to reboot first after checking that all of your options are set to 'on' - hardswitches, network settings, etc.

EDIT: ```
sudo dhclient wlan0
``` gives a dynamic IP address and might fix your troubles if the drivers are not the problem, but I'm not sure if it will 'stick' after reboot or if that is the right solution.

---

### Post by RBLevin on 2011-05-14
> **ohmy28 said:**
> 

Can you post the **exact** error message?

---

### Post by ohmy28 on 2011-05-14
@RBLevin There is no error message I'm just not able to connect to my WIFI network.

---

### Post by ohmy28 on 2011-05-14
well is there a way to install the driver for Broadcom Corporation BCM4318?

---

### Post by wildmanne39 on 2011-05-14
> **ohmy28 said:**
> well is there a way to install the driver for Broadcom Corporation BCM4318?

Hi, the driver should be in the additional drivers file, plug into a ethernet connection and click additional drivers and it should bring up a list of restricted drivers, then see if the one for your card is there if so activate it and reboot,then enter your password.):P

---

### Post by ohmy28 on 2011-05-14
> **wildmanne39 said:**
> Hi, the driver should be in the additional drivers file, plug into a ethernet connection and click additional drivers and it should bring up a list of restricted drivers, then see if the one for your card is there if so activate it and reboot,then enter your password.):P
I went there and it says there are no proprietary drivers.

---

### Post by wildmanne39 on 2011-05-15
> **ohmy28 said:**
> I went there and it says there are no proprietary drivers.

Hi, did you have an internet connection with the ethernet cable at the time?:)

---

### Post by ewalthier1 on 2011-05-15
same problem here.  Dell inspiron B130.  Need the BCM4318 driver.  I installed the latest version of Ubuntu while connected to the internet, but there are no drivers in "additional drivers".  This is my second install actually, the last time I used some terminal commands to try to get it working, and I did eventually get my computer to see the nearby networks, but it wouldn't actually connect, it just asked for the WPA key every minute or so.  I thought maybe I did something wrong.  Since this was a  brand new install, I had nothing to lose by doing it over. So here I am, super fresh,  but now my computer can't even see the local networks again.  I must have done at least one thing right before!  I figured I'd chime in here before I retry the previous method.

---

### Post by wildmanne39 on 2011-05-15
> **ewalthier1 said:**
> same problem here.  Dell inspiron B130.  Need the BCM4318 driver.  I installed the latest version of Ubuntu while connected to the internet, but there are no drivers in "additional drivers".  This is my second install actually, the last time I used some terminal commands to try to get it working, and I did eventually get my computer to see the nearby networks, but it wouldn't actually connect, it just asked for the WPA key every minute or so.  I thought maybe I did something wrong.  Since this was a  brand new install, I had nothing to lose by doing it over. So here I am, super fresh,  but now my computer can't even see the local networks again.  I must have done at least one thing right before!  I figured I'd chime in here before I retry the previous method.

Hi, I had the bcm 4306 and I used to have to manually install it but then they put it in the additional drivers file and it made it much easier, when you tried additional drivers you were connected to the internet by ethernet cable right? If you put in your exact wireless model number you should be able to find a forum on hear that deals with that model.:)

---

### Post by bkratz on 2011-05-15
Pretty good summation of Broadcom devices and how to get them working.

[http://ubuntuforums.org/showpost.php?p=10796508&postcount=44](http://ubuntuforums.org/showpost.php?p=10796508&postcount=44)

---

### Post by RBLevin on 2011-05-15
> **ohmy28 said:**
> @RBLevin There is no error message I'm just not able to connect to my WIFI network.

So, you see the panel status icon attempting to connect, but it never connects?

---

### Post by RBLevin on 2011-05-15
> **bkratz said:**
> Pretty good summation of Broadcom devices and how to get them working.

[http://ubuntuforums.org/showpost.php?p=10796508&postcount=44](http://ubuntuforums.org/showpost.php?p=10796508&postcount=44)

There is a problem on 11.04 that no amount of driver installations seems to resolve. I have the Broadcom chipset and the proprietary drivers available, but that doesn't help. See [http://ubuntuforums.org/showthread.php?t=1744892](http://ubuntuforums.org/showthread.php?t=1744892)

If he is getting the "wireless disabled by hardware switch" message in the panel menu, this might be his problem.

---

### Post by ewalthier1 on 2011-05-16
In Terminal:
 
~$ sudo apt-get install b43-fwcutter
 
and then
 
~$ sudo apt-get install b43-fwcutter firmware-b43-installer
 
SHUT OFF computer, restart worked for me.  That's it, no additional drivers program or anything.  I ran it, but it didn't find any.  I suppose it can't hurt to run it after the above steps before shutting down and restarting.

---

### Post by Opie Wick on 2011-05-16
I remember also a free (as in freedom) driver for some (if not most) of the broadcom chipsets. It can be found at:
	git://git.kernel.org/pub/scm/linux/kernel/git/gregkh/staging-next-2.6.git
in the drivers/staging/brcm80211 directory.
I also remember a well documented way to set it up in the readme, but using this may be a pretty big task for someone brand new to GNU/Linux - would definitely be a great learning experience though!

---

### Post by computerandu on 2011-05-16
Here is the link for broadcom driver...

[http://ie.archive.ubuntu.com/ubuntu/pool/restricted/b/bcmwl/bcmwl-kernel-source_5.60.48.36+bdcom-0ubuntu5_i386.deb](http://ie.archive.ubuntu.com/ubuntu/pool/restricted/b/bcmwl/bcmwl-kernel-source_5.60.48.36+bdcom-0ubuntu5_i386.deb)

---

