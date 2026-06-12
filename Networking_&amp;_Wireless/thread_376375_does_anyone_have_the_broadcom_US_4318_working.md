---
title: "does anyone have the broadcom US 4318 working?"
date: 2007-03-04
forum: Networking &amp; Wireless
---

### Post by 22350 on 2007-03-04
does anyone have this card working?

02:03.0 Network controller: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller (rev 02)


i have been trying to get it going for 2 weeks and frankly it is starting to upset me.

and yes, i have been through every topic relating to it.

you can see what i've done here:

[http://www.ubuntuforums.org/showthread.php?t=366819&page=5](http://www.ubuntuforums.org/showthread.php?t=366819&page=5)


if you do have it working, please let me know what you did.

paul

---

### Post by DarkN00b on 2007-03-04
I got mine working using the HOWTO [here]("http://ubuntuforums.org/showthread.php?p=1071920&mode=linear"). Make sure you read it before trying it.

Good luck.

---

### Post by 22350 on 2007-03-04
yes, but are you using the "airforce one" version of the card?  there are two versions.

---

### Post by DarkN00b on 2007-03-04
> **22350 said:**
> yes, but are you using the "airforce one" version of the card?  there are two versions.

Yep.

```
03:00.0 Network controller: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller (rev 02)
```

---

### Post by pebo on 2007-03-04
This is how I got my card with the BCM4318 chipset working with ndiswrapper:
```
sudo echo "Blacklist BCM43xx" >> /etc/modprobe.d/blacklist
```
Downloaded 80211g.zip [ftp://ftp.support.acer-euro.com/note...ers/80211g.zip](ftp://ftp.support.acer-euro.com/note...ers/80211g.zip).  Uncompressed the zip file.
cd'ed to 80211g folder. You must be in the folder when running the following commands as ndiswrapper needs some of the additional files.
```
sudo ndiswrapper -i bcmwl5a.inf
sudo ndiswrapper -l (output should give 'driver installed, hardware present')
sudo modprobe ndiswrapper
sudo ndiswrapper -m
```wlan0 should now show up in 
```
ifconfig -a
```hth

---

### Post by 22350 on 2007-03-05
and your card is the airforce one chipset?

---

### Post by spacebetween on 2007-03-05
I just installed Ubuntu two days ago and have been going at wireless ever since. It was pretty much the most frustrating thing. It took a LOT of time to do, and I have tests to study for!

Anyway, I somehow managed to get it working. I followed about every how-to in the world, and finally came across a wiki how-to. What sparked my interest about this one was that it clued me in to uninstalling ndiswrapper and installing a more updated version.

In the how-to that is fairly popular on this board, it includes a script that will install ndiswrapper and the driver you need for the wireless card. But that ndiswrapper is sorely out of date!

I would recommend uninstalling ndiswrapper and making sure you have the latest one. Then manually add the driver using ndiswrapper.

If that didn't make any sense at all, I'll clarify. All I know is after doing that (and rebooting!), it started working. 

I'm using network-manager right now, and I can detect wireless networks. Only problem is I can't connect, but I'm sure I'll manage around that somehow.

---

