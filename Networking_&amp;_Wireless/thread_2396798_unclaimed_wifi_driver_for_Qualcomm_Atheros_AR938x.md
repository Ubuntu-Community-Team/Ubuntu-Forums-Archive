---
title: "unclaimed wifi driver for Qualcomm Atheros AR938x"
date: 2018-07-20
forum: Networking &amp; Wireless
---

### Post by kenzo-zombie on 2018-07-20
[FONT=arial]I just bought a wifi [/FONT][FONT=arial]pcie[/FONT][FONT=arial] card from [/FONT][FONT=arial]amazon[/FONT][FONT=arial] with the [/FONT][FONT=arial]qualcomm[/FONT][FONT=arial]atheros[/FONT][FONT=arial] chipset thinking it has a better compatibility with [/FONT][FONT=arial]linux[/FONT][FONT=arial]. Somehow it still fails to work for my system. The details are as follows:**OS: **Kubuntu 18.04 - [COLOR=#000000]4.15.0-29-generic

These are the details:

[/COLOR][/FONT][FONT=monospace][COLOR=#000000][FONT=arial]uname[/FONT][/COLOR][/FONT][FONT=arial][COLOR=#000000] -a [/COLOR]
```
Linux WS 4.15.0-29-generic #31-Ubuntu SMP Tue Jul 17 15:39:52 UTC 2018 x86_64 x86_64 x86_64 GNU/Linux

```[COLOR=#000000]

lspci
[/COLOR][/FONT]```
[FONT=monospace][COLOR=#000000]06:00.0 Ethernet controller: Qualcomm Atheros Device abcd (rev 01)[/COLOR]
[/FONT]
```[FONT=arial][COLOR=#000000]

sudo lshw -C network
[/COLOR][/FONT]```
[FONT=monospace][COLOR=#000000]  *-network                  [/COLOR]
       description: Ethernet interface
       product: RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:05:00.0
       logical name: enp5s0
       version: 0c
       serial: 1c:1b:0d:e3:f6:6c
       size: 1Gbit/s
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=full firmware=rtl8168g-2_0.0.1 02/06/13 ip=192.168.1.17 latency=0 link=yes multi
cast=yes port=MII speed=1Gbit/s
       resources: irq:33 ioport:f000(size=256) memory:fd600000-fd600fff memory:f2100000-f2103fff
  *-network UNCLAIMED
       description: Ethernet controller
       product: Qualcomm Atheros
       vendor: Qualcomm Atheros
       physical id: 0
       bus info: pci@0000:06:00.0
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress cap_list
       configuration: latency=0
       resources: memory:fd500000-fd51ffff memory:fd520000-fd52ffff
[/FONT]
```[FONT=arial][COLOR=#000000]

I added the line in the following file /etc/modprobe.d/ath9k.conf
[/COLOR][/FONT][FONT=monospace][COLOR=#000000]cat /etc/modprobe.d/ath9k.conf [/COLOR]
```

options ath9k nohwcrpt=1

```

I even tried editing the modules file, but still no help
[/FONT]```
[FONT=monospace][COLOR=#000000]# /etc/modules: kernel modules to load at boot time.[/COLOR]
#
# This file contains the names of kernel modules that should be loaded
# at boot time, one per line. Lines beginning with "#" are ignored.

ath9k
ath5k
[/FONT]
```[FONT=monospace]

Could anyone please tell me what's going wrong? I have already spent 2~3 hours on this searching online, with no help.[/FONT]

---

### Post by wildmanne39 on 2018-07-20
*Thread moved to **Networking & Wireless for a more appropriate fit**.*

---

### Post by chili555 on 2018-07-20
> Ethernet controller: Qualcomm Atheros Device abcd (rev 01)The abcd problem. Please see: [https://pci-ids.ucw.cz/read/PC/168c/abcd](https://pci-ids.ucw.cz/read/PC/168c/abcd)  and also: [http://ath9k-devel.ath9k.narkive.com/1PgCqOyP/sparklan-wpea-121n-ar9382-168c-abcd](http://ath9k-devel.ath9k.narkive.com/1PgCqOyP/sparklan-wpea-121n-ar9382-168c-abcd) and also: [https://askubuntu.com/questions/1042215/wireless-ath9k-suddenly-stopped-working-on-ubuntu-16-04](https://askubuntu.com/questions/1042215/wireless-ath9k-suddenly-stopped-working-on-ubuntu-16-04)> I updated my ASUS H170 Pro Gaming motherboard to the latest BIOS and the problem got fixed.If that doesn't fix it., I am afraid that I have no other suggestions.

---

### Post by kenzo-zombie on 2018-07-22
Thank you so much for the reply. I did update the bios to the latest release. I followed the three links that you had provided.

The wifi device works perfectly in windows (as it was before the BIOS update), it is just on ubuntu where the device has a problem working. So I do not suppose it is a BIOS issue. Can this be an issue with some motherboard chipset compatibility??

It is still not working in ubuntu, with lspci still showing the same output.

---

### Post by praseodym on 2018-07-22
Please show
```

dmesg | grep ath
```

---

### Post by kenzo-zombie on 2018-07-24
> **praseodym said:**
> Please show
```

dmesg | grep ath
```

This the reply that I got. 

```
[FONT=monospace][COLOR=#54FF54]**kenzo@WS**[/COLOR][COLOR=#000000]:[/COLOR][COLOR=#5454FF]**~**[/COLOR][COLOR=#000000]$ dmesg | grep ath [/COLOR]
[    3.705343] [COLOR=#FF5454]**ath**[/COLOR][COLOR=#000000]9k: unknown parameter 'nohwcrpt' ignored [/COLOR]
[COLOR=#54FF54]**kenzo@WS**[/COLOR][COLOR=#000000]:[/COLOR][COLOR=#5454FF]**~**[/COLOR][COLOR=#000000]$ [/COLOR]
[/FONT]
```

I added the line following [this link]("https://askubuntu.com/questions/224619/how-to-resolve-wireless-disconnect-problem-in-atheros-ath9k").

---

### Post by chili555 on 2018-07-24
The parameter is:```
parm:           nohwcrypt:Disable hardware encryption (int)
```In other words, nohwcrypt; not as you spelled it, nohwcrpt.

Please correct your misspelling.

---

### Post by kenzo-zombie on 2018-07-25
> **chili555 said:**
> The parameter is:```
parm:           nohwcrypt:Disable hardware encryption (int)
```In other words, nohwcrypt; not as you spelled it, nohwcrpt.

Please correct your misspelling.


I did correct the spelling, now the dmesg | grep atk shows no output. But still the issue remains.

---

### Post by chili555 on 2018-07-26
I am afraid that I have no other suggestions.

My colleagues and I have worked on the abcd problem here and on other forums and, so far, there is no known solution. Sorry.

---

### Post by kenzo-zombie on 2018-07-28
okay, then can you suggest me any other wireless adapter which works out of the box? That would be really helpful.

Edit: It's because this is my 3rd wireless adapter I have to return. :(

---

### Post by chili555 on 2018-07-28
If internal, I like any of the Intels. For USB, see my post #22 here: [https://ubuntuforums.org/showthread.php?t=2359573&highlight=box](https://ubuntuforums.org/showthread.php?t=2359573&highlight=box)

---

