---
title: "Torrent download causing wifi to hang – Intel Pro 3945ABG"
date: 2013-12-25
forum: Networking &amp; Wireless
---

### Post by simonlee.2005 on 2013-12-25
Hi, all fellow Ubuntu-ians:

I am also having the "torrent download causing wifi to hang" problem.

I am using a Intel Wireless Pro 3945ABG on a HP/Compaq DV2000.
I had tried the "iwconfig wlan0 power off" command and had verified that the power
management is indeed off using "iwconfig" command.

I only started experiencing this problem after I changed my ISP (to Maxis, Malaysia).
When I used Transmission or Deluge to download torrents, after a while the wifi will
just hang (still connected but cannot browse or ping the internet, e.g. 8.8.8.8).
Torrent download using the Win7 OS and uTorrent is fine though, which is why I suspect
something is amiss with Ubuntu.

Please help. I actually prefer Ubuntu over Windows.

Thanks in advance.
Simon Lee @ Kuala Lumpur, Malaysia

---

### Post by coffeecat on 2013-12-26
I have moved your post into its own thread. The thread you posted to was about a different wireless device. I have also edited out your email address to protect you from spammers. Support is given in the forum, not by email.

---

### Post by sanderj on 2013-12-26
> **simonlee.2005 said:**
> Hi, all fellow Ubuntu-ians:

I am also having the "torrent download causing wifi to hang" problem.

I am using a Intel Wireless Pro 3945ABG on a HP/Compaq DV2000.
I had tried the "iwconfig wlan0 power off" command and had verified that the power
management is indeed off using "iwconfig" command.

I only started experiencing this problem after I changed my ISP (to Maxis, Malaysia).
When I used Transmission or Deluge to download torrents, after a while the wifi will
just hang (still connected but cannot browse or ping the internet, e.g. 8.8.8.8).
Torrent download using the Win7 OS and uTorrent is fine though, which is why I suspect
something is amiss with Ubuntu.

Please help. I actually prefer Ubuntu over Windows.

Thanks in advance.
Simon Lee @ Kuala Lumpur, Malaysia

I think it's your router/NAT-devcie that hangs, and not your Wifi.

Bittorrent opens a lot of sessions and does a lot of traffic over those sessions ... and badly designed/implemented routers/NAT-devices can't handle that and stop working.

So:
- is there a firmware upgrade for your router?
- if not: lower the amount of simultaneous torrent sessions (and maybe the amount of traffic)

HTH

---

### Post by ian-weisser on 2013-12-26
sanderj is right.

In the torrent setups I have...ahem...seen, the biggest issues is the number of peers. It overloads the router's tracking of active connections. Capping the number of peers to 10 or 15 at a time, and resetting the router to flush the connection table, has cleared up the cases I have seen.

---

### Post by simonlee.2005 on 2013-12-26
Thanks for all the feedback, brothers in Ubuntu.

I don't think it is a case of router hanging in my case, as I can still access the internet via WiFi using other devices or laptops
when the "wifi hang on ubuntu" happens. Actually, I had thought the same thing and even contacted my ISP to complain.
They asked me to switch the wireless channels. Needless to say, it didn't work. But via the forum I do know that they
are throttling torrent downloads between 8pm - 12am Malaysia time (GMT+8) though.

I had also try resetting the router, even the modem at times, and the "hang" will come back after 5 mins.

I had tried limiting the number of connections to less than 200 and set each torrent to have <= 30 peers and the problem
persists. I will try setting the peer count per torrent lower to see if that helps.

Just wondering if going back to Ubuntu 12.04 LTS might resolve this issue or perhaps reconfigure or re-compile the wifi
driver?

As usual, any insights and suggestions are appreciated. Thanks in advance.

---

