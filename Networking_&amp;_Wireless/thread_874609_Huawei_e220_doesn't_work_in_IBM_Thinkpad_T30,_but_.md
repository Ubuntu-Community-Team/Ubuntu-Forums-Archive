---
title: "Huawei e220 doesn't work in IBM Thinkpad T30, but work everywhere else"
date: 2008-07-30
forum: Networking &amp; Wireless
---

### Post by shellhrs on 2008-07-30
I am running Hardy on my Thinkpad T30. Last week I got a Huawei e220 USB modem and have been trying to get it running here with no avail. This is what I did:

Connect the modem to a USB port, then check if the modem was detected by the system:

```
lsusb
```

After making sure the modem was detected, I set the dialing configuration:

```
sudo wvdialconf
```

Then, I edit the resulting file, /etc/wvdial.conf to the following:

> [Dialer Defaults]
Init1 = ATZ
Init2 = ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
Init3 = AT+CGDCONT=1,"ip","internet"
Modem Type = Analog Modem
Baud = 460800
New PPPD = yes
Modem = /dev/ttyUSB0
ISDN = 0
Auto DNS = 1
Stupid mode = 1
Phone = *99#
Username = { }
Password = { }

Then the dialing:

```
wvdial
```

I got the usual dialing log, including the IP and DNS address, but when I run Firefox, I couldn't connect to any website. I tried pinging anywhere, but still no connection.

I tried the above method in two other box (a Compaq Presario 2500 laptop, and an old desktop), and they can access the internet without any problem.

Can anyone help me get this modem working in my IBM?

---

