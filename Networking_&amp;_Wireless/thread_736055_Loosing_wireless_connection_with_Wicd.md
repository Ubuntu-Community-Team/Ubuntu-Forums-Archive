---
title: "Loosing wireless connection with Wicd"
date: 2008-03-26
forum: Networking &amp; Wireless
---

### Post by Wikzo on 2008-03-26
Hello,

I am using a Zepto Znote 3215W laptop with a Intel Pro/Wireless 4965AGN 300Mbit wireless card on Ubuntu 7.10. I use the Wicd program to connect to my shcool's wireless network with WEP 64/128 bit HEX.

The driver in Wicd is "Wext" or something like that. I works fine sometimes, but other times I loose the connection and can't get it to work again. The program just turns black and tells me there is no signal (I know there is, a friend of mine is using Windows and doesn't loose the connection). I tried to restart the program several times, but the only solution is to turn off my machine and boot it up again.

Why do I loose the connection? It only happens at my school with encryption (at home I have no encryption, and I don't loose the connection). Is there any way to "restart" my wifi card?

---

### Post by pseudo-random on 2008-03-26
from a terminal you can turn your interfaces on and off:
```
ifconfig eth0 up
ifconfig eth0 down
```
replacing eth0 with whatever your adaptor is called (use ifconfig to find out)
You then have iwconfig for manipulating your wireless adaptor:
> iwconfig eth0 mode managed (standard)
iwconfig eth0 mode monitor (for monitoring ;) )
Sure your problem isn't hardware? If your friends wireless card is more sensitive then you will lose the signal before he does. Just a thought.

---

### Post by Wikzo on 2008-03-26
Dunno about the hardware. It works great at my home connection, as I wrote. I bought that Intel card, because I read it would run great on Ubuntu/Linux.

I'll try those commandos tomorrow :)

---

