---
title: "Upgraded, now wifi doesn't work???"
date: 2007-10-20
forum: Networking &amp; Wireless
---

### Post by electronikjunkie on 2007-10-20
Hi,

I'm running edgy with a Robtics MaxG wifi card in an Inspiron 8100. Using ndiswrapper and wpasupplicant to my router. Everything was working before I upgraded (it's been working for about a year).  When I upgraded wpasupplicant it asked me if I wanted to replace the existing wpa_supplicant.conf file and I said no. Now my wifi card inital powers on for a second or two when I put it in and then turns back off. dmesg says this:
```
ADDRCONF(NETDEV_UP): wlan0: link is not ready
```

I made a copy of my wpa_supplicant.conf and reinstalled wpasupplicant and the put the copy back as /etc/wpa_supplicant.conf, but still no luck. Anyone got some ideas?

Thanks,

TK

---

### Post by electronikjunkie on 2007-10-20
some more info. when i run:

sudo wpa_supplicant -iwlan0 -c/etc/wpa_supplicant.conf -Dusrmaxg -w
```

Unsupported driver 'usrmaxg'.

Segmentation fault (core dumped)
```

dmesg | grep ndis```

ndiswrapper version 1.28 loaded (preemt=no,smp=yes)
usbcore: registered new driver ndiswrapper
ndiswrapper: driver usrmaxg (U.S. Robotics Corporation,02/09/2005, 3.100.46.5) loaded
ndiswrapper: using IRQ 10
```

this is weird cause my card worked perfectly before...

---

### Post by electronikjunkie on 2007-10-21
bump cause i still need help.

---

