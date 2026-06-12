---
title: "Stuck with &quot;looking up&quot; websites in Ubuntu 7.04/7.10"
date: 2008-02-18
forum: Networking &amp; Wireless
---

### Post by tirux on 2008-02-18
Hello,

So I just installed a fresh copy of Ubuntu 7.10, and first I got stuck with the "82% scanning for mirrors" problem. I disconnected my ethernet cable and rebooted, and this time I could finally install it.

However, firefox is very slow in displaying websites. I can barely navigate in google, and I can't view any other websites. I can't also connect to MSN or download updates.

I disabled the IPv6 in modprobe.d/aliases, but no luck.
I removed the hosts with IPv6, but no luck either.
I changed the DNS of my router to my ISP or OpenDNS, but still didn't work.
I disabled the IPv6 mode in Firefox, but didn't help at all.

I decided to try Ubuntu 7.04 but the problem persists. So I had to come back to Windows and post this.

I am not sure what's the problem. I use SiS190 100/10 Ethernet Device, and Advantek Networks ABR-241H Router. I updated my Router Firmware but it did nothing to fix this problem.

Any ideas of what can I try? I really want to use Ubuntu, but without internet, it's pretty useless.

---

### Post by tirux on 2008-02-18
Well... I guess I am going to change my router or add another network card and see if it helps.

---

### Post by Iowan on 2008-02-18
Is Gutsy using the router address for DNS?

---

### Post by tirux on 2008-02-18
Yes, it is using the router DNS address. But I also used the OpenDNS and my ISP DNS with no luck, still slow.

I just noticed something odd. I can ping websites without a problem. I can receive all the packets and in 22ms average. Maybe I should try using Opera?

---

### Post by Rogers on 2008-02-18
It's probably your video driver.  if your running some sort of emulation mode **EVERYTHING **appears slow.  Thats why firefox "appears" slow.  It's taking awhile for it to render to the screen.

Take a look at /etc/X11/xorg.conf look under the "Device" section.  What is the driver and what is the identifier?

---

### Post by tirux on 2008-02-18
> **Rogers said:**
> It's probably your video driver.  if your running some sort of emulation mode **EVERYTHING **appears slow.  Thats why firefox "appears" slow.  It's taking awhile for it to render to the screen.

Take a look at /etc/X11/xorg.conf look under the "Device" section.  What is the driver and what is the identifier?

I doubt it's the video driver cause I can see pictures and movies just fine.


I installed Opera and guess what, it didn't work either. Too slow. I can still ping websites or traceroute without a problem, but I can't view the ******* websites. (except google, its pretty fast with gmail, image search, etc.)

I am getting a little frustrated now. :(

---

### Post by Rogers on 2008-02-18
I doubt it's the browser since your ping time is fine.   We can't help you troubleshoot if you **WON'T** provide the details.

---

### Post by tirux on 2008-02-18
> **Rogers said:**
> I doubt it's the browser since your ping time is fine.   We can't help you troubleshoot if you **WON'T** provide the details.

Well I tried to access /etc/X11/xorg.conf but I didn't find it in Ubuntu 7.04. Is it case sensitive?

---

### Post by tirux on 2008-02-18
Ok I found out now.

Identifier: nVidia Corporaion G71 [GeForce 7900 GS]
Driver: nv
BusID: PC:1:0:0

---

### Post by Rogers on 2008-02-18
[http://wiki.x.org/wiki/nv](http://wiki.x.org/wiki/nv)

Looks like the nv driver is culprit IMHO.  Prove me wrong....  Go to: 

System \ Administration \ Restricted Drivers Manager 

Open it and load the NVIDIA restricted driver.  It should be in the list.  You will need to reboot.  Let me know how that works for you... at the very least you'll have a LOT faster video and the ability to run OPENGL games and such :-)

---

### Post by tirux on 2008-02-18
I finally fixed it.

Apparently Ubuntu doesn't like SiS190 ethernet chip. I installed a D-Link Ethernet card and the internet is fast already, without even the need to disable IPv6.

---

