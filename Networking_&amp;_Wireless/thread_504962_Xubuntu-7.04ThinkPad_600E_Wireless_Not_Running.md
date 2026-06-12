---
title: "Xubuntu-7.04/ThinkPad 600E: Wireless Not Running"
date: 2007-07-19
forum: Networking &amp; Wireless
---

### Post by fuzzydoc on 2007-07-19
This ThinkPad has run another Debian derivative, Red Hat, and Slackware; wireless networking has worked with all of them. Just replaced Slackware-11.0 with Xubuntu-7.04 on this laptop, and everything else -- including wired networking -- functions. The wireless doesn't.

  The card is a Lucent Technologies GOLD that uses the orinoco drivers. /etc/networking/interfaces contains:
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface

auto eth1
iface eth1 inet static
address 192.168.55.5
netmask 255.255.255.0
gateway 192.168.55.4

auto eth0
iface eth0 inet static
address 192.168.55.5
netmask 255.255.255.0
gateway 192.168.55.4

  ifconfig -a shows that eth1 is configured, but it's not running.

  Any and all suggestions and recommendations are appreciated.

Rich

---

### Post by jimrz on 2007-07-19
> **fuzzydoc said:**
> This ThinkPad has run another Debian derivative, Red Hat, and Slackware; wireless networking has worked with all of them. Just replaced Slackware-11.0 with Xubuntu-7.04 on this laptop, and everything else -- including wired networking -- functions. The wireless doesn't.

  The card is a Lucent Technologies GOLD that uses the orinoco drivers. /etc/networking/interfaces contains:
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface

auto eth1
iface eth1 inet static
address 192.168.55.5
netmask 255.255.255.0
gateway 192.168.55.4

auto eth0
iface eth0 inet static
address 192.168.55.5
netmask 255.255.255.0
gateway 192.168.55.4

  ifconfig -a shows that eth1 is configured, but it's not running.

  Any and all suggestions and recommendations are appreciated.

Rich

did you use "acpi=force" at boot? if so, add also "pci=noacpi" as the first can interfere with pcmia card functions. those 2 parameters are the only addition needed to make my 600x work "out of the box"

---

### Post by fuzzydoc on 2007-07-19
Jimrz:

  I had not used 'acpi=force' because this old a laptop uses apm instead. Regardless, I added the two options to the kernel line in /boot/grub/grub.lst and rebooted. No difference. 'ifconfig -a' shows the interface, but it's not running.

Many thanks,

Rich

---

### Post by jimrz on 2007-07-20
looking closer at your initial post, I may see the problem if you are using network-manager

```
inet static
```

have seen a bit of discussion that network-manager does not work with static ip's. 

to get around this on my internal network I use the address reservation feature in my router settings. this allows me to set an ip address, by comp name + mac address, for each computer on my network and the router will assign that ip to the comp each time it connects. this effectively gives me static ip functionality within my network while still using dhcp, which can avoid problems (such as the dreaded ip conflict) when connecting a laptop to other wifi networks and forgetting to change to dhcp from static. the one drawback is that I have to set 2 reservations (1 = wifi + 1 = wired)for each of the 2 laptops since each card has it's own mac addy. have not figured a way around this, but if a similar setup would fit your needs you might give it a shot. otherwise, i beleive you would have to remove network-manager and work only with interfaces.conf / System > Administration > Networking features.

---

