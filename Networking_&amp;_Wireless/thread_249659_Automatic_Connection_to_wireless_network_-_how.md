---
title: "Automatic Connection to wireless network - how?"
date: 2006-09-02
forum: Networking &amp; Wireless
---

### Post by Timokl on 2006-09-02
Hi everybody,

I own an Acer Aspire 5021NWLCI notebook on which I run Ubuntu Dapper 32-Bit (in spite of the AMD 64 cpu). I managed to get my wireless card working using this excellent manual in the ubuntu wiki: [https://help.ubuntu.com/.../Acer5021WLMi_Amd64]("https://help.ubuntu.com/community/WifiDocs/Acer5021WLMi_Amd64").

However, one small glitch remains - I would like Ubuntu to connect automatically to my router. Right now, I have to start the networking application, manually deactivate eth0, and then manually first deactive wlan0 and second reactivate it.

It's not really a big deal, but it would be nice to set up Ubuntu to activate the wlan port automatically on start-up. :-D 

I searched this forum already. Anyone with an idea how to achieve this?

Thank you!!!

Bye,
Timo

---

### Post by baldy1324 on 2006-09-02
for my powerbook g4 i arranged all the settings (disabled wired, enables wireless, dhcp) and saved to a profile by clicking profile new and enter settings. on the next reboot it should auto-connect:D

---

### Post by stupidkid on 2006-09-02
Edit the /etc/networking/interfaces file. I'm not exactly sure how, since I'm not in ubuntu right now.

---

### Post by Timokl on 2006-09-03
My /etc/network/interfaces looks like this:

```
# The loopback network interface
auto lo
iface lo inet loopback

iface wlan0 inet dhcp
wireless-essid RT2561_5



iface eth0 inet dhcp





auto wlan0

```

Not very much documented. :rolleyes:  OK, but I can google for it. Thanks for pointing me there!

---

