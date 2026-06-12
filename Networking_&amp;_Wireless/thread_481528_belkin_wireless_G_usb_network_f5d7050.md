---
title: "belkin wireless G usb network f5d7050"
date: 2007-06-22
forum: Networking &amp; Wireless
---

### Post by mummra1 on 2007-06-22
Hi everyone,
 I have the aforementioned belkin wireless usb adapter running on ubuntu desktop 6.0.6. The driver according to windows is rt2500usb.sys
In ubuntu it shows as rt73. I have not actually installed ubuntu, but was just running the os off of the cd to work out these kinds of issues.

Either way, ubuntu is not seeing the wireless adapter as a network such as ath0. I tried installing the ndiswrapper and it seemed to work until I tried to run ndiswrapper -i ~/drivers/rr2500.sys. I got an error message saying it could not find ndiswrapper. Well I'm really at a loss here and if anyone has any experience with belkins working on ubuntu I would be most grateful. Thanks in advance...

---

### Post by stchman on 2007-06-22
> **mummra1 said:**
> Hi everyone,
 I have the aforementioned belkin wireless usb adapter running on ubuntu desktop 6.0.6. The driver according to windows is rt2500usb.sys
In ubuntu it shows as rt73. I have not actually installed ubuntu, but was just running the os off of the cd to work out these kinds of issues.

Either way, ubuntu is not seeing the wireless adapter as a network such as ath0. I tried installing the ndiswrapper and it seemed to work until I tried to run ndiswrapper -i ~/drivers/rr2500.sys. I got an error message saying it could not find ndiswrapper. Well I'm really at a loss here and if anyone has any experience with belkins working on ubuntu I would be most grateful. Thanks in advance...

I have read that the USB wireless adapters have limited support from madwifi.

---

### Post by bren on 2007-06-22
does your belkin have an ethernet port?
do you have an ethernet cable?
is this router configurable by webpage?

bren

---

### Post by mummra1 on 2007-06-22
The Belkin adapter is talking to a linksys router, I believe.  But for now this is the least of my problems.  I know that ubuntu sees recognizes the fact that it is a belkin wireless adapter when I run lsusb.  The problem is that it doesn't see it in the System->Adminstration->Networking.  

So far I've seen two strategies to handle this:

  1) Go with ndiswrapper to trick linux into recognizing the native windows inf and sys files as linux drivers.  This involves installing ndiswrapper.  

2) Screw ndiswrapper and go with the native linux drivers, as described in:
[http://doc.gwos.org/index.php/Rt2x00drivers](http://doc.gwos.org/index.php/Rt2x00drivers)

So far I haven't completely installed ubuntu; I only ran it off the cd to work out hardware testing, mainly b/c I cannot get online (yet) when ubuntu is running.  It seems like I should take the chance and do the install, but before I do this I want to make sure that I can  upgrade the build-essentials and kernel headers w/o internet access, in other words from the cd. Is this possible?  Any logical step-by-step instructions would be fantastic.  I'm new to Ubuntu, but do have some Unix/Linux experience.  Thanks again in advance.

---

### Post by jairtrejo on 2007-06-22
You are not using the correct driver... see, there is a problem with the driver tha ubuntu uses by default for your kind of adapter. I had the ame problem, and solved it using the serial monkey rt73-usb driver. google it around

---

### Post by mummra1 on 2007-06-22
right.  I was wondering about why it was defaulting to the rt73 as opposed to  2500.  Should  I still use the ndiswrapper to install the driver?  Thanks.

---

