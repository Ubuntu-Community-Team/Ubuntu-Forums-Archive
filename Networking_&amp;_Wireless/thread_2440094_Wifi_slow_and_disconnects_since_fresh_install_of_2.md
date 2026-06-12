---
title: "Wifi slow and disconnects since fresh install of 20.04"
date: 2020-04-05
forum: Networking &amp; Wireless
---

### Post by wildmanne39 on 2020-04-05
I did a fresh install of Ubuntu Mate 20.04 daily iso, since then my wifi has been slow and disconnects, I have made all the changes in my router that AT&T allows and I still have a very slow connection at 2mbps with 18.04 it was 40mbps, I have set some driver parameters but it still has not helped, I set a fixed channel of 1 in my router but the wireless info shows I am on channel 11, about half the time when I run the wireless script I only see 2 networks and the other half I see 18 networks show up, sometimes it shows my network 4 times and others only once, in dmesg sometimes I see a lot of connects and disconnects to different instances of my network and other times I see connection to my network once, it seems something strange is going on, I am not feeling well so I am tired of trying to track this issue down and fix it myself, I appreciate any help I can get.

I am connected to a wifi extender, I have been using it for a few months with no issue, it this it in the network scan:

> <MAC '\00\00\00\00\00\00\00\00\00' [AC2]>  Infra  11    2462 MHz  130 Mbit/s  100     &#9602;&#9604;&#9606;&#9608;  WPA2      no

I just ran a new script and it shows two networks, the one I ran thirty minutes earlier showed 18 networks.

I also have a TP-Link AC1200 usb adapter which keeps disconnecting with the driver that comes installed and I tried different versions of the driver from github and it installs but afterwords does not work and my internal wifi stopped working as well so I hope to just fix the internal device, when I first installed and connected to the internet with 20.04 the speed was 35mbps for about five ten minutes.

[https://pastebin.com/Y3jABhMm](https://pastebin.com/Y3jABhMm)

Thanks in advance.

---

### Post by wildmanne39 on 2020-04-06
bump.

---

### Post by praseodym on 2020-04-06
What kind of extender is that? Did you configure it properly?

Add the MAC-address of the stronger AP to BSSID of the profile and re-connect.

---

### Post by wildmanne39 on 2020-04-06
It's an Air 4920 from A T&T, I had it installed when I switched to A T&T internet last December, it plugs into the wall with an ethernet cable instead of connecting to the router through wifi, no configuration was required and it worked flawlessly with 18.04, I think all I did was set a couple of driver parameters when I installed 18.04 about three years ago but I do not remember for sure, I will set the  MAC-address BSSID and see if that helps.

Thanks praseodym, good to see you.

---

### Post by wildmanne39 on 2020-04-06
I set the mac address, here is new wireless info after making that change,  it did add a lot more to dmesg:

[https://pastebin.com/ArznsCWM](https://pastebin.com/ArznsCWM)

I now see:
> rtl8188ee 0000:03:00.0 wlo1: disabling HT as WMM/QoS is not supported by the AP
which was not there before and it shows I am connected to two networks at the same time, the speed has not improved any, I have been thinking about backporting the 18.04 driver and see if that fixes the issue but I have not found directions to do that and I am short on time and energy so I have not pursued it yet. I have seen that message while helping users before, I have already changed everything I can in my router as far as I know.

---

### Post by wildmanne39 on 2020-04-07
I have searched here:

[https://packages.ubuntu.com/bionic-backports/](https://packages.ubuntu.com/bionic-backports/)

for rtl8188ee, I am thinking it may be in linux firmware file but if it is I do not have the name exactly right because I still can not find it and I do not see the rtl8188ee driver listed, if someone can point me to the backport driver for 18.04 I would appreciate it.

Thanks

---

### Post by wildmanne39 on 2020-04-08
I tried every driver parameter one at a time and changed every setting that I could in the router to what is recommended, set to google DNS server, used the MAC address, tried to set a fixed channel, even though in the router configuration page the channel was set to 1 I was always connect to 11 my internal device and my usb adapter both use rtlwifi, when I installed a new driver for the internal and again for the usb adapter my wifi completely stopped working, dmesg said something like the updated rtlwifi taints kernel, I ended up reinstalling 18.04 to get the issue resolved, it still is not as fast as it should be but it is a lot better, the driver for the usb adapter is performed very poorly, slow and discounted from a few seconds to every two minutes.

Does anyone know if I can install an intel wifi device in my hp laptop? if I remember correctly some manufacturers make it hard.

[https://support.hp.com/us-en/product/hp-pavilion-17-g100-notebook-pc-series/8499304/model/8961418/manuals](https://support.hp.com/us-en/product/hp-pavilion-17-g100-notebook-pc-series/8499304/model/8961418/manuals)

Thanks

---

