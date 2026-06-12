---
title: "Wireless-to-ethernet bridging on Feisty"
date: 2007-04-07
forum: Networking &amp; Wireless
---

### Post by bugnotme on 2007-04-07
Edit: I solved my problem. I need to set the gateway on the client as the laptop.


I have a laptop connected to a router through ethernet. The laptop has a wireless card.
I want to turn the laptop into a (temporary) wireless access point; transparently passing packets from the wireless interface to the LAN. I thought it would be straightforward but I can't seem to get it working. Here are the steps I take:

```

sudo /etc/dbus-1/event.d/25NetworkManager stop # Don't let network manager control settings
sudo modprobe iptable_nat
sudo iptables -t nat -A POSTROUTING -o eth0 -j MASQUERADE
sudo bash -c 'echo 1 > /proc/sys/net/ipv4/ip_forward'
sudo iwconfig eth1 mode ad-hoc essid NetworkName channel 2

```

eth1 is my wireless interface.


My wireless PDA sees the WLAN and is able to connect, but I don't think the packets are being passed properly because 
1- It does not retrieve a DHCP lease.
2- When set to a static IP it still doesn't seem to be able to pass packets, although I can ping the PDA from the laptop

Any help is appreciated. This is driving me nuts.


Feisty Beta, ipw2200

---

### Post by Paris Heng on 2007-07-14
Hi, do you solved your problem already? on the bridging...

---

