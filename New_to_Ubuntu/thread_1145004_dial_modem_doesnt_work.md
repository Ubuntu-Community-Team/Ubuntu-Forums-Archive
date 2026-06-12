---
title: "dial modem doesnt work"
date: 2009-05-01
forum: New to Ubuntu
---

### Post by freeburn on 2009-05-01
i'm using ubuntu 8.04LTS, i have'nt able to configure my dial up modem in ubuntu. 

i've done the following,but it didnt work,

[B]lsusb

sudo modprobe usbserial vendor=0x05c2 product=0x3197

sudo wvdialconf

sudo gedit /etc/wvdial.conf

[/B]here i changed the login name,password,and dial number.
but when i call [B]
wvdial

[/B]it gives me a message that the name,password and dial numbers are invalid.

i also tried a manual configuration,but it didnt work either. and the file /dev/ttyUSB0 is not on the list in the port adress. i manually typed it.what should i do?

another thing it does initiate my modem .

---

### Post by lkraemer on 2009-05-01
When wvdial finds your modem your /etc/wvdial.conf
should look something like this:
Your /dev/.... listing will be different along with
dialed number, login, password.
```

[Dialer Defaults]
Init1 = ATZ
Init2 = ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
Modem Type = USB Modem
Baud = 115200
New PPPD = yes
Stupid Mode = yes
Modem = /dev/ttyACM0
ISDN = 0
Phone = 5833855
Password = yourpassword
Username = login_name@isp.net

```

You might want to double check what is in pap-secrets
and chap-secrets in the /etc/ppp subdirectory.

These files should contain:

[email]login_name@isp.net[/email] * yourpassword

Then wvdial should work correctly.  Once wvdial works, just setup
Gnome-PPP.

If you're trying to use a winmodem, then you need to go to:
[www.linmodems.org](www.linmodems.org) and download their script and execute it,
then post on their forum the listing that is generated.
Those folks can help you a lot.

lkraemer

---

