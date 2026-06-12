---
title: "Unable to Automount nfs lan partions upon boot, mounts manually"
date: 2008-03-05
forum: Networking &amp; Wireless
---

### Post by Idiot_Box on 2008-03-05
I am having an issue with nfs mounts in fstab during boot.

Wired NIC was set manually in /etc/network/interfaces

    auto lo
    iface lo inet loopback

    auto eth0
    iface eth0 inet static
    address 192.168.1.100
    netmask 255.255.255.0
    network 192.168.1.0
    broadcast 192.168.1.255
    gateway 192.168.1.1

fstab settings:

    192.168.1.50:/Media/Documents /home/user/Documents nfs rw 0 0
    192.168.1.50:/Media/Pictures /home/user/Pictures nfs rw 0 0
    192.168.1.50:/Media/MP3s /home/user/Music nfs rw 0 0
    192.168.1.50:/Media/Backups /home/user/.Backups nfs rw 0 0

This does not mount automatically upon boot, but once the machine is up and running, these folders DO mount sometimes when I restart my network (/etc/init.d/network restart).  

When the network interface is restarted manually, it either mounts successfully, or I receive an SIODCART error.  If this error pops up, restarting the network will not work.  I have to reboot and restart the network manually until it mounts successfully.  Help me please...this is really annoying.

---

