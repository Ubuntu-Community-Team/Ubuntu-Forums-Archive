---
title: "USB Wireless Card."
date: 2008-01-13
forum: Networking &amp; Wireless
---

### Post by liquidfunk on 2008-01-13
I'm looking for a new wireless card. USB Preferably. The name and product number would be very helpful too. One that works straight away, out of the box as such. As I'm tired of my current one cutting out after a few hours. 

 Any ideas?

---

### Post by liquidfunk on 2008-01-22
Anyone?

---

### Post by Hightide on 2008-01-22
HI Liquidfunk

I have a Netgear WG111 USB adaptor connected to a Netgear ADSL Modem/Router which worked 'out of the box' with Gutsy.

Have a look
[http://www.amazon.co.uk/Netgear-WG111-Wireless-54Mbps-Adapter/dp/B0002LHX8O/ref=pd_bbs_sr_1?ie=UTF8&s=gateway&qid=1201038406&sr=8-1](http://www.amazon.co.uk/Netgear-WG111-Wireless-54Mbps-Adapter/dp/B0002LHX8O/ref=pd_bbs_sr_1?ie=UTF8&s=gateway&qid=1201038406&sr=8-1)

hope this helps

:)

---

### Post by jerome1232 on 2008-01-22
I've got a Belkin F5D7050v4 that works out of box on gusty, it's usb

---

### Post by liquidfunk on 2008-02-02
Your Netgear WG111 USB recommendation doesn't work at all. 

 I'm currently using LinuxMint Fluxbox, with the Wicd manager, didn't find my network at all.

 Tried it on the Live CD of Gutsy, still nothing?

 Do you think it may be my router?

---

### Post by Hightide on 2008-02-02
hi liquidfunk

its not your router. have a look at this Netgear wg111v2 [thread]("http://ubuntuforums.org/showthread.php?t=329299") particularly further down the page.

regards
:)

---

### Post by liquidfunk on 2008-02-02
That doesn't help. 

 Are you sure we have the same card? I have the WG111v3 when I do a  

lsusb | grep NetGear

 I get 

Bus 001 Device 007: ID 0846:4260 NetGear, Inc.

On the page it says the output is 0846:4240 for Version 2. 

 It also says to download and extract the driver. My driver is a .exe file. I tried with Wine in the hope it would give the .inf file. Not at all.

 Help!

---

### Post by sennep on 2008-02-02
I think you have to use ndiswrapper for that one.

I found this link on the forum to some drivers for WG111v3 that is not stored in an exe. 
[http://www.avengergear.com/upload/WG111v3.tar.bz2](http://www.avengergear.com/upload/WG111v3.tar.bz2)

Note that I haven't actually tried them myself so I can't say whether they will work or not.

Also, you have to untar that file, by using the command ```
tar xvvf YOUR_FILENAME_HERE.tar.bz2
```

---

### Post by liquidfunk on 2008-02-03
Your a genius, it works like a dream.

 Thanks

---

