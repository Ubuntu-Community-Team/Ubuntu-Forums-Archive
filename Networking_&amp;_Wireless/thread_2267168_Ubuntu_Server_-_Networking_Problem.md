---
title: "Ubuntu Server - Networking Problem"
date: 2015-02-27
forum: Networking &amp; Wireless
---

### Post by Martin_Naylor on 2015-02-27
Hi, 

Bit of a Ubuntu Server novice and first post. I am struggling solving a networking issue im having. I have a HP Microserver using the onboard NIC with 2 drive with RAID setup as a NAS and this has been working fine for a couple of months.

All of a sudden this week the networking dropped off, just no connectivity. The cable is good, the lights on the back of the card are on, ive checked all physicals. I can't ping the device and the device can only ping itself.

I have a static IP address set under nano /etc/network/interfaces as below

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto em1
iface em1 inet static
address 192.168.0.20
gateway 192.168.0.1
netmask 255.255.255.0
network 192.168.0.0
broadcast 192.168.0.255
Then restarted the networking - /etc/init.d/networking restart  - still no joy.

I have enclosed outputs from the following

ifconfig -a 


[ATTACH=CONFIG]260318[/ATTACH]
lshw -class network

[ATTACH=CONFIG]260317[/ATTACH]

sudo ethtool em1

[ATTACH=CONFIG]260316[/ATTACH]

If theres anyone who can help or who can point me in the right direction i'd be very grateful. 

Im thinking it could possibly be the network card although it does seem have some traffic going through it and the lights are on the card at the back. Bit stumped.

Thanks, Martin

---

### Post by Doug S on 2015-02-27
Hi and welcome to Ubuntu forums.> **Martin_Naylor said:**
> Im thinking it could possibly be the network card although it does seem have some traffic going through it and the lights are on the card at the back. Bit stumped.Well, I'm stumped also. Everything looks O.K.

If you try to ping from the problem computer to another computer on your LAN, do you observe one of the lights on the NIC card blink once per second?
If you try to ping from another computer on your LAN to the problem computer, do you observe one of the lights on the NIC card on the problem computer blink once per second?

Is there a switch on your LAN? If yes, have you powered it down and powered it up again? Have you tried a different cable plug in spot on the switch?
Is there a router on your LAN?  If yes, have you powered it down and powered it up again? Have you tried a different cable plug in spot on the router?

You have re-booted the problem computer, right?

---

