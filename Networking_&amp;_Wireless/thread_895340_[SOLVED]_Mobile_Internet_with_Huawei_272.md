---
title: "[SOLVED] Mobile Internet with Huawei 272"
date: 2008-08-20
forum: Networking &amp; Wireless
---

### Post by Incie83 on 2008-08-20
Hi,

Having just installed eeebuntu 1.0 (which is basically Hardy Heron) on my EeePC 1000, I would like to make use of mobile broadband so I can work outside/on the train/in the pub/etc...

I've got a Huawei 272 USB modem (Vodafone UK), and have been trying to use the [betavine drivers]("http://www.betavine.net/bvportal/web/linux_drivers") to connect to my provider.

At the moment, I get stuck after installing the drivers and the vodafone connect GUI, and running it to get to a screen which lists the Huawei 272 as a 'Known Device'. Then, after clicking 'OK' to this, I get a pop-up saying the software can't connect to my device. Can anybody help me out?

I aim to keep updating this thread until I get it working, because there's hardly any information on the Huawei 272 and linux on the net.

Thanks in advance.

PS: The modem works out of the box with Windows XP and the pre-installed EeePC Xandros OS.

---

### Post by Incie83 on 2008-08-21
Well, that was easy:

I just went to [this website]("http://polishlinux.org/linux/ubuntu/three-uk-3g-modem-in-ubuntu-linux/"), followed the instructions on wvdial and 'BANG' - a connection.

These is my /etc/wvdial.conf:

```

[Dialer Defaults]
Auto DNS = 0
Init1 = ATZ
Init2 = ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
Stupid Mode = 1
Modem Type = Analog Modem
ISDN = 0
Phone = *99***16#
Modem = /dev/ttyUSB0
Username = web
Dial Command = ATDT
Password = web
Baud = 9600

[Dialer huawei]
Init2 = ATZ
Init3 = ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
Init4 = at+cops=3,2
ISDN = 0
Buad = 460800
INIT8 = AT+CGDCONT=1,"IP","internet"
Modem Type = Analog Modem
```

Note: Apparently there's some issues around hooking up the modem to the laptop whilst switched on (I did it before booting up), but I haven't tested that.

---

### Post by Incie83 on 2008-08-21
I've managed to solve that post-boot mounting issue as well, using [these instructions]("http://www.tohack.eu/show_45_VodafoneInternetKeysottoLinux.html"). They're in Italian but quite easy to follow. You could also try [Google's translated version]("http://translate.google.com/translate?hl=en&sl=it&u=http://www.tohack.eu/show_45_VodafoneInternetKeysottoLinux.html&sa=X&oi=translate&resnum=3&ct=result&prev=/search%3Fq%3Dhuawei%2Be272%2Bhack%2Byour%2Blife%26hl%3Den%26client%3Dfirefox-a%26rls%3Dorg.mozilla:en-GB:official%26hs%3DFyU%26sa%3DG") of this page.

Please be patient when you go from plug to connect (wvdial) as it might take the modem about 10-15 seconds to be mounted properly.

I'm planning to write a simple script to be executed upon mount so it auto-connects. In my opinion this beats the bloated vodafone GUI (no I'm not a linux purist; I just don't like useless apps occupying space on my tiny 10 inch screen).

---

