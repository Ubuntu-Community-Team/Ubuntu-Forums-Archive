---
title: "Not able to find or connect to  wireless networks"
date: 2008-07-31
forum: Networking &amp; Wireless
---

### Post by dthomas08 on 2008-07-31
Hey there, I'm still pretty much a newbie at this. I have a laptop on which I installed Gutsy and it worked great for quite awhile (though it's old and dying). Recently it has been unable to find local Wireless networks and it is unable to connect to them even if I know the name and passwords. Is there anything I can do to correct this issue? I fear I may have changed some of the wireless settings trying to set it up for my school's server (which apparently doesn't even support non-windows/mac ...)

I really appreciate any help I can get. Thanks!

---

### Post by superprash2003 on 2008-08-01
it could be a drivers issue.. in the terminal type lshw -C network and post output.. also type iwconfig and post output

---

### Post by Kevbert on 2008-08-01
It's a firmware problem (and at a guess you're using a Broadcom based wireless card).

---

### Post by dthomas08 on 2008-08-01
This should be the output you asked for (yes it is Broadcom :( ). Also, I had to type it from the screen because the ethernet jack is broken (I told you it was dying) and I don't have any workable memory sticks available. ie. It should all be correct, but if there is an inconsistency, my apologies. Thank you all for helping me!

```
$lshw -C network

*-network:0
   description: Ethernet interface
   product: Broadcom Corporation
   physical id: 0
   bus info: pci@0000:02:00.0
   logical name: eth0
   version: 01
   serial: 00:0f:1f:1a:de:66
   capacity: 1GB/s
   width: 64 bits
   clock: 66MHz
   capabilities: pm vpd msi bus_mater cap_list ethernet mii 10bt 10bt-fd 1000bt 1000bt-fd autonegotiation
   configuration: autonegotiation=on broadcast=yes driver=tg3 driverversion=3.77 firmware=5705-v3.11 latency=32 link=no mingnt=64 module=tg3 multicast=yes port=twisted pair

*-network:1 DISABLED
   description: Wireless interface
   product: BCM4306 802.11b/g Wireless LAN Controller
   vendor: Broadcom Corporation
   physical id: 3
   bus info: pci@0000:02:03.0
   local name: eth1
   version: 03
   serial: 00:90:96:ac:d7:0e
   width: 32 bits
   clock: 33MHz
   capabilities: bus_mater ethernet physical wireless
   configuration: broadcast=yes driver=bcm43xx driverversion=2.6.22-15-generic latency=32 link=no module=bcm43xx multicast=yes wireless=IEEE 802.11b/g

```

```
$iwconfig

lo      no wireless extensions

eth0    no wireless extensions.

eth1    IEEE 802.11b/g ESSID:0ff/any  Nickname:"Broadcom 4306"
        MODE:Managed   Access Point: Invalid
        RTS thr:off   Frament thr:off
        Encryption key: off
        Link Quality=0/100   Signal level=-256 dBm   Noise level=-256 dBm
        Rx invalid nwid:0   Rx invalid crypt:0   Rx invalid frag:0
        Tx excessive retries:0   Invalid misc:0    Missed beacon:0


```

---

### Post by Kevbert on 2008-08-01
Earlier in July some changes were made regarding the Broadcom drivers hence you now have the problems.  You may be able to get away with just downloading and copying firmware to your /lib/firmware directory.  Please note I haven't tried this, but the drivers in my other post work with both Hardy and Intrepid.  Please try [[COLOR="Red"]this[/COLOR]]("http://ubuntuforums.org/showpost.php?p=5469730&postcount=13") and if it works I'll amend that post.

---

### Post by dthomas08 on 2008-08-02
Sadly, that didn't seem to work ... I'll look at that thread you referred and see if anything there works. Anyone else have some ideas?

I see that my output says:
```
*-network:1 DISABLED
   description: Wireless interface
```

Is this normal? Thank you for your help!

---

### Post by Kevbert on 2008-08-03
You could try 
```
ifconfig eth1 up
```
in case wireless is just powered down.

---

### Post by dthomas08 on 2008-08-03
It seems that the previous attempt to reinstall the driver that you redirected me to removed eth1 (according to lshw: network 1 is unclaimed [though it did know the specs of the wireless]). iwconfig also shoes no eth1. What can I do to allow it to recognize it again? Thanks for your help

---

### Post by Kevbert on 2008-08-03
If you go to the /lib/firmware directory, do you have Broadcom firmware files in there ?  They'll possibly be in their own directory (b43, b43xx or something like that).  It may be worth taking a look at this [post]("http://ubuntuforums.org/showthread.php?p=4789728#post4789728").  The method should be valid for Gutsy.  It's possible that your drivers have been blacklisted.

---

