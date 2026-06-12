---
title: "linksys is racist against wifi radar"
date: 2008-03-13
forum: Networking &amp; Wireless
---

### Post by skydiver|goose on 2008-03-13
I know my wireless card works, because before I left town I could connect to my network and my friend's network (which is linksys), but I'm out of town at a friend's house who uses a linksys router and every time I try and connect to it I can't get it to assign me an IP address of anything. I know it's not a MAC filter, because it's disabled on their network. Someone else here with a windows laptop can connect fine. Wifi Radar and Network Manager both pick up the signal fine. It's now WEP or WPA or anything. And ideas?

---

### Post by skydiver|goose on 2008-03-13
bump

---

### Post by jago25_98 on 2008-03-13
I've had this problem from time to time too.

I noticed it can be separate problems for me though:

1) KNetworkManager sometimes sees WPA networks as WEP. Solution was having to type it all in manually including key.

2) Seems to work but doesn't get can IP through DHCP. I haven't solved this problem yet, seems to be my luck. I tracked it down to this by setting up with knetman and then `dhclient eth2`

3) Also, sometimes /etc/resolv.conf doesn't always set up properly, yet windows is ok. No idea why. I have to fix by typing it in.

All problems drive me mad.

---

### Post by skydiver|goose on 2008-03-13
I meant to say there's no WEP or WPA. The only internet access I have up here is on my pda-phone, so I can't download anything on my laptop. How can I fix it? Manually enter the info? and if so, what all do I need?

---

### Post by jago25_98 on 2008-03-13
I don't use wifi radar. I use knetworkmanager, right click it > connect to other wireless network > input ssid and details manually; need to know the station ID

---

### Post by skydiver|goose on 2008-03-13
if I take a screenshot of ipconfig /all in windows, ca you tell me what to punch in and where?

---

### Post by skydiver|goose on 2008-03-13
fixed it.

I changed the router settings to only broadcast on G instead of B & G and it magically worked.

---

