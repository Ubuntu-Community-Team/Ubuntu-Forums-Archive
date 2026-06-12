---
title: "wireless connection problem"
date: 2006-12-28
forum: Networking &amp; Wireless
---

### Post by illusion on 2006-12-28
Hey,

I am trying to get a wireless connection from ubuntu 6.  It is a dual boot system, wireless,wired works from windows, and wired connection works in ubuntu.  The wireless parameters in ubuntu are as follows:

the etc/network/interfaces file is as follows

iface eth1 inet dhcp
wireless-essid default
wireless-channel 6
wireless-mode managed

iwconfig is as follows

ethi IEEE 802.11b/g ESSID="" Nickname=Broadcom 4311"
mode:Managed Frequency=2.437 Ghz Access Point: Invalid
RTS thr:off Fragment thr:off
Link Quality:0 Signal level:0 Noise level:0
Rx invalid nwid:0 Rx invalid crypt:0 Rx invalid frag:0
Tx excessive retries:0 invalid misc:0 Missed beacon:0

Also added the address of router for dns server in gui admin/networking/dns servers 192.168.0.1

Nothing can be pinged, router etc, network unreachable message

Any assistance would be greatly appreciated,
Illusion

---

### Post by discord on 2007-01-25
look here got it working and with network manager!

[https://launchpad.net/ubuntu/+source/ndiswrapper/+bug/59983](https://launchpad.net/ubuntu/+source/ndiswrapper/+bug/59983)

---

