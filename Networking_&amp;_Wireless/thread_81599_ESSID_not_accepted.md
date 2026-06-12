---
title: "ESSID not accepted"
date: 2005-10-24
forum: Networking &amp; Wireless
---

### Post by astroaniket on 2005-10-24
I have put Ubuntu 5.10 (with KDE as well).
Using tips in ubuntuforums I was able to make my laptop recognise Netgear MA111 wlan card.
Now when I give
sudo iwconfig essid "reuterwmhwlan"
it says somthing like "unrecognised network request reuterwmhwlan".
Kwifimanager shows that MA111 is working properly.
The SSID is correct I used the same in windows XP and it works peacefully. Any suggestions?

---

### Post by ubutthead on 2005-10-24
[QUOTE=astroaniket]I have put Ubuntu 5.10 (with KDE as well).
Using tips in ubuntuforums I was able to make my laptop recognise Netgear MA111 wlan card.
Now when I give
sudo iwconfig essid "reuterwmhwlan"
it says somthing like "unrecognised network request reuterwmhwlan".
Kwifimanager shows that MA111 is working properly.
The SSID is correct I used the same in windows XP and it works peacefully. Any suggestions?[/QUOTE]

what happens when you run:

```

#:sudo iwlist ath0 scan

```

---

### Post by astroaniket on 2005-10-25
I just booted the machine today morning and it accepted the essid without any complaints (and there were no spelling mistakes in the command I was typing yesterday as I just used uparrow to give the command again). So now I am connected to net. Thanks for the tip.
BTW, that command gives,
ath0 interface does not support scanning.

Now that I have given essid in iwconfig, do I have to give it again at every boot or there is some default method to do it? Thanks.

---

### Post by knappen on 2005-10-25
[QUOTE=astroaniket]I have put Ubuntu 5.10 (with KDE as well).
Using tips in ubuntuforums I was able to make my laptop recognise Netgear MA111 wlan card.
Now when I give
sudo iwconfig essid "reuterwmhwlan"
it says somthing like "unrecognised network request reuterwmhwlan".
Kwifimanager shows that MA111 is working properly.
The SSID is correct I used the same in windows XP and it works peacefully. Any suggestions?[/QUOTE]

I think you have add your wlano or eth0.

Like sudo iwconfig (wlan0 or eth0) essid "reuterwmhwlan"

---

