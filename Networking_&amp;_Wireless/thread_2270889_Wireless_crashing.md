---
title: "Wireless crashing"
date: 2015-03-26
forum: Networking &amp; Wireless
---

### Post by EL-FRIAKH_Zakarya on 2015-03-26
Hello every one, 
I've been having a problem with my wireless connection since yesterday: I can't connect to some of my wifi networks -my password doesn't seem to work-, and when I do, the connection is slow, keeps getting slower after few browser requests and finally just crashes and disconnects me. I have also noticed that the signal is low on all my wifi networks.
I suspect it has something to do with an update of the kernel that I made yesterday, but I am not sure, can someone please help me?

my laptop is an Asus N56VJ, running ubuntu 14.04 LTS, kernel version: 3.13.0-48-generic

Solutions I have already tried:
adding "options ath9k nohwcrypt=1" to /etc/modprobe.d/ath9k.conf and rebooting
didn't work...


here are the outputs of:

```
lspci:
```
```
00:00.0 Host bridge: Intel Corporation 3rd Gen Core processor DRAM Controller (rev 09)
00:01.0 PCI bridge: Intel Corporation Xeon E3-1200 v2/3rd Gen Core processor PCI Express Root Port (rev 09)
00:02.0 VGA compatible controller: Intel Corporation 3rd Gen Core processor Graphics Controller (rev 09)
00:14.0 USB controller: Intel Corporation 7 Series/C210 Series Chipset Family USB xHCI Host Controller (rev 04)
00:16.0 Communication controller: Intel Corporation 7 Series/C210 Series Chipset Family MEI Controller #1 (rev 04)
00:1a.0 USB controller: Intel Corporation 7 Series/C210 Series Chipset Family USB Enhanced Host Controller #2 (rev 04)
00:1b.0 Audio device: Intel Corporation 7 Series/C210 Series Chipset Family High Definition Audio Controller (rev 04)
00:1c.0 PCI bridge: Intel Corporation 7 Series/C210 Series Chipset Family PCI Express Root Port 1 (rev c4)
00:1c.1 PCI bridge: Intel Corporation 7 Series/C210 Series Chipset Family PCI Express Root Port 2 (rev c4)
00:1c.3 PCI bridge: Intel Corporation 7 Series/C210 Series Chipset Family PCI Express Root Port 4 (rev c4)
00:1d.0 USB controller: Intel Corporation 7 Series/C210 Series Chipset Family USB Enhanced Host Controller #1 (rev 04)
00:1f.0 ISA bridge: Intel Corporation HM76 Express Chipset LPC Controller (rev 04)
00:1f.2 SATA controller: Intel Corporation 7 Series Chipset Family 6-port SATA Controller [AHCI mode] (rev 04)
00:1f.3 SMBus: Intel Corporation 7 Series/C210 Series Chipset Family SMBus Controller (rev 04)
01:00.0 VGA compatible controller: NVIDIA Corporation GF108M [GeForce GT 635M] (rev a1)
03:00.0 Network controller: Qualcomm Atheros AR9485 Wireless Network Adapter (rev 01)
04:00.0 Ethernet controller: Qualcomm Atheros AR8161 Gigabit Ethernet (rev 10)
```

and :
```
sudo lshw -c network
```
```
*-network
       description: Wireless interface
       product: AR9485 Wireless Network Adapter
       vendor: Qualcomm Atheros
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: wlan0
       version: 01
       serial: dc:85:de:31:99:6c
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list rom ethernet physical wireless
       configuration: broadcast=yes driver=ath9k driverversion=3.13.0-48-generic firmware=N/A ip=192.168.43.122 latency=0 link=yes multicast=yes wireless=IEEE 802.11bgn
       resources: irq:17 memory:f7900000-f797ffff memory:f7980000-f798ffff
  *-network
       description: Ethernet interface
       product: AR8161 Gigabit Ethernet
       vendor: Qualcomm Atheros
       physical id: 0
       bus info: pci@0000:04:00.0
       logical name: eth0
       version: 10
       serial: 50:46:5d:30:92:02
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm pciexpress msi msix bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=alx latency=0 link=no multicast=yes port=twisted pair
       resources: irq:47 memory:f7800000-f783ffff ioport:d000(size=128)
```

Thank you all.

[SIZE=3]** EDIT:**[/SIZE] here's the link to the ubuntu pastebin that contains wireless script output: [http://paste.ubuntu.com/10683487/](http://paste.ubuntu.com/10683487/)
I hope that helps

---

### Post by EL-FRIAKH_Zakarya on 2015-03-26
Pleeease, I'am starting to lose hope...

---

### Post by jeremy31 on 2015-03-26
Reboot and hold the Shift key until the grub menu appears.  Then select Advanced options for Ubuntu or Previous Linux versions and select an older kernel to boot into and see if it helps

---

### Post by EL-FRIAKH_Zakarya on 2015-03-26
Oh thank you so much for answering, okay will try it, just few questions before I do that:
1- Which version of the kernel will that make me start up with?
2- Will this be only for that one start up? i.e if I reboot again will it be in the current version of kernel I have?

Thank you again, it feels good to know someone's willing to help

---

### Post by EL-FRIAKH_Zakarya on 2015-03-26
Well I ust googled those questions, and rebooted using older versions of the kernel, and it didn't solve it, I also tested my wifi under windows 7, and it was a bit slow...starting to suspect my wireless card to cause the problem, is there a way to make sure of that?
Thanks again to anyone who's willing to help

---

### Post by kc1di on 2015-03-26
[This thread]("http://ubuntuforums.org/showthread.php?t=2221294") may be of help to you in figuring out whats going on. 
that wireless card seems to have been problematic for awhile now.

---

### Post by EL-FRIAKH_Zakarya on 2015-03-26
Will do! Thank you in advance.

---

### Post by EL-FRIAKH_Zakarya on 2015-03-26
Just came back from that thread, phy0 is not hard nor soft blocked for me, so it doesn't help....thank you though!

---

