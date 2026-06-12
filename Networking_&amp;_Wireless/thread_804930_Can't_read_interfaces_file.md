---
title: "Can't read interfaces file"
date: 2008-05-23
forum: Networking &amp; Wireless
---

### Post by kbow on 2008-05-23
Can anyone help me figure out why this is happening ? Anytime I try to do anything that needs to read the interfaces file I am getting these errors.


kwaters@kwaters-laptop:~$ sudo /etc/init.d/networking restart
[sudo] password for user: 
 * Reconfiguring network interfaces...                                          /etc/network/interfaces:28: too few parameters for iface line
ifdown: couldn't read interfaces file "/etc/network/interfaces"
/etc/network/interfaces:28: too few parameters for iface line
ifup: couldn't read interfaces file "/etc/network/interfaces"


Looks like read is on the file

-rw-r--r-- 1 root root  323 2008-05-23 11:51 interfaces

---

### Post by Iowan on 2008-05-23
Can you post **/etc/network/interfaces**? Apparently something's amiss inside.

---

### Post by kbow on 2008-05-23
Ok -

auto lo
iface lo inet loopback

auto eth0
iface eth0 inet dhcp

auto wlan0
iface wlan0 inet dhcp






I use nano to edit - FYI

---

### Post by Iowan on 2008-05-24
Hmmm... looks kosher. Here's mine:```
auto lo
iface lo inet loopback

auto eth0
#iface eth0 inet dhcp

auto eth1
#iface eth1 inet dhcp

auto eth2
#iface eth2 inet dhcp

auto ath0
#iface ath0 inet dhcp

auto wlan0
#iface wlan0 inet dhcp


iface eth0 inet dhcp
~
~
~

```

---

### Post by chili555 on 2008-05-24
kbow-
Are you sure that's the whole entire file?. Also, may I please see:```
ls -l /etc/network | grep interfaces
```Let's make sure we don't accidently have 2 or 3 files.

---

### Post by Iowan on 2008-05-24
> **kbow said:**
> /etc/network/interfaces[COLOR="Red"]:28:[/COLOR] too few parameters for iface lineProblem on line 28??

---

