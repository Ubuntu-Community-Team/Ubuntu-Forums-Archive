---
title: "Disable network adapter"
date: 2008-04-26
forum: Networking &amp; Wireless
---

### Post by tompagenet on 2008-04-26
I have two network adapters in my Inspiron 8200 - the awful internal Dell card and a Linksys CardBus card. The second one is good and has a decent range.

After a bit of prodding both work in Ubuntu 8.04, but this is the problem - every time I restart the machine it defaults to connecting via the inbuilt Dell card. How can I disable this card? It appears as wmaster0 with wireless interface wlan0 in Network Tools.

I've looked at the page in Ubuntu support:

[https://help.ubuntu.com/7.10/internet/C/networking-disable.html](https://help.ubuntu.com/7.10/internet/C/networking-disable.html)

But this seems to only disconnect a connection (i.e. doesn't disable the card).

Any help much appreciated!

---

### Post by sisco311 on 2008-04-26
If your bios supports you can disable it from there (read the documentation of your motherboard).

Or you can comment out the appropriate entries from the /etc/network/interfaces file.

---

### Post by tompagenet on 2008-04-26
Ah - I perhaps naively imagined there'd be something more user friendly such as a tick box somewhere...

Given that my home network needs WPA (and, not knowing which adapter was which the first time I installed I gave both adapters by WPA key) is there a way of me removing this knowledge from just wlan0?

Tom

---

### Post by tompagenet on 2008-04-26
While we're on this, and I'm really sorry to know so little about this, when I open up the /etc/network/interfaces file this is all I have:

auto lo
iface lo inet loopback

I have three network devices (the two wireless ones mentioned earlier on in this thread and the one wired connection). I don't know which lines I'd comment out here to disable *one* of the wireless connections.

---

### Post by Iowan on 2008-04-27
Kinda odd - I'd have expected to see all adapters in there.  If Network Manager is handling things, only one adapter should be active.  You might check under **Manual network configuration** icon (Upper right corner near date/clock) to see if more than one is active.

---

### Post by tompagenet on 2008-04-27
Iowan

Thanks for replying - it's not that more than one adapter is active - only one device is connected at any one time. It's that it *always* connects via the internal (bad) card when I start the system up. I then have to switch to the other, external (good) card. I just want to remove the internal card from the equation by disabling it.

Many thanks, Tom

---

