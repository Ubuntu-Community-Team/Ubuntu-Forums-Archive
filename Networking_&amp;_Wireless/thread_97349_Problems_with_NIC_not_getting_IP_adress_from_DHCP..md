---
title: "Problems with NIC not getting IP adress from DHCP..."
date: 2005-11-30
forum: Networking &amp; Wireless
---

### Post by RichardJ on 2005-11-30
I have a clean Ubuntu 5.10 install on the workstation, but the network wont configure correctly... The lspci-command display my Netgear card as "Lite-on...something" and i also tried swapping the NIC to my older Surecom card, but that is displayed as "Realtec...something".

My problem is the cards wont recieve an ip-adress from my dhcp-server in the router. Just for the record, i have set up static dhcp for my MAC-adress on the Netgear-card, but that shouldnt have any impact on the client side, should it?

I have tried setting the cards up with static ip-adresses, but with no luck. "Ping 192.168.0.1" just says "Netword unreachable" or something like that. "Dhclient eth0" doesnt get any DHCPOFFER's either...

My /etc/network/interfaces looks about right, as it should since i set the card up via X... (right?)

Any other ideas? My intuition tells me my system recognizes these cards faulty and i need to manually install the correct drivers or something, but since im somewhat of a linux-noob i dont really know how to do that, so any help is appreciated :)

-----
Edit: Another strange thing, i commented away IPv6 in /etc/modprobe.d/aliases, but my cards still get an ipv6-adress upon boot, why is that?

---

### Post by RichardJ on 2005-12-01
...so do anyone know if i need to install a new driver to my NIC?  Its a "NETGEAR FA310TX"

---

### Post by Lambert on 2005-12-01
[QUOTE=RichardJ]
My problem is the cards wont recieve an ip-adress from my dhcp-server in the router. Just for the record, i have set up static dhcp for my MAC-adress on the Netgear-card, but that shouldnt have any impact on the client side, should it?[/QUOTE]

No this shouldn't matter as that's my set up and it works fine.

> I have tried setting the cards up with static ip-adresses, but with no luck. "Ping 192.168.0.1" just says "Netword unreachable" or something like that. "Dhclient eth0" doesnt get any DHCPOFFER's either...

When you tried static, did you check the command ifconfig to see if the address is there for the device? second line should say inet address: xxx.xxx.x.x If this is good then check the command route to see if there is a route to your gateway. there should be a line like

default xxx.xxx.x.x ug u u u u eth0

or something like that. Where xxx.xxx.x.x = your routers ip

There have been a few posts in the past few weeks about no dhcpoffer and it's baffling quite a few people. I haven't seen a post with a solution. Some by just playing and rebooting found it to work but have no idea what happend.

> Any other ideas? My intuition tells me my system recognizes these cards faulty and i need to manually install the correct drivers or something, but since im somewhat of a linux-noob i dont really know how to do that, so any help is appreciated :)

If you run iwconfig and have good output on the device then your driver should be working ok. Try this command iwlist ethx scan to see if the device can see the router. (where ethx = your devices logical name)

Let's find what driver the nic is using.

sudo lshw -C network

find the device and a line starting with "configuration:" and notice what driver it says it's using.

---

