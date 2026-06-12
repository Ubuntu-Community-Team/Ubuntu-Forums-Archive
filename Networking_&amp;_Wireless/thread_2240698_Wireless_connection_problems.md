---
title: "Wireless connection problems"
date: 2014-08-21
forum: Networking &amp; Wireless
---

### Post by laurietruluck on 2014-08-21
Hello,

I'm having intermittent problems connecting to wireless networks (it's the same in different houses). I often lose connection and it often takes 5/10 mins for the connection to be re-established. Does anyone have a solution?

Here's the result of the nm tool:
```

NetworkManager Tool

State: connected (global)

- Device: eth0 -----------------------------------------------------------------
  Type:              Wired
  Driver:            sky2
  State:             unavailable
  Default:           no
  HW Address:        54:42:49:14:5A:F4

  Capabilities:
    Carrier Detect:  yes

  Wired Properties
    Carrier:         off


- Device: wlan0  [BTHub4-698R] -------------------------------------------------
  Type:              802.11 WiFi
  Driver:            ath9k
  State:             connected
  Default:           yes
  HW Address:        78:DD:08:D5:42:E3

  Capabilities:
    Speed:           39 Mb/s

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points (* = current AP)
    BTWifi-with-FON: Infra, CC:33:BB:76:02:A5, Freq 2462 MHz, Rate 54 Mb/s, Strength 40
    *BTHub4-698R:    Infra, CC:33:BB:76:02:A2, Freq 2462 MHz, Rate 54 Mb/s, Strength 47 WPA WPA2

  IPv4 Settings:
    Address:         192.168.1.65
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.1.254

    DNS:             192.168.1.254

```

Thanks,
Laurie

---

### Post by jeremy31 on 2014-08-21
Follow the instructions in this thread to run a script in terminal and post the resulting wireless-info file
[http://ubuntuforums.org/showthread.php?t=370108](http://ubuntuforums.org/showthread.php?t=370108)

---

### Post by laurietruluck on 2014-08-22
File attached.

Thanks.

---

### Post by Hadaka on 2014-08-22
Hi, please open a terminal ctrl/alt/t and do.
```
echo "options ath9k nohwcrypt=1" | sudo tee -a /etc/modprobe.d/ath9k.conf 
```
then.
edit your network connect to look like the attached,
[ATTACH=CONFIG]255725[/ATTACH][ATTACH=CONFIG]255726[/ATTACH][ATTACH=CONFIG]255727[/ATTACH]

next:
change your router setting from TKIP  to WPA2 CCMP
thanks

---

### Post by laurietruluck on 2014-08-22
Hi @Hadaka
I followed the first 2 steps. How do I change the router from TKIP to WPA2 CCMP?
Thanks

---

### Post by jeremy31 on 2014-08-22
I would try modifying router setting by entering ```
http:192.168.1.254
``` in a browser whether firefox, chromium, or chrome and enter the username and password to change router settings

---

### Post by Hadaka on 2014-08-22
Hi, in the browser please enter
```
192.168.1.254
```
to access the settings
If you dont have your routers manual you 
should be able to find it online. If you need
help, please post back the router make and
model.

---

