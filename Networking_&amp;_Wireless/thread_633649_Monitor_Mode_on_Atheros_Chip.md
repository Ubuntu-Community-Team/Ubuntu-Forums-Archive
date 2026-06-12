---
title: "Monitor Mode on Atheros Chip"
date: 2007-12-06
forum: Networking &amp; Wireless
---

### Post by AltF4Warrior on 2007-12-06
Hi,

    _What I'm using:_ 
    I'm running Ubuntu 7.10 (Gutsy) with a Belkin F5D7000 v5100 pci wifi card. That card has an Atheros chipset. Doing a bit of web research told me that it's AR5005G, bu the full writing on the actual chip says:
- Atheros
- AR 2413A-001
- 8502008
- D641 
(Just in cse any of that is necessary)
I'm using the default drivers that came with Gutsy.

   _What I'm trying to do:_
    Put the card into monitor mode.

    _What I can manage to do:_
    A previous thread was of a bit of help, but it didn't fully solve the problem. If I go right out and say:
**sudo ifconfig ath0 mode monitor**
It tells me it's an invalid argument. Apparently this problem is shared with other Atheros users, though. Instead, I can make a new interface:
**sudo wlanconfig ath create wlandev wifi0 wlanmode monitor**
And it successfully creates an "ath1" that is in monitor mode. I can see it under **iwconfig** and it even says monitor mode. However, the bitrate is at zero, and I can't ever get any packets from it. Even after:
**sudo ifconfig ath1 up**
It appears to be unusable.

Also, the ath0 is by default in managed mode, and I can connect just fine with it. I'm using it right now.

  Is it just a matter of changing the bitrate? If so, I haven't been able to do it. How might I? Or is it something completely different?

Thanks in advance.
Ubuntu Novice,
-AltF4

---

### Post by kabeeth on 2007-12-06
I have the same problem in same version of ubuntu 7.1 
i try to reinstall the madwifi to work in monitor mode so when i trying  to 
remove the old module it tell me that 
module wlan ...
and module Wlan_scan_st ...
are running so i think these are make the card always in managed mode so how someone can stop these modules from running

---

### Post by AltF4Warrior on 2007-12-07
Okay,

   Well, I looked through the man pages for "wlanconifg" and was able to put the bit rate for my created interface to 54 Mb/s. But that didn't solve the issue.

I'm still not able to put the default interface (ath0) into monitor mode, and when I create a new interface in monitor mode it doesn't recieve any packets.

Certainly I'm not the only one trying to do this?

Thanks again,
-AltF4

---

### Post by tturrisi on 2007-12-07
> **AltF4Warrior said:**
> Okay,

   Well, I looked through the man pages for "wlanconifg" and was able to put the bit rate for my created interface to 54 Mb/s. But that didn't solve the issue.

I'm still not able to put the default interface (ath0) into monitor mode, and when I create a new interface in monitor mode it doesn't recieve any packets.

Certainly I'm not the only one trying to do this?

Thanks again,
-AltF4
Receive any packets from where & how?  Kistmet?  Wireshark?
Wjhat you are describing is not a bug, it is how madwifi drivers work.
Madwifi always creates 2 interfaces, a parent wifiX and a viryual interface athX.
If you have ath0 in managed mode and try to create a monitor mode interface you will get ath1.  You must forst destroy the ath0 interface,

wlanconfig ath0 destroy
wlanconfig ath0 create wlandev wifi0 wlanmode monitor
ifconfig ath0 up

If the above does not work then it is probably due to the piece of crap (my opinion) network-manager program packaged w/ ubuntu.  Kill the network-manager process and its daemon first.

---

### Post by kabeeth on 2007-12-07
What I mean that there is a piece of software are running with the system start for scaning essid of networks and thats make the card always in managed mode like these appletes that come with this version 
i try to stop these applets but that didn't solve it, still something put the card in managed mode.
and in all previos virsion of ubuntu I put the ath0 and not anything else in monitor mode and didn't need to create another interface but with this version i really don't know how to do it
and it's a real problem because the driver support the monitor mode but something interfere with it

---

### Post by AltF4Warrior on 2007-12-08
> Receive any packets from where & how? Kistmet? Wireshark?
Wjhat you are describing is not a bug, it is how madwifi drivers work.
Madwifi always creates 2 interfaces, a parent wifiX and a viryual interface athX.
If you have ath0 in managed mode and try to create a monitor mode interface you will get ath1. You must forst destroy the ath0 interface,

wlanconfig ath0 destroy
wlanconfig ath0 create wlandev wifi0 wlanmode monitor
ifconfig ath0 up

If the above does not work then it is probably due to the piece of crap (my opinion) network-manager program packaged w/ ubuntu. Kill the network-manager process and its daemon first.

Yup, that did the trick.

I went and disabled the Network-Manager's daemon, and then ended the process. After that, when I create an interface in monitor mode it actually works!

Oh, and yea, I was checking it in wireshark and airodump. 

Thanks a lot for the help!
-AltF4

---

### Post by tturrisi on 2007-12-11
I use a script I wrote and put a launcher for in the panel and menu.  I call it Wifi Refresh.  Sometimes I need to kill off the existing connection and restart it, esp if another app like kismet fails to properly bring up managed mode when quitting kismet.  I don't use network-manager, don't have it installed either, I just use the /etc/network/interfaces file for my connections.
```
 #/bin/bash
wlanconfig ath0 destroy
wlanconfig ath0 create wlandev wifi0 wlanmode sta
ifconfig ath0 up
/etc/init.d/networking restart
```

You could do similar to kill network-manager and place the device in monitor mode:
```
 #/bin/bash
killall NAME-OF-NETWORK-MANAGER-PROCESS-HERE
wlanconfig ath0 destroy
wlanconfig ath0 create wlandev wifi0 wlanmode monitor
ifconfig ath0 up 
```

---

### Post by Masteroc on 2008-02-02
hey, the above script does work for me...however, every time that i run it, i get a new ath* interface with a larger number (im up to ath4 now). how can i keep it to ath0??

Thanks

---

### Post by tturrisi on 2008-02-02
To keep the virtual interface ids fro incrementing (ath0, ath1,ath2, etc), you need to edit 2 files:

/etc/udev/rules.d/z25_persistant-net.rules
delete all line pairs that have an athX interface

example line pairs:

# PCI device 0x168c:0x001c (ath_pci)
# SUBSYSTEM=="net", DRIVERS=="?*", ATTR{address}=="00:1a:4d:34:66:92", ATTR{type}=="1", NAME="ath0"

# PCI device 0x168c:0x001c (ath_pci)
# SUBSYSTEM=="net", DRIVERS=="?*", ATTR{address}=="00:1a:4d:34:66:92", ATTR{type}=="1", NAME="ath1"

# PCI device 0x168c:0x001c (ath_pci)
# SUBSYSTEM=="net", DRIVERS=="?*", ATTR{address}=="00:1a:4d:34:66:92", ATTR{type}=="1", NAME="ath2"

Next:

edit /etc/udev/persistent-net-generator.rules

change this:

# ignore "secondary" raw interfaces of the madwifi driver
KERNEL=="ath*", ATTRS{type}=="802",	GOTO="persistent_net_generator_end"

to this:

# ignore "secondary" raw interfaces of the madwifi driver
KERNEL=="ath*", 	GOTO="persistent_net_generator_end"

reboot and /etc/udev/rules.d/z25_persistant-net.rules will contain only one reference for ath0

---

### Post by Masteroc on 2008-02-02
i just checked...and i dont have either of those files...

this is the listing of my /etc/udev/rules.d directory:

file:///etc/udev/rules.d/README
file:///etc/udev/rules.d/99-udevmonitor.rules
file:///etc/udev/rules.d/95-hal.rules
file:///etc/udev/rules.d/90-modprobe.rules
file:///etc/udev/rules.d/85-pcmcia.rules
file:///etc/udev/rules.d/85-linux-wlan-ng.rules
file:///etc/udev/rules.d/85-ifupdown.rules
file:///etc/udev/rules.d/85-hwclock.rules
file:///etc/udev/rules.d/85-hdparm.rules
file:///etc/udev/rules.d/85-brltty.rules
file:///etc/udev/rules.d/85-alsa.rules
file:///etc/udev/rules.d/80-programs.rules
file:///etc/udev/rules.d/65-persistent-storage.rules
file:///etc/udev/rules.d/65-persistent-input.rules
file:///etc/udev/rules.d/60-symlinks.rules
file:///etc/udev/rules.d/60-libpisock.rules
file:///etc/udev/rules.d/50-xserver-xorg-input-wacom.rules
file:///etc/udev/rules.d/45-libsane.rules
file:///etc/udev/rules.d/45-libgphoto2.rules
file:///etc/udev/rules.d/45-fuse.rules
file:///etc/udev/rules.d/40-permissions.rules
file:///etc/udev/rules.d/30-cdrom_id.rules
file:///etc/udev/rules.d/025_gpsd.rules
file:///etc/udev/rules.d/25-iftab.rules
file:///etc/udev/rules.d/25-dmsetup.rules
file:///etc/udev/rules.d/20-names.rules
file:///etc/udev/rules.d/05-options.rules
file:///etc/udev/rules.d/00-init.rules

this is a fresh install of FIESTY 7.04...but i even did an upgrade to Gutsy and i had the same problem, so its not the version.

---

