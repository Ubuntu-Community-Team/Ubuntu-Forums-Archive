---
title: "Wireless USB adapter problem."
date: 2019-03-04
forum: Networking &amp; Wireless
---

### Post by ashu00 on 2019-03-04
hi,
I'm connecting to my router via USB WiFi adapter (tplink TL-WN822N). If I kept it connected to PC while booting, ubuntu shows 'Activation of network Connection failed'.
When I remove the adapter and re-plug it and, it works again flawlessly. if I rebooted then ubuntu again shows 'Activation of Network Connection failed'.
I also have Windows 10 installed, but it doesn't show such problem.

I'm running Ubuntu Desktop 18.04 with all latest updates installed.
any help would be appreciated.

---

### Post by ashu00 on 2019-03-09
Bump?

---

### Post by praseodym on 2019-03-09
Please run the wireless script from the sticky thread and show the outputs

---

### Post by ashu00 on 2019-03-09
thanks for reply.
I have run the script and attached the results below.
first is run after I booted up PC and the connecting the Wifi Adapter
[ATTACH]282730[/ATTACH]

This one is taken after a reboot when Ubuntu was showing 'Activation of network connection Failed'
[ATTACH]282731[/ATTACH]

---

### Post by praseodym on 2019-03-11
Chenge the encryption mode in your router to WPA2-AES (CCMP), not mixed mode WPA/WPA2

---

### Post by ashu00 on 2019-03-16
> **praseodym said:**
> Chenge the encryption mode in your router to WPA2-AES (CCMP), not mixed mode WPA/WPA2

thank you.. now its working properly.

---

