---
title: "wifi problem with PRISM3"
date: 2006-10-04
forum: Networking &amp; Wireless
---

### Post by dphipps on 2006-10-04
I have a ESC A535 laptop and had some troulbe with the prism3 wifi.  The problem is sometimes the it shows up at startup and sometimes it doesn't.

Also I can conect with it from the Networking control panal.  To conect with it I run these camands from a scrip.
```
gksu wlanctl-ng wlan0 lnxreq_autojoin ssid="" authtype=opensystem
gksu dhclient wlan0
```

Sometimes when I us this it won't conect and when I dose this it disapers form the Networking control panal.

I am using the linux-wlan-ng drivers.

Thanks for the help.

---

### Post by dphipps on 2006-10-04
I forgot ot add this in my original post but this wifi card is internal and uses a USB interface.

---

### Post by dphipps on 2006-10-08
bump

---

### Post by dphipps on 2006-10-09
no response???

---

### Post by dphipps on 2006-10-10
I tried to use the ndiswraper and I get this.

```
~$ ndiswrapper -l
Installed ndis drivers:
avwlpnic                driver present, hardware present
~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     no wireless extensions.

sit0      no wireless extensions.

~$
```

---

### Post by tormod on 2006-10-13
Did you read through the wiki documentation?

[https://help.ubuntu.com/community/WifiDocs/Driver/prism2_usb](https://help.ubuntu.com/community/WifiDocs/Driver/prism2_usb)

---

### Post by dphipps on 2006-10-14
Thanks for the link tormod.  I had not found that documentation (I had not thought to look under prism2).

---

