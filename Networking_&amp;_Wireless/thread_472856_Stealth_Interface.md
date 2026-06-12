---
title: "Stealth Interface"
date: 2007-06-13
forum: Networking &amp; Wireless
---

### Post by cthesoup on 2007-06-13
I'd like to set up a stealth interface, and have done so on Red Hat/Fedora distros, but can't figure out how to do it on Ubuntu.

Here's how I'd accomplish it on Fedora:

1 -- Edit [FONT="Courier New"]/etc/sysconfig/network-scripts/ifcfg-eth2[/FONT]

2 -- Remove all entries and add:
[FONT="Courier New"]DEVICE=eth2
ONBOOT=yes
PROMISC=yes
ARP=no[/FONT]


This will active the interface, put it in promiscuous mode without an IP address and will turn off arp - which is important as the interface will still respond to an ARP request even without the IP address.

Any Ubuntu gurus able to help out?

Thanks.

---

### Post by dannyboy79 on 2007-06-13
you can read how to do it within the man pages
man ifconfig
after you enter the command thru the terminal, I am not completely sure how to make them stick each time you reboot or whatnot, maybe it could be added to the interfaces file with the pre-up line. good luck

---

### Post by cthesoup on 2007-06-13
That seems to be the crux of the matter.  I'm adept with the ifconfig command; what I'm looking for instructions on how to configure it permanently, not just runtime.

---

### Post by dannyboy79 on 2007-06-13
write your command in a script file somewhere in /etc/init.d
make it executable

run: 

update-rc.d your_script_name defaults

and this will make it permanent.

---

### Post by ler0y on 2007-11-25
Sorry to revive an old post, but I ran into the same issue and found a resolve. I found this link that had a great write-up on the interfaces file:
[http://www.cyberciti.biz/faq/setting-up-an-network-interfaces-file/]("http://www.cyberciti.biz/faq/setting-up-an-network-interfaces-file/")

Here is what I did with my /etc/network/interfaces:

```
:~$ cat /etc/network/interfaces
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto eth0
iface eth0 inet static
        address 192.168.1.8
        netmask 255.255.255.0
        gateway 192.168.1.254

auto eth2
iface eth2 inet manual
        up ifconfig $IFACE 0.0.0.0 up
        up ip link set $IFACE promisc on
        down ip link set $IFACE promisc off
        down ifconfig $IFACE down

auto eth3
iface eth3 inet manual
        up ifconfig $IFACE 0.0.0.0 up
        up ip link set $IFACE promisc on
        down ip link set $IFACE promisc off
        down ifconfig $IFACE down
```

Works after reboot with no need for extra scripting.

---

