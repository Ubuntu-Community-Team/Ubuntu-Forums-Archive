---
title: "hp pavilion dv2500 wireless connection"
date: 2009-11-24
forum: New to Ubuntu
---

### Post by kowalsky on 2009-11-24
hi all,
I just installed ubuntu 9.10 on a HP Pavilion dv2500 and I had the very pleasant surprise to see that all devices were working less the wireless card.
My question(s) are as follows:
1. how do i get the brand/model of the wireless device? is it even possible to query for it from inside ubuntu? - i guess the alternative is to go to hp's site but somehow i doubt that they advertise this kind of information
2. once I get the info what do I do next?

I am trying to get to speed with Linux but I don't think I can do it on my own,
Thanks,
kowalsky

---

### Post by Sealbhach on 2009-11-24
Hi, first go to System/Administration/Hardware Drivers and see if there is a driver there you can activate. If not, run this command in a terminal:
```

lshw -C network
```

and copy and paste the results back here.

.

---

### Post by kowalsky on 2009-11-24
thanks Sealbchach,
the hardware drivers do list 2 Broadcom wireless drivers:

1. Broadcom B43 wireless driver (no license, tested by Ubuntu developers)
fwcutter is a tool which can extract firmware from various source files; it is written for BCM43xx driver files

2. Broadcom STA wireless driver (proprietary, tested by Ubuntu developers)
These package contains Broadcom 802.11 Linux STA wireless drivefor use with Broadcom's BCM4311-, BCM4312-, BCM4321-, andBCM4322-based hardware

From all the above I understand I have 2 drivers, one of them probably needs some third party to activate.

How do I decide if any of them applies?

Thanks,
kowalsky

---

### Post by northd_tech on 2009-11-24
Hi kowalsky.  From what I remember you probably need to "blacklist" the b43 driver and use the proprietary "STA" driver for the newer Broadcoms.  My HP DV98xx has a Broadcom 4321AG (which is sometimes called a 4328 by Linux), and the "bcwl6.inf" Windows driver worked quite well for my WiFi using ndiswrapper.

I posted quite a bit on a few threads here about a month ago on the Broadcoms.  I've got too many tabs open right now, so you might need to search a little through the following links:

[http://ubuntuforums.org/showthread.php?t=896713](http://ubuntuforums.org/showthread.php?t=896713)

[http://ubuntuforums.org/showthread.php?t=1314852](http://ubuntuforums.org/showthread.php?t=1314852)

[http://ubuntuforums.org/showthread.php?t=1056446](http://ubuntuforums.org/showthread.php?t=1056446)

[http://ubuntuforums.org/showthread.php?t=1332242](http://ubuntuforums.org/showthread.php?t=1332242)

---

### Post by kowalsky on 2009-11-24
thanks northd_tech,
ok,
so i did the lshw -C network: 

description: Network controller
       product: BCM4311 802.11b/g WLAN
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:04:00.0
       version: 02
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: driver=b43-pci-bridge latency=0

I'll definitely look at the links, hopefully I'll figure out what to do ... it's slowly coming back to me :-)

thanks again,
kowalsky

---

### Post by northd_tech on 2009-11-24
Hi again kowalsky- I got a few of those unruly tabs taken care of (on yet another brand of WiFi Linux problem- much worse for 64-bit Realtek BTW).

I looked up one of my older posts, and it even has a direct link where you can download the proper STA driver directly from Broadcom- see my post #10 (and this shorter thread):

[http://ubuntuforums.org/showpost.php?p=8175070&postcount=10](http://ubuntuforums.org/showpost.php?p=8175070&postcount=10)

I'm reasonably sure that your Broadcom is basically the same thing as a 4312 (and I think there was a 4310 too).  Actually my 4321AG will use the same older "bcmwl5.inf" Windows drivers that yours takes (without the faster 802.11 Draft-N speeds), if you decided to go the ndiswrapper/Windoze way.

The native Linux STA driver is probably the best way though, from what I've read.  Ndiswrapper(windows drivers) has worked pretty well for me for over a year now though on my HP laptop.

Now that accursed Toshiba I'm working on tonight though... :o

---

### Post by kowalsky on 2009-11-24
thanks a bunch, nordthd_tech,
i'll go for the driver from Broadcom - I will confirm if it worked, but that's got to be sometime tomorrow ...

kowalsky

---

### Post by northd_tech on 2009-11-24
Actually, a guy just barely had the exact Broadcom 4311 and it sounds like it just took a few mouse clicks for the "STA" fix- check this thread out:

[http://ubuntuforums.org/showthread.php?t=1334754](http://ubuntuforums.org/showthread.php?t=1334754)

One thing you'll want to beware of- if you keep multiple Linux kernels- you will need to install/compile/whatever for each of those kernel setups individually (and it's always good to have a "spare" wireless configuration that works in case an "update" bites you).

---

### Post by kowalsky on 2009-11-30
northd_tech,
thanks a bunch - I used the link below:

[http://www.broadcom.com/support/802.11/linux_sta.php]("http://www.broadcom.com/support/802.11/linux_sta.php")

the wireless card is working just fine.

thanks again,
kowalsky

---

