---
title: "Atheros AR9462 continuos re-authentication on 14.04"
date: 2014-05-11
forum: Networking &amp; Wireless
---

### Post by eren-canpolat-t on 2014-05-11
```
[10142.253910] wlan0: deauthenticating from <MAC address removed> by local choice (reason=3)[10164.707775] wlan0: authenticate with <MAC address removed>
[10164.724659] wlan0: send auth to <MAC address removed> (try 1/3)
[10164.727047] wlan0: authenticated
[10164.730164] wlan0: associate with <MAC address removed> (try 1/3)
[10164.735341] wlan0: RX AssocResp from <MAC address removed> (capab=0x431 status=0 aid=4)
[10164.735392] wlan0: associated
```

Here are the full logs: [http://paste.ubuntu.com/7441771/](http://paste.ubuntu.com/7441771/)

Any suggestions?

---

### Post by praseodym on 2014-05-11
Have you tried to deactivate the hardware encryption of the driver:
```

echo "options ath9k nohwcrypt=1" | sudo tee -a /etc/modprobe.d/ath9k.conf
sudo modprobe -rfv ath9k
sudo modprobe -v ath9k
```

---

### Post by eren-canpolat-t on 2014-05-12
Thank you for the response. I'll try it and report back in a couple of hours...

---

### Post by eren-canpolat-t on 2014-05-13
It has been difficult to reproduce this issue. I didn't see it happening on every boot. Today, I got it again. Applied the suggestion, but had to restart the PC afterwards. I'll be monitoring dmesg to see if I get it again (and post here if it happens). After a couple of days, if I don't observe the problem, I will consider it "solved" and update the thread accordingly.

---

