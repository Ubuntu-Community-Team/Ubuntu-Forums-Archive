---
title: "Cant connect to internet using pon"
date: 2005-05-02
forum: Networking &amp; Wireless
---

### Post by ntlnsideidiotoutside on 2005-05-02
Hi noob here
cant connect to internet, i configure a connection using pppconfig.
when i try to connect by typing pon in the minicommader i can hear the modem but it does not dial out. are there other ways to connect using a modem,other than pon.



thank you
usig ubuntu 5.04
 ](*,)

---

### Post by jodef on 2005-05-02
The syntax for the command would be : **sudo pon nameofconnection** so for eg if you call your connection tset then do sudo pon tset. If it still doesn't connect you can look at some other settings : DNS etc.

Alternatively you could try : **sudo wvdial** ; wvdial is an alternate dialer.

---

### Post by Professor X on 2005-05-02
I use wvdial to connect and recommend it.  You should first run ```
sudo wvdialconf /etc/wvdial.conf
```.  Then edit the file /etc/wvdial.conf so it contains your username/password/ISP number.  Finally connnect using ```
sudo wvdial
```

---

### Post by ntlnsideidiotoutside on 2005-05-03
ok i tried wvdial, the modem dials the number and dies right after.

heres my wvdial.conf

modem=/dev/modem
baud=115200
INIT1=ATZ
INIT2=ATQ0 VI E1 S0=0 & CI & D2+FCLASS=0
ISDN=0
MODEM TYPE=ANALOG
PHONE ********
USERNAME ********
PASSWORD ********


where do i place the nameservers and chap authentication? i tried to look for wvdial examples but had no luck.

 at this point i really like ubuntu after trying like six or seven other distros but i always run into problems trying to connect to the internet. :???: 

thanks

---

### Post by Professor X on 2005-05-03
Place your nameservers in the file /etc/resolv.conf.  It sounds like there might be an issue with your ISP.  What error does wvdial give after the connection dies?  Does your ISP use a nonstandard authentication protocol?

---

### Post by ntlnsideidiotoutside on 2005-05-04
thanx professor x for the help but i still have the same problem.
it gives me error 10, ppp could not find any protocol. btw this is a zoom hardware pcmcia modem, i used it before with sh** mandrake. i also have a ethernet card, not configured, and a wireless card that ubuntu doesn't recognize.

i really like this distro but i'm about to give up  ](*,)

---

### Post by Professor X on 2005-05-04
Add the line 'Stupid Mode = 1' to your /etc/wvdial.conf.

Good luck.

---

