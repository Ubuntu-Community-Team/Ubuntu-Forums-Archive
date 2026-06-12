---
title: "wpa_supplicant config issue in hardy"
date: 2008-02-17
forum: Networking &amp; Wireless
---

### Post by rouble on 2008-02-17
Hi All,

If I have the following at the top of my /etc/wpa_supplicant.conf file:
```
ctrl_interface=/var/run/wpa_supplicant
```

I get this when I run wpa_supplicant:
```
~$ sudo /sbin/wpa_supplicant -D wext -i wlan0 -c /etc/wpa_supplicant.conf 
ioctl[SIOCSIWAUTH]: Operation not supported
WEXT auth param 4 value 0x0 - ioctl[SIOCSIWAUTH]: Operation not supported
WEXT auth param 5 value 0x1 - Failed to initialize control interface '/var/run/wpa_supplicant'.
You may have another wpa_supplicant process already running or the file was
left by an unclean termination of wpa_supplicant in which case you will need
to manually remove this file before starting wpa_supplicant again.
```

Also, wireless does not work. If I comment out that line, like this:
```
#ctrl_interface=/var/run/wpa_supplicant
```

Then wireless works, but I can't use wpa_action or wpa_cli etc.

I need wpa_action to work, because I want to setup wpa_supplicant in roaming mode.

Any tips on what might be wrong here? Why is it not able to initialize control interface '/var/run/wpa_supplicant'?

tia,
rouble

---

