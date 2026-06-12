---
title: "[SOLVED] BluetoothDialup-VZW EVDOphone

BluetoothDialup for Verizon Wireless EVDO c"
date: 2008-01-27
forum: Networking &amp; Wireless
---

### Post by s1m0n13 on 2008-01-27
I'm trying to use my Verizon Wireless Motorola Q as a broadbrand modem via bluetooth.  I've followed the ubuntu dialup guide ([https://help.ubuntu.com/community/BluetoothDialup](https://help.ubuntu.com/community/BluetoothDialup)) but seem to be getting hung up with my /etc/chatscripts/BluetoothDialup file.  Specifically, I don't know what to set for my APN.  Everything I've read about Verizon Wireless says that you don't need to specify an APN. However, when I leave it out I receive a 'connect script failed' error in syslog. Anyone know how to modify this file accordingly for Verizon Wireless?

This is what my /etc/charscripts/BluetoothDialup file looks like.  I've been experimenting w/ supplying different parameters where it says "your-apn-here". 

TIMEOUT 35
ECHO    ON
ABORT   '\nBUSY\r'
ABORT   '\nERROR\r'
ABORT   '\nNO ANSWER\r'
ABORT   '\nNO CARRIER\r'
ABORT   '\nNO DIALTONE\r'
ABORT   '\nRINGING\r\n\r\nRINGING\r'
''      \rAT
OK      'AT+CGDCONT=2,"IP","your-apn-here"'
OK      ATD*99***1#
CONNECT ""

---

### Post by s1m0n13 on 2008-01-28
Just realized that the /etc/charscripts/BluetoothDialup file ref'd in this article was generic and that the specific file for each carrier is listed further down in the article.

---

