---
title: "DLink DSL 200 Rev B Install probs"
date: 2005-07-13
forum: Networking &amp; Wireless
---

### Post by de049 on 2005-07-13
Hi,
How can i install my D Link DSL-200 (Rev B) ADSL modem on my Ubuntu OS?

I have Ubuntu 5.04 which i have just downloaded and installed.

Please advise on locating drivers and relevant procedures.

I have tried the site that explained about getting the eciADSL stuff but i cannot follow it. Im totally new to UBUNTU and am lost with this.

Many thanks guys!!!!

---

### Post by adwait on 2005-07-13
Hey,

Well, as far as I know, some of the modems/routers don't need any configuration at all. They work independently of the OS. Anyway, if that's not the case.......you'll need to visit the website of the manufacturer. Download linux drivers. Install them (if you need help on that, post the file type of the driver file.....). AFter that, run pppoeconf.

---

### Post by de049 on 2005-07-13
I see. The question is, when i do an 'lsusb', it returns info telling me that it clearly sees the Modem. Now, is this enough to assume Ubuntu has enough info to use that device? Or will it stil require driver installs despite already seeing it on the 'lsusb'.

There are no official DLink driversa available for Linux.

Thanks

---

### Post by adwait on 2005-07-13
AFAIK, Ubuntu should be able to see the modem connected.......but I think it still needs the drivers to make the modem work.

---

### Post by de049 on 2005-07-14
Can someone please help me on installing the necessary drivers for my modem. I have just instlled Ubuntu as my first linux OS, but im getting rather frustrated at not being able to install my modem to get to work on my machine. 

If anyone is to help me out, please,please,please keep it as simple as poss.i am new to this, and the little experience i have is on Redhat, and thats very minimal.

Essentially, what im after (seeing the OS sees the usb modem) is how to install the drivers, and then some sort of way to set my ADSL connection settings (i.e. username, password, etc for y PPPoE dialup).

Please help, i need to work from home and desperately require internet connection. Otherwise i will be forced to revert to Windows  :( 

Thanks!

---

### Post by julio77it on 2005-08-09
Hi,

I've the same modem and the same problem too.

Visit 

[http://eciadsl.flashtux.org](http://eciadsl.flashtux.org) 

you'll find a driver for a lot of ADSL USB Modems, even for the DLink 200 Rev B.

Pay attentions, you have to download the the development version (also called Nortek), only available in source tarball.

My problem now is that my Ubuntu installation doesn't have any compiler ... :D

Bye,
Giulio

---

