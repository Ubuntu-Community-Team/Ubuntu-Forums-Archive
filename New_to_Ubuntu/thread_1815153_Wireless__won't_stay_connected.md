---
title: "Wireless  won't stay connected"
date: 2011-07-30
forum: New to Ubuntu
---

### Post by Ajanfreak on 2011-07-30
i am running ubuntu 11.04. i have a belkin wireless g plus mimo usb network adapter. ubuntu finds the networks but it rapidly disconnects and reconnects. i have checked the fourm and found nothing up to date.

Any help would be greatly appreciated.

Thanks in advance. :)

---

### Post by wildmanne39 on 2011-07-30
Hi, I will try to help you with this, please run these commands in a terminal
```
sudo lshw -C network
```
```
lspci -nn | grep 0280
```
```
lsusb
```
```
iwconfig
```
```
rfkill list all
```
and post the outcome here by clicking on new reply and click # and paste the information between the brackets.

How long does it stay connected?

---

### Post by Ajanfreak on 2011-07-30
> bob@bob-computer-123:~$ sudo lshw -C network
[sudo] password for bob: 
  *-network               
       description: Ethernet interface
       product: 82566DM-2 Gigabit Network Connection
       vendor: Intel Corporation
       physical id: 19
       bus info: pci@0000:00:19.0
       logical name: eth0
       version: 02
       serial: 00:21:9b:89:15:70
       size: 100Mbit/s
       capacity: 1Gbit/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=e1000e driverversion=1.2.20-k2 duplex=full firmware=1.4-0 ip=192.168.137.170 latency=0 link=yes multicast=yes port=twisted pair speed=100Mbit/s
       resources: irq:42 memory:fe9e0000-fe9fffff memory:fe9db000-fe9dbfff ioport:ecc0(size=32)
  *-network
       description: Wireless interface
       physical id: 1
       bus info: usb@2:6
       logical name: wlan0
       serial: 00:1c:df:26:aa:d9
       capabilities: ethernet physical wireless
       configuration: broadcast=yes driver=rt73usb driverversion=2.6.38-10-generic firmware=1.7 link=no multicast=yes wireless=IEEE 802.11bg
bob@bob-computer-123:~$ lspci -nn
00:00.0 Host bridge [0600]: Intel Corporation 82Q35 Express DRAM Controller [8086:29b0] (rev 02)
00:01.0 PCI bridge [0604]: Intel Corporation 82Q35 Express PCI Express Root Port [8086:29b1] (rev 02)
00:02.0 VGA compatible controller [0300]: Intel Corporation 82Q35 Express Integrated Graphics Controller [8086:29b2] (rev 02)
00:02.1 Display controller [0380]: Intel Corporation 82Q35 Express Integrated Graphics Controller [8086:29b3] (rev 02)
00:03.0 Communication controller [0780]: Intel Corporation 82Q35 Express MEI Controller [8086:29b4] (rev 02)
00:03.2 IDE interface [0101]: Intel Corporation 82Q35 Express PT IDER Controller [8086:29b6] (rev 02)
00:03.3 Serial controller [0700]: Intel Corporation 82Q35 Express Serial KT Controller [8086:29b7] (rev 02)
00:19.0 Ethernet controller [0200]: Intel Corporation 82566DM-2 Gigabit Network Connection [8086:10bd] (rev 02)
00:1a.0 USB Controller [0c03]: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #4 [8086:2937] (rev 02)
00:1a.1 USB Controller [0c03]: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #5 [8086:2938] (rev 02)
00:1a.7 USB Controller [0c03]: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #2 [8086:293c] (rev 02)
00:1b.0 Audio device [0403]: Intel Corporation 82801I (ICH9 Family) HD Audio Controller [8086:293e] (rev 02)
00:1c.0 PCI bridge [0604]: Intel Corporation 82801I (ICH9 Family) PCI Express Port 1 [8086:2940] (rev 02)
00:1d.0 USB Controller [0c03]: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #1 [8086:2934] (rev 02)
00:1d.1 USB Controller [0c03]: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #2 [8086:2935] (rev 02)
00:1d.2 USB Controller [0c03]: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #3 [8086:2936] (rev 02)
00:1d.7 USB Controller [0c03]: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #1 [8086:293a] (rev 02)
00:1e.0 PCI bridge [0604]: Intel Corporation 82801 PCI Bridge [8086:244e] (rev 92)
00:1f.0 ISA bridge [0601]: Intel Corporation 82801IO (ICH9DO) LPC Interface Controller [8086:2914] (rev 02)
00:1f.2 SATA controller [0106]: Intel Corporation 82801IR/IO/IH (ICH9R/DO/DH) 6 port SATA AHCI Controller [8086:2922] (rev 02)
00:1f.3 SMBus [0c05]: Intel Corporation 82801I (ICH9 Family) SMBus Controller [8086:2930] (rev 02)
bob@bob-computer-123:~$ grep 0280
lsusb
iwconfig
rfkill list all


ok this is what the command came up with in terminal.

---

### Post by wildmanne39 on 2011-07-30
Hi, I still need to see the results of 
```
lsusb
iwconfig
rfkill list all 
```
run these commands one at a time.
Thank you

---

