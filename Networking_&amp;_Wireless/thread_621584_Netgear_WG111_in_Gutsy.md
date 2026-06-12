---
title: "Netgear WG111 in Gutsy"
date: 2007-11-23
forum: Networking &amp; Wireless
---

### Post by JohanSwe on 2007-11-23
Wanted to share my experience with the WiFi cards Netgear wg111v2 and wg111v3

wg111v2
Works out of the box. Slow when browsing the Internet but still usable. Sometimes stops working, especially on heavy load (eg downloading) and need restart to work again.

wg111v3
not detected

tested on Dell desktop computer. both adapters work fine in windows.

---

### Post by JohanSwe on 2007-11-24
After a longer period of time testing wg111v2 in windows on this computer I also encountered problems with speed both for web surfing and downloading using torrents (not when downloading from server).

The problems I have could be related to the wifi adapter or just 256mb ram on computer.. don't know..

Anyone else using netgear wg111v2 in Ubuntu?

---

### Post by Roasted on 2007-11-25
What is the Netgear WG111US? I found circuit city has one and the ubuntu wiki says that the WG111 is fully supported, but the circuit city has the WG111US... I wonder if the US makes a difference????

---

### Post by chronographer on 2007-11-26
I find that if firefox is slow with websurfing, you can turn ipv6 off. It is a new protocol which I understand isn't used much and Ubuntu tries to use it first, slowing browsing down.

So:
[LIST=1]
[*]Open a new tab in firefox and type "about:config" without the quotes
[*]In the box at the top search for "ipv6"
[*]Double click the "false" value in the 'disable ipv6' setting, changing it to "true"
[/LIST]

This disables ipv6, and speeds up my internet browsing HEAPS! if you like you can blacklist the ipv6 modules, but i leave that as an exercise for the reader!

---

### Post by JohanSwe on 2007-11-30
Thanks chronographer, I turned ipv6 but couldn't notice a difference.. it was worth a try though ;)

---

### Post by ethan1701 on 2007-12-16
I've been having the same problem, both in 7.04 and 7.10. when turning on the computer, NetworkManager finds my network and connects with a strong signal. However, after a while, the connection is lost and has to be restarted.

Is there a known fix for Gutsy?


-Ethan

---

### Post by kilovh on 2008-01-30
Did you guys ever find a fix for the random disconnects?

---

