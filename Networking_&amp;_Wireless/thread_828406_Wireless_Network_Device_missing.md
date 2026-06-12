---
title: "Wireless Network Device missing?"
date: 2008-06-13
forum: Networking &amp; Wireless
---

### Post by Naatan on 2008-06-13
Hi,

I have an HP Pavilion dv6710ed with wifi, but in Ubuntu there is only a wired network card, though the restricted drivers manager does have the wireless card enabled.

I have tried installing the windows drivers with ndiswrapper, this worked flawlessly and it says it's installed, but when I run "ifconfig" there's only eth01 and lo, no wireless card.

Network section of lshw:

```

  *-network               
       description: Ethernet interface
       product: MCP65 Ethernet
       vendor: nVidia Corporation
       physical id: 6
       bus info: pci@0000:00:06.0
       logical name: eth0
       version: a3
       serial: 00:1e:68:1d:ca:6b
       size: 100MB/s
       capacity: 1GB/s
       width: 32 bits
       clock: 66MHz
       capabilities: pm bus_master cap_list ethernet physical mii 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=forcedeth driverversion=0.61 duplex=full ip=192.168.2.104 latency=0 link=yes maxlatency=20 mingnt=1 module=forcedeth multicast=yes port=MII speed=100MB/s
  *-network UNCLAIMED
       description: Ethernet controller
       product: AR242x 802.11abg Wireless PCI Express Adapter
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:03:00.0
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix cap_list
       configuration: latency=0

```

Does anyone know what might cause this?

---

### Post by Naatan on 2008-06-19
bump

---

### Post by lswest on 2008-06-19
How have you installed/set up the wireless drivers for the atheros card?

*EDIT* never mind, didn't notice you mentioned that already.

First off, did you remove the restricted driver module?  and what is the output of ```
sudo ndiswrapper -l
```

---

### Post by Naatan on 2008-06-19
Yes I did, I followed the steps on the ndiswrapper site.

The output is

```
net5211 : driver installed
    device (168C:001C) present (alternate driver: ath_pci)
```

That seems correct to me (?)

But when I click the network icon in the system tray it only says "Wired network"

---

### Post by lswest on 2008-06-19
hmm, try this:
```
sudo modprobe -r ath_pci
sudo modprobe -r ndiswrapper
sudo modprobe ndiswrapper
``` and if that doesn't work run this command before you try it again: ```
sudo ndiswrapper -m
```

---

### Post by Naatan on 2008-06-19
hmm when I run the first command I get:

FATAL: Could not load /lib/modules/2.6.18-ovz028stab053.5-smp/modules.dep: No such file or directory

---

### Post by wesswei on 2008-06-19
I'm in the same boat...

Was using rt2570 usb device for wireless, but wanted to connect via wpa.

SO... i tried ndiswrapper. to make a long story short, now the wireless device is not even listed. no wlan0 or rausb0...

---

### Post by lswest on 2008-06-22
@ the OP:

Can you instead do this (replacing the first line) ```
sudo gedit /etc/modprobe.d/blacklist
``` and add ```
blacklist ath_pci
``` at the end of that file, then re-run the commands from line 2 onwards (reboot first)

---

### Post by Naatan on 2008-06-25
Awesome !! That worked! :D

Will it stick now or do I have to re-run the commands after every reboot?

Thanks a lot Iswest :)

---

### Post by Naatan on 2008-06-26
It appears I have to re-run the commands every time I reboot..

any way to make it stick?

---

