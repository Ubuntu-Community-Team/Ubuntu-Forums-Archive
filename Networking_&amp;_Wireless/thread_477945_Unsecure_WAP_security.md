---
title: "Unsecure WAP security"
date: 2007-06-18
forum: Networking &amp; Wireless
---

### Post by p_quarles on 2007-06-18
Apologies for the slightly oxymoronic subject header. Anyway, now that I've got my home wireless working and secured (WPA2 with a looong key, no SSID broadcast), I'm curious about what measures people here take for using their laptops in coffee shops and airports and the like. 

From what I understand, the main things to do are 1) make sure file sharing is off; 2) don't manage your bank account and buy stuff from Amazon. 

But, what else? Are there any other measures to take, or useful apps to install? Should I encrypt everything on my HDD that's the slightest bit sensitive? 

Finally, I've read that it's okay to check your e-mail so long as you're using an SSL connection. I'm a total noob when it comes to encryption, but my limited understanding would suggest that in order for a standard protocol like SSL to work, it would require a common key that could easily be hacked. Much like the whole high-def video thing: if the key exists on the hardware, people can break it. 

Any advice, explanations, and/or lists of recommended reading will be appreciated. :)

---

### Post by tturrisi on 2007-06-18
There's no risk connecting to your bank sites from open access points because the site should have a security cert and be https:// , and the browser will use 128 bit encryption, meaning your login info is not sent in clear text.

---

### Post by p_quarles on 2007-06-18
Yeah, I understand that much. What I don't yet understand is what prevents someone from capturing the handshake between myself and the SSL server (and thereby gaining access to the random key) and/or spoofing a site with a valid certificate.

---

### Post by tturrisi on 2007-06-18
> **p_quarles said:**
> Yeah, I understand that much. What I don't yet understand is what prevents someone from capturing the handshake between myself and the SSL server (and thereby gaining access to the random key) and/or spoofing a site with a valid certificate.

Chances of that happenening are about one in several billion.
The criminal would have to:
1. setup his laptop as a fake access point.
2. deauth you.
3. trick you into connecting to his fake AP.
4. forge the bank's security cert.
5. create a duplicate appearing bank login page.

The above, though possible, is not likely to fool a somewhat saavy user because the url in browser address bar will not display the bank's url, on linux you would have to manualy "reconnect" once you've been deauthed, etc etc.  Easy to trick a dimwitted Windows user though because Wireless Zero Config will tell him that the network disconnected and then prompt to view available wlans and the user will connect to what he thinks is the open AP.

---

### Post by p_quarles on 2007-06-19
Cool. Thanks for explaining it to me. 

I just recently switched from Windows, actually, so it's taking me a little while to get used to this weird feeling called "security." ;-)

---

### Post by tturrisi on 2007-06-19
> **p_quarles said:**
> Cool. Thanks for explaining it to me. 

I just recently switched from Windows, actually, so it's taking me a little while to get used to this weird feeling called "security." ;-)

Just use good judgement.  If using an open AP and there are several other open APs nearby, choose the "most trusted one", be aware of who else is there using the AP, take a stroll around and if spot linux desktops then talk to him/her, they may not then target you!  Realize that it's highly unlikely that you will be at risk from someone using a Windows laptop.

---

### Post by Austin_KW on 2007-06-19
If you are worried, use a vpn. Either a commercial one or setup your home network so that you connect home using a VPN and then when you surf out you are using your home internet connection.

---

