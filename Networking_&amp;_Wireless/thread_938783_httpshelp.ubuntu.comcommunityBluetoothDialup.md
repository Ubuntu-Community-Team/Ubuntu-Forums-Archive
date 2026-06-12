---
title: "https://help.ubuntu.com/community/BluetoothDialup"
date: 2008-10-05
forum: Networking &amp; Wireless
---

### Post by spydergt on 2008-10-05
in refrence to this , im trying to get my ppc 6800 to dial up internet , i have cricket service in houston tx, i followed the examples for the verizon and modded where i though i needed but im oviously missing something , 

if you see anything in my files that i have configured incorretly please god tell me , i cant figure this one out on my own righ now .. spent all night working on three or four diffrent problems  this being one , 

happy reading ,



these are three diffrent attempts to manipulate and all yeild the same error from systems log , 

in other words when i type gksudo gedit syslog ,
these are the error that i read for my failed miserable attempts .... haha , stop laughing my misery is not funny ... ok .. you can laugh ...

Oct  5 16:06:01 spydergt-laptop hcid[6517]: link_key_request (sba=00:0E:A1:35:AF:04, dba=00:17:83:46:9E:48)
Oct  5 16:06:02 spydergt-laptop chat[7233]: abort on (ERROR)
Oct  5 16:06:02 spydergt-laptop chat[7233]: abort on (NO CARRIER)
Oct  5 16:06:02 spydergt-laptop chat[7233]: abort on (NO DIALTONE)
Oct  5 16:06:02 spydergt-laptop chat[7233]: abort on (BUSYY)
Oct  5 16:06:02 spydergt-laptop chat[7233]: abort on (NO ANSWER)
Oct  5 16:06:02 spydergt-laptop chat[7233]: send (ATZ^M)
Oct  5 16:06:02 spydergt-laptop chat[7233]: expect (ATDT#777)
Oct  5 16:06:02 spydergt-laptop chat[7233]: ^M
Oct  5 16:06:02 spydergt-laptop chat[7233]: OK^M
Oct  5 16:06:02 spydergt-laptop chat[7233]: ATZ^M^M
Oct  5 16:06:02 spydergt-laptop chat[7233]: OK^M
Oct  5 16:06:08 spydergt-laptop chat[7233]: SIGTERM
Oct  5 16:06:08 spydergt-laptop pppd[7229]: Connect script failed
Oct  5 16:06:09 spydergt-laptop pppd[7229]: Exit.v




Oct  5 16:05:52 spydergt-laptop hcid[6517]: link_key_request (sba=00:0E:A1:35:AF:04, dba=00:17:83:46:9E:48)
Oct  5 16:05:53 spydergt-laptop chat[7204]: abort on (ERROR)
Oct  5 16:05:53 spydergt-laptop chat[7204]: abort on (NO CARRIER)
Oct  5 16:05:53 spydergt-laptop chat[7204]: abort on (NO DIALTONE)
Oct  5 16:05:53 spydergt-laptop chat[7204]: abort on (BUSYY)
Oct  5 16:05:53 spydergt-laptop chat[7204]: abort on (NO ANSWER)
Oct  5 16:05:53 spydergt-laptop chat[7204]: send (ATZ^M)
Oct  5 16:05:53 spydergt-laptop chat[7204]: expect (ATDT#777)
Oct  5 16:05:53 spydergt-laptop chat[7204]: ^M
Oct  5 16:05:53 spydergt-laptop chat[7204]: OK^M
Oct  5 16:05:53 spydergt-laptop chat[7204]: ATZ^M^M
Oct  5 16:05:53 spydergt-laptop chat[7204]: OK^M
Oct  5 16:05:56 spydergt-laptop chat[7204]: SIGTERM
Oct  5 16:05:56 spydergt-laptop pppd[7200]: Connect script failed
Oct  5 16:05:57 spydergt-laptop pppd[7200]: Exit.

all three scripts fail at what resembles the same spot each time , 

Oct  5 15:58:43 spydergt-laptop chat[7150]: abort on (ERROR)
Oct  5 15:58:43 spydergt-laptop chat[7150]: abort on (NO CARRIER)
Oct  5 15:58:43 spydergt-laptop chat[7150]: abort on (NO DIALTONE)
Oct  5 15:58:43 spydergt-laptop chat[7150]: abort on (BUSYY)
Oct  5 15:58:43 spydergt-laptop chat[7150]: abort on (NO ANSWER)
Oct  5 15:58:43 spydergt-laptop chat[7150]: send (ATZ^M)
Oct  5 15:58:43 spydergt-laptop chat[7150]: expect (OK)
Oct  5 15:58:43 spydergt-laptop chat[7150]: ^M
Oct  5 15:58:43 spydergt-laptop chat[7150]: OK
Oct  5 15:58:43 spydergt-laptop chat[7150]:  -- got it 
Oct  5 15:58:43 spydergt-laptop chat[7150]: send (ATDT#777^M)
Oct  5 15:58:43 spydergt-laptop chat[7150]: expect (CONNECT)
Oct  5 15:58:43 spydergt-laptop chat[7150]: ^M
Oct  5 15:58:43 spydergt-laptop chat[7150]: ATZ^M^M
Oct  5 15:58:43 spydergt-laptop chat[7150]: OK^M
Oct  5 15:58:43 spydergt-laptop chat[7150]: ATDT#777^M^M
Oct  5 15:58:43 spydergt-laptop chat[7150]: NO CARRIER
Oct  5 15:58:43 spydergt-laptop chat[7150]:  -- failed
Oct  5 15:58:43 spydergt-laptop chat[7150]: Failed (NO CARRIER)
Oct  5 15:58:43 spydergt-laptop pppd[7146]: Connect script failed
Oct  5 15:58:44 spydergt-laptop pppd[7146]: Exit.

gksudo gedit /etc/chatscripts/BluetoothDialup

# abortstring

ABORT 'ERROR' ABORT 'NO CARRIER' ABORT 'NO DIALTONE' ABORT 'BUSYY' ABORT 'NO ANSWER'

#MODEMINIT

'' ATZ

# ISPNUMBER

OK-AT-OKL3 ATDT#777   (can anyone tell me what the hell ok-at-okl3 is/means????)

# ISPCONNECT

CONNECT \d\c


gksudo gedit /etc/ppp/peers/BluetoothDialup yeilds this file , 

hide-password

/dev/rfcomm0

connect " usr/sbin/chat -v -f /etc/chatscripts/BluetoothDialup"

noauth

defaultroute

usepeerdns

connect-delay 10000

user "8328813174@mycricket.com"

lock

lcp-echo-failure 4

lcp-echo-interval 65535


115200



well thanks for lookin'
 
come back soon!

---

