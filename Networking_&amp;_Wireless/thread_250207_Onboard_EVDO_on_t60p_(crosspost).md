---
title: "Onboard EVDO on t60p (crosspost)"
date: 2006-09-03
forum: Networking &amp; Wireless
---

### Post by CoryLinden on 2006-09-03
(Cross posted in case Notebook support was the wrong fourm)

Of course, *now* they start selling it with Linux preinstalled :-(  I wonder if I can get that . . .

Anyway, have most things working despite being a n00b -- Thank you ubuntu forums! -- including ATI accelerating.  However, the onboard Sierra Wireless EVDO part doesn't seem to turn on under ubuntu.  I have logged on and registed under Windows and it works fine, so I followed the following steps:

> lsusb

to get the wireless card and product id

[FONT="Fixedsys"]Bus 005 Device 002: ID 0a5c:2110 Broadcom Corp.
Bus 005 Device 001: ID 0000:0000
Bus 002 Device 002: ID 1199:0218 Sierra Wireless, Inc.
Bus 002 Device 001: ID 0000:0000
Bus 001 Device 001: ID 0000:0000
Bus 004 Device 001: ID 0000:0000
Bus 003 Device 003: ID 04b3:4485 IBM Corp.
Bus 003 Device 001: ID 0000:0000
[/FONT]

> sudo modprobe usbserial vendor=0x1199 product=0x0218

Then setup up the files for ppp.

/etc/ppp/peers/1xevdo
[FONT="Fixedsys"][/-detach
ttyUSB0
921600
debug
noauth
defaultroute
usepeerdns
connect-delay 10000
user ##########@vzw3g.com
show-password
crtscts
lock
lcp-echo-failure 0
lcp-echo-interval 65535
connect '/usr/sbin/chat -v -t3 -f /etc/ppp/peers/1xevdo_chat'
FONT]

and /etc/ppp/peers/1xevdo_chat:
[FONT="Fixedsys"]'' 'AT'
'OK' 'AT+CSQ'
'OK' 'ATE0V1&F&D2&C1&C2S0=0'
'OK' 'ATE0V1'
'OK' 'ATS7=60'
'OK' 'ATDT#777'
[/FONT]

When I then kick off:
>  sudo pppd call 1xevdo

and tail -f /var/log/messages

I get:

[FONT="Fixedsys"]
[AAug 31 08:19:37 localhost pppd[24020]: pppd 2.4.4b1 started by cory, uid 0
Aug 31 08:19:38 localhost chat[24021]: send (AT^M)
Aug 31 08:19:38 localhost chat[24021]: expect (OK)
Aug 31 08:19:38 localhost chat[24021]: ^M
Aug 31 08:19:38 localhost chat[24021]: OK
Aug 31 08:19:38 localhost chat[24021]:  -- got it
Aug 31 08:19:38 localhost chat[24021]: send (AT+CSQ^M)
Aug 31 08:19:39 localhost chat[24021]: expect (OK)
Aug 31 08:19:39 localhost chat[24021]: ^M
Aug 31 08:19:39 localhost chat[24021]: ^M
Aug 31 08:19:39 localhost chat[24021]: 99, 99^M
Aug 31 08:19:39 localhost chat[24021]: ^M
Aug 31 08:19:39 localhost chat[24021]: OK
Aug 31 08:19:39 localhost chat[24021]:  -- got it
Aug 31 08:19:39 localhost chat[24021]: send (ATE0V1&F&D2&C1&C2S0=0^M)
Aug 31 08:19:39 localhost chat[24021]: expect (OK)
Aug 31 08:19:39 localhost chat[24021]: ^M
Aug 31 08:19:39 localhost chat[24021]: ^M
Aug 31 08:19:39 localhost chat[24021]: OK
Aug 31 08:19:39 localhost chat[24021]:  -- got it
Aug 31 08:19:39 localhost chat[24021]: send (ATE0V1^M)
Aug 31 08:19:39 localhost chat[24021]: expect (OK)
Aug 31 08:19:39 localhost chat[24021]: ^M
Aug 31 08:19:39 localhost chat[24021]: ATE0V1^M^M
Aug 31 08:19:39 localhost chat[24021]: OK
Aug 31 08:19:39 localhost chat[24021]:  -- got it
Aug 31 08:19:39 localhost chat[24021]: send (ATS7=60^M)
Aug 31 08:19:39 localhost chat[24021]: expect (OK)
Aug 31 08:19:39 localhost chat[24021]: ^M
Aug 31 08:19:39 localhost chat[24021]: ^M
Aug 31 08:19:39 localhost chat[24021]: OK
Aug 31 08:19:39 localhost chat[24021]:  -- got it
Aug 31 08:19:39 localhost chat[24021]: send (ATDT#777^M)
Aug 31 08:19:39 localhost pppd[24020]: Serial connection established.
Aug 31 08:19:39 localhost pppd[24020]: Using interface ppp0
Aug 31 08:19:39 localhost pppd[24020]: Connect: ppp0 <--> /dev/ttyUSB0
Aug 31 08:20:19 localhost pppd[24020]: LCP: timeout sending Config-Requests
Aug 31 08:20:19 localhost pppd[24020]: Connection terminated.
Aug 31 08:20:19 localhost pppd[24020]: Receive serial link is not 8-bit clean:
Aug 31 08:20:19 localhost pppd[24020]: Problem: all had bit 7 set to 0
Aug 31 08:20:20 localhost pppd[24020]: Modem hangup
Aug 31 08:20:20 localhost pppd[24020]: Exit.
[/FONT]

Since 'AT+CSQ' is giving me 99, 99, and I know that the modem works here under windows, I suspect that it is somehow off.  Cycling the "turn on wireless" function key doesn't seem to do anything and rebooting to windows and then coming back to Linux also has no effect.  I've been poking through the forums and haven't found this particular problem, so apologies if this is a n00b dupe :-)

Thanks for the help -- if this works I will be able to complete my transfer off of OS X and make sure that the Second Life Linux client keeps rolling forward :-)!

---

### Post by rockdon on 2006-12-12
I have the exact same problem and am feverishly looking to resolve the issue

---

