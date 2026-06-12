---
title: "usb slmodem dailup problem, no dialtone"
date: 2005-08-20
forum: Networking &amp; Wireless
---

### Post by around on 2005-08-20
Hello everyone, I am having a problem with my modem too. I have a usb modem, slmodem 2.9.10 drivers and 2.6.8.1-3-386 kernel. I installed the drivers, did "modprobe lsusb" , and then "sudo /usr/sbin/slmodemd --country=ITALY /dev/slusb0" and everything is ok to this point. 
 Then I tried to connect wvdail with no success. I tried with the network-admin with no success. I tried with ppp, I set it up with pppconfig and tried pon, the modem turns on   O:)  but after 20 seconds turns off  ](*,) . the message plog gives me is:

Aug 20 13:29:37 localhost chat[4721]:  -- got it
Aug 20 13:29:37 localhost chat[4721]: send (ATDT7010187187^M)
Aug 20 13:29:37 localhost chat[4721]: expect (CONNECT)
Aug 20 13:29:37 localhost chat[4721]: ^M
Aug 20 13:29:37 localhost chat[4721]: ATDT7010187187^M^M
Aug 20 13:29:42 localhost chat[4721]: NO DIALTONE
Aug 20 13:29:42 localhost chat[4721]:  -- failed
Aug 20 13:29:42 localhost chat[4721]: Failed (NO DIALTONE)
Aug 20 13:29:42 localhost pppd[4718]: Connect script failed
Aug 20 13:29:43 localhost pppd[4718]: Exit.

I also tried modifiying /etc/chatscripts/provider  with ATX3DT, I read that this way the modem won't wait for the dailtone but the result is the same. It doesn't work.
Can someone help me.

---

### Post by heimo on 2005-08-20
[QUOTE=around]
I also tried modifiying /etc/chatscripts/provider  with ATX3DT[/QUOTE]

Try X0 (ATX0DT) or something like that.

---

### Post by around on 2005-08-20
Thanks, things seem to get better but i'm still having a problem. When the modem turns on it gives me the forst log, then it turns off after 20 sec. and gives me the second log.

around@bestia:~ $ plog
Aug 20 14:29:57 localhost chat[5134]: abort on (DELAYED)
Aug 20 14:29:57 localhost chat[5134]: send (ATZ^M)
Aug 20 14:29:57 localhost chat[5134]: expect (OK)
Aug 20 14:29:57 localhost chat[5134]: ATZ^M^M
Aug 20 14:29:57 localhost chat[5134]: OK
Aug 20 14:29:57 localhost chat[5134]:  -- got it
Aug 20 14:29:57 localhost chat[5134]: send (ATDT7010187187^M)
Aug 20 14:29:57 localhost chat[5134]: expect (CONNECT)
Aug 20 14:29:57 localhost chat[5134]: ^M
Aug 20 14:29:57 localhost chat[5134]: ATDT7010187187^M^M
around@bestia:~ $ plog
Aug 20 14:29:57 localhost chat[5134]:  -- got it
Aug 20 14:29:57 localhost chat[5134]: send (ATDT7010187187^M)
Aug 20 14:29:57 localhost chat[5134]: expect (CONNECT)
Aug 20 14:29:57 localhost chat[5134]: ^M
Aug 20 14:29:57 localhost chat[5134]: ATDT7010187187^M^M
Aug 20 14:30:16 localhost chat[5134]: NO CARRIER
Aug 20 14:30:16 localhost chat[5134]:  -- failed
Aug 20 14:30:16 localhost chat[5134]: Failed (NO CARRIER)
Aug 20 14:30:16 localhost pppd[5133]: Connect script failed
Aug 20 14:30:17 localhost pppd[5133]: Exit.

I am guessing it has a problem with the carrier check. On the readme file of the driver it says that with wvdial you need to add the option 'Carrier Check = no' . I'm guessing it is the same thing with pon. Where do I need to add it and what d I need to add?

---

### Post by heimo on 2005-08-20
Searching wiki led me to this page, which says the correct file would be wvdial.conf
[https://wiki.ubuntu.com/SmartLinkModemDriverHowTo/FromSource](https://wiki.ubuntu.com/SmartLinkModemDriverHowTo/FromSource)

---

### Post by around on 2005-08-20
I already tried with wvdial but it did not work, I wanted to know if in any of the "pon" I needed to add anything like in wvdial. Since pon is the only one giving results I wanted to stick with it

---

### Post by heimo on 2005-08-20
I think that configuration option is wvdial specific. You could try to add M2 (AT-command, just like the X0/X3 thing), to keep speaker always on for debugging - to hear what the modem is actually doing. Doublecheck the cables too.

You can install minicom (sudo apt-get install minicom) and try commands atz (to reset modem) and atm2 (turn on speaker) and ata to open line, you should here at least faint dial tone (unless you need to dial 0 or 9 for out). You can also try manual dialing, same command as on the script / conf - atdt [phonenumber] and see what happens.

---

### Post by around on 2005-08-20
my luck..... my modem has no speaker. I have an Atlantis Land Web runner USB 56k modem, i didn't even know they made modems without spekers....... ](*,)

[http://www.atlantisland.it/scheda_prodotto.php?prodottiID=22](http://www.atlantisland.it/scheda_prodotto.php?prodottiID=22)

---

### Post by around on 2005-08-23
I tried setting it up with wvdial, this is my wvdial.conf file:

[I][Dialer Defaults]
Modem = /dev/ttySL0
Baud = 115200
Carrier check = no
Init1 = ATZ
Init2 = ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
ISDN = 0
Modem Type = Analog Modem
Dial Command = ATX0DT


[Dialer Teleconomy]
Phone = 7010187187
Username = Telecom
Password = Telecom
Stupid mode = 0[/I]

I run "sudo wvdial teleconomy" and this is the result:

[I]--> WvDial: Internet dialer version 1.54.0
--> Initializing modem.
--> Sending: ATZ
ATZ
OK
--> Sending: ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
OK
--> Modem initialized.
--> Sending: ATX0DT7010187187
--> Waiting for carrier.
ATX0DT7010187187
NO CARRIER
--> No Carrier!  Trying again.
--> Sending: ATX0DT7010187187
--> Waiting for carrier.
NO CARRIER[/I]

Even if in the config file I added the line "Carrier Check = no" I get that error, can someone help me

---

