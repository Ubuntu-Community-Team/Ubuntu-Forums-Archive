---
title: "Cannot Connect to Secured Wireless Networks"
date: 2007-01-30
forum: Networking &amp; Wireless
---

### Post by darkkterror on 2007-01-30
I recently installed Ubuntu on my Dell E1505 laptop.  Now, nearly everything runs smoothly so far.  I installed the latest version of ndiswrapper (1.35) and have my wireless card installed properly.

With the wireless I can detect wireless networks and am currently connected to my home wireless network.  The problem is the fact that I can't seem to connect to wireless networks that use any form of encryption (I've tried WEP and WPA).  Right now I'm relying solely on MAC address filtering, which is probably fine.  I live in a bit of a rural area and I highly doubt there are any uber leet hax0rx around capable of sniffing/spoofing a proper MAC address.  However, I'd still like to be able to use at least WEP, especially since there is an encrypted network at school I like to connect to.

So, a synopsis:

I can connect to unsecured wireless networks just fine.
My computer can detect wireless networks just fine.
My computer cannot connect to any secured network.

I have used both network manager and wifi-radar to attempt to connect to a secured network.  Both of them fail to do so when any encryption key is required but both have no problem with connecting to unsecured networks.  In the case of wifi-radar, I ran that from a terminal so I was able to see what was going on when it tried to connect.  It looked like my computer wasn't receiving a DHCP offer from the router (this happens perfectly fine on an unsecured network).

Now I have literally attempted to do this over a dozen times and I know for a fact that each time the key I entered was correct.  I have no idea what the problem is (bit of a linux noob).

I'm hoping someone can help me with this.

Also, back on the topic of me being a bit of a linux noob, if there is any output you need to try to diagnose the problem, just tell me how to do it.

Thanks.

---

### Post by spd106 on 2007-01-30
You've said that you use ndiswrapper, but you didn't say which type of wireless card you have. It might be a good idea to download the latest driver from dell support and use it with ndiswrapper.

It's rare that WEP just doesn't work, does your AP broadcast it's SSID?

---

### Post by darkkterror on 2007-01-30
I have a Dell 1390 WLAN MiniCard or whatever (Broadcom chipset).  I already went to Dell and got the latest driver (bcmwl5).  And yes, my router does broadcast the ESSID.

---

### Post by krayzee8 on 2007-03-21
I have a Compaq V5209US lappie with the same Broadcom Dell 1390 wireless card.  I have been able to get the card to work with Ndiswrapper, however I have the same problem - only unencrypted networks.  I used the driver straight from the Compaq site and unencrypted works great, but I would like to use WPA/WEP if I can.  Please post if you can figure out how to use encrypted wireless.  I will do the same.

Reading more and more about the 1390, I am inclined to think that replacing the card will most likely be the easy fix.

---

### Post by Jcarr_toonist on 2008-02-07
I am having the same problem with my wireless card on a HP 1420 running gutsy. I have tried Network manager, WICD and wi-fi radar all to no avail. 

I know that Ubuntu has the required wireless drivers for me because it used to work up until it stopped working all of a sudden.

---

