---
title: "Logitech wireless mouse conflicting with RT61 wifi..."
date: 2007-12-10
forum: Networking &amp; Wireless
---

### Post by brodiepearce on 2007-12-10
Hello,

I bought a new mouse today (I destroyed the old one...), noticed a cheap cordless Logitech one branded especially for DSE (Australian store).  Now... it appears that this mouse is 'causing my connection to drop out after 3 to 10 minutes of connectivity.

I'm using an RT61 chipset, running the default serialmonkey driver and Wicd to control it.  Up till now Wicd has been running perfectly during the day, Network-Manager drops out spontaneously with heavy load with RT61 and WPA2 (this is known issue).

The wireless all worked fine for the half hour or so that I tried it with a corded mouse, I also don't get this issue at all in Windows (from which I am now posting).

I have tried all channels from 1 through to 11 in my router config (my router can do up to channel 13, but these last two channels are inaccessible to the wext driver), with no effect.  I have also disabled IPv6 through /etc/modprobe.d/aliases, still to no avail.  Each time I boot up, the following is also in my dmesg output:

```

wlan0: duplicate address detected!

```

However, I have been seeing that in dmesg for the past few months, and the wireless has been running stable with wicd.  

Has anybody else had problems similar to these?

---

### Post by supertux on 2007-12-18
i dont know, but maybe i have the same problem. Just bought a logitech mx revolution, and since a few days also connection problems. It just drops after some time. I have to reboot in order to fix it.

My wifi device is a linksys wmp54g

---

