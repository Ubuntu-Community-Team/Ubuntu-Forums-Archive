---
title: "SprintPCS Connection Card PC-5740"
date: 2007-07-18
forum: Networking &amp; Wireless
---

### Post by appzattak on 2007-07-18
I have this card and want to know if anyone has been able to get it to work under ubuntu 7.04 I can't seem to find that anyone has got it to work.

Thanks.


--Steve

---

### Post by appzattak on 2007-07-19
hey all, any one use this card??? 

I did find this tut for Verizon but one guy says he did it and it worked for his sprint card. This is the link.  [http://kenkinder.com/evdo-pc5740/](http://kenkinder.com/evdo-pc5740/)

I did all this but I get this and don't know how to get around it.

steve@ubuntulappy:~$ pppd call 1xevdo
steve@ubuntulappy:~$ tail -f /var/log/messages
Jul 19 09:51:49 ubuntulappy chat[5454]: abort on (NO DIALTONE)
Jul 19 09:51:49 ubuntulappy chat[5454]: abort on (BUSY)
Jul 19 09:51:49 ubuntulappy chat[5454]: abort on (NO ANSWER)
Jul 19 09:51:49 ubuntulappy chat[5454]: send (ATTEV1&F;&D2;&C1;&C2S0;=0S7=60^M)
Jul 19 09:51:49 ubuntulappy chat[5454]: expect (OK)
Jul 19 09:51:49 ubuntulappy chat[5454]: ATTEV1&F;&D2;&C1;&C2S0;=0S7=60^M^M
Jul 19 09:51:49 ubuntulappy chat[5454]: ERROR
Jul 19 09:51:49 ubuntulappy chat[5454]:  -- failed
Jul 19 09:51:49 ubuntulappy chat[5454]: Failed (ERROR)
Jul 19 09:51:50 ubuntulappy pppd[5452]: Exit.



Any help would be greatly appreciated.

---

### Post by appzattak on 2007-07-19
sweet, did some more digging and now it works!! This is great. Here is what did or rather used, so if anyone else needs this.

Here is my /etc/ppp/peers  
ttyACM0
115200
debug
noauth
defaultroute
usepeerdns
connect-delay 10000
user [email]MYUSERNAMEHERE@sprintpcs.com[/email]
show-password
crtscts
lock
lcp-echo-failure 4
lcp-echo-interval 65535
connect '/usr/sbin/chat -v -t3 -f /etc/ppp/peers/1xevdo_chat'

And here is my /etc/ppp/peers/1xevdo_chat
# AT$QCMIPGETP  "login" name used for MobileIP, which usually matches your MIN.
# AT+GSN        ESN in hex
# AT+GMR        firmware revision and build date.
# AT+CSQ        first number indicates the signal strength above -109 dBm (in
#               2 dBm increments).  A value of 7 or higher (-95 dBm) can be
#               considered adequate. 31 is the max.  (Possible values in
#               Audiovox PC5740 are 0, 7, 15, 23, 31.)
# AT+CDV=*22899 Update PRL.  at+cdv=*22899 | OK | Lost carrier.
ABORT 'NO CARRIER' ABORT ERROR ABORT 'NO DIALTONE' ABORT BUSY ABORT 'NO ANSWER'
'' 'ATTEV1&F&D2&C1&C2S0=0S7=60'
'OK-ATTEV1&F&D2&C1&C2S0=0S7=60-OK-ATTEV1&F&D2&C1&C2S0=0S7=60-OK' 'AT+CSQ;D#777'
TIMEOUT 70
'CONNECT-AT+CSQ;D#777-CONNECT'



This is my speedtest
[[IMG]http://www.speedtest.net/result/157158066.png[/IMG]](http://www.speedtest.net)

---

