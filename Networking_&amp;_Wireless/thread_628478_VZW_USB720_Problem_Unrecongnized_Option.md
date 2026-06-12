---
title: "VZW USB720 Problem: Unrecongnized Option"
date: 2007-12-01
forum: Networking &amp; Wireless
---

### Post by egraves7 on 2007-12-01
Hello all. I am trying to connect to the internet with my USB720 modem. I followed these instructions to get the modem to work:
> 

/etc/modprobe.d/options

add the folowing text and save:
# Options for u720
options usbserial vendor=0x1410 product=0x2110
options airprime endpoints=1


/etc/modules

add the folowing text and save:
usbserial
airprime


/etc/ppp/peers/verizon

add the folowing text and save:
noauth
connect “/usr/sbin/chat -v -f /etc/ppp/peers/verizon_chat”
defaultroute
usepeerdns
ttyUSB0
230400
local
debug
-detach

/etc/ppp/peers/verizon_chat

‘’ ‘ATZ’
‘OK’ ‘ATDT#777'
‘CONNECT’ ‘’

sudo pppd call verizon

However, when I use that sudo command, I get a message that says "pppd: In file /etc/ppp/peers/verizon: unrecognized option 'ttyUSB0' " Does anyone know how to rectify this problem? I am quite n00bish here, so I appreciate any help you can give. Thanks!

---

