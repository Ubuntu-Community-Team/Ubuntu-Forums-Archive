---
title: "wpa-ap-scan"
date: 2008-11-08
forum: Networking &amp; Wireless
---

### Post by cccc on 2008-11-08
hi

according to this HOWTO:

[http://ubuntuforums.org/showthread.php?t=318539](http://ubuntuforums.org/showthread.php?t=318539)```

* wpa-ap-scan:
"1" = Broadcast of ESSID.
"2" = Hidden broadcast of ESSID.
```

pls be very carefully !
the wpa-ap-scan depends upon which driver is installed.

I tested with 2 notebooks:
1.) Toshiba Satellite Pro U200 with wireless chipset **Pro/Wireless 3945 ABG**.
2.) Asus eee 1000H with chipset **Ralink rt2860**

on both notebooks is the same OS, debian lenny installed,
I'm using the same wireless router Netgear WGU624 and the same WPA2-PSK configuration. 
ESSID is hidden.

I've tried on both notebooks:```
wpa-ap-scan 1
``` and ```
wpa-ap-scan 2
```

**Pro/Wireless 3945 ABG works only with wpa-ap-scan 1 !**

and 

**Ralink rt2860 works only with wpa-ap-scan 2 !**


btw. according to /usr/share/doc/wpasupplicant/README.modes.gz```

In order to be able to associate to hidden
ssids, please try to set the option 'ap_scan=1' in the global section, and
'scan_ssid=1' in your network block section of your wpa_supplicant.conf file.
If you are using the managed mode, you can do so by these stanzas:

iface eth1 inet dhcp
wpa-ap-scan 1
wpa-scan-ssid 1
# ... additional options for your setup
```


**could someone correct this HOWTO ?**

greetings
cccc

---

### Post by Arabiest on 2008-11-09
thank u

---

