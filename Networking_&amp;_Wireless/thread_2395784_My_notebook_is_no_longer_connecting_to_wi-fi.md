---
title: "My notebook is no longer connecting to wi-fi"
date: 2018-07-06
forum: Networking &amp; Wireless
---

### Post by Dedalo on 2018-07-06
Hi there. Since yesterday my notebook doesn't seem to be detecting the wi-fi signal. I know the problem is my notebook because I have wi-fi in my cellphone. Two days ago was working just fine, and yesterday when I started my notebook, it wasn't able to connect to the internet. Now I am posting with a wired connection.

I've tried to get information from my wi-fi card, but I'm not sure if it is working:
*:sudo lshw -class network*
*  *-network UNCLAIMED     *
*       description: Network controller*
*       product: BCM43142 802.11b/g/n*
*       vendor: Broadcom Corporation*
*       physical id: 0*
*       bus info: pci@0000:07:00.0*
*       version: 01*
*       width: 64 bits*
*       clock: 33MHz*
*       capabilities: pm msi pciexpress bus_master cap_list*
*       configuration: latency=0*
*       resources: memory:f7c00000-f7c07fff*
*  *-network*
*       description: Ethernet interface*
*       product: RTL8101/2/6E PCI Express Fast/Gigabit Ethernet controller*
*       vendor: Realtek Semiconductor Co., Ltd.*
*       physical id: 0*
*       bus info: pci@0000:09:00.0*
*       logical name: enp9s0*
*       version: 05*
*       serial: e0:db:55:88:71:bd*
*       size: 10Mbit/s*
*       capacity: 100Mbit/s*
*       width: 64 bits*
*       clock: 33MHz*
*       capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation*
*       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=half firmware=rtl_nic/rtl8105e-1.fw latency=0 link=no multicast=yes port=MII speed=10Mbit/s*
*       resources: irq:17 ioport:e000(size=256) memory:f0004000-f0004fff memory:f0000000-f0003fff*

Looking on google, it is told to modify a file, which my system is not able to find:

* sudo  /etc/pm/config.d/config*
[I]sudo: /etc/pm/config.d/config: command not found

[/I]My notebook is a bit old, it's a dell inspiron 3420, I was wondering if my wi-fi card stopped working, or if there might be something else going on. In the attachment you can see a picture of my networks.

[ATTACH=CONFIG]280296[/ATTACH]

---

### Post by Autodave on 2018-07-07
This may or may not help, but it is the very first thing that I do when I get a weird thing happening on a laptop:

1. Power down and disconnect power cord.
2. Unplug all peripherals.
3. Remove battery.
4. Wait 10 minutes.
5. Reinstall battery.
6. Connect power cord.
7. Boot computer and test to see if condition is gone.
8. If good so far, now you can reconnect peripherals.

---

### Post by jeremy31 on 2018-07-07
Moved to networking, post results from terminal for ```
uname -a
```

---

### Post by Dedalo on 2018-07-10
> **jeremy31 said:**
> Moved to networking, post results from terminal for ```
uname -a
```
Hi, thank you both.

*~$ uname -a*
*Linux Ullysses 4.15.0-24-generic #26~16.04.1-Ubuntu SMP Fri Jun 15 14:35:08 UTC 2018 x86_64 x86_64 x86_64 GNU/Linux*

---

### Post by Dedalo on 2018-09-09
Hi. I've upgraded to ubuntu 18.04 today, and now it's fixed. Just disconnected the wire minutes ago, and still working. The new version of ubuntu looks nice!

---

