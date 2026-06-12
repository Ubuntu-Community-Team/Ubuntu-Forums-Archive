---
title: "Belkin F5D7001 (Broadcom Chipset)"
date: 2005-06-19
forum: Networking &amp; Wireless
---

### Post by smedstadc on 2005-06-19
Hi, I'm having one helluva time to get this particular piece of hardware to play nice with ndiswrapper. I've read and re-read multiple posts and howtos on the Ubuntu forums on the subject of getting broadcom chip based network card configured with ndiswrapper and try as I might I can't get it to work properly.

I've found the guide at URL: [http://ubuntuforums.org/showthread.php?t=25683&highlight=broadcom+belkin](http://ubuntuforums.org/showthread.php?t=25683&highlight=broadcom+belkin) particularly helpful. By following it I've gotten as far as getting my wlan0 available for configuration via my System > Administration > Networking] dialogue.

Though, I have two problems. When Ubuntu is booting, the "Initializing Network Devices" step takes a very long time, and I usually need to ^C at that point to continue booting. Once I'm logged in a ```
$sudo modprobe ndiswrapper
``` is usually required to get the device to show up properly anywhere.

Once I get it working, my main problem is, I cannot configure it to work with my network and actually allow me access to the internet. My router doesn't have any wireless protection settings, or anything else that would interfere with connectivity enabled at the moment. Everything is pretty much at the factory defaults, except for one thing: I have reserved the IP address of 192.168.1.4 for hardware that has my wireless cards MAC address.

Right now I'm at the end of my rope. I've been sitting on this problem and working through it as patiently as I can for more than a month, and I'm about to just throw out my belkin wireless card and buy something more compatable.

Can anyone help me, ideally another user with a Belkin F5D7001?

---

### Post by smedstadc on 2005-06-20
Update: Removed ndiswrapper, its configs and devices, reinstalled a newer package. Used the device drivers from the ndiswrapper phpwiki. Now the device is recognized more properly, network doesn't hang on boot anymore and the device shows up normally in the networking list, however, DHCP does not work. I've removed any funky settings from my router to make it easier to determine what is wrong, but I still can't connect to the network. And configuration seems to stall for long periods of time when I change settings.

Anyboy have any experience configuring these cards, or are there any gnome utilities that make detecting and connecting to wireless networks simpler?

---

### Post by tmmuk on 2005-09-25
I have a f5d7001uk and I couldn't get it to work at all (kubuntu 5.04)

EDIT: now I did using the recommended driver for df5d7001 on ndiswrappers site

( it is a bcmwl5a from dell)

---

