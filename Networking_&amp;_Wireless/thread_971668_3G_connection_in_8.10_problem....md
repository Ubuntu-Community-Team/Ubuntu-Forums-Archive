---
title: "3G connection in 8.10 problem..."
date: 2008-11-05
forum: Networking &amp; Wireless
---

### Post by blackcoatman on 2008-11-05
Hello there...

I have been using Network Manager 0.7 in alpha versions of Ubuntu 8.10. My 3G usb stick modem (huawei E172) was working quite well with it.

When I did a clean install of the final Ubuntu 8.10, i can't connect at all. The "auto gsm connection" in Network Manager is gone (which used to work out-of-the-box in the alpha-beta versions of 8.10). The device is, nevertheless, recognised, I get to choose my provider and a new GSM connection is added, but it fails to connect a second after I choose to do so. I don't know what to do, i've tweaked the connection settings, used another usb port, still can't connect. I have no other means of using the internet in Linux but my 3G usb stick... (boo huu :P)

Any ideas...? :/

---

### Post by pvanonselen on 2008-11-24
After upgrading to Ubuntu 8.10 I also had problems connecting with 3G.

I found a workaround by using wvdial ( install via apt-get)

My problem was related to my PIN on my 3G modem.


Use wvdialconf file to automatically configure 

The configuration is in /etc/wvdial.conf and can be customized there if neede.  Here is my example

```
[Dialer vodafone]
Init1 = ATZ
; Init3 = ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
Stupid Mode = 1
Modem Type = Analog Modem
ISDN = 0
New PPPD = yes
; Dial Command = ATDT
Phone = *99***16#
Modem = /dev/ttyUSB0
Username = vodafone
Password = vodafone
Baud = 9600

[Dialer pin]
Phone = *99***16#
;  Next line is your PIN on the modem
Init3 = ATQ0 +CPIN=4456
Modem = /dev/ttyUSB0
Username = vodafone
Password = vodafone

[Dialer Defaults]
Init1 = ATZ
Init2 = ATQ0 V1 E1 S0=0 &C1 &D2
Modem Type = Analog Modem
ISDN = 0
Modem = /dev/ttyUSB0
Init333 = ATQ0 V1 E1 S0=0 &C1 &D2
Baud = 9600

```

To run i usually do 
```
sudo wvdial pin
``` 

to set the pin and then

```
sudo wvdial vodafone
``` 

to connect.

Works pretty well for me.

After running the first wvdial to set the pin I can use the Network manager to connect as well.

---

