---
title: "Drivers for Qualcomm Atheros ar9285"
date: 2016-12-31
forum: Networking &amp; Wireless
---

### Post by t4ggs on 2016-12-31
Hi,

I got this wireless PCI card with works extremely slow. The PC it's like 3 meters away from the router but still the signal is just around 50%!!

I tried google but all the posts I found are about the drivers not working, well in my case they work but extremely slow, any idea?

This is a not so new card, so it's weird it doesn't work out of the box in ubuntu.

Any idea?

Thanks

P.S. using 16.10 64 but

---

### Post by jeremy31 on 2016-12-31
Drivers for that card are part of the kernel.  Did you connect any external antennas?

You may also have issues with the wifi router encryption as Atheros cards seem to be pickier than most and prefer WPA2 only with no WEP or TKIP

---

### Post by praseodym on 2017-01-01
Lets try

```
echo "options ath9k nohwcrypt=1" | sudo tee /etc/modprobe.d/ath9k.conf
sudo modprobe -rfv ath9k
sudo modprobe -v ath9k
```

---

### Post by t4ggs on 2017-01-06
> **jeremy31 said:**
> Drivers for that card are part of the kernel.  Did you connect any external antennas?

You may also have issues with the wifi router encryption as Atheros cards seem to be pickier than most and prefer WPA2 only with no WEP or TKIP

These are the options I have and the one I'm currently using is the one with the check mark. I think it's good, isn't it?

[ATTACH=CONFIG]273074[/ATTACH]

---

### Post by t4ggs on 2017-01-06
> **praseodym said:**
> Lets try

```
echo "options ath9k nohwcrypt=1" | sudo tee /etc/modprobe.d/ath9k.conf
sudo modprobe -rfv ath9k
sudo modprobe -v ath9k
```


Did it, ir disconnected and then reconnected automatically but signal remains very low even though the computer is like 2 meters away from the router with no physical interference (all other wifi devices work well).

This is a desktop computer and the atheros card has an antenna.

---

### Post by jeremy31 on 2017-01-06
I would double check to see if the antenna connections at the back are actually connected to the board itself as some manufacturers use an adapter so they can use a PCI(e) card in a PCI slot

---

### Post by t4ggs on 2017-01-21
> **jeremy31 said:**
> I would double check to see if the antenna connections at the back are actually connected to the board itself as some manufacturers use an adapter so they can use a PCI(e) card in a PCI slot

YES, the antenna is connected to the board and it's a PCI card and slot (no adapters whatsoever).

There are multiple threads on the internet of this card working with Windows but having issues with Ubuntu.

Seems like I'll have to switch to Windows :(

Thanks

---

