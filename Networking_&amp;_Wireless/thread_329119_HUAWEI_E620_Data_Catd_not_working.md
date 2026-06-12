---
title: "HUAWEI E620 Data Catd not working"
date: 2007-01-01
forum: Networking &amp; Wireless
---

### Post by willeb on 2007-01-01
I ran wvdial and got the following:

wvdail: internet dialer version 1.55
Cannot get information for serial port
Initiallize modem
sending : ATZ
ATZ
OK
Sending: ATQ0 V1 E1 SO=0 &C1 &D2
ATQ0 V1 SO=0 &C1 &D1
OK
Modem initialized
Configuration does not specify a valid phone number
Configuration does not specify a valid login name
Configuratio does not specify a valid password

I cannof find the wvdial.conf file/info

what can i do to get this card working and picked up by the network setup

thks
willie

---

### Post by Hellhound on 2007-01-01
here is my /etc/wvdial.conf  file ..... either edit it or use just as is ..... to connect, 
use 
  wvdial hsdpa internet


note that you might have to change some of the strings to suit your specific ISP..... it works locally for both MTN and Vodacom

Hendrik

# wvdial for Vodacom Data. Created by Tazz_tux
# Version 1.0

# Change Log:
#
# Added support for HSDPA.
# Added Headers and version control.

[Dialer Defaults]

Phone = *99***1#
Username = username
Password = password
Stupid Mode = 1
Dial Command = ATDT

[Dialer pin]

Init1 = AT+CPIN=1234

[Dialer novatel]
Modem = /dev/ttyS1
Baud = 460800
Init2 = ATZ
Init3 = ATE0V1&D2&C1S0=0+IFC=2,2
ISDN = 0
Modem Type = Analog Modem

[Dialer option]

Modem = /dev/tts/USB0
Baud = 460800
Init2 = ATZ
Init3 = ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
ISDN = 0
Modem Type = Analog Modem

[Dialer hsdpa]


Modem = /dev/ttyUSB0
Baud = 460800
Init2 = ATZ
Init3 = ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
ISDN = 0
Modem Type = Analog Modem

[Dialer e1000]

Modem = /dev/usb/acm/0
Baud = 460800
Init2 = ATZ
Init3 = ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
ISDN = 0
Modem Type = Analog Modem

[Dialer onboard]

Modem = /dev/ttySHSF0
Baud = 460800
Init2 = ATZ
Init3 = ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
ISDN = 0
Modem Type = Analog Modem

[Dialer 2gonly]

Init4 = AT+COPS=0,0,"Vodacom-SA",0

[Dialer 3gonly]

Init4 = AT+COPS=0,0,"Vodacom-SA",2

[Dialer internet]

Init5 = AT+CGDCONT=1,"IP","internet";

[Dialer internetvpn]

Init5 = AT+CGDCONT=1,"IP","internetvpn";

[Dialer myapn]

Init5 = AT+CGDCONT=1,"IP","myapn"

[Dialer 384k]

Init6 = AT+CGEQMIN=1,4,64,384,64,384
Init7 = AT+CGEQREQ=1,4,64,384,64,384

[Dialer 144k]

Init6 = AT+CGEQMIN=1,4,64,144,64,144
Init7 = AT+CGEQREQ=1,4,64,144,64,144

[Dialer 64k]

Init6 = AT+CGEQMIN=1,4,64,64,64,64
Init7 = AT+CGEQREQ=1,4,64,64,64,64

---

### Post by Hellhound on 2007-01-03
u should have at least nano installed .... sudo nano /etc/wvdial.conf

I leeched this file from another forum and it worked for me ..... but you say you get the following error now :

--> Sending: ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
ERROR

makes me wonder if your computer doesn't enumerate the Huawei data card as another USB device. Remeber the PCMCIA card is seen as a USB device 
Modem = /dev/ttyUSB0

There should be a way to list the devices on USB, but being a beginner, i don't know the command to see what device i would say ls /dev/ttyUSB* and edit wvconf and try each one of the devices ... there should be an easier way

Hendrik

---

### Post by mozzi on 2007-04-13
Yeah there is :) 
sudo lsusb
sudo dmesg
sudo cat /proc/bus/usb/devices

Also go have a look @ /var/log/messages

Mozzi

---

