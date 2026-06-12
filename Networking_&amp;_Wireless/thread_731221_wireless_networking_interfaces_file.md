---
title: "wireless networking interfaces file"
date: 2008-03-21
forum: Networking &amp; Wireless
---

### Post by Teronap on 2008-03-21
Hi,
I was wondering how i could put this in /etc/network/interfaces
```

iwconfig wlan0 essid Dlink
iwconfig wlan0 chan 6
iwconfig wlan0 enc XXXXXXXXXX
iwconfig wlan0 enc restricted

```

I have tried Network Manager, but it does not connect with my wireless card.
Thanks!

---

### Post by jan quark on 2008-03-22
I would suggest installing WiCD
[http://wicd.sourceforge.net/](http://wicd.sourceforge.net/)

it works where nm often fails


to edit the interfaces file manually do this:

run in terminal
```
gksudo gedit /etc/network/interfaces
```
now you can edit the file and save

---

