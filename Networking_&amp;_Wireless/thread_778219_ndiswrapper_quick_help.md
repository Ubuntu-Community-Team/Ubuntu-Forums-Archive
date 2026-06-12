---
title: "ndiswrapper quick help"
date: 2008-05-01
forum: Networking &amp; Wireless
---

### Post by jgriffinpark on 2008-05-01
Hi,

I just did a fresh install of 8.04 on my HP Pavilion dv6405us laptop. Under 7.10, I had ndiswrapper working flawlessly. Upgrading, however, messed up the wireless card, graphics card, and sound, for some reason. Under the fresh install, I'm trying to get ndiswrapper configured again: I have compiled the package from source and installed the driver (bcmwl5) and run modprobe. It still doesn't work, and the output of iwconfig doesn't show wlan0 at all.

ndiswrapper -l shows that bcm43xx is present as alternate driver, but it was also listed when it was working under 7.10, so I don't think that this is the problem. Any ideas? Much appreciated.

---

### Post by markeee on 2008-05-01
hi buddy

have you tried sudo modprobe bcm43xx

Thats how I used to activate my bcm43xx wifi card on Ubuntu 7.04 using ndis

mark

---

### Post by Goombie on 2008-05-02
I used to use ndiswrapper, but I use the fw-cutter package now. It works just as well, with comparable connection speeds. And, it took me three minutes to install, instead of the three hours ndiswrapper took on Gutsy. :)

---

### Post by Ayuthia on 2008-05-02
You will also need to blacklist b43 and before loading ndiswrapper (modprobe ndiswrapper), you will need to unload ssb (modprobe -r ssb).

---

### Post by jgriffinpark on 2008-05-02
Hello all:

Thanks for your replies, I have blacklisted b43, but have not removed ssb. I'll try that when I get home. 

Also, the fwcutter package didn't work under 7.10, but it is working under Hardy? I have no ethernet connection so would I be able to install those from a .deb package if ndiswrapper refuses to work? Thanks much.

---

### Post by Ayuthia on 2008-05-02
> **jgriffinpark said:**
> Also, the fwcutter package didn't work under 7.10, but it is working under Hardy? I have no ethernet connection so would I be able to install those from a .deb package if ndiswrapper refuses to work? Thanks much.
The answer is a maybe for the fwcutter.  This kernel is experiencing some problems with some of the Broadcom chipsets.  If you post your lspci -nn, we can tell you if yours might work or not.  The b43-fwcutter is on the liveCD if I recall correctly, but it does not have the firmware.  You can get the firmware (there are two files) from:
[http://downloads.openwrt.org/sources/wl_apsta-3.130.20.0.o](http://downloads.openwrt.org/sources/wl_apsta-3.130.20.0.o)
[http://downloads.openwrt.org/sources/broadcom-wl-4.80.53.0.tar.bz2](http://downloads.openwrt.org/sources/broadcom-wl-4.80.53.0.tar.bz2)
It will ask you if you want it to install it for you or not so make sure that you say no or else it will get stuck.

---

