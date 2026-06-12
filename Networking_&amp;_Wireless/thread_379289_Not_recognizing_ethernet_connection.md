---
title: "Not recognizing ethernet connection"
date: 2007-03-08
forum: Networking &amp; Wireless
---

### Post by BrienVW on 2007-03-08
Hello,

I just built my first computer and decided to give ubunto a try.  I'm new to linux, so please speak slowly :).  When I go to System->Administration->Networking the only network option displayed is the Modem (i don't have any option to connect through the onboard LAN).  I'm trying to connect directly (rather than wirelessly).

I mention that I just built the computer, because I havn't accessed the internet through this computer before (so it may be something more basic - something not involving Ubuntu).  I checked my bios and the LAN connection is enabled.  I'm not really sure how to even begin trying to fix this.  The motherboard is a GIGABYTE GA-965P-DS3.  The other onboard connections seem to be working (my sound is working just fine and the usb ports seem to be up and running).  

Any ideas?

Thanks so much in advance for your help.

---

### Post by youthforlinux on 2007-03-08
put this command into the terminal and post what comes out of it(also make sure that your ethernet cable is plugged in):

```
ifconfig -a
```

---

### Post by BrienVW on 2007-03-08
Ok... the ethernet cord is plugged in and this is the response that I get:


lo           Link ncap:Local loopback
             inet addr:127.0.0.1  Mask:255.0.0.0
             inet6 addr: ::1/128 Scope:Host
             UP LOOPBACK RUNNING  MTU:16436  Metric:1
             RX packets:406 errors:0 dropped:0 overruns:0 frame:0
             TX packets:406 errors:0 dropped:0 overruns:0 carrier:0
             Collisions:0 txqueuelen:0
             RX bytes:30776 (30.0 KiB)   TX bytes:30776 (30.0 KiB)   

sit0        Link ncap:Ipv6-in-IPv4
             NOARP  MTU:1480  Metric: 1
             RX packets:0 errors:0 dropped:0 overruns:0 frame:0
            TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
             Collisions:0 txqueuelen:0
             RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

---

### Post by BrienVW on 2007-03-08
bump...

---

### Post by BrienVW on 2007-03-08
Ok.. so I've been looking through the forum threads to try to get a handle on this.  What i've learned is that it looks like the ifconfig -a response is telling me that the system isn't picking up on my onboard Ethernet... I went to the manual and found that the LAN model is a Marvell 88E8056 phy (10.100/1000 mbit)

This is a pretty popular motherboard, so I'd imagine that there would be out-of-box driver support, but here I am.  Where do i need to go from here?

Thanks again

---

### Post by Mr. C. on 2007-03-08
BrienVW,

The system is not recognizing your onboard Ethernet.  This is likely because you are using a brand new board, and the current system does not have the driver required to work with your card.  That's not to say it doesn't exist; it is likely not packaged with this release of Ubuntu.

ifconfig will give you no useful information, because you've already discovered that there is no card detected - ifconfig can only report on hardware known to the system.

You can run lspci to see all the key information for identifying the card.  Please show that output.

You have identified the chip it seems, but a driver appropriate for that chip needs to be identified.  This can only be done with the information requested above.

MrC

---

### Post by BrienVW on 2007-03-08
Thanks Mr C.

I'm at work now and can post the full result when i get home.  I called to have my roomate give it a try.  It was too long to have him read it all to me over the phone, but here's the ethernet line - maybe this is all that is needed to identify it?  I have no idea if this is helpful at all but...

That line reads:

04:00.0 Ethernet Controller: Marvell Technology Group Ltd. Unknown Device 4364 (rev 13)

As a side note:  I was considering downloading the alpha ubuntu since it may have newer drivers.  Do you think that would be a good option?

Thanks for your help

---

### Post by chili555 on 2007-03-08
I think this may help. A reinstall is not needed. [http://www.ubuntuforums.org/showthread.php?t=365385](http://www.ubuntuforums.org/showthread.php?t=365385) Check posts #9 and #11.

---

### Post by Mr. C. on 2007-03-08
[ edit: the sky2 driver in the 2.6.20 kernel has support for your 4364 chip.  If the link given by the previous poster has this driver, you may be able to use that.  You do want the sky2 driver. ]

If this is just a play install, and you can stomach any bugs and issues, give it a whirl!

However, I looked at Gigabyte's support area, which refers Linux user's to the Marvell site.  At that site, there is an updated driver.  The support even in the 2.6.20 kernel is very old, and I did not find your device ID: 4364 in the kernel source.  You will need to download the driver from Marvell, and build it.  The link is:

[http://www.marvell.com/drivers/driverDisplay.do?dId=153&pId=36](http://www.marvell.com/drivers/driverDisplay.do?dId=153&pId=36)

The README should help you get started.  Once build and installed into your system, your LAN controller should be detected and usable.

MrC

---

