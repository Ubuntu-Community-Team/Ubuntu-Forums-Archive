---
title: "Pcmcia Wireless Cdma Modem Not Working"
date: 2006-11-09
forum: Networking &amp; Wireless
---

### Post by rgogada on 2006-11-09
Hi, I am a relatively newbie and trying to set up my PCMCIA WIRELESS CDMA MODEM. after i insert the card, dmesg shows the following

[17186550.300000] pccard: PCMCIA card inserted into slot 0
[17186550.300000] cs: memory probe 0xfbf00000-0xfbffffff: excluding 0xfbf00000-0xfbf0ffff 0xfbff0000-0xfbffffff
[17186550.320000] pcmcia: registering new device pcmcia0.0
[17186550.604000] ttyS3: detected caps 00000700 should be 00000100
[17186550.604000] 0.0: ttyS3 at I/O 0x2e8 (irq = 5) is a 16C950/954
[17186654.428000] CSLIP: code copyright 1989 Regents of the University of California
-------------------------------------------------

and my wvdial.conf is as follows

[Modem0]
Modem = /dev/ttyS3
Baud = 230400
SetVolume = 0
Dial Command = ATDT
Init1 = ATZ
FlowControl = Hardware (CRTSCTS)

[Dialer cdma]
Username = 9316080737
Password = 9316080737
Phone = #777
Stupid Mode = 1
Inherits = Modem0
--------------------------------------

and when I did sudo wvdial cdma, the following is the output

rgogada@rgogada-laptop:~$ sudo wvdial cdma
--> WvDial: Internet dialer version 1.55
--> Initializing modem.
--> Sending: ATZ
--> Sending: ATQ0
--> Re-Sending: ATZ
--> Modem not responding.
--------------------------------------------

I am completely struck and looking for help desperately. your help is highly appreciated

regards
ram.

---

### Post by ozorba on 2006-11-23
Try this one:

[http://www.ubuntuforums.org/showpost.php?p=1797018&postcount=2](http://www.ubuntuforums.org/showpost.php?p=1797018&postcount=2)

---

### Post by thekoez on 2008-05-21
Hi, i have similar situation also, and recently i have found the solution from guys from china .. and I wonder why I can't find it everywhere on english forum :(

run dmesg to find what serial interface is simulated by your PCMCIA card

$ dmesg | grep tty
..
..
[ 695.124000] ttyS3: detected caps 00000700 should be 00000100 [695.124000] ttyS3: detected caps 00000700 should be 00000100
[ 695.124000] 0.0: ttyS3 at I/O 0x2e8 (irq = 3) is a 16C950/954 [695.124000] 0.0: ttyS3 at I / O 0x2e8 (irq = 3) is a 16C950/954
..
..
since this kind of modem simulate serial interface with baud rate 230400, you need "setserial" to set ttyS3 accordingly

$ sudo apt-get install setserial
..
..
$ setserial /dev/ttyS3 baud_base 230400
$ sudo setserial /dev/ttyS3 -a
/dev/ttyS3, Line 0, UART: 16950/954, Port: 0x03f8, IRQ: 3
Baud_base: 230400, close_delay: 50, divisor: 0
closing_wait: 3000
Flags: spd_normal skip_test

Then you need to edit wvdial.conf

$ sudo gedit /etc/ wvdial.conf

[Dialer Defaults]
Init1 = ATZ
Init2 = ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
Stupid Mode = 1
Dial Command = ATDT

[Dialer pcmcia]
Baud = 57600
SetVolume = 1
Modem = /dev/ttyS3
Password = password
Username = username
Phone = #777
FlowControl = Hardware (CRTSCTS)

then try to dial using wvdial...

$ sudo wvdial pcmcia
--> WvDial: Internet dialer version 1.60
--> Initializing modem.
--> Sending: ATZ
--> Sending: ATQ0
OK
--> Re-Sending: ATZ
OK
--> Initializing modem.
--> Sending: ATZ
--> Sending: ATQ0
OK
--> Re-Sending: ATZ
OK
--> Initializing modem.
--> Sending: ATZ
OK
--> Sending: ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
OK
--> Modem initialized.
--> Sending: ATDT#777
--> Waiting for carrier.
ATDT#777
CONNECT
--> Carrier detected. Starting PPP immediately.
--> Starting pppd at Tue May 20 05:57:44 2008
..
..

at this point you should be able to access internet.

Happy ubuntuing

---

