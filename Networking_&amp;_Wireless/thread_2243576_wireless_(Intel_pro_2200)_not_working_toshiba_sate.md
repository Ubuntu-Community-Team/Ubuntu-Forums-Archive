---
title: "wireless (Intel pro 2200) not working toshiba satellite pro m30 using xubuntu 14.04"
date: 2014-09-09
forum: Networking &amp; Wireless
---

### Post by romduf on 2014-09-09
Hi all
I am sorry to post again this trouble, i search the whole forum for hours and tries many commands, but it didnt work.
My system : toshiba satellite pro m30
512 MB
NVIDIA GeForce FX Go5200 - 64 MB DDR SDRAM 
Intel Pentium M 735 / 1.7 GHz

I installed a fresh new xubuntu 14.04 (had a few troubles enabling PAE on this laptop)

The wireless wont work, even if i press FN + F8, i checked in the bios, nothing there.

I downloaded the firmware for ipw2200 and copied them in /lib/firmware but nothing changed...
I tried many commands from other posts as i am completely new to linux but nothing changed...

Can someone help ?

Thanks

---

### Post by weatherman2 on 2014-09-10
Are you sure there isn't a physical toggle switch for the wireless card?  Those older laptops usually have a physical switch to turn the card on/off.  If so, doing FN + F8 would do nothing.

---

### Post by romduf on 2014-09-10
Hi weatherman.
Indeed !!! I found this physical toggle, i never heard of or seen it in the manual...
BUT even after toggling it and rebooting, nothing changed.
I copy here some infos

lspci


```
00:00.0 Host bridge: Intel Corporation 82855PM Processor to I/O Controller (rev 21)
00:01.0 PCI bridge: Intel Corporation 82855PM Processor to AGP Controller (rev 21)
00:1d.0 USB controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #1 (rev 03)
00:1d.1 USB controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #2 (rev 03)
00:1d.7 USB controller: Intel Corporation 82801DB/DBM (ICH4/ICH4-M) USB2 EHCI Controller (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 83)
00:1f.0 ISA bridge: Intel Corporation 82801DBM (ICH4-M) LPC Interface Bridge (rev 03)
00:1f.1 IDE interface: Intel Corporation 82801DBM (ICH4-M) IDE Controller (rev 03)
00:1f.5 Multimedia audio controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller (rev 03)
00:1f.6 Modem: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Modem Controller (rev 03)
01:00.0 VGA compatible controller: NVIDIA Corporation NV34M [GeForce FX Go5200 64M] (rev a1)
02:07.0 FireWire (IEEE 1394): Texas Instruments TSB43AB22A IEEE-1394a-2000 Controller (PHY/Link) [iOHCI-Lynx]
02:08.0 Ethernet controller: Intel Corporation 82801DB PRO/100 VE (MOB) Ethernet Controller (rev 83)
02:0b.0 CardBus bridge: Toshiba America Info Systems ToPIC100 PCI to Cardbus Bridge with ZV Support (rev 33)
02:0d.0 System peripheral: Toshiba America Info Systems SD TypA Controller (rev 05)



```

ifconfig
```
eth0      Link encap:Ethernet  HWaddr 00:08:0d:78:8f:fe  
          inet adr:192.168.1.100  Bcast:192.168.1.255  Masque:255.255.255.0
          adr inet6: fe80::208:dff:fe78:8ffe/64 Scope:Lien
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          Packets reçus:2178 erreurs:0 :0 overruns:0 frame:0
          TX packets:2003 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 lg file transmission:1000 
          Octets reçus:1671333 (1.6 MB) Octets transmis:322235 (322.2 KB)


lo        Link encap:Boucle locale  
          inet adr:127.0.0.1  Masque:255.0.0.0
          adr inet6: ::1/128 Scope:Hôte
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          Packets reçus:545 erreurs:0 :0 overruns:0 frame:0
          TX packets:545 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 lg file transmission:0 
          Octets reçus:56854 (56.8 KB) Octets transmis:56854 (56.8 KB)

```

iwconfig
```

lo        no wireless extensions.


eth0      no wireless extensions.

```
sudo lshw -c network  *-network               
```
       
description: Ethernet interface
       produit: 82801DB PRO/100 VE (MOB) Ethernet Controller
       fabriquant: Intel Corporation
       identifiant matériel: 8
       information bus: pci@0000:02:08.0
       nom logique: eth0
       version: 83
       numéro de série: 00:08:0d:78:8f:fe
       taille: 100Mbit/s
       capacité: 100Mbit/s
       bits: 32 bits
       horloge: 33MHz
       fonctionnalités: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=e100 driverversion=3.5.24-k2-NAPI duplex=full ip=192.168.1.100 latency=66 link=yes maxlatency=56 mingnt=8 multicast=yes port=MII speed=100Mbit/s
       ressources: irq:11 mémoire:c2004000-c2004fff portE/S:3000(taille=64)



```

dmesg | grep ipw


```
[   21.193284] libipw: 802.11 data/management/control stack, git-1.1.13
[   21.193292] libipw: Copyright (C) 2004-2005 Intel Corporation <jketreno@linux.intel.com>
[   21.313339] ipw2200: Intel(R) PRO/Wireless 2200/2915 Network Driver, 1.2.2kmprq
[   21.313346] ipw2200: Copyright(c) 2003-2006 Intel Corporation
[  358.632379] libipw: 802.11 data/management/control stack, git-1.1.13
[  358.632384] libipw: Copyright (C) 2004-2005 Intel Corporation <jketreno@linux.intel.com>
[  358.684190] ipw2200: Intel(R) PRO/Wireless 2200/2915 Network Driver, 1.2.2kmprq
[  358.684194] ipw2200: Copyright(c) 2003-2006 Intel Corporation
[  449.856185] libipw: 802.11 data/management/control stack, git-1.1.13
[  449.856193] libipw: Copyright (C) 2004-2005 Intel Corporation <jketreno@linux.intel.com>
[  449.877135] ipw2200: Intel(R) PRO/Wireless 2200/2915 Network Driver, 1.2.2kmprq
[  449.877143] ipw2200: Copyright(c) 2003-2006 Intel Corporation



```


I want to point out that i have no idea of those commands or what they do, i just copy/paste from other threads in the forums in the terminal...

Thanks in advance for your help !!

---

### Post by romduf on 2014-09-10
I checked on other threads, but somehow cannot find any solution.
Strange is, somehow my wireless card doesnt seem to appear ?
I will try to clean the card and reconnect. I already checked all bios options (very few), with no changes.
Thanks for your help !

---

### Post by romduf on 2014-09-10
UPDATE
I am very sorry, i just discover that the wireless card is dead, so i took it out, i will try to find a replacement. I just used an old wifi usb key which is working now ! SOLVED

---

