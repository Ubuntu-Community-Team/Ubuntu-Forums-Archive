---
title: "MAC address keeps changing"
date: 2007-08-25
forum: Networking &amp; Wireless
---

### Post by arizonagroovejet on 2007-08-25
So the MAC address of my new (~ two week old) PC's network card keeps changing. I noticed because the IP address it was being given by my router keeps changing, (which is annoying when trying to copy files between machines), and when I check the routers DHCP client list, the PC in question is listed X times each time with a different MAC address. I've absolutely no idea why this is happening. Anyone ever seen this or have an idea what may be causing it?

Asus P5K mobo with onboard Ethernet. Kubuntu 7.04.

```
mike@continuity:~$ uname -a
Linux continuity 2.6.20-16-generic #2 SMP Thu Jun 7 20:19:32 UTC 2007 i686 GNU/Linux
mike@continuity:~$ lspci | grep Ethernet
02:00.0 Ethernet controller: Attansic Technology Corp. L1 Gigabit Ethernet Adapter (rev b0)
```

I could statically configure the IP address I know, but that's just working around the problem not solving it.

ta,

mike

---

### Post by wirelessmonkey on 2007-08-25
I've noticed several people with ASUS boards having the same problem, it makes me wonder if this is a hardware issue.  Maybe the card is not providing the OS with the burnt in MAC, so the system has to provide a fudged MAC.... 
The easy fix for this is to create a shell script that runs at startup, which sets a MAC for you.

sudo nano -w macscript.sh
#!/bin/bash
sudo ifconfig [interface name] hw ether [new MAC address]

close nano
sudo ./macscript.sh

I suggest using a MAC address that you have seen previously from your machine, but it isn't strictly necessary.

if this works for you, you'll want to add it to your startup scripts.

---

### Post by arizonagroovejet on 2007-08-25
Still a work around rather than a fix but a cunning one, thanks. May well give that a go.

These other people you've noticed having this problem - is that noticed as in seen reference on the interweb? If so, do you have any links? I didn't find anything when I looked.

---

