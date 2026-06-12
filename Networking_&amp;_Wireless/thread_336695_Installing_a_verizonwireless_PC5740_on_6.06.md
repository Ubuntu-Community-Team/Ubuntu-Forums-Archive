---
title: "Installing a verizonwireless PC5740 on 6.06"
date: 2007-01-11
forum: Networking &amp; Wireless
---

### Post by loxety on 2007-01-11
-----------------------------------------------
First off the links that helped me:

[http://kenkinder.com/evdo-pc5740/](http://kenkinder.com/evdo-pc5740/)
Site has main scripts and most relevent info to get this working asap

[http://www.evdoforums.com/viewtopic.php?p=6180](http://www.evdoforums.com/viewtopic.php?p=6180)
Some experimental ideas once you get it going after using info on kenkinder.com
-----------------------------------------------

The following are changes from the instructions that are found on the kenkinder site

/etc/ppp/peers/1xevdo_chat - modified a few places I thought had errors in the AT commands and made things more simple

# AT$QCMIPGETP  "login" name used for MobileIP, which usually matches your MIN.
# AT+GSN        ESN in hex
# AT+GMR        firmware revision and build date.
# AT+CSQ        first number indicates the signal strength above -109 dBm (in
#               2 dBm increments).  A value of 7 or higher (-95 dBm) can be
#               considered adequate. 31 is the max.  (Possible values in
#               Audiovox PC5740 are 0, 7, 15, 23, 31.)
# AT+CDV=*22899 Update PRL.  at+cdv=*22899 | OK | Lost carrier.
ABORT 'NO CARRIER' ABORT ERROR ABORT 'NO DIALTONE' ABORT BUSY ABORT 'NO ANSWER'
#'ATTEV1&F;&D2;&C1;&C2S0;=0S7=60'
#'OK-ATTEV1&F;&D2;&C1;&C2S0;=0S7=60-OK-ATTEV1&F;&D2;&C1;&C2S0;=0S7=60-OK' 'AT+CSQ;D#777'
'' 'ATZ'
'OK' 'ATD#777'
TIMEOUT 70
#'CONNECT-AT+CSQ;ATDT#777-CONNECT'
'CONNECT'

Created a bash script to automate the initialization of the card and start the connection:

#!/bin/bash
/sbin/modprobe ohci-hcd
/sbin/modprobe usbserial vendor=0x106c product=0x3701
/usr/sbin/pppd call 1xevdo
/usr/bin/tail -f /var/log/messages



I used a DELL Inspiron 5160 with ubuntu 6.06lts (2.6.15-27-386), and verizon 5740 wireless card.  Am seeing about 22KB down and 14KB up.  Hope to get the speed up as I get the usb and cdc-acm patched.  Good luck!

---

