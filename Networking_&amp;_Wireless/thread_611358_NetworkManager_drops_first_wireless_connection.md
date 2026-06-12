---
title: "NetworkManager drops first wireless connection"
date: 2007-11-12
forum: Networking &amp; Wireless
---

### Post by wsmoser2004 on 2007-11-12
I've noticed recently that the KNetworkManager seems to always drop my wireless connection the first time I try to connect.  So I'll boot up my laptop, click on the icon for it to connect, and it will connect and be ready to go.  I can even browse a page or two.  However, without fail, it will drop the connection in about 30 seconds or so.  I can just click on it right away and tell it to connect, and then it works great for hours.  It's just that annoying first time that it drops.

Any idea why this might be?  I noticed it since I upgraded to Gutsy, but it may have been present before.  (Before Gutsy, I used to run iwconfig and wpa_supplicant by hand, so I didn't use it all that much.)

And help would be appreciated!

---

### Post by Brbotalnik on 2007-11-18
The same annoying problem here... I've just recently installed Kubuntu on HP-Compaq notebook and as said wsmoser2004 the connection drops after 10 or 20 seconds. When I reconnect to the wifi network all works flawlessly. I have an Intel 2200BG wireless card.

---

### Post by Brbotalnik on 2007-11-22
I've switched to kwalletmaneger for storing my passwords and the strange behavior was cured. It looks like a bug. Can anyone else confirm it?

Cheers.

---

### Post by wsmoser2004 on 2007-11-26
I think I'm using kwalletmanager for my passwords too.  Although I don't see the wallet icon on the kicker, so maybe I'm using something else and don't remember what it was...  Is the kwalletmanager the default?  Or is it the only way to store passwords?

---

### Post by Brbotalnik on 2007-11-26
it is the default password manager in KDE. See if it is enabled (Kubuntu Menu->System Settings->Advanced->Service Manager). There you have KWallet Daemon Module, it should be running.

---

### Post by wsmoser2004 on 2007-11-29
Yes, the KWallet Daemon is running.  Apparently I disabled the notification icon.  

One thing I have found out is that if I let the KNetworkManager automatically connect to networks, it seems to work fine.  For example, if I boot up my laptop and let it automatically find and connect to the network, it doesn't drop the connection.

Could it be that when I manually select a network, the KNetworkManager drops the connection because it is looking for other networks?  I have no idea if that is the reason, it just seemed like there might be a correlation there.

EDIT: I also have the Intel 2200BG card.

---

### Post by eincello on 2008-04-09
This is also happening to me on 7.10, and I also have an Intel 2200bg.  If I use the kwalletmanager, then knetworkmanager will automatically connect to my preferred wireless network and _stay_ connected.  If I use the config file, though, it doesn't automatically connect, and it disconnects about 15-20 seconds after I connect manually the first time.

Has anyone submitted a bug report to the kde folks?  Is this solved already?

---

