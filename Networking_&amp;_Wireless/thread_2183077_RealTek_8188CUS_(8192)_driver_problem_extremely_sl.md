---
title: "RealTek 8188CUS (8192) driver problem: extremely slow"
date: 2013-10-23
forum: Networking &amp; Wireless
---

### Post by z4zJKYN on 2013-10-23
Hey there!

I almost died googling for help today. Everything I tried didn't work!

The problem: I bought [this]("http://www.amazon.de/CSL-Adapter-Raspberry-automatische-Netzeinbindung/dp/B00D1876LO") device, which features a 8188 (or 8192) CUS chip from RealTek. I did manage to install the latest driver from the RealTek homepage and blacklisted the rtl8192cu driver (which seems to be absolutely useless) and WiFi works now. BUT: It is soo damn slow. I only sometimes get to a maximum at around ~1 MBit/s, which is a sixth of what my Windows machine achieves.

I'm running elementary OS luna (which is based on ubuntu as you may know). The integrated rtl8192 didn't find any connections on elementary OS. On Linux Mint live it did find my router, but the connector wheel kept spinning. Connection couldn't be established.

Could you please help me?

EDIT: Connection information shows rtl8192cu as driver, although it is blacklisted and I even added 8192cu to /etc/modules and lsmod only shows 8192cu.

[B]tl;dr:
[/B]RealTek driver works
but: is too damn slow
OS: elementary OS luna

Thanks!

---

### Post by kurt18947 on 2013-10-23
Judging by the size, that's most likely an 8188CUs device.  Element Luna is I believe based on Ubuntu 12.04.  If so, I believe the driver from Realtek should build and work.  The RealTek driver includes an install.sh script to be run from a terminal.

[http://www.realtek.com.tw/downloads/downloadsView.aspx?Langid=1&PNid=21&PFid=48&Level=5&Conn=4&DownTypeID=3&GetDown=false&Downloads=true#2742](http://www.realtek.com.tw/downloads/downloadsView.aspx?Langid=1&PNid=21&PFid=48&Level=5&Conn=4&DownTypeID=3&GetDown=false&Downloads=true#2742)

---

### Post by z4zJKYN on 2013-10-24
Yeah, I know..
I installed the driver and everything works, as stated in first post. The problem is, it is too slow!
Most of the time the KB/s loop from 0 to 40, and sometimes go up to 200.

---

### Post by kurt18947 on 2013-10-24
Has your router or access point been powered down or rebooted lately?  If not and you have access, that might be worth a try.  Is this machine portable where you could try connecting to another access point?  Other than that, if you're running Realtek's driver I have no further thought.

---

