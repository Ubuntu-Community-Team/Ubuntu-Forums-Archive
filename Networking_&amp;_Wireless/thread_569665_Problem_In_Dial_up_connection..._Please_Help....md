---
title: "Problem In Dial up connection... Please Help..."
date: 2007-10-07
forum: Networking &amp; Wireless
---

### Post by Rabindranath on 2007-10-07
I have tried to use a dial up connection in kubuntu using a k510i USB modem and I have tried kppp an dwvdial. When I type wvdial i nthe terminal , I get the following error.


rabindranath@Home-Computer:~$ wvdial
--> WvDial: Internet dialer version 1.56
--> Cannot get information for serial port.
--> Initializing modem.
--> Sending: ATZ
ATZ
OK
--> Sending: ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
OK
--> Modem initialized.
--> Configuration does not specify a valid phone number.
--> Configuration does not specify a valid login name.
--> Configuration does not specify a valid password.
rabindranath@Home-Computer:~$ 



When I use kppp, it seems to connect to the internet perfectly but I am not able to browse the internet. It shows i tis connected but I am not able to use the connection. When I use konquerer,


An error occurred while loading [http://ubuntuforums.org/forumdisplay.php?f=136:](http://ubuntuforums.org/forumdisplay.php?f=136:)
Could not connect to host [http://ubuntuforums.org/forumdisplay.php?f=136](http://ubuntuforums.org/forumdisplay.php?f=136).



The wvdial.conf file is as follows


[Dialer Defaults]
Init1 = ATZ
Init2 = ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
New PPPD = yes
Modem Type = USB Modem
Stupid Mode = 1
{*99***1# Phone} = *99***1#
Baud = 460800
Auto DNS = yes
a Password = a
Modem = /dev/ttyACM0
ISDN = 0
; Phone = *99***1#
Airtel Username = <Your user name here> 
; Password = <Your Password>
; Username = < Your User name here>



Please help me.... Thanks in advance...

---

### Post by sonicx on 2007-10-07
have you setup the ip for your isps domain name server (DNS)?
if you prefer to use wvdial over kppp you should configurate a connection for it with wvdialconf.

btw you might want to edit out the private data of your configuration when you post it to a forum.
regards,
jonas

---

### Post by Rabindranath on 2007-10-07
I have tried wvdialconf and changed the settings. But I have the same problem. ( The username and password are the same for all airtel users :)  ) Anyway I edited it. Thanks for the reply. Any suggestions?

---

### Post by TheThinker on 2007-10-29
I just solved  that problem recently. Go back to your wvdial configuration settings in the Terminal by this command:

sudo wvdialconfig

Then look at the lines concerning your password, your login name and your dialup number. If I'm right, these lines should look something ike this:

; password = <password>
; login name = <login name>
; phone number = <phone_number>

Now, get rid of the first character you see in each line so that they now look like this:

password = <password>
login name = <login_name>
phone number = <phone_number>

You don't need to enter the information with brackets. After you're done, press CTRL+O to save and press enter, then press CTRL+X to exit into the terminal. Type in wvdial and voila! It should  no longer say that the information you entered was "invalid".

This may be a bug in Gutsy, and I'm not even sure why it's there in the first place. It could be that the installation of GnomePPP, which uses Wvdial as its backend, screwed up the wvdial settings slightly. I hope this solves your problem.

---

### Post by Rabindranath on 2007-11-02
Thanks for the reply. Ill try this out when i go home...

---

