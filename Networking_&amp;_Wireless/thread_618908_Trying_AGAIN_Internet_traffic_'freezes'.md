---
title: "Trying AGAIN: Internet traffic 'freezes'"
date: 2007-11-20
forum: Networking &amp; Wireless
---

### Post by Angelbeast on 2007-11-20
I have a Broadcom WLan card and have been using it with noproblem with ndiswrapper all durring Feisty...well since upgrading to Gutsy i am having a problem with my internet traffic freezing. And sometimes the whole deskbar will lock up when it happens. I WAS also having a problem with hard crshes system wide. well when i installed Feisty in the beginning i just used the driver from my Windows dis which was actually 32 bit. I changed that a few days ao to the 4 bit driver and that seems to have remedied the hard crashes and i thought too the internet trffic freees but sadly today i had the internet traffic freeze twice today and had to restart to restore it. 

Has anyone else experienced this and found a solution?

---

### Post by Angelbeast on 2007-11-20
and i've tried blacklisting ipv6

---

### Post by Angelbeast on 2007-11-21
*bump*

---

### Post by Angelbeast on 2007-11-23
*bump*

---

### Post by Angelbeast on 2007-11-24
Okay i just had another freeze.This is what was in the system log...is the network manager crashing and locking some of the other tuff on the panel up and the internet traffic? does ANYONE have ANY ideas?

daemon.log

Nov 24 04:37:39 ron-laptop init: tty5 main process (4301) killed by TERM signal
Nov 24 04:37:39 ron-laptop init: tty2 main process (4305) killed by TERM signal
Nov 24 04:37:39 ron-laptop init: tty3 main process (4306) killed by TERM signal
Nov 24 04:37:39 ron-laptop init: tty1 main process (4307) killed by TERM signal
Nov 24 04:37:39 ron-laptop init: tty6 main process (4308) killed by TERM signal
Nov 24 04:37:39 ron-laptop init: tty4 main process (4300) killed by TERM signal
Nov 24 04:37:42 ron-laptop avahi-daemon[5203]: Got SIGTERM, quitting.
Nov 24 04:37:42 ron-laptop avahi-daemon[5203]: Leaving mDNS multicast group on interface eth1.IPv4 with address 192.168.1.105.


kern.log

Nov 24 04:36:50 ron-laptop kernel: [19732.766884] 
Nov 24 04:36:50 ron-laptop kernel: [19732.766885] 
Nov 24 04:36:50 ron-laptop kernel: [19732.766886] Code: 89 30 89 74 24 30 bb 04 00 00 00 40 b5 01 49 8b 85 88 23 00 
Nov 24 04:36:50 ron-laptop kernel: [19732.766893] RIP  [phys_startup_64+5010259/-2147483648]
Nov 24 04:36:50 ron-laptop kernel: [19732.766897]  RSP <ffff81003ddafb48>
Nov 24 04:36:50 ron-laptop kernel: [19732.766899] CR2: 0000000000000018
Nov 24 04:36:50 ron-laptop kernel: [19732.766902] note: NetworkManager[4824] exited with preempt_count 1


syslog

Nov 24 04:36:50 ron-laptop kernel: [19732.766902] note: NetworkManager[4824] exited with preempt_count 1
Nov 24 04:37:39 ron-laptop init: tty5 main process (4301) killed by TERM signal
Nov 24 04:37:39 ron-laptop init: tty2 main process (4305) killed by TERM signal
Nov 24 04:37:39 ron-laptop init: tty3 main process (4306) killed by TERM signal
Nov 24 04:37:39 ron-laptop init: tty1 main process (4307) killed by TERM signal
Nov 24 04:37:39 ron-laptop init: tty6 main process (4308) killed by TERM signal
Nov 24 04:37:39 ron-laptop init: tty4 main process (4300) killed by TERM signal
Nov 24 04:37:42 ron-laptop avahi-daemon[5203]: Got SIGTERM, quitting.
Nov 24 04:37:42 ron-laptop avahi-daemon[5203]: Leaving mDNS multicast group on interface eth1.IPv4 with address 192.168.1.105.


messages

Nov 24 04:36:50 ron-laptop kernel: [19732.766851]  [vfs_ioctl+116/720] vfs_ioctl+0x74/0x2d0
Nov 24 04:36:50 ron-laptop kernel: [19732.766856]  [fd_install+37/96] fd_install+0x25/0x60
Nov 24 04:36:50 ron-laptop kernel: [19732.766863]  [sys_ioctl+149/176] sys_ioctl+0x95/0xb0
Nov 24 04:36:50 ron-laptop kernel: [19732.766871]  [system_call+126/131] system_call+0x7e/0x83
Nov 24 04:36:50 ron-laptop kernel: [19732.766884] 
Nov 24 04:36:50 ron-laptop kernel: [19732.766885] 
Nov 24 04:36:50 ron-laptop kernel: [19732.766886] Code: 89 30 89 74 24 30 bb 04 00 00 00 40 b5 01 49 8b 85 88 23 00 
Nov 24 04:36:50 ron-laptop kernel: [19732.766897]  RSP <ffff81003ddafb48>
Nov 24 04:36:50 ron-laptop kernel: [19732.766902] note: NetworkManager[4824] exited with preempt_count 1
Nov 24 04:39:28 ron-laptop kernel: [19818.240894] Inbound IN=eth1 OUT= MAC=00:14:a5:1d:94:ad:00:1c:10:9d:76:2e:08:00 SRC=205.188.13.60 DST=192.168.1.105 LEN=40 TOS=0x00 PREC=0x00 TTL=105 ID=857 DF PROTO=TCP SPT=5190 DPT=49095 WINDOW=16384 RES=0x00 ACK URGP=0

---

### Post by Angelbeast on 2007-11-25
*bump*
*bump*
*bump*
*bump*
*bump*
*bump*

---

### Post by mgmiller on 2007-11-25
Just a guess, but if you have your wireless card set to a static IP, try changing it to dhcp mode or try enabling roaming.

---

### Post by Angelbeast on 2007-11-25
> **mgmiller said:**
> Just a guess, but if you have your wireless card set to a static IP, try changing it to dhcp mode or try enabling roaming.

dhcp mode is indeed enabled. it's just like it was set in feisty where it worked perfectly

---

### Post by Angelbeast on 2007-11-26
*bump*
*bump*

---

### Post by Angelbeast on 2007-12-11
*BUMP*

*LOL* so no one else in the world is having this problem?

---

### Post by mgmiller on 2007-12-11
Although you have blacklisted ipv6, did you disable it in Firefox?

In the Firefox address bar, type about:config and then in the filter area near the top, put in ipv6.

You should get the following line:
```
network.dns.disableIPv6    userset   boolean   false
```


just double click on the false to change it to true.

exit and restart firefox.


See if that helps.

---

### Post by Angelbeast on 2007-12-11
> **mgmiller said:**
> Although you have blacklisted ipv6, did you disable it in Firefox?

In the Firefox address bar, type about:config and then in the filter area near the top, put in ipv6.

You should get the following line:
```
network.dns.disableIPv6    userset   boolean   false
```


just double click on the false to change it to true.

exit and restart firefox.


See if that helps.

thanks for replying...yeah all of that is disabled...i just don't get why it worked fine in feisty and not in gutsy...

---

### Post by jingo811 on 2007-12-11
Sounds like you should file a bug report if you want it to work in the future versions or patches.
[https://launchpad.net/ubuntu](https://launchpad.net/ubuntu)
This happens very often every time Ubuntu does a distro or kernel upgrade.

I'd say switch back to Feisty you don't need Gutsy to enable Compiz Fusion with the cool 3D cube and all.  You just need to do a little more work to enable it.




> **Angelbeast said:**
> I have a Broadcom WLan card and have been using it with noproblem with ndiswrapper all durring Feisty...well since upgrading to Gutsy i am having a problem with my internet traffic freezing. And sometimes the whole deskbar will lock up when it happens. I WAS also having a problem with hard crshes system wide. well when i installed Feisty in the beginning i just used the driver from my Windows dis which was actually 32 bit. I changed that a few days ao to the 4 bit driver and that seems to have remedied the hard crashes and i thought too the internet trffic freees but sadly today i had the internet traffic freeze twice today and had to restart to restore it. 

Has anyone else experienced this and found a solution?

Or it could be that you're lacking kernel headers.  I had to install that on Debian Etch don't remember if I had to do it on Ubuntu Feisty.  It was way too long ago to remember how I played with NDISwrapper I no longer remember all the steps.  
I think you should describe exactly how you installed and setup your system for NDISwrapper on Feisty.  And how you did it on Gutsy.  The process will surely reveal the solution for someone.

---

