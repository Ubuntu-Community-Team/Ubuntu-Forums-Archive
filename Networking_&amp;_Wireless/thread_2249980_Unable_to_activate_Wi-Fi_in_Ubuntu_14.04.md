---
title: "Unable to activate Wi-Fi in Ubuntu 14.04"
date: 2014-10-25
forum: Networking &amp; Wireless
---

### Post by Stefano1970 on 2014-10-25
Hallo,
I just switched to Ubuntu 14.04 LTS and I still haven't been able after many attempts to acrivate Wi-Fi. Could you please help me? Thanks a lot

](*,)

---

### Post by Bucky Ball on 2014-10-25
Open a terminal and paste this in:

```
sudo lshw -C network
```

Post the output back here, please.

You say 'many attempts' but don't say what that involved. Have you checked in Additional Drivers?

---

### Post by Stefano1970 on 2014-10-26
> **Bucky Ball said:**
> Open a terminal and paste this in:

```
sudo lshw -C network
```

Post the output back here, please.

You say 'many attempts' but don't say what that involved. Have you checked in Additional Drivers?

Hallo,
here we go:

```
*-network DISABLED      
       description: Wireless interface
       product: AR9285 Wireless Network Adapter (PCI-Express)
       vendor: Qualcomm Atheros
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: wlan0
       version: 01
       serial: 00:25:d3:72:3c:8e
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ath9k driverversion=3.13.0-37-generic firmware=N/A latency=0 link=no multicast=yes wireless=IEEE 802.11bgn
       resources: irq:17 memory:fbff0000-fbffffff
  *-network
       description: Ethernet interface
       product: AR8132 Fast Ethernet
       vendor: Qualcomm Atheros
       physical id: 0
       bus info: pci@0000:01:00.0
       logical name: eth0
       version: c0
       serial: 90:e6:ba:5b:d7:d0
       capacity: 100Mbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress vpd bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=atl1c driverversion=1.0.1.1-NAPI latency=0 link=no multicast=yes port=twisted pair
       resources: irq:45 memory:f7fc0000-f7ffffff ioport:ec00(size=128)
```

I have tried to check in additional drivers but I've found no driver available.

Thenks a lot

---

### Post by Bucky Ball on 2014-10-26
That looks like the right driver, it's broadcasting, but the card is disabled for some reason. There isn't a hardware switch on the laptop anywhere that switches the card on perhaps? This should work out of the box. When you click the network icon, you do have 'Enable Wifi' and 'Enable Networking' ticked ?

You could try this. Create a new file /etc/modprobe.d/ath9k.conf:

```
sudo mkdir /etc/modprobe.d/ath9k
```

Then ...

```
sudo nano /etc/modprobe.d/ath9k.conf
```

Add the following line to it:

```
options ath9k nohwcrypt=1
```

Save and reboot. Fix from [HERE.]("http://www.htpcbeginner.com/how-to-fix-atheros-ar9285-ar9287-wireless-problems-in-ubuntu-1104/")

---

### Post by Stefano1970 on 2014-10-26
> **Bucky Ball said:**
> That looks like the right driver, it's broadcasting, but the card is disabled for some reason. There isn't a hardware switch on the laptop anywhere that switches the card on perhaps? This should work out of the box. When you click the network icon, you do have 'Enable Wifi' and 'Enable Networking' ticked ?

You could try this. Create a new file /etc/modprobe.d/ath9k.conf:

```
sudo mkdir /etc/modprobe.d/ath9k
```

Then ...

```
sudo nano /etc/modprobe.d/ath9k.conf
```

Add the following line to it:

```
options ath9k nohwcrypt=1
```

Save and reboot. Fix from [HERE.]("http://www.htpcbeginner.com/how-to-fix-atheros-ar9285-ar9287-wireless-problems-in-ubuntu-1104/")

Hallo Bucky Ball,
I tried to switch the card on in some way but unfortunately still haven't succeeded. I did follow the instruction above but nothing happened. 
Thanks anyway for your support

---

