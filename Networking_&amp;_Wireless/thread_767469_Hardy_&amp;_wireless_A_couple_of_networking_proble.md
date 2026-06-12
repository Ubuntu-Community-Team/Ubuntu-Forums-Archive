---
title: "Hardy &amp; wireless: A couple of networking problems"
date: 2008-04-25
forum: Networking &amp; Wireless
---

### Post by odiseo77 on 2008-04-25
Hi people. I installed Hardy Heron yesterday and I'm having a couple of specific networking issues (not sure if they're related).

1st: apt-get works very very slow. I'm on a 1mb/s connection that usually works at about 120 kb/s, but when I use apt-get, the velocity goes from some bytes per second and reaches a maximum of 30 kb/s (for shorts periods of time). I thought it could be the repositories overloaded with people upgrading to hardy and downloading packages in their new installs, but a friend from Argentina told me the repos are working fast for him. I edited my sources.list and changed "ve.archive.ubuntu.com" to "ar.archive.ubuntu.com" and simply to "archive.ubuntu.com", but apt-get continued working slowly, so I'm thinking it might be something wrong with wireless connection. 

2nd: I use mercury to connect to the MSN IM protocol, but it simply cannot connect. When I attempt to connect, it says the msn server could not be found (seems like a DNS problem or something, but all other applications seem to work fine, except for apt-get, as I told before). Pidgin and Emesene connect fine, but I just prefer to use Mercury, since it's the one I'm used to.

Some possibly relevant information: I'm using a wireless card with the rt2500 chipset and Hardy's default driver (which I think it's the rt2x00 driver), and connected to my router with nm-applet, so I right clicked on the nm icon and then on "Connection information", and checked the velocity and it's only 1 mb/s (I think it's supposed to be higher).

Thanks in advance for your help.

---

### Post by odiseo77 on 2008-04-26
Solved! (So far) I blacklisted the rt2500pci module and installed the rt2500 cvs driver from the serialmonket site and now everything is working fine.

---

### Post by mschering on 2008-04-26
I have the same problem here. Will the driver be updated in ubuntu 8.04? Everything was working fine in 7.10.

---

### Post by BuFu on 2008-04-26
I was having same problems (slow connection, 50% signal strength) and the rt2500 driver didn't helpt. In [https://bugs.launchpad.net/ubuntu/+source/linux-ubuntu-modules-2.6.24/+bug/190515](https://bugs.launchpad.net/ubuntu/+source/linux-ubuntu-modules-2.6.24/+bug/190515) i found the answer. I set my rate to 54M (sudo iwconfig wlan0 rate 54M) and all the problems are gone ;)

---

### Post by odiseo77 on 2008-04-26
> **BuFu said:**
> I was having same problems (slow connection, 50% signal strength) and the rt2500 driver didn't helpt. In [https://bugs.launchpad.net/ubuntu/+source/linux-ubuntu-modules-2.6.24/+bug/190515](https://bugs.launchpad.net/ubuntu/+source/linux-ubuntu-modules-2.6.24/+bug/190515) i found the answer. I set my rate to 54M (sudo iwconfig wlan0 rate 54M) and all the problems are gone ;)

I installed the "legacy" driver (rt2500) but it alone didn't help. Then I executed ***sudo iwconfig ra0 rate 54M auto*** and now it's working fine (with the legacy driver). If I just had known before I could solve it with this simple command without blacklisting modules and installing new drivers :-|

---

