---
title: "how to connect ot internet using sony ericsson k750i on  linux (ubuntu7.04)"
date: 2007-09-10
forum: Networking &amp; Wireless
---

### Post by yosahaj on 2007-09-10
hi

i've just installed the ubuntu 7.04 on my pc...

i've **sony ericsson k750i **handset with** unlimited gprs acces**...
but i dont know how to** access the internet** on linux....
coz when i'm using windows...i've the** sony ericsson pc suit** which have*** mobile networking wizard***..
using that i used to connect to internet.. But here it seems to dificult coz[U] the sony ericsson pc suit is not
supported to linux so i cant install it on linux...[/U]
so anybody plz tell me how to connect to internet using  sony eri..k750i  on linux....
coz i'm new to linux...i dont have any idea...:confused:
help me out plz..

---

### Post by eee.imtiaz on 2008-05-10
1.Write the following in a text file and save it with name "wvdial.conf".

```
[Modem0]
Modem = /dev/ttyACM0
Baud = 115200
SetVolume = 0
Dial Command = ATDT
Init1 = ATZ
Init3 = ATM0
FlowControl = CRTSCTS
[Dialer gpinternet]
Username = gpinternet
Password = gpinternet
Phone = *99#
Stupid Mode = 1
Init1 = ATZ
Init2 = ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
Init3 = AT+CGDCONT=1,"IP","gpinternet"
Inherits = Modem0
```

2.Now, as a root, copy this file to /etc/

```
sudo -i

%%give your password here%%

cp wvdial.conf /etc/
```

3.Now you can connect to the internet by typing

```
wvdial gpinternet&
```

Note that, the APN 'gpinternet' is for my operator. You must have to change it according to yours. And you might have to change the username and password in the "wvdial.conf" file as well.

There are many ways to connect to the internet using a mobile phone connected to a linux system. I have just mentioned one.. :-)

Thank you.

---

