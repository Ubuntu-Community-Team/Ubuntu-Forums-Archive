---
title: "&quot;iw reg get&quot; returns &quot;country 00: DFS-UNSET&quot; although CRDA is configured"
date: 2018-10-16
forum: Networking &amp; Wireless
---

### Post by adelpozoman-f on 2018-10-16
sudo iw reg get:
```

global
country 00: DFS-UNSET
        (2402 - 2472 @ 40), (6, 20), (N/A)
        (2457 - 2482 @ 20), (6, 20), (N/A), AUTO-BW, PASSIVE-SCAN
        (2474 - 2494 @ 20), (6, 20), (N/A), NO-OFDM, PASSIVE-SCAN
        (5170 - 5250 @ 80), (6, 20), (N/A), AUTO-BW, PASSIVE-SCAN
        (5250 - 5330 @ 80), (6, 20), (0 ms), DFS, AUTO-BW, PASSIVE-SCAN
        (5490 - 5730 @ 160), (6, 20), (0 ms), DFS, PASSIVE-SCAN
        (5735 - 5835 @ 80), (6, 20), (N/A), PASSIVE-SCAN
        (57240 - 63720 @ 2160), (N/A, 0), (N/A)

```



CRDA:
```

# Set REGDOMAIN to a ISO/IEC 3166-1 alpha2 country code so that iw(8) may set
# the initial regulatory domain setting for IEEE 802.11 devices which operate
# on this system.
#
# Governments assert the right to regulate usage of radio spectrum within
# their respective territories so make sure you select a ISO/IEC 3166-1 alpha2
# country code suitable for your location or you may infringe on local
# legislature. See `/usr/share/zoneinfo/zone.tab' for a table of timezone
# descriptions containing ISO/IEC 3166-1 alpha2 country codes.

REGDOMAIN=ES

```



I've had problems using USB wifi on this PC. Checking the system log when failing, it always says something about CTRL region dom change. Could that be the reason? Is there a fix?

---

### Post by chili555 on 2018-10-16
What is the response to the terminal command:```
sudo iw reg set ES && sudo iw reg get
```> Checking the system log when failing, it always says something about CTRL region dom change.Please capture and post the messages.

Thanks.

---

### Post by praseodym on 2018-10-17
Maybe your driver doesn't support it? Lets see

```
lsmod
```
completely. If it works with the cfg80211 subsystem, then REG doesn't work. Then you could try

```
echo 'options cfg80211 ieee80211_regdom="ES"' | sudo tee /etc/modprobe.d/cfg80211_options.conf
```
and reboot

---

### Post by adelpozoman-f on 2018-10-17
```
global
country ES: DFS-ETSI
        (2400 - 2483 @ 40), (N/A, 20), (N/A)
        (5150 - 5250 @ 80), (N/A, 23), (N/A), NO-OUTDOOR, AUTO-BW
        (5250 - 5350 @ 80), (N/A, 20), (0 ms), NO-OUTDOOR, DFS, AUTO-BW
        (5470 - 5725 @ 160), (N/A, 26), (0 ms), DFS
        (5725 - 5875 @ 80), (N/A, 13), (N/A)
        (57000 - 66000 @ 2160), (N/A, 40), (N/A)


```

So now its supposed to be fixed. Will try in the next week a USB device that couldnt be used on my pc. As always, thanks @chili555
@praseodym response looks promising too

---

### Post by adelpozoman-f on 2018-10-17
can I mark as solved?

---

