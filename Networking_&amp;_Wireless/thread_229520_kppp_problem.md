---
title: "kppp problem"
date: 2006-08-04
forum: Networking &amp; Wireless
---

### Post by nishoba on 2006-08-04
im using kubuntu and my modem works fine
i normaly connect to net with wvdial

conf file of wvdial:
```
[Dialer Defaults]
Modem = /dev/ttySL0
Baud = 115200
Init1 = ATZ
Init2 = ATQ V1 E1 S0=0 &C1 &D2 +FCLASS=0 X3
Carrier Check = no
ISDN = 0
Modem Type = Analog Modem

[Dialer cmu]
Phone = "phone nummber"
Username = "username"
Password = "pass"
```

but when i try to connect with kppp connection fails with error 1
log:
```
Aug  4 19:38:50 nish-lap pppd[5828]: The remote system is required to authenticate itself
Aug  4 19:38:50 nish-lap pppd[5828]: but I couldn't find any suitable secret (password) for it to use to do so.
Aug  4 19:38:50 nish-lap pppd[5828]: (None of the available passwords would let it use an IP address.)

```

i have used live-cd mepis and kppp works there perfectly with the same configuration(except i didnt have to install slmodemdemon there because my winmodem was recognized)

what should i do?
thx

---

### Post by Cariboo1938 on 2006-08-08
> **nishoba said:**
>  
 
log:
```
Aug  4 19:38:50 nish-lap pppd[5828]: The remote system is required to authenticate itself
Aug  4 19:38:50 nish-lap pppd[5828]: but I couldn't find any suitable secret (password) for it to use to do so.
Aug  4 19:38:50 nish-lap pppd[5828]: (None of the available passwords would let it use an IP address.)

``` 

what should i do?
thxGo to /etc/ppp/peers and edit the file "kppp-options". Activate the line [COLOR="Blue"]#noauth[/COLOR] by removing the comment # sign.

---

