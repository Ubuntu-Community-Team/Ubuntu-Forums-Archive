---
title: "Ethernet problems (Dell Vostro 2000)"
date: 2008-05-14
forum: Networking &amp; Wireless
---

### Post by scottevan on 2008-05-14
I just installed Kubuntu 8.04 (KDE4) on a new Dell Vostro 2000. Things work great, but I can't get online because my ethernet card doesn't appear to be functioning. KNetworkManager says "Device: No active device". Can anyone give me any suggestions?

lspci -nn shows:
```
00:19.0 Ethernet controller [0200]: Intel Corporation 82562V-2 10/100 Network Connection [8086:10c0] (rev 02)
```

According to [http://hardware4linux.info/component/34798/](http://hardware4linux.info/component/34798/), this card had problems prior to kernel 2.6.23, but my kernel is 2.6.24-16-generic.

Any ideas appreciated! Thanks.

---

### Post by nixscripter on 2008-05-14
Does the card have an interface according to **ifconfig -a**? I don't know much about KDE, so make sure it's not just a problem there.

---

### Post by scottevan on 2008-05-14
> **nixscripter said:**
> Does the card have an interface according to **ifconfig -a**? I don't know much about KDE, so make sure it's not just a problem there.
Yeah, I haven't used KDE before either, and it is a little confusing to me. "ifconfig -a" shows eth0. I'm not sure if that is my card.

---

### Post by nixscripter on 2008-05-14
Let's assume for the moment that eth0 is the card.

If you know an IP that would be safe to try, see what happens if you set up the card manually: ```
sudo ifconfig eth0 **safe-ip-addr** up
``` Then try to ping something on the local network, like the IP of a router.

---

### Post by scottevan on 2008-05-14
> **nixscripter said:**
> Let's assume for the moment that eth0 is the card.

If you know an IP that would be safe to try, see what happens if you set up the card manually: ```
sudo ifconfig eth0 **safe-ip-addr** up
``` Then try to ping something on the local network, like the IP of a router.
Thanks for the guidance!

I chose a safe ip address, ifconfiged as you suggested and then pinged the router but the host was unreachable.

PS - I'm downloading Ubuntu 8.04 to see if this is a Kubuntu issue.

---

### Post by scottevan on 2008-05-14
Yep. Same problem with the Ubuntu 8.04 Live CD. Any ideas? This is a brand new machine, all I've done is adjust the bios (changed hard-drive to RAID to resolve an unrelated issue).

Thanks!

---

### Post by nixscripter on 2008-05-15
Two things come to mind.

First, perhaps it's something in the network topography. Try a hard route to the router as well: ```
sudo route add default gw **router-ip**
``` If it doesn't work, then you can undo it with: ```
sudo route del default gw **rotuer-ip**
```

Also, assuming it won't annoy somebody, try a broadcast ping: ```
 sudo ping -c 1 255.255.255.255
``` That will ask _everyone_ to respond who will listen. Theoretically, the router will answer first, and that will give its IP. This is just in case you mis-guessed the IP.

Second, just to make sure it is the card, is eth0 the only device in that list produced by **ifconfig -a**, or are there others? There will always be **lo**, the loopback interface, but ignore that one.

---

### Post by scottevan on 2008-05-15
> **nixscripter said:**
> 
First, perhaps it's something in the network topography.

Great news! You comment about topography motivated my to rearranged my network. The machine has been on the same line as my Cisco VOIP phone. As soon as I moved it to its own ethernet line, it started working. At some point, I'll try a 7.10 Live CD to see if the quirk originates with 8.04 or the Vostro hardware.

Thanks for the asssistance!

---

