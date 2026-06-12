---
title: "nokia 6300 as modem in ubuntu"
date: 2008-07-09
forum: Networking &amp; Wireless
---

### Post by cai23 on 2008-07-09
Hi!

Im trying to use a nokia 6300 mobile phone as a modem in ubuntu.
The phone itself can connect to the internet with its default browser which means the GPRS as activated and working.
So I run wvdialconf via terminal to get the wvdial.conf configuration. Here's my /etc/wvdial.conf file:


[Dialer Defaults]
Init2 = ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
Modem Type = USB Modem
; Phone = <Target Phone Number>
ISDN = 0
; Username = <Your Login Name>
Init1 = ATZ
; Password = <Your Password>
Modem = /dev/ttyACM1
Baud = 460800


Then I setup KPP to connect to the modem 
I use "TERMINAL-BASED" Authentication at account setting (Im not sure if this is the right authentication to use but when I tried PAP/CHAP it'll ask me for login ID and password w/c I do not have).
I used *99# as a phone number to dial which I get from other forum.

Then when I tried to connect..it goes...

Modem Ready...

Then at Login Terminal Window I'll click "Continue"
Logging on to network


And I got a popup message from the phone 
"SUSCRIBED TO PACKET DATA FIRST!"


I even tried to use GNOME PPP but didnt succeed.


Heres the PPP Log:

Jul  9 16:15:03 rnfa-desktop pppd[7668]: pppd 2.4.4 started by emp, uid 1001
Jul  9 16:15:03 rnfa-desktop pppd[7668]: Using interface ppp0
Jul  9 16:15:03 rnfa-desktop pppd[7668]: Connect: ppp0 <--> /dev/ttyACM0
Jul  9 16:15:33 rnfa-desktop pppd[7668]: Terminating on signal 15
Jul  9 16:15:39 rnfa-desktop pppd[7668]: Connection terminated.
Jul  9 16:15:39 rnfa-desktop pppd[7668]: Modem hangup
Jul  9 16:15:39 rnfa-desktop pppd[7668]: Exit.


Hopefully someone can help me.
Thanks...

---

### Post by jajabinx on 2008-07-16
I believe you need to add your network's APN or access point in your /etc/wvdial.conf...

```
Init3 = AT+CGDCONT=1,"IP","Internet"
```

You must ask your service provider what to use here. Mine is as is. The "Internet" there is the APN. This will resolve your packet data issue.

Also, uncomment

```
Phone = *99#
Username = anyusername
Password = anypassword
```

And then to connect, simply type in your terminal

```
me@me-mylaptop:~$ **wvdial**
```.

You should see the logs after you issue the command.

If you want an interface, unfortunately, I haven't used KPP dialer, but you mentioned Gnome. In your Gnome PPP, you need to configure your init strings. 

Go to **Setup > Modem > Init Strings** and edit the field for Init 3 which should be the same as the one above with your carrier's APN of course.

The same goes for your Phone, Username and Password.

This should work, I hope. I had the same problem on packet data before and both my gnome ppp and wvdial are working now. 

Let me know what happens to yours.:)

---

### Post by cai23 on 2008-07-16
Thanks. But I already solve this issue. 
Just an update:

My Cuurent /etc/wvdial.conf file:

[Dialer Defaults]
Init2 = ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
Modem Type = USB Modem
Phone = *99#
ISDN = 0
Username = ""
Init1 = ATZ
Password = ""
Modem = /dev/ttyACM1
Baud = 460800


The problem has nothing to do with my pc dialer settings but with smart GPRS settings on my Phone. I just deactivate the GPRS and asked smart to send me a new settings for my nokia 6300. 

Thanks...

---

