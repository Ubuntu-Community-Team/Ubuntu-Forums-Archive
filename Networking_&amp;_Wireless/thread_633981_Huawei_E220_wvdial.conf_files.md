---
title: "Huawei E220 wvdial.conf files"
date: 2007-12-07
forum: Networking &amp; Wireless
---

### Post by daka on 2007-12-07
This thread is set up to offer one location for all of the wvdial.conf files from different countries and providers.  If you want to add your wvdial.conf file to make it available to others just send it to me in a private message.. I will cut-paste and edit this thread.  Please offer the same information that you see here: 
[U]
COUNTRY /  PROVIDER / DISTRO /  YOUR FORUM NAME[/U]

SPAIN - VODAFONE - GUTSY / Mint Daryna - wvdial.conf (daka)

[Dialer hsdpa]
Phone = *99***1#
Username = vodafone
Password = vodafone
Stupid Mode = 1
Dial Command = ATDT
Modem = /dev/ttyUSB0
Baud = 460800
Init2 = ATZ
Init3 = ATE0V1&D2&C1S0=0+IFC=2,2
ISDN = 0
Modem Type = Analog Modem
Init5 = AT+CGDCONT=1,"IP","ac.vodafone.es";
_______________________________________
UK - TMOBILE - DEBIAN - wvdial.conf (dragon2611)

[Dialer pin]
Modem = /dev/ttyUSB0
Baud = 460800
Init1 =AT+Cpin=12345

[Dialer tmob]
Modem = /dev/ttyUSB0
Baud = 460800
Init2 =AT
Init3 = AT&FE0V1X1&D2&C1S0=0
ISDN = 0
Modem Type = Analog Modem
Phone = *99***1#
Username = username
_________________________________________
PORTUGAL- VODAFONE - GUTSY wvdial.conf (mizwete)

[Dialer hsdpa]
Phone = *99***1#
Username = vodafone
Password = vodafone
Stupid Mode = 1
Dial Command = ATDT
Modem = /dev/ttyUSB0
Baud = 460800
Init2 = ATZ
Init3 = ATE0V1&D2&C1S0=0+IFC=2,2
ISDN = 0
Modem Type = Analog Modem
Init5 =AT+CGDCONT=1,"IP","internet.vodafone.pt";
______________________________________________________

UK Vodafone Gutsy wvdial.conf  (Viking777)

[Dialer Defaults]
Phone = *99***16#
Username = web
Password = web
Stupid Mode = 1
Dial Command = ATDT
Auto DNS = 0
Modem = /dev/ttyUSB0

[Dialer huawei]
Buad = 460800
Init2 = ATZ
Init3 = ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
Init4 = at+cops=3,2
INIT8 = AT+CGDCONT=1,"IP","internet"
ISDN = 0
Modem Type = Analog Modem

______________________________________________________

UK -  TMobile  -  GUTSY   -    wvdial.conf file  - (Helliewm)


[Dialer pin]
Modem = /dev/ttyUSB0
Baud = 460800
Init1 =AT+Cpin=12345


[Dialer tmob]
Modem = /dev/ttyUSB0
Baud = 460800
Init2 =AT
Init3 = AT&FE0V1X1&D2&C1S0=0
ISDN = 0
Modem Type = Analog Modem
Phone = *99***1#
Username = username
Password = password
Stupid Mode = 1
Dial Command = ATDT
__________________________________________
COUNTRY / PROVIDER / DISTRO / YOUR FORUM NAME
Australia - Three - Gutsy, wvdial.conf - (ellyaht)

[Dialer 3g]

Init2 = ATZ
Init3 = ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
Stupid Mode = 1
Modem Type = Analog Modem
ISDN = 0
Phone = *99#
Modem = /dev/ttyUSB0
username = username
Password = password
Dial Command = ATDT
Baud =466600
Init4 = AT+CGDCONT=1,"IP","3netaccess"
-----------------------------------------

Egypt - VODAFONE - GUTSY - wvdial.conf (mostafaberg)

[Dialer Defaults]
Phone = *99***1#
Username = internet
Password = internet
Stupid Mode = 1
Dial Command = ATDT
Modem = /dev/ttyUSB0
Baud = 460800
Init2 = ATZ
Init3 = ATE0V1&D2&C1S0=0+IFC=2,2
ISDN = 0
Modem Type = Analog Modem
Init5 = AT+CGDCONT=1,"IP","internet.vodafone.net";
__________________
Mostafa Berg
[http://www.mostafaberg.com](http://www.mostafaberg.com) 
_________________________________________________________

---

### Post by brutc001 on 2008-05-21
Australia - Vodafone - Hardy - wvdial.config

[Dialer 3g]

Init2 = ATZ
Init3 = ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
Stupid Mode = 1
Modem Type = Analog Modem
ISDN = 0
Phone = *99#
Modem = /dev/ttyUSB0
username = username
Password = password
Dial Command = ATDT
Baud =460800
Init4 = AT+CGDCONT=1,"IP","vfinternet.au"
----------------------------------------------------------------

---

### Post by practicalweb on 2008-05-25
UK / [www.three.co.uk](www.three.co.uk) / ubuntu 8.04, Hardy Heron / practicalweb

[Dialer defaults]
Modem = /dev/ttyUSB1


[Dialer three]

Init2 = ATZ
Init3 = ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
Stupid Mode = 1
Modem Type = Analog Modem
ISDN = 0
Phone = *99\#
Modem = /dev/ttyUSB0
username = username
Password = password
Dial Command = ATDT
Baud =466600
Init4 = AT+CGDCONT=1,"IP","three.co.uk"

---

### Post by WillemToerien on 2008-05-25
South Africa - Vodacom

[Dialer hsdpa]
Phone = *99***16#
Username = vodafone
Password = vodafone
Stupid Mode = 1
Dial Command = ATDT
Modem = /dev/ttyUSB0
Baud = 460800
Init2 = ATZ
Init3 = ATE0V1&D2&C1S0=0+IFC=2,2
ISDN = 0
Modem Type = Analog Modem
Init5 = AT+CGDCONT=1,"IP","internet";

---

### Post by csrster on 2008-05-27
TDC Broadband-2-Go (Denmark), Huawei e220, Gutsy
I had to some usb sniffing under windows to get some of these parameters,
but they seem to work:

[Dialer pin]
Init1 = AT+CPIN=<<your sim pin here>>

[Dialer Defaults]
Init1 = ATZ
Init2 = ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
Abort on No Dialtone = off
Password = tdc
Check Def Route = on
Phone = *99***16#
Modem Type = Analog Modem
Stupid Mode = 1
SetVolume = 0
Baud = 460800
Dial Command = ATDT
Dial Attempts = 3
Modem = /dev/ttyUSB0
ISDN = 0
Username = tdc

[Dialer connect]
Init2 = ATZ
Init3 = ATQ0 V1 E0 S0=0 &C1 &D2 +FCLASS=0
Init4 = AT+CGDCONT=16,"IP","internet"
ISDN = 0
Modem = /dev/ttyUSB0
Modem Type = Analog Modem
Baud = 460800

---

### Post by csrster on 2008-05-27
> **csrster said:**
> TDC Broadband-2-Go (Denmark), Huawei e220, Gutsy
I had to some usb sniffing under windows to get some of these parameters,
but they seem to work:

[Dialer pin]
Init1 = AT+CPIN=<<your sim pin here>>

[Dialer Defaults]
Init1 = ATZ
Init2 = ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
Abort on No Dialtone = off
Password = tdc
Check Def Route = on
Phone = *99***16#
Modem Type = Analog Modem
Stupid Mode = 1
SetVolume = 0
Baud = 460800
Dial Command = ATDT
Dial Attempts = 3
Modem = /dev/ttyUSB0
ISDN = 0
Username = tdc

[Dialer connect]
Init2 = ATZ
Init3 = ATQ0 V1 E0 S0=0 &C1 &D2 +FCLASS=0
Init4 = AT+CGDCONT=16,"IP","internet"
ISDN = 0
Modem = /dev/ttyUSB0
Modem Type = Analog Modem
Baud = 460800

Well, they don't seem to work now :-(
However I manged to get connected with the latest (beta) version of this software
[https://forge.vodafonebetavine.net/projects/vodafonemobilec/](https://forge.vodafonebetavine.net/projects/vodafonemobilec/)
and a profile with:

username: tdc
password: tdc (I think these are ignores)
Preferred Connection: 3G preferred
Authenitcation mode: default
APN host: internet

(and dynamic DNS)

---

### Post by tigerplug on 2008-05-27
I've been using a Huawei E220 for a good while now on Vista (Dual Boot) because I can't get it to work with Hardy.

Can anyone point me in the right direction?
I also need configuration information/files for O2 Ireland.


Any help appreciated!

---

### Post by Tche² on 2008-06-26
Hey

for vodafone Ireland HSPDA, use this wvdial.conf... I also added the Eircom one, just in case your 3G was weak.

Good luck :-) 
Tche²

[Dialer hsdpa]

Phone = *99#

Username = vodafone

Password = vodafone

Stupid Mode = 1

Dial Command = ATDT

Modem = /dev/ttyUSB0

Baud = 460800

Init2 = ATZ

Init3 = ATE0V1&D2&C1S0=0+IFC=2,2

ISDN = 0

Modem Type = Analog Modem

Init5 =AT+CGDCONT=1,"IP","hs.vodafone.ie";


[Dialer Defaults]
Phone = 1892150150
Username = eircom
Password = eircom
New PPPD = yes

---

### Post by __iso__ on 2008-07-19
Sweden - Telia - Arch - wvdial.conf (__iso__)

[Dialer telia]
Init2 = ATZ
Init3 = ATE0V1&D2&C1S0=0+IFC=2,2
Stupid Mode = 1
Modem TYPE = Analog Modem
ISDN = 0
Phone = *99#
Init5 = AT+CGDCONT=1,"IP","online.telia.se";
Modem = /dev/ttyUSB0
username = 3G
Dial Command = ATDT
password = 3G
Baud = 460800



Sweden - Tele2 - Arch - wvdial.conf (__iso__)

[Dialer Tele2]
Init2 = ATZ
Init3 = ATE0V1&D2&C1S0=0+IFC=2,2
Stupid Mode = 1
Modem TYPE = Analog Modem
ISDN = 0
Phone = *99#
Init5 = AT+CGDCONT=1,"IP","internet.tele2.se";
Modem = /dev/ttyUSB0
username = username
Dial Command = ATDT
password = password
Baud = 460800

---

### Post by Tech Eddie on 2008-07-19
Denmark file: /etc/wvdial.conf 
Hardy 8.04


Denmark TDC     Tech Eddie:

[Dialer hsdpa]
Phone = *99#
Username = irrelevant
Password = irrelevant
Stupid Mode = 1
Dial Command = ATDT
Modem = /dev/ttyUSB0
Baud = 460800
Init2 = ATZ
Init3 = ATE0V1&D2&C1S0=0+IFC=2,2
ISDN = 0
Modem Type = Analog Modem
Init5 =AT+CGDCONT=1,"IP","internet";

[Dialer pin]
Init1 = AT+CPIN=****

Denmark M1      Tech Eddie:

[Dialer hsdpa]
Phone = *99#
Username = irrelevant
Password = irrelevant
Stupid Mode = 1
Dial Command = ATDT
Modem = /dev/ttyUSB0
Baud = 460800
Init2 = ATZ
Init3 = ATE0V1&D2&C1S0=0+IFC=2,2
ISDN = 0
Modem Type = Analog Modem
Init5 =AT+CGDCONT=1,"IP","internet";

[Dialer pin]
Init1 = AT+CPIN=****

Denmark 3      Tech Eddie:

[Dialer hsdpa]
Phone = *99***1#
Username = irrelevant
Password = irrelevant
Stupid Mode = 1
Dial Command = ATDT
Modem = /dev/ttyUSB0
Baud = 460800
Init2 = ATZ
Init3 = ATE0V1&D2&C1S0=0+IFC=2,2
ISDN = 0
Modem Type = Analog Modem
Init5 =AT+CGDCONT=1,"IP","data.3.dk";

[Dialer pin]
Init1 = AT+CPIN=****

Denmark 3 (If above wvdial.conf not work) Tech Eddie:

[Dialer hsdpa]
Phone = *99#
Username = irrelevant
Password = irrelevant
Stupid Mode = 1
Dial Command = ATDT
Modem = /dev/ttyUSB0
Baud = 460800
Init2 = ATZ
Init3 = ATE0V1&D2&C1S0=0+IFC=2,2
ISDN = 0
Modem Type = Analog Modem
Init5 = AT+CGDCONT=1,"IP","data.3.dk"

[Dialer pin]
Init1 = AT+CPIN=****

What you must know:

**** = your pin number

To connect to internet:

You can start E220 by typing:
sudo wvdial hsdpa
in Terimnal.

Start your internet browser. 

If need pin, type in Terminal:

sudo wvdial pin
then type:
sudo wvdial hsdpa

Start your internet browser.

---

