---
title: "Ethernet not working on fresh Ubuntu 14.04 LTS install"
date: 2016-01-05
forum: Networking &amp; Wireless
---

### Post by PamelaPopo on 2016-01-05
Dear all,

I have an old Dell Latitude D520 on which Ubuntu 12 LTS has been running for a couple of years. Yesterday I decided that I should upgrade to 14.04 LTS, so I went ahead and I installed it from a live DVD. 
I ended up with no internet connection, either through wireless (which didn't surprized me much) nor through ethernet. 
I did a new install this morning, this time from a USB stick, and I ended up with the same problem. 

What is strange is that the ethernet controller does work in a live environment, and during the installation process (Ubuntu was able to download packages).
The cable is working perfectly fine (I use it everyday with a Raspberry Pi), and the ethernet port on the computer is also working fine. My ethernet controller is a Broadcom BCM4401 - B0 100Base - TX.

Without any access to internet I dan't update the system, nor download a proprietary driver for the wireless card, so I'm pretty much stuck ! I looked around on the web but I couldn't find anything usefull.

I did find a couple of commands to try :
```
ifconfig
``` : doesn't show any eth0.
```
sudo lshw -C network
``` : tells me that the ethernet controller is "UNCLAIMED".

I get the feeling that it's no big deal, but without access to the internet I don't know what to do.

Thank you in advance.



If that matter I've installed Ubuntu 14.04 LTS 32-bit (I only have 1GB of RAM).

---

### Post by jeremy31 on 2016-01-05
Post the result for ```
lspci -nnk | grep -iA2 net; dkms status
```

---

### Post by PamelaPopo on 2016-01-06
Here's the output of the command above :
```
02:00.0 Ethernet controller [0200]: Broadcom Corporation BCM4401-B0 100Base-TX [14e4:170c] (rev 02)
	Subsystem: Dell Device [1028:01d4]
02:01.0 CardBus bridge [0607]: O2 Micro, Inc. Cardbus bridge [1217:7135] (rev 21)
--
0c:00.0 Network controller [0280]: Broadcom Corporation BCM4311 802.11b/g WLAN [14e4:4311] (rev 01)
	Subsystem: Dell Wireless 1390 WLAN Mini-Card [1028:0007]
	Kernel driver in use: wl
bcmwl, 6.30.223.248+bdcom, 3.19.0-25-generic, i686: installed
```


There seems to be something wrong with this version of Ubuntu (14.04 LTS 32-bit, at least on my computer) that goes beyond the ethernet controller, because it also won't shutdown. I see something like "Waiting for all processes to stop" (or something close), and I see the white/red dots of the Ubuntu splashscreen behind, and it just won't stop (yesterday I waited 3 hours before forcing my machine to shutdown).

---

### Post by jeremy31 on 2016-01-06
This should get the ethernet back working ```
sudo apt-get install firmware-b43-installer
sudo apt-get remove bcmwl-kernel-source broadcom-sta-common broadcom-sta-dkms
```

Reboot, ethernet and wireless should work unless you have b44 and b43 blacklisted in a second file

---

### Post by PamelaPopo on 2016-01-11
Thank you for your reply. I'm sorry I've been unfaithful and I've installed Debian instead. The fact that the computer wouldn't shut down (on top of the internet connection issue) made me do it.

---

