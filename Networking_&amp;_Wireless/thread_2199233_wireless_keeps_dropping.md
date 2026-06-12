---
title: "wireless keeps dropping"
date: 2014-01-12
forum: Networking &amp; Wireless
---

### Post by scholzilla on 2014-01-12
Others have posted similar issues:
[http://ubuntuforums.org/showthread.php?t=2039809&p=12170200#post12170200](http://ubuntuforums.org/showthread.php?t=2039809&p=12170200#post12170200)
[http://ubuntuforums.org/showthread.php?t=2046109&highlight=wireless+dropping](http://ubuntuforums.org/showthread.php?t=2046109&highlight=wireless+dropping)	
but i haven't found a solution. 
I'm running 12.10 and have the rtl8187 wireless chipset. My connection drops repeatedly. It comes back on if I close the computer to sleep it and then open it again. Here's the output of iwconfig:
```

wlan0     IEEE 802.11bg  ESSID:"CasaViva"  
          Mode:Managed  Frequency:2.412 GHz  Access Point: FC:F5:28:B6:E7:71   
          Bit Rate=54 Mb/s   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=70/70  Signal level=-40 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:1012   Missed beacon:0

lo        no wireless extensions.

eth0      no wireless extensions.

```
any help is greatly appreciated

---

### Post by Bucky Ball on 2014-01-12
Please post the output of this to give us a better look:

```
sudo lshw -C network
```

---

### Post by scholzilla on 2014-01-12
Thanks for the response. Here's the output you requested

```

  *-network               
       description: Ethernet interface
       product: 88E8038 PCI-E Fast Ethernet Controller
       vendor: Marvell Technology Group Ltd.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: 14
       serial: 00:e0:b8:d3:d8:d5
       capacity: 100Mbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm vpd msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=sky2 driverversion=1.30 latency=0 link=no multicast=yes port=twisted pair
       resources: irq:16 memory:c0200000-c0203fff ioport:a000(size=256)
  *-network
       description: Wireless interface
       physical id: 2
       bus info: usb@1:6
       logical name: wlan0
       serial: 00:c0:a8:d8:96:a1
       capabilities: ethernet physical wireless
       configuration: broadcast=yes driver=rtl8187 driverversion=3.5.0-45-generic firmware=N/A ip=192.168.0.3 link=yes multicast=yes wireless=IEEE 802.11bg

```

---

### Post by slaytons on 2014-01-12
Who is the maker of your wireless card?
>  description: Wireless interface
       physical id: 2
       bus info: usb@1:6
       logical name: wlan0
Basically states that Ubuntu does not know the driver to use.

> description: Wireless interface
       product: Centrino Wireless-N 2230
       vendor: Intel Corporation
Is what my output shows.

If you can figure out the make/type of wireless card, you can get the correct driver installed.

---

### Post by Bucky Ball on 2014-01-13
> **slaytons said:**
> If you can figure out the make/type of wireless card, you can get the correct driver installed.

Exactly what we're attempting to do, although the correct driver is probably installed. ;)

Are you positive it is the rtl8187 chipset? Your kernel appears to have installed that driver, so it probably is, but do you know for certain? What is the make and model of the USB wireless dongle?

---

### Post by scholzilla on 2014-01-13
> **Bucky Ball said:**
> Exactly what we're attempting to do, although the correct driver is probably installed. ;)

Are you positive it is the rtl8187 chipset? Your kernel appears to have installed that driver, so it probably is, but do you know for certain? What is the make and model of the USB wireless dongle?

Yep, I'm certain about the chipset. I've actually opened the computer before to see it written on the chip. I've had this chipset for a long time with previous ubuntu versions, but don't recall having had this problem before version 12 (though other wireless problems occurred in the past).

---

### Post by scholzilla on 2014-02-01
This is still an issue. Can someone help? Thanks.

---

