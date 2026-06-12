---
title: "Acer Aspire One D257 Wireless not working"
date: 2016-08-28
forum: Networking &amp; Wireless
---

### Post by carlopau on 2016-08-28
Hi!

First off, let me say that I've searched in the forums (and the internet) for this issue and had no luck solving it. Also, I have tried some other distros besides the one I have on the machine right now (Xubuntu 16.04) and it's all the same.

The issue itself is that after I install the distro, or run the "try without installing" option, wifi stops working. The FN+F3 combination does not work, and it shows "Device not ready" when I click the connectitons icon.

Now, I tried some things (just one that I can remember actually, rfkill) and got this:

Wireless is not soft/hard blocked.
I can hard block it/unblock it using FN+F3, but the led light never turns on, and it never gives an option to connect, it just says "Device not ready" or "Device hardblocked" (Not the actual phrase, but something like that, I have the machine off and I'm using another one.

Also, just in case, the notebook has Intel Wireless-N 100 card on it, in case that can be useful.

Anything I need to post or do, will be more than happy to. Thanks in advance!

---

### Post by howefield on 2016-08-28
Thread moved to the "*Networking & Wireless*" forum for a better fit.

---

### Post by Bucky Ball on 2016-08-28
Welcome. Perhaps to start with, you could open a terminal and post the output of these two commands before digging deeper.

```
sudo lshw -C network
iwconfig
```

If it is a USB wireless dongle, please also post the output of this:

```
lsusb
```

Please post the outputs between code tags for ease of reading. See the green link in my signature at bottom of this post for how. Thanks.

---

### Post by carlopau on 2016-08-28
> **Bucky Ball said:**
> Welcome. Perhaps to start with, you could open a terminal and post the output of these two commands before digging deeper.

```
sudo lshw -C network
iwconfig
```

If it is a USB wireless dongle, please also post the output of this:

```
lsusb
```

Please post the outputs between code tags for ease of reading. See the green link in my signature at bottom of this post for how. Thanks.

Of course, first one is 

lshw
```

paulino@paulino-AOD257:~$ sudo lshw -C network
[sudo] password for paulino: 
  *-network               
       description: Ethernet interface
       product: RTL8101/2/6E PCI Express Fast/Gigabit Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:01:00.0
       logical name: enp1s0
       version: 05
       serial: e8:9a:8f:e1:bf:86
       size: 10Mbit/s
       capacity: 100Mbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=half firmware=rtl_nic/rtl8105e-1.fw latency=0 link=no multicast=yes port=MII speed=10Mbit/s
       resources: irq:28 ioport:3000(size=256) memory:50004000-50004fff memory:50000000-50003fff
  *-network DISABLED
       description: Wireless interface
       product: Centrino Wireless-N 100
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: wlp2s0
       version: 00
       serial: 78:92:9c:66:62:90
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=iwlwifi driverversion=4.4.0-31-generic firmware=39.31.5.1 build 32895 latency=0 link=no multicast=yes wireless=IEEE 802.11bgn
       resources: irq:31 memory:54000000-54001fff

```

iwconfig:
```

paulino@paulino-AOD257:~$ iwconfig
lo        no wireless extensions.


enp1s0    no wireless extensions.


wlp2s0    IEEE 802.11bgn  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=0 dBm   
          Retry short limit:7   RTS thr:off   Fragment thr:off
          Power Management:off

```

I am not using an usb wireless dongle (for now).

---

