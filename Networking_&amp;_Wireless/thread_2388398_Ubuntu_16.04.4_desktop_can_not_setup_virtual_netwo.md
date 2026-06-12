---
title: "Ubuntu 16.04.4 desktop can not setup virtual network interface"
date: 2018-04-02
forum: Networking &amp; Wireless
---

### Post by flashbang on 2018-04-02
For Clonezilla SE

example in sudo gedit /etc/network/interfaces:

Loopback
auto lo
iface lo inet loopback

#Network Interface, this should match your network
auto eno1
iface eno1 inet static
address 192.168.1.200
netmask 255.255.255.0
gateway 192.168.1.1

#Virtual Interface for Clonezilla, make sure you use a "class C" IP (192.168.x.x)
auto eth0:0
iface eth0:0 inet static
address 192.168.99.200
netmask 255.255.255.0

then sudo /etc/init.d/networking restart

won't show in ifconfig.

can't get past this step for days.

I only have one built in network card.

any input other than clonezilla SE just won't work in ubuntu desktop?

Yes even reboot.
ifconfig only shows
eno1

lo

Unmanaged network-manager also with same results.

Do the entry's have to be indented or tabed?

---

### Post by TheFu on 2018-04-02
indent or tabs don't matter, but the network adapter device must be correct. You are showing eth0 and eno1 above.  

On my systems running systemd, the network device name is based on the MAC for the NIC(s) in the machine with a new install.
[https://ubuntuforums.org/showthread.php?t=2368932](https://ubuntuforums.org/showthread.php?t=2368932) shows the new setup in 16.04.  At least it appears to.  The device:0 method doesn't work anymore.

Using *sudo gedit* can cause issues.  Best to use **sudoedit** instead.  This command is always safe.

Please post text files using "code tags" - that is Adv Reply (#)

---

### Post by flashbang on 2018-04-02
Was a typo.

Thanks I'll keep trying.

---

