---
title: "Wireless disappeared"
date: 2008-04-29
forum: Networking &amp; Wireless
---

### Post by laststanding on 2008-04-29
Okay so yesterday after spending two hours , finally i got the wireless working after my very first Ubuntu install. I got home today , brought my laptop back up.. it was working fine until i rebooted. 

I dont see wireless network under network connection anymore. 

Please help!... i hope this is not going to be a daily issue..

Dell XPS M1330
Ubuntu 8.04

---

### Post by laststanding on 2008-04-29
By the way my wireless interface file only has entry listed below. I dont know what if this means anything.

"
auto lo
iface lo inet loopback


auth eth0
"

ie: /etc/network/interfaces file.

---

### Post by greyspace2004 on 2008-04-30
try 
System > administration > Keyring manager > 
I had to click allow to get one of my wireless working.

I am brand new also with the same troubles... 
I have spend over two weeks with wireless issues because
I have three wireless cards and I am trying to learn
wireshark, I have never got it to work, but that is my interest.

Later,

Grey

---

### Post by Brain-free on 2008-04-30
The above may work on gutsy and feisty but I'm positive it won't work with hardy.

@laststanding. It would help if you posted the results of
```
 ifconfig 
``` and ```
 lshw -C network 
```

---

