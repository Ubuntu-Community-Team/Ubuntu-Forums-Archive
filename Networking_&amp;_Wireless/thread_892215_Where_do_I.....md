---
title: "Where do I...."
date: 2008-08-16
forum: Networking &amp; Wireless
---

### Post by Schmarvin on 2008-08-16
Where can I find where to put my broadcom drivers? I'm new to Ubuntu, I'm more of a Fedore Core user. But, I can't seem to find where to put my broadcom/fwcutter drivers. Does anyone have an idea?

---

### Post by Ayuthia on 2008-08-16
> **Schmarvin said:**
> Where can I find where to put my broadcom drivers? I'm new to Ubuntu, I'm more of a Fedore Core user. But, I can't seem to find where to put my broadcom/fwcutter drivers. Does anyone have an idea?

If you are just looking for the home for the firmware, it is /lib/firmware/b43 for b43, /lib/firmware/b43legacy for b43legacy and /lib/firmware for bcm43xx.

---

### Post by Schmarvin on 2008-08-16
Thanks for that. Hopefully I can get my wireless setup. It says I'm on generic ubuntu at the moment. And after I update, hopefully I'll be on a named version.

---

### Post by NullHead on 2008-08-17
I believe when you install b43-fwcutter is asks you if you want to automatically install the proper firmware. Did you do this? 

Also, I'd use ndiswrapper. It always seems to work better, but you don't have to if you don't want to.

---

### Post by Schmarvin on 2008-08-17
Well, thanks for the help. But, I've found out, by testing ALL guides here on the forums, that I can't get wireless with Ubuntu. It just does not work. Even with Ndiswrapper. So, I've given up. Was hoping to try this. Sorry to say it, but Fedora Core is still better in my book.

---

### Post by Crafty Kisses on 2008-08-17
> **Schmarvin said:**
> Where can I find where to put my broadcom drivers? I'm new to Ubuntu, I'm more of a Fedore Core user. But, I can't seem to find where to put my broadcom/fwcutter drivers. Does anyone have an idea?

Check "Restricted Drivers Manager" or just go on the official website and see if they offer Linux drivers.

---

### Post by Schmarvin on 2008-08-17
Already did, its all installed and such. But, just will not give me an interface. But, I did try to go just off a config file and start the wireless by a config file. That didn't work either. As in, sudo wlan0 on/off, and then setting up the bssid and such.

---

### Post by Ayuthia on 2008-08-17
> **Schmarvin said:**
> Already did, its all installed and such. But, just will not give me an interface. But, I did try to go just off a config file and start the wireless by a config file. That didn't work either. As in, sudo wlan0 on/off, and then setting up the bssid and such.

Out of curiosity, can you let us know which chipset you have and which version you are using:
```
lspci -nn
uname -a
cat /etc/issue.net
```

---

