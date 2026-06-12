---
title: "Frustrating Network (samba?) Problem"
date: 2008-05-18
forum: Networking &amp; Wireless
---

### Post by azrael-uk on 2008-05-18
Hi all,

I am hoping someone can help me with my networking problem. I don't even fully know how to diagnose the issue, so if I can get help with that too, I would be very grateful.

Brief explanation:

I was using 7.10 and then upgraded to 8.04. A short time after this (and possibly unrelated) the network shares on my Ubuntu box (shared via samba) started to become flaky when accessed from (anything, but specifically) my MacPro (running OS X 10.5).

I found that at times I just could not connect to a samba share, and yet have no problem connecting to the Ubuntu machine via ssh.

After a few frustrating days of this, I found myself completely unable to access my Ubuntu box via samba or ssh, and when physically logging into my Ubuntu box, I found it was unable to access the router.

Thinking it might be a faulty network card (eth0), I purchased a new one (eth1 - r8169). This did not help. I did a clean install of 8.04, this did not help. I did a clean install of 7.10, and this slightly helped.

I am currently on 7.10 using eth0 and I find the network connection unstable. Right now I am able to access (via samba) my home share, but not 2 other shares that I have previously not had issues with. I am semi-resolving this by just mounting those other 2 (partitions) as folders in my home folder. This at least lets me access the contents from my Mac, but not with any great reliability, the connection still drops far too often for comfort. NB: MacPro is sitting on my network wirelessly, so some blippage is to be expected, it is the blippage in samba connections with no corresponding internet blippage that worries me.

So, I need help. I need help diagnosing the precise problem, and then resolving it.

Many thanks to anyone prepared to wade into these murky waters with me.

---

### Post by azrael-uk on 2008-05-20
Just wondering if it is possible that the samba share drops after several 100 MB of data gets transferred, and if so, if that's a problem anyone has come across before.

---

### Post by mothbitten on 2008-05-20
I am wondering if it might be a problem with your router/switch, since you have replaced the network card. Maybe a bad port on the switch? Do other devices on the network talk to one another happily?

---

### Post by SpaceTeddy on 2008-05-20
what does 
```
dmesg
```
say to your connection aborts ? are there any failures reported for the driver of your network card ? 

i'd also try to run tcpdump/wireshark on the ubuntu machine and then try to crash the connection - see if anything even reaches the ip layer after the connection has broken or if the pakets get lost somewhere before that.

I am just pushing ideas here - i have never heard let alone fixed a problem like that before...

hope it helps :)

---

### Post by azrael-uk on 2008-05-21
> **mothbitten said:**
> I am wondering if it might be a problem with your router/switch, since you have replaced the network card. Maybe a bad port on the switch? Do other devices on the network talk to one another happily?

I suspected this might be the case at one point, because a mac Mini was plugged into the router and working fine, and the router light for the Ubuntu server was flickering. I swapped them around, and the mini carried on working happily, and Ubuntu carried on not-working happily. I tried other ports as well.

I am content there is no router port failure. If it is a router issue, it would have to be a 'router decided to start hating Ubuntu' issue.

Thank you for the reply and the suggestion, very much appreciated!!

---

### Post by azrael-uk on 2008-05-21
> **SpaceTeddy said:**
> what does 
```
dmesg
```
say to your connection aborts ? are there any failures reported for the driver of your network card ? 


The output from dmesg is lengthy, so I'm only pasting what appears to be relevant. If you want me to paste in the /entire/ output, I can do that too. I pasted mentions of eth1, but that's not plugged in to the router, so only eth0 should be relevant.

dmesg:

```

[    0.000000] Linux version 2.6.22-14-generic (buildd@terranova) (gcc version 4
.1.3 20070929 (prerelease) (Ubuntu 4.1.2-16ubuntu2)) #1 SMP Tue Feb 12 07:42:25
UTC 2008 (Ubuntu 2.6.22-14.52-generic)

<snip>

[   11.156197] IP route cache hash table entries: 4096 (order: 2, 16384 bytes)
[   11.156276] TCP established hash table entries: 16384 (order: 5, 196608 bytes
)
[   11.156650] TCP bind hash table entries: 16384 (order: 5, 131072 bytes)
[   11.156935] TCP: Hash tables configured (established 16384 bind 16384)
[   11.156938] TCP reno registered

<snip>

[   14.388508] forcedeth.c: Reverse Engineered nForce ethernet driver. Version 0
.60.

<snip>

[   15.201727] eth0: forcedeth.c: subsystem: 01043:0c11 bound to 0000:00:04.0


<snip>

[   16.609528] eth1: RTL8169sb/8110sb at 0xde83e000, 00:1c:f0:f9:15:cb, XID 1000
0000 IRQ 18


<snip>

[   25.030447] r8169: eth1: link down

<snip>

[   41.456992] eth0: no IPv6 routers present

<snip>

[140495.249148] eth0: link down.
[140502.549234] eth0: link up.

```

---

