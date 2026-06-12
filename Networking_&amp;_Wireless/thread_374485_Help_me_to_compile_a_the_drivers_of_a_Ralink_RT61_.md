---
title: "Help me to compile a the drivers of a Ralink RT61 wireless card offline"
date: 2007-03-02
forum: Networking &amp; Wireless
---

### Post by bestiarosa on 2007-03-02
Hello,
I've just performed a fresh Edgy Eft install on my computer and I wanted to setup the wifi card. I have a RalinkRT61 and there's a well done [[COLOR="Navy"]help here[/COLOR]]("https://help.ubuntu.com/community/Rt61WirelessCardsHowTo?action=show").
I have to download all I need manually from [[COLOR="navy"]packages.ubuntu.com[/COLOR]]("packages.ubuntu.com") using another computer as I'm offline as long as I can't get this wireless card to work so I can't just ```
sudo apt-get install build-essential gcc linux-headers
``` It'd be too easy. This said, I can't seem to get the driver to compile. I've followed the instructions on the [[COLOR="Navy"]help page[/COLOR]]("https://help.ubuntu.com/community/Rt61WirelessCardsHowTo?action=show"): I have downloaded and installed build-essential-11.3, gcc-4.1.1, linux headers-2.6.17.10 and linux-headers-2.6.17.11 (and all the other linux-headers related packages) but still I get this error when I make all:

> make[1]: Entering directory `/usr/src/linux-headers-2.6.17-10-generic'
make[1]: *** No rule to make target `DWG-510'.  Stop.
make[1]: Leaving directory `/usr/src/linux-headers-2.6.17-10-generic'
make: *** [all] Error 2

But I have installed and reinstalled everything! Something else must be missing then, I think. However, if I run ```
./Config
```this is the output:

> -------------------- Ralink RT61 Station Configuration -------------------- 

  Linux kernel source directory [/usr/src/linux-2.6.17-10-generic]: 
 
Linux source tree '/usr/src/linux-2.6.17-10-generic' is incomplete or missing!

Configuration failed

What on Earth is linux-2.6.17-10-generic anyway? I wonder what the configuration program is looking for. I'd be also curious to know which packages are actually downloaded if you type ```
sudo apt-get install build-essential gcc linux-headers
``` on a computer with Internet access so I can check if I've missed something...

Thanks for any help...

[SIZE="1"]P.S. The irony is I had those drivers compiled quite easily a few days ago and then I broke my system trying to do some backup. Now I can't have them compiled for the life of me. Sigh![/SIZE]

---

### Post by port on 2007-03-19
I'm having the same problem installing my Belkin F5D7050, when i run make it tells me:
"No rule to make target `WUSB` Stop.
Im also using 2.6.17-11-generic

---

