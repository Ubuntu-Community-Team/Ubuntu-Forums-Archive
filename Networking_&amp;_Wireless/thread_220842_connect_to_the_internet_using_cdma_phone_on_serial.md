---
title: "connect to the internet using cdma phone on serial port"
date: 2006-07-22
forum: Networking &amp; Wireless
---

### Post by akay56 on 2006-07-22
Hi

i am running ubuntu breezy on an IBM T20. the lucent winmodem works fine and everything else too. I have a CDMA phone (ZTE Model WP805). It connects to any PC using the serial port. I can use this phone to connect to the internet from any windows environment - the steps are as follows:

1. Install the phone from Phone&Modem options of the control panel as a Standard 28800 bps modem on port COM 1.
2. on the newly created modem select the maximum speed as 115200. In the advanced area add the following extra settings:  "at+fclass=0;at+crm=2;qcmdr=3" and finally disable flow control
3. create a new dialup connection using the above installed modem. dialup number is "#777" and fill in the blanks for username and password

Having done the above if one clicks on connection shortcut, the phone connects to the internet and one can surf.

I would like to connect to the internet using this cdma phone in ubuntu too. I would appreciate if i could be pointed in the right direction. On searching the internet for this I have found some pages on connecting using usb port but none with serial port.

Thanks in advance.

ash.

---

### Post by akay56 on 2006-07-24
UPDATE:

Hi

I have the dapper drake live CD, so I tried this cdma phone modem while running the dapper live CD and I managed to get it to work. however when I replicated the exact same settings under Breezy, it failed and i could not connect to the internet.

the 3 keys things were: /etc/ppp/options, /etc/ppp/peers/ppp0 and /etc/chatscripts/ppp0

contents of the peers/ppp0 is as follows:

connect "/usr/sbin/chat -v -f /etc/chatscripts/ppp0"
usepeerdns
noauth
defaultroute
/dev/ttyS0
115200
user "user"

contents of the chatscripts/ppp0 is as follows:

ABORT ERROR 
ABORT BUSY 
ABORT VOICE 
ABORT "NO CARRIER" 
ABORT "NO DIALTONE" 
ABORT "NO DIAL TONE" 
ABORT "NO ANSWER" 
"" "ATZ" 
OK "ATDT#777" 
CONNECT 

and finally the contents of /etc/ppp/options is as follows:

If I do the following: egrep -v '#|^ *$' /etc/ppp/options   i get back

asyncmap 0
auth
crtscts
lock
hide-password
modem
proxyarp
lcp-echo-interval 30
lcp-echo-failure 4
noipx


the above 3 files are exactly the same on both the systems i.e. the dapper drake live CD and the Breezy installation, however the modem works in dapper live CD but fails in Breezy.

On Breezy when i run:  sudo pppd call ppp0
i get the following if i tail the /var/log/messages file:

Jul 24 20:37:02 localhost pppd[9643]: pppd 2.4.3 started by root, uid 0
Jul 24 20:37:03 localhost chat[9644]: abort on (ERROR)
Jul 24 20:37:03 localhost chat[9644]: abort on (BUSY)
Jul 24 20:37:03 localhost chat[9644]: abort on (VOICE)
Jul 24 20:37:03 localhost chat[9644]: abort on (NO CARRIER)
Jul 24 20:37:03 localhost chat[9644]: abort on (NO DIALTONE)
Jul 24 20:37:03 localhost chat[9644]: abort on (NO DIAL TONE)
Jul 24 20:37:03 localhost chat[9644]: abort on (NO ANSWER)
Jul 24 20:37:03 localhost chat[9644]: send (ATZ^M)
Jul 24 20:37:03 localhost chat[9644]: expect (OK)
Jul 24 20:37:48 localhost chat[9644]: alarm
Jul 24 20:37:48 localhost chat[9644]: Failed
Jul 24 20:37:49 localhost pppd[9643]: Exit.


Now please can somebody help me.

Thanks in advance.

Regards
Ash.

---

