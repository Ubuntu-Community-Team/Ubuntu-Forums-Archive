---
title: "Problems running Netgear wireless n-300 usb adapter and WNA 3100 adapter"
date: 2014-12-29
forum: Networking &amp; Wireless
---

### Post by wafflefriend on 2014-12-29
Hey everyone,

**The background**

I recently downloaded ubuntu on my dekstop due to my roommates suggestion Unfortunately, upon downloading Ubuntu I realized that the wireless drivers were not compatible with Ubuntu. I've been reading through the forums the last few days and have come upon a variety of solutions, all of which I've tried in one form or another. I think that the issues i am facing are rather unique and that is why I chose to create a separate thread. 


**Troubleshooting**

I  read through and implement the solutions I found online however I've come across two main issues. One is that my desktop has no way of connecting to the internet other then the wireless adapter since its too far away from the modem. I chose to work around this by trying to download the necessary drivers such as WINE and Ndiwrapper on my brother's  windows 7 laptop, transferring the files onto a usb and then plugging that into my desktop. But, the drivers are not being detected when I try and access the drivers on my desktop.  

The second issue that I've encountered is that I am not entirely sure which drivers are necessary because multiple threads have suggested multiple drivers, from what I gathered; NDiswrapper and WINE are a must but I have no idea how to download them and what to do from there. 

Please help, I am now without a computer and being not very tech savvy its put in me in a rather uncomfortable situation. 

Thanks

---

### Post by Bucky Ball on 2014-12-29
Welcome. There is no way you can download Wine without an internet connection that I know of and it is not necessary to use ndiswrapper.

There are some networking gurus about who will be able to help with your issue. Hopefully one will chime in soon. Good luck. ;)

PS: The wna 3100 is known to be problematic. Not sure about the Netgear. I suggest you plug the Netgear in (unplug the wna 3100) and post the output of this from a terminal:

```
lsusb
```

Your other option is to grab a wifi dongle that is known to work 'out of the box' with Ubuntu. They are very cheap now.

---

### Post by wafflefriend on 2014-12-29
[COLOR=#000000]ubuntu@ubuntu:~$ lsusb[/COLOR]
[COLOR=#000000]Bus 002 Device 002: ID 0781:5571 SanDisk Corp. Cruzer Fit[/COLOR]
[COLOR=#000000]Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub[/COLOR]
[COLOR=#000000]Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub[/COLOR]
[COLOR=#000000]Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub[/COLOR]
[COLOR=#000000]Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub[/COLOR]
[COLOR=#000000]Bus 001 Device 004: ID 0846:9020 NetGear, Inc. WNA3100(v1) Wireless-N 300 [Broadcom BCM43231][/COLOR]
[COLOR=#000000]Bus 001 Device 002: ID 03f0:5307 Hewlett-Packard [/COLOR]
[COLOR=#000000]Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub[/COLOR]
[COLOR=#000000]Bus 004 Device 002: ID 046d:c52b Logitech, Inc. Unifying Receiver[/COLOR]
[COLOR=#000000]Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub[/COLOR]
[COLOR=#000000]Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub[/COLOR]
[COLOR=#000000]ubuntu@ubuntu:~$[/COLOR]

---

### Post by wafflefriend on 2014-12-29
What other drivers would I need other than WINE? I'm not entirely sure what drivers I have to download at this point tbh.

---

### Post by Bucky Ball on 2014-12-29
Wine is not a driver. It is software for using Windows programs in Ubuntu. You don't want to go there.

Okay, so the Netgear *is* the WNA 3100. They are one in the same, not two different USB wireless dongles? 

Yes, the 3100 can be made to work. Look for the fix by chili555 on these forums. It is one of the few cards that ndiswrapper I think still needs to be used with. Ndiswrapper is largely superceded now, but this may still be one of the exceptions (it was when it was first released).

Perhaps have a look at [THIS]("http://ubuntuforums.org/showthread.php?t=2221251") solved thread and see if it gets you anywhere.

---

### Post by wafflefriend on 2014-12-30
Hey,

Thanks for the tip, I tried following the directions on that thread before, but I realized that my biggest issue that I'm facing is that I need somehow get Ndiswrapper installed onto my desktop without any access to internet, so like i mentioned previously I tried to put ndiswrapper in a separate usb drive and try installing the program that way. However, ubuntu would not or could not identify the files.

---

### Post by Bucky Ball on 2014-12-30
This might get you rolling ... [https://help.ubuntu.com/community/Wi...er/Ndiswrapper](https://help.ubuntu.com/community/Wi...er/Ndiswrapper)

---

### Post by wafflefriend on 2014-12-31
Awesome thank you for the tip! I'll take a look at it and keep you updated. 

And to anyone reading this thread have a safe and happy new years!

---

