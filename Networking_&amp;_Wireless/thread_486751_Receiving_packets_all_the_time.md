---
title: "Receiving packets all the time"
date: 2007-06-28
forum: Networking &amp; Wireless
---

### Post by Basicalyptic on 2007-06-28
I keep receiving packets all the time. It slows down my computer and internet connection. I've looked a solution from the internet but I haven't found it. Now, the packet count is 748190 and I get 10 packets in second. I have Firestarter running. Could someone tell me what's happening?

---

### Post by t4thfavor on 2007-06-28
Is it wireless traffic, ethernet traffic. bittorrent? You have to give a bit more information if your goint to ask a question. Post ifconfig, do a tcpdump. there are many things you can do. Besides 10packets/sec isn't that many. It may be just normal traffic on you LAN/WAN.

Try installing ethereal/wiretap or something like that and capturing it then look at it and see what it is.

---

### Post by finite9 on 2007-06-28
i have same problem...do you run wirelessly?  I found that other peoples wireless cards in my area transmit packets to my laptop wireless card in what seems to be a kind of scanning mode...just to identify if my wireless card is a potential router they can connect to.  This I think, is not malicious or done manually by the other user, it is just the wireless card itself trying to identify routers as per the wireless standards.  Why linux does not simly drop or ignore these packets, I do not know.  It is worse with my Broadcom bcm43xx card...my other laptop with intel ipw3945 does not seem to be as bad.

Check your logs, syslog in particular reports new packets that are not relevant to you but were received anyway.

---

### Post by Anonymvs on 2007-06-28
Packets are data going over your network, those packets are your internet, without them, surfing the web/downloading would stop.

---

### Post by Basicalyptic on 2007-06-29
I have wireless, thank you finite9 for telling me what's going on. :popcorn:

---

