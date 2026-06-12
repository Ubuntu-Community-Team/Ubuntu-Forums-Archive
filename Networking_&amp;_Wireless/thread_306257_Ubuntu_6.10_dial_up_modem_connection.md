---
title: "Ubuntu 6.10 dial up modem connection"
date: 2006-11-24
forum: Networking &amp; Wireless
---

### Post by surfzombie on 2006-11-24
Hi, 
    I am new to Linux and Ubuntu.  I can connect to the internet with my modem using version 6.06 no problem.  I just got version 6.10 and try to set up my modem and it is different the in 6.06.  It doesn't autodetect my modem and it doesn't have an activate and deactivate buttons like in 6.06.  How do I activate and deactivate my connection?  My modem is a serial BEst Data 56k modem.  It works fine with 6.06.:confused:

---

### Post by ReaderRat on 2006-11-24
[**Modem HowTo**](https://help.ubuntu.com/community/DialupModemHowto)

---

### Post by ggiulion on 2006-12-11
Hi,
I had the same problem that I solved in the following way.

I switched from the network administrator to the command line starting the connection with the pon command.

To do this you need to write or modify two files that are in
/etc/ppp/peers/ 
/etc/chatscripts/

the file already present should be
/etc/ppp/peers/ppp0 
/etc/chatscripts/ppp0

and

/etc/ppp/peers/provider 
/etc/chatscripts/provider

you can modify one of this or write a new one.

I modified the ppp0

now they look as follow

/etc/ppp/peers/ppp0:

*****************************************************

connect "/usr/sbin/chat -v -f /etc/chatscripts/ppp0"

usepeerdns

noauth

defaultroute

/dev/insert your modem device
user "telecom"
115200 

******************************************************

/etc/chatscripts/ppp0:

******************************************************
TIMEOUT 60 
ABORT ERROR 
ABORT BUSY 
ABORT VOICE 
ABORT "NO CARRIER" 
ABORT "NO DIALTONE" 
ABORT "NO DIAL TONE" 
ABORT "NO ANSWER" 
"" "ATZ" 
"" "ATM1M0" 
OK-AT-OK "ATDTW insert here your provider's phone number" 
TIMEOUT 75
CONNECT

*******************************************************

once adapted these files I run

pon ppp0

on the command line and the pc start dialing.

Hope this can help you

regards

---

