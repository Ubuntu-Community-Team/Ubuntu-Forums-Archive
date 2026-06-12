---
title: "Wireless disconnects"
date: 2010-04-08
forum: New to Ubuntu
---

### Post by Vistz on 2010-04-08
My wireless will disconnect often. I usually reconnect manually afterwards. Under Network Tools, the Network Device is set to "Loopback Interface (lo)". Does this mean anything?

---

### Post by Vistz on 2010-04-08
Does this by any chance have anything to do with the WEP Index?

---

### Post by adam22 on 2010-04-08
Need to know more about the wireless card/adapter...in terminal type
```
lspci
``` and paste it in your reply. I had the same issue, and resolved it through the backports described in [this](http://ubuntuforums.org/showthread.php?t=1316126) thread.

---

### Post by Vistz on 2010-04-09
This is what I came up with:

```
00:00.0 Host bridge: Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT Express Memory Controller Hub (rev 03)
00:01.0 PCI bridge: Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT Express PCI Express Root Port (rev 03)
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 01)
00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 01)
00:1c.1 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 2 (rev 01)
00:1c.2 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 3 (rev 01)
00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #1 (rev 01)
00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #2 (rev 01)
00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #3 (rev 01)
00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #4 (rev 01)
00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 01)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e1)
00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 01)
00:1f.2 IDE interface: Intel Corporation 82801GBM/GHM (ICH7 Family) SATA IDE Controller (rev 01)
00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 01)
01:00.0 VGA compatible controller: nVidia Corporation G72M [Quadro NVS 110M/GeForce Go 7300] (rev a1)
03:01.0 CardBus bridge: O2 Micro, Inc. OZ601/6912/711E0 CardBus/SmartCardBus Controller (rev 40)
09:00.0 Ethernet controller: Broadcom Corporation NetXtreme BCM5752 Gigabit Ethernet PCI Express (rev 02)
0c:00.0 Network controller: Intel Corporation PRO/Wireless 3945ABG [Golan] Network Connection (rev 02)

```

---

### Post by adam22 on 2010-04-09
What version of Ubuntu?

---

### Post by Vistz on 2010-04-09
8.10

---

### Post by adam22 on 2010-04-09
Alright, let's try this.....

~Open up Synaptic. Settings>Updates>Unsupported updates

~Close out, bring up the terminal, type:
```
sudo apt-get install linux-backports-modules-intrepid
```and then:
```
sudo apt-get install linux-backports-modules-wireless-intrepid-generic
```

then:
```
sudo apt-get update
```

and lastly

```
sudo apt-get upgrade
```

Then reboot the computer.

---

### Post by Vistz on 2010-04-09
The first command was fine. However, when I ran the second one, I got

```
:~$ sudo apt-get install linux-backports-modules-wireless-intrepid-generic
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package linux-backports-modules-wireless-intrepid-generic

```

---

### Post by adam22 on 2010-04-09
Did you reboot? You may not need that last part...search backports in synaptic and look for one with a similar name..

---

### Post by Vistz on 2010-04-09
> **adam22 said:**
> Did you reboot? You may not need that last part...search backports in synaptic and look for one with a similar name..

What do you mean by search for backports? As in "backports"?

---

### Post by adam22 on 2010-04-09
Yes, but in all honesty, support for Intrepid will soon end as the next LTS is coming out. I would consider upgrading.

---

### Post by Vistz on 2010-04-11
> **adam22 said:**
> Alright, let's try this.....

~Open up Synaptic. Settings>Updates>Unsupported updates

~Close out, bring up the terminal, type:
```
sudo apt-get install linux-backports-modules-intrepid
```and then:
```
sudo apt-get install linux-backports-modules-wireless-intrepid-generic
```then:
```
sudo apt-get update
```and lastly

```
sudo apt-get upgrade
```Then reboot the computer.

I recently upgraded to karmic and am disconnecting frequently. Should I run this except replacing "intrepid" with "karmic"?

---

