---
title: "Wireless and wired printer drama"
date: 2007-04-01
forum: Networking &amp; Wireless
---

### Post by neogenesis213 on 2007-04-01
I have a printer (HP laserjet 4 plus) connected to my only lan cable (i'm guessing eth0).

I have an atheros based wireless card (i'm guessing ath0), which i use to connect to my wireless router, which connects me to my home network and the internet.

I'm a noob when it comes to networking and an even bigger noob on Ubuntu Feisty 7.04 beta.

**My problem is when I turn the printer on, my internet stops working. **

Network manager tells me i'm connected. 
If i do iwconfig in the terminal it tells me its associated. 

But in firefox it says page not found and if im running synaptic at the moment or downloading using bittorrent they stop downloading. 

It's almost as if i'm disconnected from the internet even though i'm not.

Symptoms reverse when i turn the printer off and restart.
[I]
Is there a way my printer and internet can coexist?[/I]

---

### Post by chili555 on 2007-04-01
I believe you have a Network Manager problem. NM is supposed to give preference to wired connections  and disconnect wireless if wired is available. I think when activity is detected on eth0, NM shuts down ath0.

Do you actually roam with this machine, to motels, coffee shops, etc.? If not, you might (let the flames begin) remove NM.

If i remember correctly, NM controls devices that you have **not** enabled in System -> Administration -> Networking, so you might go in and enable your wired, eth0, connection and the restart networking */etc/init.d/networking restart* and see if the problem is fixed.

---

