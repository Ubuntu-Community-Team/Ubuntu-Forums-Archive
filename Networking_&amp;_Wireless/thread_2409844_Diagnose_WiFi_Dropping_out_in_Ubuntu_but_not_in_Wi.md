---
title: "Diagnose WiFi Dropping out in Ubuntu but not in Windows-10?"
date: 2019-01-07
forum: Networking &amp; Wireless
---

### Post by 2CV67 on 2019-01-07
Ever since I started using my "new" PC with Ubuntu 14.10 on my main partition in 2014 with "Think Penguin" TPE-N150USBL dongle, I have had occasional instances of WiFi dropping out.

Currently, with 18.04, WiFi drops out several times per day.
Sometimes, the WiFi indicator on the top panel switches to a "?" & sometimes not.
It can also show "?" when WiFi seems to be working OK.
It never shows the "Empty triangle" sign for no WiFi.
I can always reconnect immediately by clicking > Indicator > my router > Turn Off > Panel > WiFi Off > Turn On.

Other PC's & phones use the same router with absolutely no problem.

On my same PC with same "Think Penguin" WiFi dongle, my Ubuntu LTS (currently 16.04) partition has never shown any problem (but is used less frequently & less long, so maybe proves nothing?).
On same PC & dongle, Windows 10 also has never shown any problem (used infrequently but for long sessions).

So I think I am looking for a problem internal to my main Ubuntu partition, rather than router or dongle?

Over the years, I have often tried to follow troubleshooting guides but never got anywhere.

Can anybody help by pointing to a suitable procedure, or by suggesting steps to start diagnosis?

I just installed "pastebinit" & generated a wireless-info.txt file (while WiFi was working OK) & hopefully attached it...
Should I run wireless-info script again when WiFi is down?

Thanks for any suggestions to help somebody who really has no idea about WiFi!

Thanks!

---

### Post by praseodym on 2019-01-07
Try reducing the current uptake

```
echo 'KERNEL=="wlan0", ACTION=="add", RUN+="/sbin/iwconfig wlan0 txpower 15"' | sudo tee /etc/udev/rules.d/10-wlan-stick.rules
```
Reboot and change the encryption mode in your router to WPA2 instead of WPA (or mixed mode WPA/WPA2)

---

### Post by 2CV67 on 2019-01-11
Thanks, praseodym, for your kind suggestion.

I didn't try it yet, hoping there might be some further input (agreement, explanation...)

In the meantime, I did run wireless-info script again, this time while the problem was present.
At a glance, I don't see any obvious sign the connexion is not working.
Does this add anything to the story?

Thanks!

---

