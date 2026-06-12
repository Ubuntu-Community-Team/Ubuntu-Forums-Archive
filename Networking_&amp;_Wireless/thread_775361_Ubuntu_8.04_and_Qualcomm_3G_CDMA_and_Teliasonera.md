---
title: "Ubuntu 8.04 and Qualcomm 3G CDMA and Teliasonera"
date: 2008-04-30
forum: Networking &amp; Wireless
---

### Post by Tobbe1027 on 2008-04-30
Hi, I had the Qualcom 3G modem work ok. in Ubunutu 7.10 but with exactly the same config it don't work ok in 8.04. I have copied the /etc/ppp and /etc/chatscripts with no differense.
I have fixed the driver for the modem with "icon_switch.c" and "/etc/udev/rules.d/10-local.rules" as mentioned in earlier post in this forum.

/etc/wvdial.conf
[Dialer Defaults]
Modem = /dev/ttyUSB0
Phone = *99#
Username = username
Password = password
Baud = 3600000
Dial Command = ATDT
ISDN = 0
Modem Type = USB Modem
New PPPD = yes
Stupid Mode = 1

When I run "sudo wvdial" i get this:
--> WvDial: Internet dialer version 1.60
--> Cannot get information for serial port.
--> Initializing modem.
--> Sending: ATZ
ATZ
OK
--> Modem initialized.
--> Sending: ATDT*99#
--> Waiting for carrier.
ATDT*99#
CONNECT 3600000
--> Carrier detected.  Starting PPP immediately.
--> Starting pppd at Wed Apr 30 07:31:54 2008
--> Pid of pppd: 11960
--> Using interface ppp0
--> Authentication (CHAP) started
--> Authentication (CHAP) successful
--> Disconnecting at Wed Apr 30 07:31:56 2008
--> The PPP daemon has died: A modem hung up the phone (exit code = 16)
--> man pppd explains pppd error codes in more detail.
--> Try again and look into /var/log/messages and the wvdial and pppd man pages for more information.
--> Auto Reconnect will be attempted in 5 seconds
--> Cannot get information for serial port.
--> Initializing modem.
--> Sending: ATZ
ATZ
OK
--> Modem initialized.

Output from /var/log/messages
Apr 30 07:38:20 inttev-laptop pppd[12246]: pppd 2.4.4 started by root, uid 0
Apr 30 07:38:20 inttev-laptop pppd[12246]: speed 3600000 not supported
Apr 30 07:38:20 inttev-laptop pppd[12246]: Using interface ppp0
Apr 30 07:38:20 inttev-laptop pppd[12246]: Connect: ppp0 <--> /dev/ttyUSB0
Apr 30 07:38:20 inttev-laptop pppd[12246]: CHAP authentication succeeded
Apr 30 07:38:20 inttev-laptop pppd[12246]: CHAP authentication succeeded
Apr 30 07:38:22 inttev-laptop pppd[12246]: Modem hangup
Apr 30 07:38:22 inttev-laptop pppd[12246]: Connection terminated.
Apr 30 07:38:22 inttev-laptop pppd[12246]: Exit.


And then it loops with this error all the time:
"The PPP daemon has died: A modem hung up the phone (exit code = 16)"

If I use kppp instead of wvdial I get same error and there I can see that I get DNS-information and more from Teliasonera but I dont get any further in my connection.


How do I fix this?? 
Best regards, Tobbe

---

