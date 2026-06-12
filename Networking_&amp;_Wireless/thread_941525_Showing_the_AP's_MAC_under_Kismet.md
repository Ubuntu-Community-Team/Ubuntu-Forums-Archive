---
title: "Showing the AP's MAC under Kismet"
date: 2008-10-08
forum: Networking &amp; Wireless
---

### Post by s_force on 2008-10-08
Hi everyone!

I'm using Ubuntu since yesterday and I'm pretty surprised. This is a very cool OS!

Now I want to use Kismet, but I have a question:

How can I get the MAC-Adress of a specific AP (Hotspot...)?

I opened kismet_ui.conf.

I first set the intro to false, that worked ok.

Then I set:

```
columns=mac,name,type,wep,channel,flags
```
But there is only the name, channel, wep and flags visible!

What the f*** is this? In client mode, I can see mac adresses, but I want to see the AP's like in Windows's NetStumbler.

Thank you guyz!

---

### Post by s_force on 2008-10-08
Sorry, I found in the readme (bssid) <--- RTFM:(

But I have another question concerning kismet.
If I have the bssid shown, how can i copy the bssid out of that program? (I am in the full-screen virtual terminal (STRG+ALT+F1)?

Thank you.

---

