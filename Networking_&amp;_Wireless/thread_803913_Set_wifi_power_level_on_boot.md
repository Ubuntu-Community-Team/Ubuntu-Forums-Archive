---
title: "Set wifi power_level on boot"
date: 2008-05-22
forum: Networking &amp; Wireless
---

### Post by alderman01 on 2008-05-22
Hi, I am new to Ubuntu.

Does anyone know how I can run
   "iwconfig wlan0 power on"
or
   "echo 5 > /sys/bus/pci/drivers/iwl4965/*/power_level"
when my laptop boots up? I have tried a few things in /etc/init.d, but am not having any luck.

The reason I want this is because the WiFi card on my Thinkpad X61 is under the right palm-rest, and it gets very hot when power_level is set for 6 (the default).

Thanks.

---

### Post by chili555 on 2008-05-22
Did you try in /etc/rc.local? I think that's where such things should go. I might try:```
iwconfig wlan0 txpower 20
```Fiddle with the 20 part a bit to get a cool, yet connecting laptop.

---

### Post by alderman01 on 2008-05-22
I tried adding your line of code in "/etc/rc.local", between the comments and the "exit 0", but when I restart my system and look at the output of iwconfig, I see a larger number for "Tx-Power". It does get set correctly when I run the command from the terminal window, so I know that its syntax is correct.

So I still have the same problem -- I can't get these settings to stick after a restart. Is it possible that they are being reset later in the boot process?

Thanks

---

### Post by alderman01 on 2008-05-23
I also note that when my laptop comes out of suspend mode, that my changes revert back (assuming that I set them by hand after booting).

---

