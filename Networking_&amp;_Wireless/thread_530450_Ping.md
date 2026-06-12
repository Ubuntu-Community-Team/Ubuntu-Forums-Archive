---
title: "Ping"
date: 2007-08-20
forum: Networking &amp; Wireless
---

### Post by ABX on 2007-08-20
How can use ping in Linux to make it display packet lost in real time?

In windows I do ping -t [www.google.com](www.google.com) and I can see when I get a packet drop, but in linux until I stop the ping command I don't see any packet drop.

---

### Post by jakev383 on 2007-08-20
You can try (I don't get packet loss here, so I can't verify):
ping -v whatever.com
or if you like to see dots created for every ping sent, with 1 being deleted for every reply:
sudo ping -f whatever.com
Just be careful with that one.  It floods the host with ICMPs.

---

### Post by ABX on 2007-08-27
Thanks I'll try it.

Luckily my line is stable too, but sometimes the international lines aren't exactly 100% reliable, I'd like just to find out when they are bad.

So far I didn't have any packets lost, so I'll report back when I'll have the possibility to test it out.

---

### Post by steve.horsley on 2007-08-27
You might also find **mtr** interesting.

---

### Post by ABX on 2007-08-29
I tend to use the provided tools as much as I can. Often when you jump from one system to another you don't have the luxury to use 3rd party programs.

---

### Post by ABX on 2007-09-07
> **jakev383 said:**
> You can try (I don't get packet loss here, so I can't verify):
ping -v whatever.com
or if you like to see dots created for every ping sent, with 1 being deleted for every reply:
sudo ping -f whatever.com
Just be careful with that one.  It floods the host with ICMPs.



ping -v whatever.com doesn't shows any packet drops in real time.

---

