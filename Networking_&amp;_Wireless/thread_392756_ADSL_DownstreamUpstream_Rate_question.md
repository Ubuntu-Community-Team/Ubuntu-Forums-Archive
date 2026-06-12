---
title: "ADSL Downstream/Upstream Rate question"
date: 2007-03-24
forum: Networking &amp; Wireless
---

### Post by stuntgp2000 on 2007-03-24
Hi everybody, I have both Speedtouch 330 & Sagam 800 DSL modem which I finally managed to configure correctly :) , however I wonder if there is a way to know my modems downstream & upstream rate using the shell.

actually, I managed to see real-time download & upload speed using bwm-ng but I couldn't find a way to see downstream & upstream rate provided by my ISP.

I hope I was able to explain what mean :( , Thanks in advance.

Medber

---

### Post by HereInOz on 2007-03-25
The way that I understand it is that the downstream and upstream line speeds are allocated at the transport layer, not at the TCP/Ip layer, therefore those speeds would only be accessible by gaining access to your modem.

The computer would only be able to tell you what actual speeds you are currently getting, but this is not what you want to know.  The modem itself is, I think, the only device that will "know" what the line speeds are.  Most modems will show this, usually through a web based management interface.

---

### Post by stuntgp2000 on 2007-03-25
Thanks for guiding me on this, I was able to get both upstream and downstream rate for both Sagem Fast 800 & Speedtouch 330 USB Modem.

**for Sagem Fast 800 do this :**

Downstream:
```
cat /sys/bus/usb/drivers/ueagle-atm/1-2\:1.0/stat_dsrate
```
upstream:
```
cat /sys/bus/usb/drivers/ueagle-atm/1-2\:1.0/stat_usrate
```

Note: the values you obtain are in hexadecimal, use any calculator to get decimal value.


**for Speedtouch 330 do this :**

it shows both, upstream & downstream:
```
cat /var/log/kern.log | grep "ADSL line is up"
```


Note: I used ueagle-atm driver for my Sagem Fast 800 and I used speedtouch-ng package for my speedtouch 330.

:)

---

### Post by stuntgp2000 on 2007-04-02
I found another way to get more clear info about downstream/Upstream rate & modem status for Sagem Fast 800:

First, list the content of this directory
```
ls /proc/driver/ueagle-atm/
```

The file name you get after the above command is what we need. for example, we got 001-002

Now, this will show Sagem Fast 800 status:
```
cat /proc/driver/ueagle-atm/001-002 
```

Have a nice day.

---

