---
title: "[SOLVED] no wireless with wicd on amd64 intrepid"
date: 2008-11-14
forum: Networking &amp; Wireless
---

### Post by stanley drew on 2008-11-14
I had wicd working flawlessly in 8.04 (32-bit) and I had hoped to get it going again since network-manager in 8.10 is giving me hell with wpa (as noted in many many posts). But alas when I run wicd no wireless networks are found. Wired works fine with wicd, although it doesn't automatically connect on startup. Anyway I am running x86_64 8.10 with an atheros ar5007 card so i'm using ath5k, and again network-manager is working more or less but I'd rather use wicd. Any chance somebody is having the same problem or knows what I'm doing wrong?

---

### Post by stanley drew on 2008-11-16
b u m p

---

### Post by imdano on 2008-11-16
Wicd isn't finding any networks?  Does "iwlst scan" show any?  If it does, make sure wicd has the correct wireless interface selected in its preferences window.

---

### Post by stanley drew on 2008-11-18
apparently the command is iwlist and it does show networks, but you were correct to question my wicd preferences for the wireless interface. there wasn't any interface listed! simply listing wlan0 followed by a restart of wicd did the trick. thanks very much.

---

### Post by imdano on 2008-11-18
Glad you got it working (and sorry about that typo!).

---

