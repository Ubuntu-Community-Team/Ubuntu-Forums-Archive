---
title: "Wireless Networks Display"
date: 2006-11-18
forum: Networking &amp; Wireless
---

### Post by H-Radical on 2006-11-18
Hi all, 
I was wondering if there is a way to see a list of available wireless networks in Ubuntu Edgy just like in Windows XP where you can choose "show available wireless networks".
It's kinda hard to connect to wireless networks in public places (ie Starbucks, school) when you don't have this feature.

Cheers,
H-Radical

---

### Post by somerandomnerd on 2006-11-18
Try "iwlist scanning" in the Terminal.

---

### Post by FrodoB on 2006-11-18
wifi-radar:

sudo apt-get update
sudo apt-get install wifi-radar

You may need to uncomment some repository in:

/etc/apt/sources.list

This will give you something similar to what XP has in
Applications ->Internet -> Wifi Radar

---

### Post by Kamy on 2006-11-18
LOL,  I subscribed to this thread because I was curious about this too, just got this in my inbox...

"Dear Kamy,

somerandomnerd has just replied to a thread you have subscribed to entitled " <snip>

Great username :D

Kamy

---

