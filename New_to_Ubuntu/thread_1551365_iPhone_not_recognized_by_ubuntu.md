---
title: "iPhone not recognized by ubuntu"
date: 2010-08-12
forum: New to Ubuntu
---

### Post by Violated on 2010-08-12
Hi,

I've got an iPhone 3GS. Until recently, it worked fine. However, some time ago, it stopped working. Ubuntu does not recognize the iPhone, it does not even charge it for that matter. It does recognize an usb stick though.

I've tried reinstalling the iPod/iPhone packages, that didn't solve the problem.

I've got no clue what to do next.

Thanks in advance,
Vio

---

### Post by xtremesupremacy3 on 2010-08-12
First of all I would check your iPhone's USB cable since you say it doesn't charge the iPhone, but regardless of whether Ubuntu recognised it or not, it would still charge.

Try that, perhaps on a different pc. If you are satisfied that that is not the problem, please let us know

---

### Post by Violated on 2010-08-12
I've tried that off course, only forgot to mention it. Stupid me. Other PCs recognize it just fine, with the same usb cable, so that's not the problem.

---

### Post by LowSky on 2010-08-12
Do those other PCs have Ubuntu installed on them?

Your phone stopped working with Ubuntu (or whatever application in Ubutnu it was working with becasue of Apple's restrictive OS. If you want to use your iPhone you will need Windows or OS/X

Sorry but thoses are Apple's rules that you agreed to.

---

### Post by xtremesupremacy3 on 2010-08-12
But didn't Ubuntu allow users to be able to now use their iPhone on here, I have an iPhone 3G and it works just fine

---

### Post by teejmya on 2010-08-12
I have the 3Gs also, but I've never had this issue. Try checking the cable itself for what it was intended for. I know that I also have a cable for the iPhone 4, and it doesn't like charging my phone.

Also check if the Disk Utility and see if the computer can at least see it, if not mount it. (If 10.04, System > Administration > Disk Utility.)

---

### Post by Violated on 2010-08-14
> **teejmya said:**
> I have the 3Gs also, but I've never had this issue. Try checking the cable itself for what it was intended for. I know that I also have a cable for the iPhone 4, and it doesn't like charging my phone.

Also check if the Disk Utility and see if the computer can at least see it, if not mount it. (If 10.04, System > Administration > Disk Utility.)

The cable works fine, so does the spare one.
Windows recognizes the iPhone just fine (tried it at my gf). 
The disk utility does not see the iPhone. I had it connected, on homescreen unlocked. Nothing :(

---

### Post by fun-buntu on 2010-09-30
Sorry for insulting you, but the previous postings show not everything, which is on the net has a lot of merit. A lot of words, but not really any solution.

I also have the same problem. Iphone and Ubuntu 10.04 worked out of the box, but it does not do it anymore.

Yes,
the Iphone is powered up,
the USB cable is plugged in the Iphone and my computer,
the Iphone works with the same computer running MS windows and iTunes just fine,
I am usually not that inexperienced with computers.

If you can still use your Iphone with Ubuntu 10.04, then you may help me and others.

Please tell me, what packages do you you have installed in regard to using the Iphone on Ubuntu?

Please let me and all others know, which packages are essential Iphone - Ubuntu interaction.


It would be very helpful to have just that information and try to solve the issue.

Questions about cables will unfortunately not be any good for this matter.

:confused: frustrated about Iphone and Ubuntu not working together.

---

### Post by fun-buntu on 2010-09-30
Additional Info about this issue:


usb-devices provides the following info

T:  Bus=02 Lev=01 Prnt=01 Port=00 Cnt=01 Dev#= 11 Spd=480 MxCh= 0
D:  Ver= 2.00 Cls=00(>ifc ) Sub=00 Prot=00 MxPS=64 #Cfgs=  4
P:  Vendor=05ac ProdID=1294 Rev=00.01
S:  Manufacturer=Apple Inc.
S:  Product=iPhone
S:  SerialNumber=49fxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxx
C:  #Ifs= 3 Cfg#= 4 Atr=c0 MxPwr=500mA
I:  If#= 0 Alt= 0 #EPs= 3 Cls=06(still) Sub=01 Prot=01 Driver=(none)
I:  If#= 1 Alt= 0 #EPs= 2 Cls=ff(vend.) Sub=fe Prot=02 Driver=usbfs
I:  If#= 2 Alt= 0 #EPs= 0 Cls=ff(vend.) Sub=fd Prot=01 Driver=(none)

serial number for privacy matter changed. 

So this looks like that the Iphone USB is talking to the Ubuntu USB system. But nothing happens after that.

---

### Post by nono240 on 2010-10-23
Same here. Once recognized and working, the next time I plug in, won't work unless I switch to another USB port, and so on. I'm running out of ports ! lol

---

### Post by sahayes on 2010-12-15
I'm not sure if this is helpful, but mine wasn't working "out of the box," but I was able to get Ubuntu 10.04 to recognize my iphone and access music and pictures.  I went into Synaptic Package Manager, and did a search for "iphone."  I have libusbmuxd1, libusbmuxd1-dev, usbmuxd, libimobiledevice0, libimobiledevice1, python-imobiledevice, libimobiledevice-dev, ipheth-utils, ipheth-dkms, ifuse, ifuse-dbg, libplist-dev, libplist++1.    I'm not sure if all of those packages are necessary; perhaps someone more technically-savvy could indicate which of those packages, if any, are unneeded.

---

