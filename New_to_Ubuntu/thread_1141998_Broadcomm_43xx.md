---
title: "Broadcomm 43xx"
date: 2009-04-28
forum: New to Ubuntu
---

### Post by theozzlives on 2009-04-28
I'm installing a wireless network for the neighbor. I can't get Intrepid to recognize his card, I think it's a driver problem (tried NDISWrapper). NDISWrapper says it's installed, but Network Manager says it's not. There are no restricted drivers. Here's my lspci:

```
00:00.0 Host bridge: Intel Corporation 440BX/ZX/DX - 82443BX/ZX/DX Host bridge (rev 02)
00:01.0 PCI bridge: Intel Corporation 440BX/ZX/DX - 82443BX/ZX/DX AGP bridge (rev 02)
00:0d.0 Network controller: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller (rev 02)
00:14.0 ISA bridge: Intel Corporation 82371AB/EB/MB PIIX4 ISA (rev 02)
00:14.1 IDE interface: Intel Corporation 82371AB/EB/MB PIIX4 IDE (rev 01)
00:14.2 USB Controller: Intel Corporation 82371AB/EB/MB PIIX4 USB (rev 01)
00:14.3 Bridge: Intel Corporation 82371AB/EB/MB PIIX4 ACPI (rev 02)
01:00.0 VGA compatible controller: ATI Technologies Inc 3D Rage Pro AGP 1X/2X (rev 5c)
``` 

My laptop has a Broadcom 43xx and Intrepid recognized it immediately.

---

### Post by Presto123 on 2009-04-28
Broadcoms are tricky if not just so so from the beginning. If network manager isn"t working, I would suggest disabling it and going with WICD.

---

### Post by abn91c on 2009-04-28
what version ubuntu you using?, the drivers for that card-broadcomm airforce 1 43xx are available in 8.10 and 9.04. I recomend you remove ndiswrapper, its giving you a conflict, reboot then look for the card in the administration>system>hardware drivers(its the card I have on my dell inspiron 1000.)
Here are the drivers I used on 8.04

---

### Post by theozzlives on 2009-04-28
> **abn91c said:**
> what version ubuntu you using?, the drivers for that card-broadcomm airforce 1 43xx are available in 8.10 and 9.04. I recomend you remove ndiswrapper, its giving you a conflict, reboot then look for the card in the administration>system>hardware drivers(its the card I have on my dell inspiron 1000.)
Here are the drivers I used on 8.04

It's 8.10 and the live CD won't even work with it.

---

### Post by Handyandy52 on 2009-04-28
Had same problem read other posts used WICD after removing network and it detected and connected right away. wireless does not work on live cd you must install to use.

---

### Post by lkraemer on 2009-04-28
ozz,

Open a Terminal Window and do:

```

lshw -C network
lsmod
ndiswrapper -l
cat /etc/modprobe.d/blacklist
iwconfig


```
and Post the output of each

If the output of ndiswrapper shows any drivers loaded,
remove ALL of them.  If memory serves me correctly the command is:
```

sudo ndiswrapper -e bcmwl5

```

Then remove ndiswrapper:
```

sudo modprobe -r ndiswrapper


```
This should clean up nidswrapper & drivers.

Open a Terminal & Check for errors:
```

dmesg

```
looking for missing firmware or what is causing the Wifi to 
not function.  There might be a clue. Is the firmware installed
in /lib/firmware or possibly in /lib/firmware/b43  Once again
dmesg might give you a clue. ie.  [www.omattos.com/broadcom](www.omattos.com/broadcom)

If lsmod shows module b43 and others installed you will
need to blacklist them, since you are going to be using b43xx.
You may have to remove the following depending on what lsmod
shows:
```

modprobe -r b44
modprobe -r b43
modprobe -r b43legacy
modprobe -r ssb


```
You can use sudo gedit /etc/modprobe.d/blacklist
and add the necessary modules to blacklist.

Once this is all straightened up..........
I'd reboot or try:
```

/etc/init.d/networking restart

```

If you know the routers essid and the correct <interface>,
shown by using iwconfig ie wlan0, ath0, etc.... replace that
as the <interface> below:

```

sudo ifconfig <interface> down
sudo dhclient -r <interface>
sudo iwconfig <interface> essid "youressidofrouter"
sudo iwconfig <interface> mode Managed
sudo ifconfig <interface> up
sudo dhclient <interface>
iwconfig

```
Post the output of iwconfig above.

REF URL:
[http://ubuntuforums.org/showthread.php?t=571188](http://ubuntuforums.org/showthread.php?t=571188)
[https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff#Step%201:%20All%20BCM43xx%20-%20Install%20NDISWrapper%20and%20Blacklist%20Native%20Driver](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff#Step%201:%20All%20BCM43xx%20-%20Install%20NDISWrapper%20and%20Blacklist%20Native%20Driver)


lkraemer

---

### Post by theozzlives on 2009-04-29
This  is a computer that has been upgraded from Gutsy to Hardy to Intrepid, you think a clean install would do it instead of going through all that? and is wicd on the disk? That computer don't have Internet yet until the wifi is working. 8.04 did say something about firmware. I can't post the output of anything cause it's next door... I won't get to it until this evening.

---

### Post by lkraemer on 2009-04-29
ozz,
Before the upgrade did their Wifi work properly?  I'd think that
if it was working it should be easy to get it functional again.
Did they use ndiswrapper or what made it functional on the 
previous version?

As, for the update .........
If the only thing missing is the firmware, there should be some
statement in dmesg that will guide you as to where to copy the
*.fw files.  

Next I'd verify what is blacklisted, or needs to be blacklisted,
to allow the b43xx drivers to function without conflict.

Other than that, you will have to backup their data, find out what
software needs to be re-installed, and do a fresh install as last
resort, then re-install their software, and restore the data.  Don't
forget their bookmarks!

lkraemer

---

### Post by theozzlives on 2009-04-29
> **lkraemer said:**
> ozz,
Before the upgrade did their Wifi work properly?  I'd think that
if it was working it should be easy to get it functional again.
Did they use ndiswrapper or what made it functional on the 
previous version?

As, for the update .........
If the only thing missing is the firmware, there should be some
statement in dmesg that will guide you as to where to copy the
*.fw files.  

Next I'd verify what is blacklisted, or needs to be blacklisted,
to allow the b43xx drivers to function without conflict.

Other than that, you will have to backup their data, find out what
software needs to be re-installed, and do a fresh install as last
resort, then re-install their software, and restore the data.  Don't
forget their bookmarks!

lkraemer

It didn't work, and it was a broken upgrade.

---

### Post by theozzlives on 2009-05-15
A closer look at the card revealed that there may be a firmware chip missing, anyhoo, I resigned it to being Windows only and returned it. That's why I don't do free labor, even for friends.

---

### Post by RyanVanDiemen on 2009-05-15
I had broadcom wireless on my old laptop. It was a bit tricky to make it run but it worked great with jaunty.

---

