---
title: "Promiscuous mode doesn't seem to work"
date: 2008-05-29
forum: Networking &amp; Wireless
---

### Post by dubois on 2008-05-29
Hi, I have done some research in this but don't seem to be getting anywhere.

I have a Dell e1505 running the Broadcom 43xx Chipset driver(Restricted not NDISWrapper). It's got a 1390 WLAN minicard which works wonderfully, so does the wired card. 

This is a fresh install of Ubuntu and everything works, but when I use Wireshark and Driftnet, it doesn't seem to go into promiscuous mode.

Driftnet shows only what I browse, Wireshark shows no HTTP traffic other than from this PC, but shows CUPS, ARP, etc. from other PCs. 

I have tried putting my wireless(eth1) into promiscuous mode with:

```
sudo ifconfig eth1 mode promisc
```

I have changed the modes to monitor as well with: 

```
sudo iwconfig eth1 mode monitor
```

Anyway, I messed around with the modes and read up a little about iwconfig but nothing seems to have any effect. 

I saw a few sites claiming that the broadcom driver supports promiscuous mode, so I think I'm okay there. 

Anyway, that's where I'm at.

Any help is appreciated.

---

### Post by Prospero2006 on 2008-05-29
Have you tried running Kismet?

It will kick your card into prom off the bat.

---

### Post by dubois on 2008-05-30
Thanks, I haven't. I'll give that a whirl. The only thing is that Wireshark and Driftnet are both set to promisc mode when I have been running them, but I'll try Kismet too.

---

