---
title: "Static IP Does Not Work"
date: 2007-11-24
forum: Networking &amp; Wireless
---

### Post by the_cog on 2007-11-24
I have Ubuntu 7.10 with Gnome 2.20.1

I can't get the static IP to work at all.   I am connected through a hard wired router.  I also have a wireless router with local DHCP enabled for a max. 3 users.  This third router is connected through a second hard wired router back to the first hard wired router (see below).  All three are linksys.

Currently, the way I connect to internet and see other machines is by using roaming mode, which grabs an IP address from the wireless DHCP router.  I want to be able to use a static IP on the first wired router, like a normal human.

There are two other machines on the same router (Mac & PC) that are static and have no problem.

Network Description:
7 machines & 3 routers:

--------------------------------------------

Router 1 Linksys BEFSX41- 192.168.XXX.XX1
Firmware:  Linksys 1.52.15

Mac w/OS X  - Static - 192.168.XXX.XX0
PC w/XP Pro - Static - 192.168.XXX.XX1 ] - these two are same machine
PC w/Ubuntu - Static - 192.168.XXX.XX2 ] - these two are same machine
Brother MFC  - Static - 192.168.XXX.XX5
Router 2

---------------------------------------------------

Router 2 Linksys BEFSR41- 192.168.XXX.XX2
Firmware:  Linksys 1.46.02

Xbox  - Static - 192.168.XXX.XX3
Router 1
Router 3
2 spare ports

-------------------------------------------------

Router 3 Linksys WRT54G/GS- 192.168.XXX.XX3
Firmware:  DD-WRT v23 SP1 Final (05/16/06) std

Dell Laptop - Dynamic
Acer Laptop - Dynamic
Spare Dynamic
3 spare ports
Router 2

------------------------------------------------
Interfaces file:

Code:
------------------------
auto lo
iface lo inet loopback



iface eth0 inet static
address 192.168.XXX.XX2
netmask 255.255.255.0
gateway 192.168.XXX.XX1 (Router 1)

auto eth0
------------------------

resolv.conf checks out OK

Any help would be appreciated.

---

### Post by TheWizzard on 2007-11-24
the localhost's address is missing in /etc/network/interfaces
but i'm not sure this solves your problem. did you try another address for the static ip?

```
auto lo
iface lo inet loopback
address 127.0.0.1
netmask 255.0.0.0


iface eth0 inet static
address 192.168.1.102
netmask 255.255.255.0
gateway 192.168.1.1

auto eth0
```

---

### Post by the_cog on 2007-11-24
I added the loop back info to the interfaces file.  Funny thing is, the connection started working before I changed the file.  This connection hasn't worked for a week, and now all of a sudden it works! 

I have re-booted several times and it seems to still be working.

Thanks for your help.  I will post again if it breaks.

---

### Post by TheWizzard on 2007-11-25
you don't have to reboot. use:
sudo /etc/init.d/networking restart

---

