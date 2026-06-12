---
title: "Wireless Card disappeared"
date: 2016-07-27
forum: Networking &amp; Wireless
---

### Post by blacksh33p86 on 2016-07-27
Hello,

since a few days my wireless card just disappeared. I can't see it in lspci, lshw, ifconfig. (Lenovo L540)

```
 #> lspci
00:00.0 Host bridge: Intel Corporation Xeon E3-1200 v3/4th Gen Core Processor DRAM Controller (rev 06)
00:02.0 VGA compatible controller: Intel Corporation 4th Gen Core Processor Integrated Graphics Controller (rev 06)
00:03.0 Audio device: Intel Corporation Xeon E3-1200 v3/4th Gen Core Processor HD Audio Controller (rev 06)
00:14.0 USB controller: Intel Corporation 8 Series/C220 Series Chipset Family USB xHCI (rev 05)
00:16.0 Communication controller: Intel Corporation 8 Series/C220 Series Chipset Family MEI Controller #1 (rev 04)
00:19.0 Ethernet controller: Intel Corporation Ethernet Connection I217-V (rev 05)
00:1a.0 USB controller: Intel Corporation 8 Series/C220 Series Chipset Family USB EHCI #2 (rev 05)
00:1b.0 Audio device: Intel Corporation 8 Series/C220 Series Chipset High Definition Audio Controller (rev 05)
00:1c.0 PCI bridge: Intel Corporation 8 Series/C220 Series Chipset Family PCI Express Root Port #1 (rev d5)
00:1c.2 PCI bridge: Intel Corporation 8 Series/C220 Series Chipset Family PCI Express Root Port #3 (rev d5)
00:1c.4 PCI bridge: Intel Corporation 8 Series/C220 Series Chipset Family PCI Express Root Port #5 (rev d5)
00:1d.0 USB controller: Intel Corporation 8 Series/C220 Series Chipset Family USB EHCI #1 (rev 05)
00:1f.0 ISA bridge: Intel Corporation HM86 Express LPC Controller (rev 05)
00:1f.2 SATA controller: Intel Corporation 8 Series/C220 Series Chipset Family 6-port SATA Controller 1 [AHCI mode] (rev 05)
00:1f.3 SMBus: Intel Corporation 8 Series/C220 Series Chipset Family SMBus Controller (rev 05)
07:00.0 Unassigned class [ff00]: Realtek Semiconductor Co., Ltd. RTS5227 PCI Express Card Reader (rev 01)

```

```
lshw -C network
 lshw -C network
  *-network               
       Beschreibung: Ethernet interface
       Produkt: Ethernet Connection I217-V
       Hersteller: Intel Corporation
       Physische ID: 19
       Bus-Informationen: pci@0000:00:19.0
       Logischer Name: eth0
       Version: 05
       Seriennummer: 54:ee:75:0a:71:0e
       Größe: 100Mbit/s
       Kapazität: 1Gbit/s
       Breite: 32 bits
       Takt: 33MHz
       Fähigkeiten: pm msi bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       Konfiguration: autonegotiation=on broadcast=yes driver=e1000e driverversion=3.2.6-k duplex=full firmware=0.13-3 ip=192.168.3.7 latency=0 link=yes multicast=yes port=twisted pair speed=100Mbit/s
       Ressourcen: irq:27 memory:f2400000-f241ffff memory:f243f000-f243ffff ioport:5080(Größe=32)

```

Does anyone have an idea what happend? Perhaps is has sth. to do with updates?

Greets,

blacky

[ATTACH]270386[/ATTACH]

---

### Post by jeremy31 on 2016-07-27
Welcome to the forums

Have you checked in BIOS to see if wifi/WLAN is enabled?  If it is enabled in BIOS, check the wifi cards connection to the motherboard

---

### Post by blacksh33p86 on 2016-07-27
Thanks for your ideas!
I've checked the BIOS. There is no entry to enable or disable wifi. I didn't move the laptop for about 1 year. I can't imagine that the connection to the motherboard should have loosen itself in the past few weeks.

---

### Post by jeremy31 on 2016-07-27
You could reboot and hold the shift key until the grub menu appears, then scroll to advanced options for Ubuntu and then select an older kernel to boot to and see if wireless works

---

### Post by blacksh33p86 on 2016-07-27
good idea! I'll try tomorrow and report.

---

### Post by blacksh33p86 on 2016-07-28
Hm, didn't work. The wifi card is still lost

---

### Post by jeremy31 on 2016-07-28
It is likely that a hardware failure has happened or it is an connection issue.  You may want to try resetting BIOS to defaults

---

### Post by blacksh33p86 on 2016-07-28
Resetting BIOS to defaults didn't help... Doesn't look good :(

---

### Post by jeremy31 on 2016-07-28
It doesn't look good.  I have a Lenovo G710 and if I disable wireless in BIOS it does disappear from lspci results but you don't seem to have that option

Another issue with Lenovo is that a lot of them have a wireless whitelist, if the wireless card you put in doesn't match one on the list, they won't even boot so unless you get a USB wireless card you need to get one from Lenovo

---

### Post by blacksh33p86 on 2016-07-28
Resetting BIOS to defaults didn't help... 

I tried to start it with a Linux Mint live system but lscpi still showed no wifi card. I have an identical l540 here and I started this one with the live cd. lspci shows RTL8192EE PCIe ...
I opend the laptop, took out the PCIe card and put it back in. 
Now it works. The card is back in lspci... No idea where the issue was...

Thank you very much

---

