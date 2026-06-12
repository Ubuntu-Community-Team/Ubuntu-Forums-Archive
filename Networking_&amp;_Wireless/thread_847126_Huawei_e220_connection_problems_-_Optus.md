---
title: "Huawei e220 connection problems - Optus"
date: 2008-07-02
forum: Networking &amp; Wireless
---

### Post by apkp on 2008-07-02
I'm just a typical newbie (lots of enthusiasm but not much knowledge) and need some help.

I'm trying to connect to Optus Australia's wireless broadband network using the supplied Huawei E220 modem. I've followed the various threads including:

[http://ubuntuforums.org/showthread.php?t=843973&highlight=huawei+e220](http://ubuntuforums.org/showthread.php?t=843973&highlight=huawei+e220)

without much sucess.

My wvdial.conf file reads:
[INDENT][B][Dialer Defaults]
Init1 = ATZ
Init2 = ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
Stupid Mode = 1
Moden Type = Analog Modem
ISDN = 0
Phone = *99#
Modem = /dev/ttyUSB0
Username = username
Dial Command = ATDT
Password = password
Baud = 9600[/B][/INDENT]

My problem is that when running wvdial from terminal I get the following, without establishing a connection:
[INDENT]andrew@andrew-laptop:~$ wvdial
--> WvDial: Internet dialer version 1.60
--> Cannot get information for serial port.
--> Initializing modem.
--> Sending: ATZ
ATZ
OK
--> Sending: ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
OK
--> Modem initialized.
--> Sending: ATDT*99#
--> Waiting for carrier.
ATDT*99#
CONNECT
--> Carrier detected.  Starting PPP immediately.
--> Starting pppd at Wed Jul  2 19:56:59 2008
[B]--> Warning: Could not modify /etc/ppp/pap-secrets: Permission denied
--> --> PAP (Password Authentication Protocol) may be flaky.
--> Warning: Could not modify /etc/ppp/chap-secrets: Permission denied
--> --> CHAP (Challenge Handshake) may be flaky.[/B]
--> Pid of pppd: 6150
--> Using interface ppp0
--> pppd: ï¿½ï¿½[06][08][10]ï¿½[06][08]
--> pppd: ï¿½ï¿½[06][08][10]ï¿½[06][08]
--> pppd: ï¿½ï¿½[06][08][10]ï¿½[06][08]
--> pppd: ï¿½ï¿½[06][08][10]ï¿½[06][08]
--> pppd: ï¿½ï¿½[06][08][10]ï¿½[06][08]
--> pppd: ï¿½ï¿½[06][08][10]ï¿½[06][08]
--> pppd: ï¿½ï¿½[06][08][10]ï¿½[06][08]
--> Disconnecting at Wed Jul  2 19:57:35 2008
--> The PPP daemon has died: A modem hung up the phone (exit code = 16)
--> man pppd explains pppd error codes in more detail.
--> Try again and look into /var/log/messages and the wvdial and pppd man pages for more information.
--> Auto Reconnect will be attempted in 5 seconds
--> Cannot get information for serial port.[/INDENT]

There are two lines in the middle which concern me (in bold). 

Have tried using Gnome-PPP, but this simply attempts to connect and then drops out. 

Like I said, I've been able to get this far, but not nearly knowledgable enough to get over these hurdles.

Can anyone help, please?

---

### Post by damianusthesage on 2008-07-07
Much the same problem.
I don't think the lines you've written in bold are the problem. I used this device with 3 Mobile and it used to connect fine with those lines about the flaky handshake.

 Now I use vodaphone, it's a different story.

Problem is all that 

man pppd

tells me is that my modem has exited. There is nothing to suggest why and no setting in kpppd that looks like it could stop this happening.

I put all my timeouts to their maximum, then minum, and then back to default no change.

Anyone, this is the *last step*!!!

---

### Post by gregkk on 2008-07-29
Hi apkp, 

Did you find a solution? I have exactly the same problem (its a DoDo wireless service which uses the Optus network).

Many thanks,

gregkk.

---

