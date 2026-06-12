---
title: "wvdial for 2 different arriers?"
date: 2008-04-03
forum: Networking &amp; Wireless
---

### Post by Bittermormon on 2008-04-03
Sorry title should read Multiple Carriers.

I have successfully configured wvdial to work with my nokia n80 via USB with my T-mobile sim in it. My friend had a N95 on ATT (with 3g) that I'd like to use on an upcoming road trip. Right now I have 2 separate wvdial.conf files that I rename depending on which phone I need. Is there any way I can set wvdial.conf to allow for teh 2 different settings?

I gathered from [this great post](http://ubuntuforums.org/showthread.php?t=651852) that the first line could read
```
[Dialer TMo]
``` instead of ```
[Dialer Defaults]
```, but when I try that and type wvdial Tmo it won't connect. Any help would be appreciated.

Here is my wvdial.conf file:
```

[Dialer Defaults]
Init1 = ATZ
Init2 = ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
Init3 = AT+CGDCONT=, ,"wap.voicestream.com"
Modem Type = USB Modem
ISDN = 0
Modem = /dev/ttyACM0
Phone = *99***1#
Username = user
Password = pass
New PPPD = yes
BAUD = 460800
Stupid Mode = 1

```

---

### Post by Bittermormon on 2008-04-03
Why s it that as soon as I post, I figure something out. sorry to waste the space. Here's how I fixed it. Hope this helps someone down the road. I am not sure on the ATT User and PW but I think they are correct. I can confirm this works with Tmobile USA though.

```

[Dialer Defaults]
Init1 = ATZ
Init2 = ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
Modem Type = USB Modem
ISDN = 0
Modem = /dev/ttyACM0
Phone = *99***1#
New PPPD = yes
BAUD = 460800
Stupid Mode = 1

[Dialer TMo]
Init3 = AT+CGDCONT=, ,"wap.voicestream.com"
Username = user
Password = pass

[Dialer ATT]
Init3 = AT+CGDCONT=, ,"wap.cingular"
Username = WAP@CINGULAR.COM
Password = CINGULAR1

```

---

