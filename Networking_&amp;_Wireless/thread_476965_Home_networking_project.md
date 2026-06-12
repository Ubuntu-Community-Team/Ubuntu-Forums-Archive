---
title: "Home networking project"
date: 2007-06-17
forum: Networking &amp; Wireless
---

### Post by survient on 2007-06-17
Ok, I'm trying to setup my own router with an old compaq. I have two NIC adapters in it, eth0 and eth1, as well as a wireless card, ath0. I'm trying to get it to connect to the internet through eth0, and have clients connect to it through eth1 and ath0. I'm leaving the wireless access point part out for now, until I can at least get internet connection sharing working for eth0 and eth1. The internet works fine if I set eth0 up for Automatic DHCP and disable eth1. I've tried installing firestarter to help me out and make it easier, but it just isn't working. I've tried manually setting eth1 to Static IP 192.168.0.1, Subnet Mask 255.255.255.0 and Gateway 192.168.0.1, and I've installed the dhcp3server package for firestarter, and rebooted numerous times. The fact is, when I enable eth1, eth0 will no longer connect to the internet. This part shouldn't be hard, I'm missing something, but I can't seem to figure it out.

---

### Post by trak87 on 2007-06-17
When you say you've installed Firestarter, did you go through the Wizard and select the option "Enable Internet Connection Sharing"? and then select eth1 as your "Local area network device"? That should at least get the eth1 sharing with other computers on the net. I'm not sure how to get the ath0 working as I've never set up both wired and wireless networking.

---

### Post by survient on 2007-06-17
I can work around the ath0 part later, right now I'm just trying to get the machine from looking to another connection for internet access. I'm trying to tell it "go to eth0 for internet", while still having eth1 enabled. I haven't even made it that far. I ran through the wizard several times. The machine I'm using as a "router" can't connect to the internet while the adapter that goes to the LAN is enabled(eth1). I thought it might be because I specified a gateway on eth1, but even after clearing that out, it still won't work while eth1 is enabled.

---

### Post by trak87 on 2007-06-17
Sometimes the routing gets screwy with the type of setup you are doing. What you do get running "netstat -rn" (or "route -n").

---

### Post by survient on 2007-06-21
Ok ran some tests, came up with this:

route -n comes up with these results

(internet doesn't work)
when eth0 is enabled, and eth1 is unchecked it is:
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.0.0     0.0.0.0         255.255.255.0   U     0      0        0 eth1
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 eth0
192.168.0.0     0.0.0.0         255.255.0.0     U     0      0        0 eth0
0.0.0.0         192.168.0.2     0.0.0.0         UG    0      0        0 eth0

(internet works)
when eth0 is enabled, and eth1 is set to roaming mode it is:
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 eth0
192.168.0.0     0.0.0.0         255.255.0.0     U     0      0        0 eth0
0.0.0.0         192.168.0.2     0.0.0.0         UG    0      0        0 eth0

(internet doesn't work)
when eth0 is enabled, and eth1 is enabled with static IP 192.168.0.1, and subnet mask 255.255.255.0 it is:
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.0.0     0.0.0.0         255.255.255.0   U     0      0        0 eth1
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 eth1
192.168.0.0     0.0.0.0         255.255.0.0     U     0      0        0 eth0
0.0.0.0         192.168.0.2     0.0.0.0         UG    0      0        0 eth0

so, hopefully that may answer some questions. If you need the netstat results, I'll install it and give them to you no prob. thx.

---

### Post by trak87 on 2007-06-23
I'm not very good at networking, but my sense is that the routing looks correct. I'm not able to provide any more advice at this point.

---

