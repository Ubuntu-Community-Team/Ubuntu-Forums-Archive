---
title: "Netgear WG311T: iwlist error"
date: 2007-01-28
forum: Networking &amp; Wireless
---

### Post by hypnosis on 2007-01-28
Hello,

I installed Ubuntu Breezy.
My card WiFi Netgear WG311T is detected by lspci.
I installed ndiswrapper, and I used it to install the drivers Windows 2000 (those from the CD).
I set the ESSID and the WEPkey in System>Admin>Networks for the interface ath0.

But when I validate my settings and I activate the interface ath0, I'm not connected.
[B]
iwlist ath0 scan returns:
```
ath0 failed to read scan data: resource temporarily unavailable
```[/B]

ndiswrapper -l returns something like:
```
wg311t driver installed, hardware present
```

iwconfig ath0 returns:
```
ath0 IEEE 802.11 ESSID: MAISON
Mode: Managed Frequency: 2.452GHz Access Point: 00:00:00:00:00:00
...(if the all return is important, tell me because I have to reboot under linux, write the text, and reboot under windows to post it...)
```


How could I fix that problem ?
Thank you.

PS: I'm a beginner with Linux

---

### Post by hal10000 on 2007-01-28
Post the output of [COLOR="Red"]lscpci[/COLOR] and [COLOR="Red"]sudo lspci -v[/COLOR].
You can write the outputs to a file: [COLOR="Red"]lspci > lspci.txt[/COLOR] and [COLOR="Red"]sudo lspci -v > lspci-v.txt[/COLOR]
This creates two files called lspci.txt and lspci-v.txt in your current directory (probably your home directory). You can then store these files to a floppy or usbdisk (or whatever) and use them in windows for posting.

---

