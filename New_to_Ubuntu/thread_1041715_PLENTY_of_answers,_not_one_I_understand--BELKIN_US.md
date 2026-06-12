---
title: "PLENTY of answers, not one I understand--BELKIN USB network adapter"
date: 2009-01-16
forum: New to Ubuntu
---

### Post by garpt on 2009-01-16
Hi all,
 Plenty of posts on this, but still can't find one "newbie" enough to get mine going. Using Belkin F5D7050 usb network adapter, ubuntu 8.10, latest. No power to dongle. Isn't recognized, see below- showing as unknown device, I believe.....

garwyn@garwyn-laptop:~$ sudo /etc/init.d/networking restart
[sudo] password for garwyn: 
 * Reconfiguring network interfaces...                                          Ignoring unknown interface eth0=eth0.

I downloaded WINE, and downloaded the windows driver package, figured out how to install it. Get all the pretty GUI's. Tried some stuff a bit over my head with ndiswrapper (sp?). Nothing. Then downloaded the RT73 drivers, which show up in my home folder, but I don't know what to do with them. So, that's where I am right now. Is there a relatively simple way that even I can understand to make this thing work?  
Thanks!! Gary

---

### Post by jerome1232 on 2009-01-16
Well if the adapter isn't getting power are you sure that the usb port or the wifi adapter is even working? 

Does the adapter light up if plugged into another computers usb port, have you tried other ports on this computer?

What's the output of these commands with the adapter plugged in?

```
lsusb
sudo lshw -C network
```

On another note I have a belkin F5D7050v3 and it works out of box

---

### Post by Kellemora on 2009-01-17
HI garpt

I hate to say this, but you may want to put that adapter in the trash can where it belongs.

Even on just Windows XP machines, when we were stuck with a couple of these dreaded Belkin USB hubs, it was a DAILY RITUAL to keep them working.

But here are the steps we had to do every day, often more than once a day.  Leave the USB devices connected to the Hub, disconnect the INPUT USB cable from the Hub, Unplug the power cord from it's socket.  Count to 5, plug the power cord back up, then plug the INPUT USB cable back up.  If the devices are not recognized, try again, only this time plug up the USB INPUT cable first, THEN the power cable.

If that don't work, connect it to a Windows box and go into System DEVICES and uninstall the driver, reboot the windows box and they try the plugging and unplugging steps again.
It should say new hardware found, eventually.

If not, chunk it and buy some no name brand for 1/3 the price and it use it instead, it should then work flawlessly after that!

We've had nothing but GRIEF with Belkin labeled hardware, other than their cables.

The hub that gives us the least trouble was labeled by CyberPower and cost like $4.95 (who actually made it is anybodies guess!).

TTUL
Gary

---

### Post by anewguy on 2009-01-17
I also have a F5D7050, and it has worked "out of the box" with Ubuntu for at least the last 2 releases.  You may want to double check how you are trying to do it, as you may have done something to completely hose it up.  If you can, boot up using the LiveCD with the F5D7050 plugged in and see if you can access the wireless.  If so, I'd reinstall Ubuntu with the adapter plugged in.  I hate to have you take that step, but without knowing exactly step by step what you have done and each of the errors exactly as encountered, it's pretty hard to know what might be messed up.

BTW - my F5D7050 has worked beautifully in Windows XP and Ubuntu for over 2 years.

Dave:)

---

### Post by garpt on 2009-01-17
Thanks All, for the responses! 
Jerome, below is the output you requested:

garwyn@garwyn-laptop:~$ lsusb
Bus 007 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 002: ID 0d62:00a1 Darfon Electronics Corp. 
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 005: ID 05a4:9862 Ortek Technology, Inc. 
Bus 002 Device 004: ID 05a4:9837 Ortek Technology, Inc. 
Bus 002 Device 003: ID 147a:e00c Formosa Industrial Computing, Inc. 
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 005: ID 04f9:0035 Brother Industries, Ltd 
Bus 001 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
garwyn@garwyn-laptop:~$ sudo lshw -C network

  As you can see, plenty of working USB devices. I unplugged stuff and plugged the Belkin in directly, thinking I wasn't getting enough power to it. The adapter does work in a Windows machine- (I mean it lights up). 
 I have read that many got the device to work "out of the box" with this version of Ubuntu. That's frustrating as well. 

anewguy, I have thought about that. I noticed every device in my machine plus the USB devices I had plugged in when I installed Ubuntu off the live CD I created was recognized immediately and function fine with everything installing and being recognized during the install.

Kellemora, I do have another alternative, a US robotics USR5410 PC card, which is the device my Alienware laptop came with. (they were having problems with the built-in cards when I ordered my Alienware, so they bundled that card with the machine.) The problem is that getting THAT card to work looks like a REAL nightmare. I installed the windows software for that card for the heck of it, get the nice GUI's, but no luck. That card DOES get power, but locks up the machine after about 20 seconds. 
 If I could actually get a new option for under $10., I would certainly be up for that if I could get it to work with my skill set. It would be worth the investment, and I might learn something. 

 i will try the other recommendations from you all as well. 

Thanks! 
Gary

---

### Post by anewguy on 2009-01-21
I guess we should ask for one more piece of information here:

In a terminal window, with the adapter plugged in:

lsusb

Copy the line for your Belkin adapter and post back here.  It will include a version number (mine shows v4000).  Once we have that perhaps we can help you more.

The other option would be to search the net for a list of wireless cards/USB adapters that are compatible with Ubuntu.

It depends on the version which drivers you actually need.  If you know for sure that the rt73 driver is correct, here is a link with step-by-step for getting it working.  You will need a wired connection.  Please note this is for an old version (6.10) of Ubuntu and may not be correct with the new releases.

BTW - never did ask - do you actually have the windows driver for the device - in particular the .inf and .sys files?  If so, I could try walking you through ndiswrapper to see if it works for you or not.

Dave :)

---

