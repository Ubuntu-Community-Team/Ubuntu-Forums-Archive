---
title: "Bonding together wlan0, eth0 and ppp0: Network is unreachable"
date: 2008-06-20
forum: Networking &amp; Wireless
---

### Post by gasull on 2008-06-20
Hi.

I'm trying to [bond together all the network interfaces]("https://help.ubuntu.com/community/UbuntuBonding") in my laptop (Lenovo 3000 V100). This is my /etc/network/interfaces:

```
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).
 
# The loopback network interface
auto lo
iface lo inet loopback

# Bluetooth dialup with Nokia N95
iface ppp0 inet ppp
provider BluetoothDialup
 
#auto bond0
iface bond0 inet static
address 192.168.1.10
gateway 192.168.1.1
netmask 255.255.255.0
pre-up modprobe bonding
up ifconfig bond0 up
up ifenslave bond0 wlan0 eth0 #ppp0
down ifenslave --detach bond0 wlan0 eth0 #ppp0
post-down rmmod bonding
```

And this is my /etc/modprobe.d/bonding:

```
alias bond0 bonding
options bonding mode=0 miimon=100
```

So for now I'm trying just to make it work with **wlan0** and **eth0**.  Because I'm doing this with a laptop I want it to work in all these 3 scenarios:

[LIST=1]
[*]Wireless connection available but wired connection not available
[*]Wireless connection not available but wired connection available
[*]Wireless and wired connections both available
[/LIST]

In the first scenario I get a "**Network is unreachable**" message when I execute the following commands:

```
sudo ifup bond0
ping google.com
```

I've tried running "sudo iwconfig wlan0 ap any" before "sudo ifup bond0", and also after it.

Are my **configuration files right?**

With the right configuration files, **what should I do to bring the bonding interface up?**

Thank you in advance.

---

### Post by BUGabundo on 2012-04-15
did you ever got anywhere with this?

---

