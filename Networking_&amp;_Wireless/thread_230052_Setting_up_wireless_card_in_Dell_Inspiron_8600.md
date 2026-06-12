---
title: "Setting up wireless card in Dell Inspiron 8600"
date: 2006-08-05
forum: Networking &amp; Wireless
---

### Post by WebDrake on 2006-08-05
I've been unable to get my wireless card working with Ubuntu.  Here's the output of iwconfig:

```

lo        no wireless extensions.

eth0      no wireless extensions.

eth1      IEEE 802.11b/g  ESSID:off/any  Nickname:"Broadcom 4306"
          Mode:Managed  Frequency=2.437 GHz  Access Point: Invalid
          Bit Rate=11 Mb/s   Tx-Power=15 dBm
          RTS thr:off   Fragment thr:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

sit0      no wireless extensions.

```

eth1 appears to be set up as the wireless interface, but it won't work if I try activating it via Network Manager.

Incidentally the driver cited is not the correct one: it should be a Broadcom BCM4309 802.11a/b/g.  I've tried installing it with ndiswrapper, but do not get any additional devices showing up.

Can anyone advise?  I didn't have these problems, with the same hardware, with SuSE, so why do they show up in Ubuntu?

Many thanks,

    -- Joe

---

### Post by wieman01 on 2006-08-06
There may be an issue indeed if you use NetworkManager. Make sure that this file only disposes of 2 lines, no more. Delete the rest.

1. Open file:
> sudo gedit /etc/network/interfaces

2. Paste this content:
> auto lo
iface lo inet loopback

You may add other devices such as ethernet adapter later on, but try this first.

---

### Post by WebDrake on 2006-08-08
Thanks for the reply.  I should apologise because I think I may have given the wrong impression about part of the problem.  I didn't mean to refer to the package NetworkManager---I was just referring to the Networking admin in Gnome.

I seem to recall reading somewhere that the wireless network card was "turned off" by default and needed to be turned on somehow, and that achieving this was sufficiently different from machine to machine that there was no general way to achieve it...

... and I still don't understand why it's this much trouble in Ubuntu when it wasn't in SuSE.

---

### Post by wieman01 on 2006-08-08
Honestly speaking, wireless support is far from sufficient in Dapper. They have a long way to go stil, NetworkManager is a good start, but it's only cover 80% of the requirements.

I got frustrated with wireless networking in Dapper as well and finally decided to configure it manually. This works (although it took me quite a while to figure out what the correct settings are) but it's a real hassle. Windows (and possibly other distributions) does a way better job in that respect.

Anyway... you're problem seem to be solved. Let me know if you need any kind of assistance. (e.g. WPA, WPA2, etc.).

Cheers.

---

