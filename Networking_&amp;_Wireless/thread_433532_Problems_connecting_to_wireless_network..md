---
title: "Problems connecting to wireless network."
date: 2007-05-05
forum: Networking &amp; Wireless
---

### Post by silverwolfe on 2007-05-05
I have a WEP-64bit HEX wireless network that registers at around 50% strength in my room and XP picks up the signal fine and connects.

In Ubuntu, I have all the access info correct but it never connects.  I'm using the Netgear WG311v2g, which is supported already.  The card can see the network, but I can't connect.

Any suggestions?

---

### Post by sdide on 2007-05-05
What do you use to associate? wpa_supplicant?

How do you associate?

---

### Post by silverwolfe on 2007-05-05
Associate?

The network is WEP, no WPA anywhere.

I have an update on the situation now.  When I set it to roaming mode, I achieve a signal strength and it appears that I'm connected to the network, but I can't access anything on my network or use the internet.  When I check the network information, I still have no IP or any other info on that page.

If I try to set up a manual configuration, it looks like it doesn't even try to connect.

---

### Post by sdide on 2007-05-05
Do you use networkmanager to connect? 
(Where do you type in your WEP access key?)

---

### Post by Fitzy_oz on 2007-05-05
> **silverwolfe said:**
> I have a WEP-64bit HEX wireless network that registers at around 50% strength in my room and XP picks up the signal fine and connects.

In Ubuntu, I have all the access info correct but it never connects.  I'm using the Netgear WG311v2g, which is supported already.  The card can see the network, but I can't connect.

Any suggestions?

The driver support is not exactly perfect for that card, you might find you have a bit better luck with  the ndiswrapper, I had a similar issue with my dongle but I was still able to connect, it just constantly dropped out.  Switched to the NDISWRAPPER and haven't had any trouble since....  [Check this thread out]("http://ubuntuforums.org/showthread.php?t=329299&highlight=wg111v2")

---

### Post by silverwolfe on 2007-05-05
> **sdide said:**
> Do you use networkmanager to connect? 
(Where do you type in your WEP access key?)

Yes, I'm using the network manager.

[quote=Fitzy_oz]The driver support is not exactly perfect for that card, you might find you have a bit better luck with the ndiswrapper, I had a similar issue with my dongle but I was still able to connect, it just constantly dropped out. Switched to the NDISWRAPPER and haven't had any trouble since.... Check this thread out[/quote]

I'm using the WG311 v2, not the WG111 v2.

---

