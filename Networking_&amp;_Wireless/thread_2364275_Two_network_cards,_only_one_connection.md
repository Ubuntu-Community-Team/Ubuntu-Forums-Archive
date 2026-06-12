---
title: "Two network cards, only one connection"
date: 2017-06-21
forum: Networking &amp; Wireless
---

### Post by MOGuy78 on 2017-06-21
Hi everyone.  I have just installed a new media Server for me to store/watch all of my videos on.  I was planning on using the
eth0 connection, which has a DHCP IP, to connect to the internet to keep my OS up to date.

I was also wanting to set up the eth1 port as a Static IP that I can use specifically to give access to all of the other local devices
around the house, so that whoever wants to can watch the videos that I have stored on the server.

As I said above, I would like to give the eth0 port access to the internet to update the OS when needed; and I would like to
give my eth1 port a static IP so that, besides having a set IP, I can set it up where it will not have a gateway, therefore no
one can access the internet through it and watch other videos from online.

The problem is that the eth1 port is not being configured whenever I restart my server.  When I looked up the "/etc/network/interfaces"
file, eth1 is not even listed.  I know that the computer recognizes it, because When I first installed the OS, it listed
BOTH ports, then asked me which ethernet port I would like to use for my Primary connection.

What could be causing this?  And thanks for the help.

---

### Post by Bucky Ball on 2017-06-21
Bit confused. Are all the machines connected to the same network through a router or router/modem? The WAN (your internet connection) is getting into the router/modem directly to the one device?

If all machines are on the same network, it is a matter of setting the static IP on the media server and having other devices connect to it via the IP, not to do with eth*. Unless I'm misunderstanding something, which wouldn't be a first. ;)

Could you describe your hardware setup from internet to router/modem and how devices connect to that?

Or are you meaning you have no router and you have one physical internet connection and two devices you want to use with it?

* PS: Whether eth* has an IP served DHCP or a static IP set by you is up to you. Static or DHCP is not default to eth connection.
[QUOTE=MOGuy78 ]
I was planning on using the eth0 connection, which has a DHCP IP ...[/QUOTE]

---

### Post by SeijiSensei on 2017-06-21
You might want to browse this document for starters:  [https://help.ubuntu.com/community/Internet/ConnectionSharing](https://help.ubuntu.com/community/Internet/ConnectionSharing)

---

### Post by MOGuy78 on 2017-06-22
Sorry for the confusion everyone, I've never been the best at explaining things.

The basic computer layout that I'm planning on using is:
Internet ->  Modem ->  Switch ->  Slot1: Desktop;  Slot2: Desktop;  Slot3 and 4: Ubuntu Video Server;  Slot5, Slot6, etc.....
                                               
The computer that I installed the Ubuntu Server OS onto has two physical ethernet cards in it.  I connected both ports on the
ethernet adapters to 2 of the slots on the switch.  While I was installing the OS onto the computer, it listed both of the ethernet
cards on the screen, and asked which I wanted to use as the Primary Network Interface:
eth0: Silicon Integrated Systems 191 Gigabit Ethernet Adapter
eth1: Intel Corporation 82541PI Gigabit Ethernet Controller

I chose the (eth0) adapter, and was planning on using it (eth0) adapter to occasionally connect to the internet to keep the
software/drivers up to date, and to set the (eth1) controller as Static for the other local computers to access videos with.

After the server was finished installing, I wanted to edit the /etc/network/interfaces file to set the (eth1) IP address to Static.
But when I opened the file, it only has the primary adapter listed:

# The loopback network interface
auto lo
iface lo inet loopback
# The primary network interface
auto eth0
iface eth0 inet dhcp

Since it detected both ports while I was installing the system, I would assume that both ports are active.
Where is the setting for the eth1, so that I can edit it?

---

### Post by wyliecoyoteuk on 2017-06-22
Multihoming (which is what you are trying to do) is not that simple, and there are many ways to configure it, the most common being for load sharing or routing.
The system only set up the primary interface because any secondary ones need to be configured for the purpose they are intended.
You will need to define the settings for both cards and configure which services listen to which port on which card, and what the routing is between them.
in the first instance, try: 

sudo ifconfig

which will tell you what the system thinks is set up.

---

