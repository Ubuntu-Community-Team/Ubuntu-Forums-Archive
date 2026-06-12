---
title: "Multiple network connections..."
date: 2008-10-29
forum: Networking &amp; Wireless
---

### Post by GmAz on 2008-10-29
Ok, my motherboard has two ethernet ports, and I have my wifi card in it.  Is it possible to use one of my ethernet ports and my wife card simultaneously, on two differetn networks.  my wired port in my house, and my wife from my buddies wifi?  Would I be able to download stuff from both networks at once...essentially doubling my speed since I can use my wired connection for bittorrent stuff and the seperate wifi connection for usual internet usage?

---

### Post by Iowan on 2008-10-29
It *should* be possible, but you'll probably need to edit your */etc/network/interfaces* manually to make sure each desired interface has an "auto" line.

---

