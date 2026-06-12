---
title: "Wired internet no longer works"
date: 2008-05-31
forum: Networking &amp; Wireless
---

### Post by Rahu on 2008-05-31
I just unplugged my ethernet cable to use it for something else. When I plugged it back in I couldn't get a net connection. So far I've tried a reboot and disabling and re-enabling the card but it still won't work.

The ethernet works when booting to a live cd.

Anyone know where I can go to reset any configuration on this computer about my network card to get it back to the original settings?

---

### Post by darco on 2008-05-31
run ifconfig up......
if doesnt work, try sudo lshw -C network and see what it says,,,

good luck
darco

---

### Post by Rahu on 2008-05-31
lshw -C network:
>   *-network
       description: Ethernet interface
       product: 3c905C-TX/TX-M [Tornado]
       vendor: 3Com Corporation
       physical id: 8
       bus info: pci@0000:00:08.0
       logical name: eth0
       version: 78
       serial: 00:50:da:d7:1a:0c
       size: 100MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=3c59x duplex=full latency=32 link=yes maxlatency=10 mingnt=10 module=3c59x multicast=yes port=MII speed=100MB/s


ifconfig up says "error fetching interface information: device not found"

---

### Post by darco on 2008-05-31
sudo ifconfig eth0 up 
sorry
darco

---

### Post by Rahu on 2008-05-31
Think it was just my router being terrible like it does sometimes.

Renewing DHCP wouldn't work, but switching to a static IP and then back to DHCP fixed it...

---

