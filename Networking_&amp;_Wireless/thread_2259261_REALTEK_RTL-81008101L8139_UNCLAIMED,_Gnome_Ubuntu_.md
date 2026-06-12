---
title: "REALTEK RTL-8100/8101L/8139 UNCLAIMED, Gnome Ubuntu 14.04"
date: 2015-01-03
forum: Networking &amp; Wireless
---

### Post by mac75a on 2015-01-03
Hi,

I have two wired cards in my system (Gnome Ubuntu 14.04) and I have some problems with them. Some months/years ago I plugged an old REALTEK RTL-8100/8101L/8139 card because the system "refused to detect" (probably it was unclaimed) the RTL8111/8168/8411 PCI Express Gigabit mounted on my mobo (my system was not 14.04, but an older release). Now, with a fresh install of Gnome Ubuntu 14.04, the system sometimes gets both cards enabled, but other times the RTL-8100/8101L/8139 card is not claimed and I don't know why.

I paste the output from some commands. It is in spanish, but I think that no translation is needed (if it is, please tell me). Well, "NO RECLAMADO" means "UNCLAIMED".

```
  $ sudo lshw -C network
   *-network               
       descripción: Ethernet interface
       producto: RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller
       fabricante: Realtek Semiconductor Co., Ltd.
       id físico: 0
       información del bus: pci@0000:01:00.0
       nombre lógico: eth0
       versión: 03
       serie: 20:cf:30:f3:81:d8
       tamaño: 100Mbit/s
       capacidad: 1Gbit/s
       anchura: 64 bits
       reloj: 33MHz
       capacidades: pm msi pciexpress msix vpd bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuración: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=full firmware=rtl_nic/rtl8168d-2.fw ip=192.168.0.166 latency=0 link=yes multicast=yes port=MII speed=100Mbit/s
       recursos: irq:42 ioport:d800(size=256) memoria:fdfff000-fdffffff memoria:fdff8000-fdffbfff memoria:feaf0000-feafffff
  *-network NO RECLAMADO
       descripción: Ethernet controller
       producto: RTL-8100/8101L/8139 PCI Fast Ethernet Adapter
       fabricante: Realtek Semiconductor Co., Ltd.
       id físico: 0
       información del bus: pci@0000:03:00.0
       versión: 10
       anchura: 32 bits
       reloj: 33MHz
       capacidades: pm cap_list
       configuración: latency=65 maxlatency=64 mingnt=32
       recursos: ioport:ee00(size=512) memoria:febffc00-febffdff

```


```
$ lsmod
[...]
8139too                33544  0 
8139cp                 27953  0 
r8169                  67581  0 
mii                    13934  3 r8169,8139cp,8139too

```

I added 8139too and r8169 to /etc/modules to force the system to load these modules...
```
$ cat /etc/modules
# /etc/modules: kernel modules to load at boot time.
#
# This file contains the names of kernel modules that should be loaded
# at boot time, one per line. Lines beginning with "#" are ignored.
# Parameters can be specified after the module name.

lp
rtc
8139too
r8169

```

```
$ lspci -nn | grep 0200
01:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [10ec:8168] (rev 03)
03:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL-8100/8101L/8139 PCI Fast Ethernet Adapter [10ec:8139] (rev 10)

```

Please, can someone post any clue about why the card is not always claimed? (yesterday it worked perfectly... today I rebooted 5 times and no luck, so I have to use the other card... But maybe tomorrow this card will not be claimed...)
Can it be a conflict between both realtek cards? (it sounds weird though...)

Thanks in advance!

---

### Post by praseodym on 2015-01-03
This card regularly loads two drivers:
```

8139too                33544  0 
8139cp                 27953  0 
```
Blacklist the wrong one:
```

echo "blacklist 8139cp" | sudo tee -a /etc/modprobe.d/blacklist.conf
```

---

### Post by mac75a on 2015-01-03
Thanks for your answer, praseodym.

The module 8139cp is loaded even if I blacklist it:
```
$ cat /etc/modprobe.d/blacklist.conf
[...]
blacklist 8139cp
blacklist mii

```

I tried blacklisting mii as it seems to use 8139cp, but even so, both modules are loaded:
```
$ lsmod
[...]
r8169                  67581  0 
8139too                33544  0 
8139cp                 27953  0 
mii                    13934  3 r8169,8139cp,8139too

```

---

### Post by praseodym on 2015-01-03
Run:
```

sudo modprobe -rfv 8139cp 8139too
sudo modprobe -v 8139too
sudo depmod -a
sudo update-initramfs -u
```

---

### Post by mac75a on 2015-01-03
OK, 8139cp is not loaded any more.

```

$ lsmod | grep 8139
8139too                33544  0 
mii                    13934  2 r8169,8139too

```

But even so, the card keeps unclaimed :-(

```

*-network NO RECLAMADO
       descripción: Ethernet controller
       producto: RTL-8100/8101L/8139 PCI Fast Ethernet Adapter
       fabricante: Realtek Semiconductor Co., Ltd.
       id físico: 0
       información del bus: pci@0000:03:00.0
       versión: 10
       anchura: 32 bits
       reloj: 33MHz
       capacidades: pm cap_list
       configuración: latency=64 maxlatency=64 mingnt=32
       recursos: ioport:ee00(size=512) memoria:febffc00-febffdff

```

Thank you very much for your help!

---

### Post by praseodym on 2015-01-04
Is the cable plugged there?

---

### Post by mac75a on 2015-01-04
No, the cable wasn't plugged in that interface, but in the other one. When I plugged the cable nothing changed. But after two reboots with the cable plugged, suddenly it became claimed and started working...

I did some more reboots with the cable plugged, and again it became unclaimed.

After that I decided to test booting from a Windows partition, and it said that the network card could not be initialized (it was recognized in the devices management section, but with a yellow warning sign on it), and the green led of the card was off (the cable was plugged). I rebooted from Windows partition again, and this time the card worked perfectly.

I did some more reboots from Ubuntu and now it seems that the card is always claimed and it works...

So, it seems that is a hardware problem with the card or the mobo, because it is very strange that it works randomly, and it stops working without any reason in Ubuntu and in Windows...

I will mark the thread as solved (if I guess how to do it :) ). Thank you very much for your help, praseodyn!

Regards.

---

