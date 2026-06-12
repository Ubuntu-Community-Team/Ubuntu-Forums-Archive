---
title: "Network not starting on boot"
date: 2007-04-13
forum: Networking &amp; Wireless
---

### Post by pevans_om on 2007-04-13
Hi

I have a problem with Ubuntu 6.10 on my laptop. Every time I boot my computer the network is disabled. To get the network up I must open a console and type 'sudo ifdown --all', 'sudo ifup --all', then everything works fine.

My interfaces file looks like this:

```
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

iface ath0 inet dhcp
wireless-essid BU
wireless-key **********

iface eth0 inet static
address 192.168.10.22
netmask 255.255.255.0
gateway 192.168.10.0

auto eth0

auto ath0

```

I've have tried clearing all this and setting up the network from scratch, to no effect.

I did move my /var/ folder onto a new partition. I think something in that move may have caused this. I just don't know what it might be.

Also, I have vmware server installed but every time I want to run vmware I have to first run the config script. Then it all works fine until I reboot my computer. Then I need to run the config script again. This may be related (or not...)

Any help would be appreciated.

Regards
Paul

---

### Post by chili555 on 2007-04-13
> I did move my /var/ folder onto a new partition. I think something in that move may have caused this.Probably. I would look at how this was accomplished. If you just copied it over and didn't correctly modify /etc/fstab it probably didn't go well. When you do ```
df -h
```do you see a /var mountpoint? If not, you have some work to do. That's a question for a different forum than 'networking.'

Of more concern is that *both* interfaces, eth0 and ath0 are told to start automatically:```
auto eth0

auto ath0
```You really don't want two interfaces trying to get a different IP address at the same time. Pick which one is the primary interface you use daily and remove the 'auto Xth0' for the other one. You can always ifdown one and ifup the other if you need to.

---

