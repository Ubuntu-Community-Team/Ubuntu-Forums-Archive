---
title: "Found solution to networking problem. How to make automatic?"
date: 2007-01-30
forum: Networking &amp; Wireless
---

### Post by auroraborealis on 2007-01-30
I finally found a script on another website that makes my device (Senao NL-2511UB) work, but it requires I sudo execute the script everytime I reboot. How do I make it automatic, or have the changes persist through restarting the computer?

I don't know if it'll help, but this is the script, btw:

```
modprobe prism2_usb prism2_doreset=1
wlanctl-ng wlan0 lnxreq_ifstate ifstate=enable
wlanctl-ng wlan0 lnxreq_autojoin ssid=linksys authtype=opensystem
dhclient
```

Thanks.

---

### Post by Hanzerik on 2007-01-30
You can try putting those commands in /etc/rc.local
Which will run them on startup.

---

