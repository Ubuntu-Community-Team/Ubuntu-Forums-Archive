---
title: "Firestarted firewall blocks Virtual Box Windows VM"
date: 2008-11-19
forum: Networking &amp; Wireless
---

### Post by kaptain1 on 2008-11-19
Hi all,

I installed Firestarted firewall, but now it blocks my WindowsXP virtual machine, and i have to disable it in order to for Windows Virtual Box VM to go online. I tried to enable it, but can't figure it out. The Windows VM has a separate IP address, and is not using NAT.
Here's my 'Interfaces' file:

auto lo
iface lo inet loopback

iface eth0 inet static
address 192.168.32.115
netmask 255.255.255.0
gateway 192.168.32.254

iface tap0 inet dhcp
up ifconfig $IFACE 0.0.0.0 up
down ifconfig $IFACE down
tunctl_user kap1

auto br0
iface br0 inet dhcp
    bridge_ports eth0 tap

Thank You!

---

