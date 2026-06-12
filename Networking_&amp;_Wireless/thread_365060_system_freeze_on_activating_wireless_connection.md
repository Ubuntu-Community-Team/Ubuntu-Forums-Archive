---
title: "system freeze on activating wireless connection"
date: 2007-02-19
forum: Networking &amp; Wireless
---

### Post by wickstopher on 2007-02-19
I am attempting to install Xubuntu 6.06 on a friends' computer (the liveCDs for 6.10 just freeze up before getting to the options menu, I think due to his older ATI graphics card).  One problem that I've run into is this:  using a wireless usb device, upon attempting to activate the connection, the system COMPLETELY freezes up.  There is nothing to do but shut the machine off.  This happened with the liveCD and my friends' dlink wireless device.  This ALSO happened on my own PC with the liveCD and my wusb4g from linksys (which works fine on my own installation of Ubuntu 6.10).  In addition, just to be sure, I installed Xubuntu 6.06 on a partition of my own hard drive, and the same thing happened from the installed OS.  The funny thing is, it recognizes the USB device, and even shows a list of available networks (which, interestingly enough, doesn't show up in Ubuntu 6.10 on my machine, although I can get the device working just fine).  I enter all the information for the connection as I did in 6.10, and then press the "Activate" button, and get a total system freeze.  I even tried deactivating the ethernet connection (which is activated by default, even though there is no ethernet connection), and get the same results.  Any advice here?  I can't imagine why it's doing this, especially when it recognizes the device and has in fact successfully scanned for available wireless networks.  I am currently in the process of downloading regular ol' ubuntu 6.06, and will test the problem there, and let you know what happens.  But, I would really like to install Xubuntu on my friends' machine, as it will run much better.  If anyone has any advice, it would be greatly appreciated!

---

### Post by maniacmusician on 2007-02-19
Well it seems like the driver that's being used for that device can't handle it, and causes a kernel crash; that's just an educated guess. What I would do is find out what driver is being used for that device, and then 'blacklist' that driver. Someone can help you with that once you know what driver it is. 

After that, you can try and find another method (perhaps ndiswrapper, or a different driver) that will get the device working.

---

### Post by wickstopher on 2007-02-19
Sounds good.  I'm familiar with blacklisting via the modprobe.d file.  My only question is this: is there an easy way to install ndiswrapper without an internet connection?  In other words, where can I download  the package and all of the dependencies to burn to a CD that I can then use to install to my friend's computer?  I've only installed ndiswrapper on a machine using synaptic (and as such, an internet connection has already existed on the machine),

---

### Post by penduluum on 2008-02-18
I'm having exactly the same problem in Ubuntu 7.10.  Upon trying to activate my wireless connection, the system freezes completely.  This is my first time trying to install any Linux distro anywhere, so I'm pretty helpless, but:

(1) it uses rtl8180 drivers but
(2) I guess they're already blacklisted?  Using them anyway causes the freeze, but
(3) I don't know how to install or use ndiswrapper.

I tried this: [http://ubuntuforums.org/showthread.php?t=684495](http://ubuntuforums.org/showthread.php?t=684495) and it has instructions on a workaround for using the rtl818x drivers but it froze up exactly the same way right after ```
sudo ifconfig wlan0 up
```

Is ndiswrapper my answer?

---

### Post by emaag on 2008-03-04
> **maniacmusician said:**
> Well it seems like the driver that's being used for that device can't handle it, and causes a kernel crash; that's just an educated guess. What I would do is find out what driver is being used for that device, and then 'blacklist' that driver. Someone can help you with that once you know what driver it is. 

After that, you can try and find another method (perhaps ndiswrapper, or a different driver) that will get the device working.
I'm having the same problem, and I reached the same guess as you (the driver can't handle huge streams of data and chokes) how can I go about figuring out what driver it's using, if anyone can point me in the right direction I'd appreciate it.

---

### Post by {BzF}~JOKesTER on 2008-03-04
Install:

ndiswrapper

open a terminal:

type:

ndiswrapper -l

Whatever Driver Is Being Used By Your Device {I.E. ETH0 -.etc...} Is Most Likely Using A Bad Driver. And In Turn Should Be Removed And Re-installed. -{Or Use A Different Driver}

To Remove A Driver Type:

ndiswrapper -r (YourDriversNameHere}

To Assign A Driver To That Device - Assuming It Is A USB Adapter:

In The Terminal Type:

lsusb

Write Down The XXXX:XXXX Code Of Your Device.

In Terminal Type:

ndiswrapper -a XXXX:XXXX (NewDriverToBeUsedHere)

{Note: Replace XXXX:XXXX With Your Usb Cards Device Code.}

After This You May Want To Run These Commands:

ndiswrapper -m

ndiswrapper -mi

ndiswrapper -ma

Now Restart Your Computer And You Should Be Good!!

Hope This Helps!!!

---

### Post by keinefurcht on 2008-03-12
I am having the same problem with Ubuntu 7.10 (new install, never worked with this before), but I am hesitant to do anything to my device drivers because I am dual-booting XP, and I can still get on the network just fine in there. Please advise?

---

### Post by emaag on 2008-03-12
It's actually not a USB wireless card, I'm running an old laptop (dell circa 2002) with a pcmcia card. I am pretty sure it's the driver, anytime that too much data gets to the card (like torrents, or soulseek) it freezes the whole system. 

Rather than just find the quick solution, I'd like to know how to diagnose and then go about finding the fix. 

Thanks!

---

