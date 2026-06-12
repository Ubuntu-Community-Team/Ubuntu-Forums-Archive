---
title: "Driver Installation"
date: 2015-09-26
forum: Networking &amp; Wireless
---

### Post by rowen2 on 2015-09-26
I used ubuntu before but everything worked fine.
but at my new pc i have windows 8.
i dual booted ubuntu 14.04 LTS.
i have a sitecom wifi usb adapter and this doesn't work.
Also if i go to additional drivers, or do lspci -v or lsusb in live usb didnt work.
now i got it installed with lsub it detected Sitecom Europe B.V.
with ifconfig it only has eth0 and lo ofcourse
ive got this driver but its .tar.gz i extracted it but it only has some files but no readme or install.sh
i saw a makefile but how does this work ? 
plzz help
included in extracted folder:
clean, ifcfg-wlan0, Kconfig, Makefile, runwpa, wlan0dhcp
i recognize wlan0 as the default wlan name and wpa of wifi also dhcp but these others i dont know ?? 
plzz help asap :(

(other specs)
AMD FX-6300
AMD HD6970
16gb ddr3 ram
1tb drive (330g for ubuntu and 670 for win8.1)
2x 500gb drive

---

### Post by Geoffrey_Arndt on 2015-09-26
Just goto Amazon and get a "Panda Ultra Wifi" nano style dongle . . . . do a search on Amazon - Panda has at least 3 or 4 wifi usb adapters that are just plug and  play with Linux.   Cost is about $10. only.

---

### Post by Bucky Ball on 2015-09-26
*Thread moved to **Networking and Wireless**.*

Welcome. Please plug the dongle in and run this command in a terminal:

```
sudo lshw -C network
```

Post the result back here between code tags, thanks (see last link in my signature).

---

### Post by rowen2 on 2015-09-27
> **Bucky Ball said:**
> *Thread moved to **Networking and Wireless**.*

Welcome. Please plug the dongle in and run this command in a terminal:

```
sudo lshw -C network
```

Post the result back here between code tags, thanks (see last link in my signature).

ok i did sudo lshw -C network and i got this:

```

  *-network               
       description: Ethernet interface
       product: RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:05:00.0
       logical name: eth0
       version: 06
       serial: d0:50:99:54:d1:06
       size: 10Mbit/s
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=half firmware=rtl8168e-3_0.0.4 03/27/12 latency=0 link=no multicast=yes port=MII speed=10Mbit/s
       resources: irq:28 ioport:d000(size=256) memory:d0004000-d0004fff memory:d0000000-d0003fff
 
```

it doesn't even detect the adapter ? thats where im worried about :(

---

### Post by matt_symes on 2015-09-27
Hi

Unplug the adaptor. Open a terminal and type

```
tail -f /var/log/syslog
```

Plug the adaptor back in and wait 10 seconds. 

Post the output from the tail command into your next post.

That may give more diagnostic information.

Kind regards

---

### Post by rowen2 on 2015-09-28
> **matt_symes said:**
> Hi

Unplug the adaptor. Open a terminal and type

```
tail -f /var/log/syslog
```

Plug the adaptor back in and wait 10 seconds. 

Post the output from the tail command into your next post.

That may give more diagnostic information.

Kind regards

@school atm will try this later and give the diagnostic info in my next post :)

---

