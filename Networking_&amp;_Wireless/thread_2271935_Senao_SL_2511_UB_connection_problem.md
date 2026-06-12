---
title: "Senao SL 2511 UB connection problem"
date: 2015-04-02
forum: Networking &amp; Wireless
---

### Post by bixejo on 2015-04-02
Hi there,I'm trying to make work a rather old Senao SL 2511 USB wireless adapter on a rather old Acer Aspire 1620 with Lubuntu 14.04, but with no success so far.I can see wlan ssids in network manager and can try to connect to any of the. It indeed seems to connect, but immediately disconnects. I've been unsuccessfully looking for help along all posts in this forum.In the attached file you may find output from wireless_script.I'd wish to be able to attach also the output from dmesg, but I'm trying hard to do it and cannot, either as attached file or quoted as [code].Help and suggestions are welcome.Regards,--Bixejo

---

### Post by bixejo on 2015-04-03
I believe now I could attach a ZIP file with both wireless_script output and dmesg messages of connection attempts. I don't know why there's also  the former wireles-info.txt file.I don't know either why the heck my intro (end of lines) are ignored by this clumsy message editor.Help and suggestions are still welcome.Regards.

---

### Post by praseodym on 2015-04-03
Did you install the file "linux-firmware-nonfree"? It should work without ndiswrapper, so you can uninstall it:

```
sudo apt-get install linux-firmware-nonfree
sudo apt-get remove --purge ndisgtk ndiswrapper*
```
Reboot.

---

### Post by bixejo on 2015-04-03
Thank you for your answer and suggestion.

I tried that, but stil same issue. It disconnects just a few seconds after it seems to connect:

```

[  134.870451] prism2_usb 3-1:1.1 wlan0: linkstatus=CONNECTED
[  149.022584] prism2_usb 3-1:1.1 wlan0: linkstatus=DISCONNECTED (unhandled)

```

---

### Post by praseodym on 2015-04-03
Try the package linux-wlan-ng, too and change to b-mode only

Edit: Maybe it only works unencrypted or WEP?!

---

### Post by bixejo on 2015-04-04
[quote="praseodym"][...]
Edit: Maybe it only works unencrypted or WEP?!                 
[/quote]

Bingo!

That was the point. This device seems to be too old to manage WPA. Changed router WiFi encription to WEP and it works like a charm.

Thank you very much for your help!

(i apologize for being so clumsy to annoy you with that silly issue... *blush* ) :oops:

---

### Post by Vladlenin5000 on 2015-04-04
Not a silly issue, not even close... I was trying to figure out this one and I would get there too eventually but not without a lot of back and forth troubleshooting. Thankfully praseodym figure it out in just a few hours and without further troubleshooting.

---

