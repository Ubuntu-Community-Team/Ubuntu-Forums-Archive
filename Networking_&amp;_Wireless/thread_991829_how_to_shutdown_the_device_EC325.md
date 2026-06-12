---
title: "how to shutdown the device EC325"
date: 2008-11-24
forum: Networking &amp; Wireless
---

### Post by trendyabinash on 2008-11-24
Sir today I faced a new problem, I was downloading a file and my current went out.
After current was back I booted my system and connected to net through my EC325 device(it is a wireless CDMA device to connect to net). I found that no data was being received. I tried everything I could possible do to make it right. Then I booted to my windows XP, started the driver software given by the device there is an option to shutdown the device I click over it and then restarted the device and now every thing is back to normal.

I wanna know how will I shutdown the device in UBUNTU 8.10
my device location is /dev/ttyUSB0, i think unmounting it will do the trick but I don't know how to do that.

Can anyone please help me out?

---

### Post by trendyabinash on 2008-11-26
NO help?

where are the ubuntuforum staff??

---

### Post by ramsubbu on 2008-12-13
Dear Abinash,
You are far ahead of me.  I am still struggling to get the damn EC325 to work. Please kindly let me know how to make it work.
The Wvdial output looks like this:
--> WvDial: Internet dialer version 1.60
--> Cannot get information for serial port.
--> Initializing modem.
--> Sending: ATZ
ATZ
OK
--> Modem initialized.
--> Sending: ATDT#777
--> Waiting for carrier.
ATDT#777
CONNECT 230400
--> Carrier detected.  Starting PPP immediately.
--> Starting pppd at Sat Dec 13 18:56:32 2008
--> Pid of pppd: 8133
--> Using interface ppp0
--> Disconnecting at Sat Dec 13 18:56:42 2008
--> The PPP daemon has died: A modem hung up the phone (exit code = 16)
--> man pppd explains pppd error codes in more detail.
--> Try again and look into /var/log/messages and the wvdial and pppd man pages for more information.
--> Auto Reconnect will be attempted in 5 seconds

---

### Post by romainclair on 2009-01-17
Hi I have the same problem, modem hung up the phone. exit code = 16. Do u know the answer, now ? Can u help me ?

---

