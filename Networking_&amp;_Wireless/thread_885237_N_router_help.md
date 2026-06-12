---
title: "N router help"
date: 2008-08-09
forum: Networking &amp; Wireless
---

### Post by johniv on 2008-08-09
Hello ! I have a DWA-552 wireless card (that's antheros (sp?)) and i had it working in ubuntu until i bought an N-router. Now that my router is running in N mode instead of downgrading to b/g it wont work in ubuntu (but it works in vista).

Any help is appreciated!

---

### Post by SMGauna on 2008-08-10
Have you tried manually specifying the rate for the ath device?

iwconfig <dev> rate 48M

---

### Post by caljohnsmith on 2008-08-10
In the configuration settings of almost all modern routers there is a place where you can specify whether you want your network to be B, G, "mixed", or in your case will include an option for N. I would set your router for "mixed", and if that doesn't work, you could then specify "G".

---

### Post by johniv on 2008-08-10
Hey! I'm currently sifting through my router configurations for that option... first look couldn't find it but i wasn't that thorough.

A little more background info:
I had my connection working before on an N card, same one. The router i was using was a pre-n router, but i switched that for an N router from NETGEAR. Now, ubuntu finds the connection and connects to it (with two bars) but any actual connection is not there. (open firefox to google.com and it INSTANTLY says the server is not responding)

my theory is that before i was running a network in b/g mode and by switching to an N router in mixed mode i switched to an N connection and thereby i threw ubuntu off. That's just my theory, though. Maybe i need to re-do ndiswrapper?

if anyone has any advice (including how to change the network type in the NETGEAR router config (i think that they're all standardized) i would really appreciate it.

Thank you!
John

(PS: Also having trouble using the login on the forums in safari and Firefox. I enter my details.. it logs in.. then the next page acts like it never happened. Cookie problem?)

---

### Post by caljohnsmith on 2008-08-10
Johniv, from your description it does sound like it could be problem of Ubuntu now trying to use your wireless card in N mode, instead of the G mode it was forced to use when you had your old router. If you go to the [netgear website]("http://www.netgear.com/"), just search for your router model number, and I'm sure there is a manual for it available online.

Also, I would try SMGauna's suggestion and try forcing your wireless card to use 54 Mbits/s or slower, which is the 802.11G specification:
```
sudo iwconfig <interface> rate 54M auto

```
That might work, it won't hurt to try.

---

### Post by johniv on 2008-08-11
Hello!

Thanks, i was a little hesitant to try that one because i don't know how to undo it. I did it anyway, though, and i got back an error saying "no file or folder" or something like that. Check this out though.

IEEE 802.11g ESSID: XXX
Mode: Managed Frequency: 2.462 GHz
Bit Rate=54 Mb/2
Power management: off
Link quality: 50/100 Signal level: -64 dBm Noise level: -96 dBm 

and then some stuff after that.

I appreciate your replies. I'm going to redo ndiswrapper in the mean time :]

John

---

