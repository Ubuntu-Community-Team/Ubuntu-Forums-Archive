---
title: "Internet not working after upgrade to Edgy 6.10"
date: 2007-05-30
forum: Networking &amp; Wireless
---

### Post by noob12345 on 2007-05-30
I just upgraded my Dapper to Edgy, and now my Netgear MA111 wireless adapter is not working

normally, I'd activate it at start up using these commands that loads linux-wlan-ng:
sudo modprobe prism2_usb prism2_doreset=1
sudo wlanctl-ng wlan0 lnxreq_ifstate ifstate=enable
sudo wlanctl-ng wlan0 lnxreq_autojoin ssid=NETGEAR authtype= opensystem

Edgy took the commands fine, and I saw wireless connection under networking like I normally did, the LED on my adapter was even lit
But I had no internet, I tried pinging, and it returned nothing (the device setting was stuck at loopback device, I'm not sure what that means) All the settings were the same

Please help, I was planning to upgrade into Fiesty after

---

### Post by noob12345 on 2007-05-30
nevermind, it turns the internet will not work only after I enter in the commands I would do in Dapper
I just needed a reboot

---

