---
title: "Network doesn't work correctly"
date: 2016-11-05
forum: Networking &amp; Wireless
---

### Post by Uinthe on 2016-11-05
Hi everybody.
Xubuntu 16.04.1 
Every 2nd reboot/turn on my local network just doesn't work. I mean i see an applet, the option "enable networking" turned on, but no connection at all. Using ifconfig i can see only lo. No enp7s0 (it's my eth0). So i tryed to restart network manager and turn on enp7s0 using these commands:
```
service network-manager restart 
```
```
ifconfig enp7s0 down
```
```
ifconfig enp7s0 up
```
but it takes no effect. Then like a expd user :D i looked all the useful logs after login with the problem. Greping with tags like enp7s0, error, fail etc. unfortunately showed nothing to me. So i exported the last dmesg log to help with solving this issue.
Actually here is a log of ifconfig * up:
```
enp7s0: ERROR while getting interface flags: No such device

```
Thanks in advance.

---

