---
title: "Constant 5 kilobyte/s download"
date: 2008-02-11
forum: Networking &amp; Wireless
---

### Post by Royall on 2008-02-11
According to my system monitor, I'm constantly downloading at 5 k/s. I've closed my browser and Pidgin and such, but it keeps going. I run Wireshark and see that there are packets moving through ath0, but they don't look too special. Is there a way to find out which processes are communicating over ath0?

---

### Post by jetsam on 2008-02-12
You could try nethogs from the universe repository.  It breaks net usage down by process.  

Run with:
```
sudo nethogs ath0
```
To get it to listen to ath0.

---

### Post by Royall on 2008-02-12
Hmmm...
System monitor still shows the same thing, and nethogs reports that root has transported 0 over ath0. Maybe I should check out lo and wifi0.

---

### Post by jetsam on 2008-02-12
Any luck tracking it down?

**iptraf** can give you a nice breakdown of how much each interface is sending and receiving.  Run it with **sudo iptraf** and select "general interface statistics."

Nethogs is a bit rough around the edges, and I don't think it reports udp or icmp traffic.    Trouble is, I don't know of any other way of doing what it does.

---

### Post by Royall on 2008-02-12
Neither of those really shows much activity. Could this be a bug in the Gnome system monitor?

---

### Post by jetsam on 2008-02-12
Not sure.  It's possible.  I don't see anything in launchpad, and I'd be inclined to look for other explanations first...

...I wouldn't be surprised at all that nethogs was missing traffic.  Iptraf, though, is more surprising.  

Does 
```
sudo netstat -platu
```
Show you any unexpected active connections?

---

