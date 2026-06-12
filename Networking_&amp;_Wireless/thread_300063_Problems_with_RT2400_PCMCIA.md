---
title: "Problems with RT2400 PCMCIA"
date: 2006-11-15
forum: Networking &amp; Wireless
---

### Post by hairypete on 2006-11-15
Hi, I've been getting Ubuntu going on my old Toshiba Tecra 8100 laptop over tyhe past few weeks.  I used to have XP home SP2 on there, and I could scan for wireless networks through my Ralink RT2400 PCMCIA with no trouble.  I finally managed to set up access to my WPA router with wpasupplicant at the weekend on a clean install of Edgy, but since then I haven't been able to connect at all.  I've tried a few different methods to reconnect:

```
sudo dhclient ra0 
```
won't connect at all

Network Manager won't recognize my card and just says
> No Network Devices Found when I click on it

I can't work out how to enter a wpa key on iwconfig (any help would be great as this seems to be the best option for me!)

Finally, when I enter the following into the terminal

```
sudo iwlist ra0 scanning
```

I just get told that the interface doesn't support scanning, which would explain why I've had no joy with wifiradar either.

So my question is really, is it possible to set up wpa through iwconfig, and if not, does anyone know of a nice cheap pcmcia wireless card which does support scanning and would allow me to use network manager?

I hope someone can help me out here, as I've grown very fond of ubuntu (although my wife feels slightly differently after the amount of time I've spent trying to sort it out!) and I'd be rather loathed to have to go back to XP on the laptop.

By the way, just incase anyone was wondering, network manager works fine with a pcmcia wired lan card.

---

### Post by hairypete on 2006-11-16
bump

---

### Post by findus on 2006-11-16
I know your wifi card is supposed to work under Ubuntu anyway, but have you tried getting the Windows driver off the CD/ downloading it and using ndiswrapper?

---

### Post by hairypete on 2006-11-16
> **findus said:**
> I know your wifi card is supposed to work under Ubuntu anyway, but have you tried getting the Windows driver off the CD/ downloading it and using ndiswrapper?

I certainly have - no joy with that either, so for the moment I've somehow managed to hack into next door's unencrypted connection, but I've ordered a card for which I found a nice simple review and how-to in the wiki, which should enable me to set up through network manager.

---

