---
title: "ACX111 aircrack patch"
date: 2008-02-01
forum: Networking &amp; Wireless
---

### Post by Scott8855 on 2008-02-01
Running Gutsy with a WG311v2, it works great, I disabled the network configuration tool.  I do not know how to find out what driver I'm running, as far as i know i loaded the ACX111 20070101 driver, but forgot to patch it with the aircrack patch so that I can inject packets.  

1. How can i see what driver is loaded?

2. How do i remove the current driver so I can re-install it after i have patched it?

I am able to put the card into monitor mode, and confirmed it worked by running wireshark, this is the error I get when I try to run airodump-ng on the interface.

Unsupported hardware link type    0 - expected ARPHRD_IEEE80211
or ARPHRD_IEEE80211_PRISM instead.  Make sure RFMON is enabled:
run 'ifconfig wlan0 up; iwconfig wlan0 mode Monitor channel <#>'

I have tried putting the interface into monitor mode prior to starting airodump-ng and get the same results. I'm guessing this problem is related to my driver possible not being patched, but from what I have read the patch is for injection purposes and that should not effect airodump.  Any help would be great, thanks.

Scott

---

### Post by pytheas22 on 2008-02-01
I believe that that card has an atheros chipset.  Atheros cards work a little strangely; they create "virtual" interfaces all tied to the wifi0 interface, and you can't change the mode of an existing virtual interface; instead you have to destroy it and create a new interface in the mode you want.  To get an interface in injection mode, I think that the commands are:

```

sudo -s
wlanconfig ath0 destroy
wlanconfig ath0 create wlandev wifi0 wlanmode monitor
ifconfig ath0 up
airodump-ng ath0

```

If that doesn't work, you might not have the madwifi tools package installed: just open Synaptic and search for madwifi-tools and install that package.  This package, I believe, provides the "patch" that enables injection...for most other chipsets, you would need to compile the patch, but with atheros it's conveniently available via the package manager.

Also it's generally a good idea to kill Network Manager and its daemon when running airodump, because they like to interfere.

Hope this helps

---

### Post by pytheas22 on 2008-02-01
Ignore all that, I think that your card doesn't actually have an atheros chipset (WG311v1 does, not v2).  According to [http://www.linuxcompatible.org/thread30926-1.html](http://www.linuxcompatible.org/thread30926-1.html) , you download the driver from [http://acx100.sourceforge.net/](http://acx100.sourceforge.net/) .  There are directions there on how to install the driver.  It should automatically replace the driver you currently have; there's no need to remove anything.  The driver from sourceforge might also support injection on its own (generally the drivers that ship with Ubuntu are modified to disable injection for whatever reason), but if it doesn't, search the aircrack-ng site for the injection patch for your card.  When you install the patch, again, there's no need to remove anything: just compile the patch and you should be all set.  If you have trouble, post.

---

### Post by pytheas22 on 2008-02-01
[http://www.aircrack-ng.org/doku.php?id=acx&DokuWiki=583bb273bc5b7cdc2c5dfce82ee43d4b](http://www.aircrack-ng.org/doku.php?id=acx&DokuWiki=583bb273bc5b7cdc2c5dfce82ee43d4b)

---

### Post by IamAcoconut on 2008-02-18
I get the very same error.

My interface is **Texas Instruments ACX111**. I had been using it with **tnet1130** via ndiswrapper, but I've recently replaced it with acx. 
airodump-ng worked for a while yesterday, but now it doesn't. Why on earth? acx_pci IS still seen as the driver.

> **pytheas22 said:**
> [http://www.aircrack-ng.org/doku.php?id=acx&DokuWiki=583bb273bc5b7cdc2c5dfce82ee43d4b](http://www.aircrack-ng.org/doku.php?id=acx&DokuWiki=583bb273bc5b7cdc2c5dfce82ee43d4b)
They say here 
[http://acx100.sourceforge.net/wiki/Patch_2.6.22]("http://acx100.sourceforge.net/wiki/Patch_2.6.22") to save this patch to acx-20070101 directory,  I've got no such directory...
```
~$ ls /lib/modules/2.6.22-14-generic/ubuntu/wireless/acx/
acx.ko
~$ ls /lib/firmware/2.6.22-14-generic/acx/
0.1.0.11  0.4.11.9  1.0.9     1.2.1.34  1.9.8.b   default
0.4.11.4  1.0.7     1.2.0.30  1.7.0     2.3.1.31  readme.txt
```Where do I apply this patch?


PS. > How can i see what driver is loaded?```
lshw -C network
```

---

