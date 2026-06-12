---
title: "network device vanishes after being renamed [18.04 server]"
date: 2018-07-21
forum: Networking &amp; Wireless
---

### Post by nick-nick-brown on 2018-07-21
I recently installed 18.04 server on a Sabertooth 990FX motherboard with an onboard r8169 gigabit ethernet card.

When I try to find the device name with ls /dev/e* there are no results.

dmesg indicates "enp8s0: renamed from eth0"

What is going on? Why is the network device vanishing after being renamed?

---

### Post by TheFu on 2018-07-21
Ethernet devices haven't been in /dev/ for many, releases.  

There are multiple ways to get the known list. I use these:
```
sudo lshw -c network
dmesg |grep -i ethernet
```

There are others.

---

### Post by chili555 on 2018-07-21
> Why is the network device vanishing after being renamed?From where does it vanish?

What does this tell us?```
ls /etc/netplan
cat /etc/netplan/*.yaml
```

---

### Post by The Cog on 2018-07-21
The command **ip link** will list the interfaces. **ip addr** will even show the addresses they have.
As TheFu says, they have not lived in /dev for years. 

And recently they are not typically called eth* any more either, as dynamically discovered interfaces could get different interface names each reboot. Instead they are given names that correspond to the hardware such that their names don't change iven if the order that hardware discovery finds them changes. If you want to keep the old eth names this command will do it (my home PC only has one NIC so the order can't change):
```
sudo sh -c 'echo "# This file overrides the default interface naming" > /etc/udev/rules.d/80-net-setup-link.rules'
```

---

