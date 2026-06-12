---
title: "Wireless channel always needs changing"
date: 2008-03-29
forum: Networking &amp; Wireless
---

### Post by Jesuses Left Leg on 2008-03-29
I searched and couldn't find a solution to this. It is not ubuntu specific but there is good knowledge on these forums so here goes.
I have a wireless problem whereby my wireless will be fine and then when I boot the next day (into windows xp or ubuntu) it will see the network but not be bale to connect, it tries but never actually connects.
Going into router settings and changing the channel of the router fixes this, but only until it decides it doesn't like that channel any more, then I have to change it again. This is getting a bit annoying so maybe someone could shed some light on my problem.

```

matt@matt-laptop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wifi0     no wireless extensions.

ath0      IEEE 802.11g  ESSID:"Livebox-DE60"  Nickname:""
          Mode:Managed  Frequency:2.462 GHz  Access Point: 00:16:CF:01:04:D7   
          Bit Rate:54 Mb/s   Tx-Power:16 dBm   Sensitivity=1/1  
          Retry:off   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=48/70  Signal level=-48 dBm  Noise level=-96 dBm
          Rx invalid nwid:531  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

```

The card is an Atheros AR5007EG on an Acer Aspire 5315.

---

### Post by dstew on 2008-03-29
Does it reconnect after you turn off the router and turn it back on, without changing the router's channel setting?

---

### Post by Jesuses Left Leg on 2008-03-29
No it doesn't. That was the first thing I tried when it first had this problem as it's what I usually do to solve things.

---

### Post by dstew on 2008-03-29
I notice that in your iwconfig output that there were a number of packets received with an invalid network ID. But, since you use the 802.11g protocol, your network ID depends on the ESSID and the access point address. I don't know if the invalid packets are due to interference of some kind, or if the driver is running this (probably unecessary) check. You can turn network ID checking off with```
sudo iwconfig ath0 nwid off
```See the iwconfig man page for info about nwid settings. But, that is just a guess...

---

### Post by Jesuses Left Leg on 2008-03-30
```

matt@matt-laptop:~$ sudo iwconfig ath0 nwid off
[sudo] password for matt:
Error for wireless request "Set NWID" (8B02) :
    SET failed on device ath0 ; Operation not supported.

```

Thanks for helping but it seems like the card doesn't support it. Any other suggestions?

---

