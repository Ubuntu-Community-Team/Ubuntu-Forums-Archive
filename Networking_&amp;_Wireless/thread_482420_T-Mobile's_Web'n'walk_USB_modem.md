---
title: "T-Mobile's Web'n'walk USB modem"
date: 2007-06-23
forum: Networking &amp; Wireless
---

### Post by Tyrobun on 2007-06-23
Just recently installed Ubuntu 7.04. New to Linux but already reaping the rewards from an open source  society (and of course, the brilliant Ubuntu Forum Community).

I'm thinking of setting up an Ubuntu system for a relative but they cannot get a landline arranged for their property (landlord hassle).  I've just recently seen the Web'n'walk  USB modem on the t-mobile site ([www.t-mobile.co.uk](www.t-mobile.co.uk)). Just wanted to inquire whether anyone has had any experience dealing with it and whether it is advisable to use this modem for desktops (t-mobile Supports Mac and Windopes only).  I have noticed that even if ISP firms do not support Linux, some modems still appear to work fine (the ISP  I was using for Windopes does not support Linux, but is working just fine - Feisty configured it without fuss, hehehe). 

T-Mobile's Web'n'walk USB modem is for Laptops but that shouldn't mean it can't be used on a  desktop?  Any advise would be greatly appreciated.

---

### Post by MrAwesome on 2007-08-21
I also am thinking of using the web'n'walk via either the usb or pcmcia card.

I have tried to use the USB modem with no luck, however the pcmcia card does show signs of life via the lights on the modem, though I am unsure as to how to get my laptop to use that connection as an internet connection.

Does anyone have any simple suggestions as to how to get either going...

I have also seen this website, but it is far too complicated for me to understand. If anyone has an easier way of explaining this website, that would be useful: [http://www.gprsec.hu/modules/news/view.php?id=260](http://www.gprsec.hu/modules/news/view.php?id=260)

---

### Post by davidingram on 2007-12-17
Hi, same here.  I have the PCMCIA T-mobile package.  Modem shows signs of life, but I cant make it connect.  Anyone here able to help?  Anyone else making any progress with this one? :)
D

---

### Post by conch on 2007-12-21
I too would like to know the answer to this question!!

---

### Post by conch on 2007-12-21
Accessing T-Mobile 3G with Huawei USB modem using wvdial
(in part based on benlund.info )

Tested in Feisty

I had to add  the module option to /etc/modprobe.d/blacklist
also check that usb-storage isn't loaded 
disable wireless and other connections

plug in USB modem and check device details in a terminal:
# lsusb

should see amongst other things a line like:
Bus 002 Device 005: ID 12d1:1003

# modprobe usbserial vendor=0x12d1 product=0x1003

check to see the ttyS devices created:

# ls -la /dev/ttyU* 
crw-rw---- 1 root dialout 188, 0 2007-12-21 21:03 /dev/ttyUSB0
crw-rw---- 1 root dialout 188, 1 2007-12-21 21:03 /dev/ttyUSB1
crw-rw---- 1 root dialout 188, 2 2007-12-21 21:03 /dev/ttyUSB2

Add to /etc/wvdial.conf:
[Dialer tmobileusb]
Phone = *99***1#
Username = web
Password = web
Stupid Mode = 1
Dial Command = ATDT
Modem = /dev/ttyUSB0
Baud = 460800
Init2 = ATZ
Init3 = ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
ISDN = 0
Modem Type = Analog Modem
Init5 = AT+CGDCONT=1,"IP","general.t-mobile.uk";

run wvdial:

#wvdial tmobileusb

---

### Post by conch on 2007-12-21
For the T-Mobile PCMCIA datacard:

Using web'n'walk card with TMobile and Linux

My web'n'walk Card Compact II responds to lsusb with:
BUS 007 Device 003: ID 0af0:6701 Option
Card is GTMax 3.6 7.2 ready, "FT"

comgt was downloaded and compiled and installed. For info see here: [http://www.pharscape.org/content/view/46/70/](http://www.pharscape.org/content/view/46/70/)

The usb_modeswitch tool was downloaded, see [http://www.draisberghof.de/usb_modeswitch/](http://www.draisberghof.de/usb_modeswitch/)
It was then compiled and placed in /usr/sbin. Additionally usb_modeswitch.conf was edited for the card and placed in /etc

Files were set up as follows:

=================================================

#/etc/ppp/peers/tmobile
/dev/ttyUSB0
460800
#idle 7200
crtscts
modem
noauth
#maybe comment usepeerdns out
#usepeerdns
defaultroute
noipdefault
debug
noccp
nobsdcomp
novj
user "irrelevant"
password "irrelevant"
connect "/usr/sbin/chat -v -f /etc/chatscripts/tmobile"

===================================================

#etc/chatscripts/tmobile
## This is the chat script used to dial out to your default service provider.
# Please customize the entries enclosed in parenthesis to match your setup.
# Only the "provider" file will be handled by poff and pon (unless with
# extra command line arguments).
#
# Remember to edit /etc/ppp/peers/provider accordingly.
#
# ATZW2 as a default init string
# - On all hayes compatible modems, W2 will correctly report the connect
#   speed.
#
ABORT BUSY
ABORT ERROR
ABORT 'NO CARRIER'
REPORT CONNECT
TIMEOUT 10
"" "ATZ"
OK AT+CGDCONT=1,"IP","general.t-mobile.uk"
OK ATE1
#alternative:
#OK ATD*99***1#
OK ATD*99#
TIMEOUT 30
CONNECT ""

====================================================
# /etc/ppp/resolv.conf
nameserver 149.254.201.126
nameserver 149.254.192.126

====================================================

Connection is made by doing the following:
Close or disable other network connections

Open a root console and
# tail -f /var/log/messages
to see what is happening

Open another root console:

insert the card
# usb_modeswitch
don't worry about the errors
At this point the usbserial and option modules should have been loaded.

The card LED's will flash red and blue together. If they start to flash rapidly you will
have to pull the card and try again.

# comgt reg
Trying list of devices
Waiting for Registration
Registered on Home network: "T-Mobile",2

The 2 indicates a 3G connection when the blue led will give pairs of flashes
A 0 will indicate a GPRS connection when the red led will give pairs of flashes

Optional:
# comgt sig
Trying list of devices
Signal Quality: 10,99
A signal quality beginning with a 2 indicates that the account has been suspended. The blue or red led will give single flashes.

# pon tmobile
# cp /etc/ppp/resolv.conf /etc/resolv.conf

You should be able to browse!

To disconnect:

# poff

---

