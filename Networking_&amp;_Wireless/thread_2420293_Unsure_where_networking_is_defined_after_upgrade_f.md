---
title: "Unsure where networking is defined after upgrade from LTS 16.04 &gt; 18.04.2"
date: 2019-06-02
forum: Networking &amp; Wireless
---

### Post by Wintersdark on 2019-06-02
Hello!  Since upgrading my server from 16.04, I'm not entirely certain where networking is configured.  I previously had two NIC's (enp6s0 and enp7s0) defined as slaves to bond0, which had a static IP address.  However, somewhat recently after a reboot I was having enp6s0 getting an IP address via dhcp, and this resulting in conflicts (bond0 still got it's static IP, enp6s0 getting a dhcp IP).  I commented out my existing /etc/network/interfaces setup, and just set enp6s0 to a static configuration:

```
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

source /etc/network/interfaces.d/*

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
#auto enp6s0
#iface enp6s0 inet manual
#       bond-master bond0

#auto enp7s0
#iface enp7s0 inet manual
#       bond-master bond0
#
#auto bond0
#iface bond0 inet static
#       bond-slaves enp6s0 enp7s0
#       bond-mode 1
#       bond-miimon 100
auto enp6s0
iface enp6s0 inet static
        address 192.168.0.10
        netmask 255.255.255.0
        network 192.168.0.0
        broadcast 192.168.0.255
        gateway 192.168.0.1
        dns-nameservers 192.168.0.1 1.0.0.1

```

Curiously, after a reboot, ifconfig shows bond0 still existing and receiving an ip address (also 192.168.0.10).  There is nothing in /etc/netplan, and I've never done anything with netplan.  /etc/network/interfaces.d/ is empty as well.

Where else can bond0 be being defined?  How can I go about tracking this down?

---

### Post by TheFu on 2019-06-03
18.04 and later don't use interfaces or ifupdown tools.  Something called netplan has replaced it.  I know nothing about netplan. Sorry.

I have seen many threads here with people having issues using netplan, **especially with non-trivial setups**. If you have 1 NIC or need a trivial DHCP setup, it will probably be fine. If you are using bonded interfaces to multiple switches and using those for Linux bridges, good luck.
Documentation is here: [https://netplan.io/](https://netplan.io/)  hopefully it is truthful and not aspirational, like systemd.

Probably best to move /etc/network/ somewhere else, since it isn't used at all. Obviously, keep it somewhere for reference, just outside /etc/

---

### Post by #&amp;thj^% on 2019-06-03
When I first played with Netplan on only a couple of ubuntu (18.04 and 19.04<<for testing only) systems I ran:
It has been a while, but i believe i just did:
```
# apt install ifupdown
# apt remove netplan.io
```
if you not doing anything advanced I thought the netplan .yml files in /etc/netplan are pretty nice once you get use to them. I have been doing a lot of ansible lately so yml files are not to bad. 
**And a little more info to digest before ditching netplan:** [https://www.linux.com/learn/intro-to-linux/2018/9/how-use-netplan-network-configuration-tool-linux](https://www.linux.com/learn/intro-to-linux/2018/9/how-use-netplan-network-configuration-tool-linux)
Good Luck

---

