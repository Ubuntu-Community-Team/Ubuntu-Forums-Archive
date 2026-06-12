---
title: "Vodafone Mobile Connection Lite E172 + ubuntu Hardy"
date: 2008-08-04
forum: Networking &amp; Wireless
---

### Post by Erthainel on 2008-08-04
Before I begin, I am a BEGINNER with ubuntu and my english is quite poor. I work with ubuntu for about a year, since i have my own laptop. 
My problem is easy to understand and I hope it will be easy to solve.

I now have a borrowed laptop with Win XP and using it, i am connected by the Huawei VMCLite E172 to the internet. I wont have the XP computer available starting tuesday. I have a Ubuntu HH computer and i need to make the E172 modem work on it.

I tried: [http://forum.ubuntu.cz/index.php?topic=24857.0](http://forum.ubuntu.cz/index.php?topic=24857.0)
and: [http://ubuntuforums.org/showthread.php?p=5515804#post5515804](http://ubuntuforums.org/showthread.php?p=5515804#post5515804)
and: [http://ubuntuforums.org/showthread.php?p=5481703](http://ubuntuforums.org/showthread.php?p=5481703)
and: [http://ubuntuforums.org/showthread.php?t=843973](http://ubuntuforums.org/showthread.php?t=843973)

but i never got even as far as the people reporting errors there

I get:
```


erthainel@Stormwind:~$ sudo wvdial Nett
[sudo] password for erthainel: 
--> WvDial: Internet dialer version 1.60
--> Cannot get information for serial port.
--> Initializing modem.
--> Sending: ATZ
ATZ
OK
--> Sending: ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
OK
--> Sending: AT+CGDCONT=1,"IP","internet"
AT+CGDCONT=1,"IP","internet"
ERROR
--> Bad init string.
--> Cannot get information for serial port.
--> Initializing modem.
--> Sending: ATZ
ATZ
OK
--> Sending: ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
OK
--> Sending: AT+CGDCONT=1,"IP","internet"
AT+CGDCONT=1,"IP","internet"
ERROR
--> Bad init string.
--> Cannot get information for serial port.
--> Initializing modem.
--> Sending: ATZ
ATZ
OK
--> Sending: ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
OK
--> Sending: AT+CGDCONT=1,"IP","internet"
AT+CGDCONT=1,"IP","internet"
ERROR
--> Bad init string.

```
Or:
```


erthainel@Stormwind:~$ sudo wvdial
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
ERROR
--> Invalid dial command.
--> Disconnecting at Mon Aug  4 11:44:26 2008

```

It maybe is some kind of a beginner dumb error, but i really would like to solve it. 

(Could the problem be in the PIN of the SIM card???)

(roesel@gmail.com)
(320556848)

---

### Post by Sealbhach on 2008-08-04
can you paste the output from

```
cat /etc/wvdial.conf
```

I think you might need to add 

stupid mode=on

to this file....

.

---

### Post by Erthainel on 2008-08-04
```

[Dialer Nett]
Init1 = ATZ
Init2 = ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
Init3 = AT+CGDCONT=1,"IP","internet"
Modem Type = Analog Modem
ISDN = 0
New PPPD = yes
; Stupid Mode = 1
Phone = *99#
Modem = /dev/ttyUSB0
Username = internet
Dial Command = ATDT
Password = internet
Baud = 9600

[Dialer Net]
Init2 = ATZ
Init3 = ATE0V1&D2&C1S0=0+IFC=2,2
Init5 = at+cgdcont=1,"ip","internet";
Modem Type = Analog Modem
ISDN = 0
Phone = *99***16#
Modem = /dev/ttyUSB0
Username = internet
Dial Command = ATDT
Stupid Mode = 1
Password = internet
Baud = 460800

[Dialer Defaults]
Init2 = ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
Modem Type = Analog Modem
 Phone = *99#
ISDN = 0
 Username = internet
Init1 = ATZ
 Password = internet
Modem = /dev/ttyUSB0
Baud = 9600


```

I just found out that in the settings I tried it was blocked, so give me few minutes to diconnect and connect on the other comp and try it.

---

### Post by Erthainel on 2008-08-04
After removing the ; from the line with "stupid mode" in the Nett profile, the output was:

```

erthainel@Stormwind:~$ sudo wvdial Nett
--> WvDial: Internet dialer version 1.60
--> Cannot get information for serial port.
--> Initializing modem.
--> Sending: ATZ
OK
--> Sending: ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
OK
--> Sending: AT+CGDCONT=1,"IP","internet"
AT+CGDCONT=1,"IP","internet"
ERROR
--> Bad init string.
--> Cannot get information for serial port.
--> Initializing modem.
--> Sending: ATZ
ATZ
OK
--> Sending: ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
OK
--> Sending: AT+CGDCONT=1,"IP","internet"
AT+CGDCONT=1,"IP","internet"
ERROR
--> Bad init string.
--> Cannot get information for serial port.
--> Initializing modem.
--> Sending: ATZ
ATZ
OK
--> Sending: ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
OK
--> Sending: AT+CGDCONT=1,"IP","internet"
AT+CGDCONT=1,"IP","internet"
ERROR
--> Bad init string.
erthainel@Stormwind:~$

```

---

### Post by Sealbhach on 2008-08-04
Ok, well it seems it doesn't like the init string

```
AT+CGDCONT=1,"IP","internet"
```

Have you got the correct APN for your ISP? 

Who is your ISP?


.

---

### Post by Erthainel on 2008-08-04
I am totally stupid, but could you make those letters clear to me? :)

---

### Post by Erthainel on 2008-08-04
All I know is that its a vodafone stick with a vodafone SIM card (Vodafone Czech Republic).

---

### Post by Sealbhach on 2008-08-04
APN = Access Point Name. 

Why don't you try this guide here?

[http://ubuntuforums.org/showthread.php?t=843973&highlight=e220](http://ubuntuforums.org/showthread.php?t=843973&highlight=e220)

You need to make sure that your /etc/wvdial.conf file contains the dial-up settings stored in your modem.

The way to do that is to plug in the modem and type:

```
sudo wvdialconf
```

Frst, before you do this, make a backup of your /etc/wvdial.cong file:

```
cat /etc/wvdial.conf > ~/Desktop/backup_wvdial.conf
```

This will appear on your desktop.

Post it here too so we can see it.

Thanks.
.

---

### Post by Erthainel on 2008-08-04
I tried that guide as well.
The Dialer that is generated by the wvdialconf looks like this, I only have changed the phone, pass and username. 

```

[Dialer Defaults]
Init2 = ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
Modem Type = Analog Modem
 Phone = *99#
ISDN = 0
 Username = internet
Init1 = ATZ
 Password = internet
Modem = /dev/ttyUSB0
Baud = 9600

```

I will check it again. 
(Btw: is the backup really needed? I mean, doesnt wvdialconf make just another profile under the already made ones? Just curious)

---

### Post by Sealbhach on 2008-08-04
I've checked it out, the APNs for Vodafone in Czech Republic are:

"internet"

or

"ointernet"

From here:

[http://franson.com/forum/topic.asp?TOPIC_ID=6669](http://franson.com/forum/topic.asp?TOPIC_ID=6669)

Here's another link I found, you may want to try it this way:

[http://samiux.wordpress.com/2008/04/23/huawei-e169g-on-ubuntu-804/](http://samiux.wordpress.com/2008/04/23/huawei-e169g-on-ubuntu-804/)

You can get the Vodafone driver here:

[https://forge.betavine.net/frs/download.php/76/vodafone-mobile-connect-card-driver-for-linux_1.99.17_i386.deb](https://forge.betavine.net/frs/download.php/76/vodafone-mobile-connect-card-driver-for-linux_1.99.17_i386.deb)

It should install by just clicking on it.



.

---

### Post by Sealbhach on 2008-08-04
> **Erthainel said:**
> I tried that guide as well.
The Dialer that is generated by the wvdialconf looks like this, I only have changed the phone, pass and username. 

```

[Dialer Defaults]
Init2 = ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
Modem Type = Analog Modem
 Phone = *99#
ISDN = 0
 Username = internet
Init1 = ATZ
 Password = internet
Modem = /dev/ttyUSB0
Baud = 9600

```

I will check it again. 
(Btw: is the backup really needed? I mean, doesnt wvdialconf make just another profile under the already made ones? Just curious)

Thanks, try dialing with these defaults

```
sudo wvdial Defaults
```

It's always good to make a backup...


.

---

### Post by Erthainel on 2008-08-04
My 2GB flash-disk has just refused to be seen by any of the two systems, so bringing back reports will now be a little harder :( 

Please be patient with me :)

---

### Post by Erthainel on 2008-08-04
OK, after formating the flashdisk, there goes the report:

```

erthainel@Stormwind:~$ sudo wvdial Defaults
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
ERROR
--> Invalid dial command.
--> Disconnecting at Mon Aug  4 17:43:46 2008
erthainel@Stormwind:~$ 

```

---

### Post by Erthainel on 2008-08-04
> **Sealbhach said:**
> 
You can get the Vodafone driver here:

[https://forge.betavine.net/frs/download.php/76/vodafone-mobile-connect-card-driver-for-linux_1.99.17_i386.deb](https://forge.betavine.net/frs/download.php/76/vodafone-mobile-connect-card-driver-for-linux_1.99.17_i386.deb)

It should install by just clicking on it.



.

I have a problem with this. The download ends each time in the middle of the file. Once at 1.3 MB once at 876 kb...

---

### Post by GeorgeVita on 2008-08-04
Hi,

I am new to ubuntu, have an E170 modem properly installed and very novice to Linux OS, but as you have already tired, can you please try the following configuration?

[Dialer hspa]
Modem = /dev/ttyUSB0
Modem Type = Analog Modem
ISDN = 0
Baud = 115200
Username = guest
Password = guest
Phone = *99***1#
Stupid Mode =1
Init1 = ATZ
Init2 = AT&F E1 V1 X1 &D2 &C1 S0=0
Init3 =AT+CGDCONT=1,"IP","ointernet"

After saving the changes to wvdial.conf, try dialling from the terminal window by executing:

sudo wvdial hspa (give your password if asked)

As I understand from all previous tries, you have to declare the right APN service ("IP","abc...") and the proper dial number (*99...#), so after your test, pass back the results in order to find where is the error.

---

### Post by Erthainel on 2008-08-04
OK, sorry for the delay:

```

erthainel@Stormwind:~$ sudo wvdial hspa
--> WvDial: Internet dialer version 1.60
--> Cannot get information for serial port.
--> Initializing modem.
--> Sending: ATZ
ATZ
OK
--> Sending: AT&F E1 V1 X1 &D2 &C1 S0=0
AT&F E1 V1 X1 &D2 &C1 S0=0
OK
--> Sending: AT+CGDCONT=1,"IP","ointernet"
AT+CGDCONT=1,"IP","ointernet"
ERROR
--> Bad init string.
--> Cannot get information for serial port.
--> Initializing modem.
--> Sending: ATZ
ATZ
OK
--> Sending: AT&F E1 V1 X1 &D2 &C1 S0=0
AT&F E1 V1 X1 &D2 &C1 S0=0
OK
--> Sending: AT+CGDCONT=1,"IP","ointernet"
AT+CGDCONT=1,"IP","ointernet"
ERROR
--> Bad init string.
--> Cannot get information for serial port.
--> Initializing modem.
--> Sending: ATZ
ATZ
OK
--> Sending: AT&F E1 V1 X1 &D2 &C1 S0=0
AT&F E1 V1 X1 &D2 &C1 S0=0
OK
--> Sending: AT+CGDCONT=1,"IP","ointernet"
AT+CGDCONT=1,"IP","ointernet"
ERROR
--> Bad init string.
erthainel@Stormwind:~$ 


```

The thing i love on ubuntu is this forum support. Thanks for trying to help :)

---

### Post by GeorgeVita on 2008-08-04
Ok, now we must find what is the APN for your type of connection.

Could you phone at your local Vodafone customer service and ask?

If they want to help ask for APN, Tel. Dial number, and user / password.
If you cannot get help from them, search at first for the APN from your local (native language) forums because we cannot understand:

heslo: internet
Telefonní &#269;íslo: *99***1#
Pak se ješt&#283; nep&#345;ipojíme, jdeme do "nastavení".
Jsou tu t&#345;i záložky, nastavíme postupn&#283; všechny

If you find some options, change the appropriate field, SAVE the changes and dial ALWAYS the changed configuration. Do not dial default, net, nett, etc.

Go!

---

### Post by Erthainel on 2008-08-04
OK, this was supposed to work in czech rep. (at least the czech how to says it should)
```

[Dialer Defaults]
Phone = *99***1#
Username = internet
Password = internet
Stupid Mode = 1
Dial Command = ATDT
Modem = /dev/ttyUSB0
Baud = 460800
Init2 = ATZ
Init3 = ATE0V1&D2&C1S0=0+IFC=2,2
ISDN = 0
Modem Type = Analog Modem
Init5 =at+cgdcont=1,"ip","internet";

```

---

### Post by Erthainel on 2008-08-04
OK, after 10 awful minutes with the vodafone operator who hardly new what linux was, he led me to some kind of settings in XP where "we" found an init string: AT+CGDCONT=16,"IP","internet"; 
He said the number is *99# but it could be *99***1# or *99***(other number)#.
He said that you dont put username and password in windows (what a suprise) but i thing that it shouldnt be blank.

so, I will now try the new init string and i ll see.

---

### Post by Erthainel on 2008-08-04
So, no progress. the new string didnt work... same error

---

### Post by GeorgeVita on 2008-08-04
The error was after the +CGDCONT command?
What about PIN# check? Have you disable it?
Is this modem working with any ather computer or Operating System?

---

### Post by Erthainel on 2008-08-04
Its all written in the first post of the thread but here again:

I am now writing this using a XP Laptop and its working.
There is a PIN on the SIMcard. But others are using it, so i probably dont have the permission to disable it.

The error was the same as with the =1 string.

---

### Post by GeorgeVita on 2008-08-04
I made changes to the wvdial.conf file and checked with my E170 modem.

The ONLY error message I get after +CGDCONT instruction was when I remove the SIM card! So check if you have the SIM card inside at correct position and tell me about the PIN#.

---

### Post by GeorgeVita on 2008-08-04
You can enter pin# by adding the +CPIN=1234 (replace 1234 with your pin#)

Place the above command extending an INITx line like:

Init2 = AT&F E1 V1 X1 &D2 &C1 S0=0 +CPIN=1234

---

### Post by Sealbhach on 2008-08-04
> **Erthainel said:**
> OK, after formating the flashdisk, there goes the report:

```

erthainel@Stormwind:~$ sudo wvdial Defaults
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
ERROR
--> Invalid dial command.
--> Disconnecting at Mon Aug  4 17:43:46 2008
erthainel@Stormwind:~$ 

```

This was the correct init string here... because your modem dialed the carrier.

Try this phone number: *99***1#

So your /etc/wvdial.conf looks like this:

```


[Dialer Nett]
Init1 = ATZ
Init2 = ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
Init3 = AT+CGDCONT=1,"IP","internet"
Modem Type = Analog Modem
ISDN = 0
New PPPD = yes
Stupid Mode = 1
Phone = *99***1#
Modem = /dev/ttyUSB0
Username = internet
Dial Command = ATDT
Password = internet
Baud = 9600
```

If it doesn't work, remove Init string 3. Try it that way.
.

---

### Post by Erthainel on 2008-08-04
the sim card is inside correctly, because i am now connected with it through the XP comp. 

What do you want to know about the pin? it is there. is there a way to leave it or does it have to be disabled

---

### Post by Sealbhach on 2008-08-04
> **Erthainel said:**
> the sim card is inside correctly, because i am now connected with it through the XP comp. 

What do you want to know about the pin? it is there. is there a way to leave it or does it have to be disabled

With my E220, the PIN was not an issue. I would not spend time on that.


.

---

### Post by GeorgeVita on 2008-08-04
The most exciting is that London, Athens and Chech Rep. trying to solve the problem!  I insist on the problem caused by the SIM (possibly the PIN#). A GSM modem does not accept some commands if you are not logged on the network (as your phonebook).  I have already checked that the ERROR after the +CGDCONT command apears when NO SIM. In order to check with the PIN I must switch my laptop to Vista so if you know the PIN# enter it with the +CPIN command in the hspa init string.

---

### Post by Erthainel on 2008-08-04
On the XP mashine i had to fill it in.

---

### Post by Sealbhach on 2008-08-04
> **GeorgeVita said:**
>  I insist on the problem caused by the SIM (possibly the PIN#)

OK, but it was not an issue with me using my E220. 

Erthainel, can you try that other phone number?

```
[Dialer Nett]
Init1 = ATZ
Init2 = ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
Init3 = AT+CGDCONT=1,"IP","internet"
Modem Type = Analog Modem
ISDN = 0
New PPPD = yes
Stupid Mode = 1
Phone = *99***1#
Modem = /dev/ttyUSB0
Username = internet
Dial Command = ATDT
Password = internet
Baud = 9600
```

---

### Post by Erthainel on 2008-08-04
> In order to check with the PIN I must switch my laptop to Vista so if you know the PIN# enter it with the +CPIN command in the hspa init string.

Make a new string or just adjust the AT+CGDCONT string?
Maybe, how should the new string look?
If it doesnt work i will try to remove the pin.

---

### Post by GeorgeVita on 2008-08-04
Ok, the way to learn it is to change the init2 to the following:

Init2 = AT&F E1 V1 X1 &D2 &C1 S0=0 +CPIN?

The +CPIN? will show one of the following:
READY - no PIN required
SIM PIN - device waiting for PIN
SIM PUK - waiting for PUK ... etc

Erthainel can you try it?

(always be sure to SAVE and WVDIAL the appropriate changed tag e.x hspa)

---

### Post by GeorgeVita on 2008-08-04
copy & paste the following

[Dialer hspa]
Modem = /dev/ttyUSB0
Modem Type = Analog Modem
ISDN = 0
Baud = 115200
Username = user
Password = pass
Phone = *99***1#
Stupid Mode =1
Init1 = ATZ
Init2 = AT&F E1 V1 X1 &D2 &C1 S0=0 +CPIN?
Init3 =AT+CGDCONT=16,"IP","internet"

Dial using sudo wvdial hspa

---

### Post by Erthainel on 2008-08-04
```

+CPIN: SIM PIN

```

So? :)

---

### Post by GeorgeVita on 2008-08-04
ok, So your Sim requires PIN!

You must know it, I will test it on my own E170, and in my next post I will tell you the final init line!

---

### Post by GeorgeVita on 2008-08-04
Sorry, I don;t have my pin# at home! You must test the following

Init1 = ATZ
Init2 = AT&F E1 V1 X1 &D2 &C1 S0=0
Init3 = AT+CPIN="1234"
Init4 =AT+CGDCONT=16,"IP","internet"

change the 1234 to your pin#
...waiting

---

### Post by Erthainel on 2008-08-04
Lets hope it will be final.

---

### Post by Erthainel on 2008-08-04
there goes the report:

```

erthainel@Stormwind:~$ sudo wvdial hspa
--> WvDial: Internet dialer version 1.60
--> Cannot get information for serial port.
--> Initializing modem.
--> Sending: ATZ
ATZ
OK
--> Sending: AT&F E1 V1 X1 &D2 &C1 S0=0
AT&F E1 V1 X1 &D2 &C1 S0=0
OK
--> Sending: AT+CPIN="1234"
AT+CPIN="1234"
OK
--> Sending: AT+CGDCONT=1
AT+CGDCONT=1
OK
--> Modem initialized.
--> Sending: ATDT*99***1#
--> Waiting for carrier.
ATDT*99***1#
ERROR
--> Invalid dial command.
--> Disconnecting at Mon Aug  4 21:25:44 2008
erthainel@Stormwind:~$ 



```

---

### Post by GeorgeVita on 2008-08-04
Be patient, we would all be happy with your successive wvdial! ( a little bit Hardier)

Restore the
Init4 =AT+CGDCONT=16,"IP","internet"

I suppose it stops to ...CONT=1

---

### Post by Erthainel on 2008-08-04
OK, it is strange:

```

erthainel@Stormwind:~$ sudo wvdial hspa
--> WvDial: Internet dialer version 1.60
--> Cannot get information for serial port.
--> Initializing modem.
--> Sending: ATZ
ATZ
OK
--> Sending: AT&F E1 V1 X1 &D2 &C1 S0=0
AT&F E1 V1 X1 &D2 &C1 S0=0
OK
--> Sending: AT+CPIN="1234"
AT+CPIN="1234"
OK
--> Sending: AT+CGDCONT=16,"IP","internet"
AT+CGDCONT=16,"IP","internet"
OK
--> Modem initialized.
--> Sending: ATDT*99***1#
--> Waiting for carrier.
ATDT*99***1#
ERROR
--> Invalid dial command.
--> Disconnecting at Mon Aug  4 21:39:51 2008
erthainel@Stormwind:~$ 

```

But when i tried it next with other number, i got an error with the PIN init string. My idea is, maybe the pin must be given only once and is not needed the next connections?

---

### Post by GeorgeVita on 2008-08-04
no, the pin set seems ok (it responds OK),
try to change the dial no to the *99#

note: are you using the terminal command
sudo gedit /etc/wvdial.conf

then SAVE, EXIT and in the same terminal window you are pressing up / down arrow which scrolls previous commands, ENTER at the command you want...1 minute 1 test!

---

### Post by Erthainel on 2008-08-04
```

erthainel@Stormwind:~$ sudo gedit /etc/wvdial.conf
[sudo] password for erthainel: 
erthainel@Stormwind:~$ sudo wvdial hspa
--> WvDial: Internet dialer version 1.60
--> Cannot get information for serial port.
--> Initializing modem.
--> Sending: ATZ
ATZ
OK
--> Sending: AT&F E1 V1 X1 &D2 &C1 S0=0
AT&F E1 V1 X1 &D2 &C1 S0=0
OK
--> Sending: AT+CPIN="1234"
AT+CPIN="1234"
OK
--> Sending: AT+CGDCONT=16,"IP","internet"
AT+CGDCONT=16,"IP","internet"
OK
--> Modem initialized.
--> Sending: ATDT*99#
--> Waiting for carrier.
ATDT*99#
NO CARRIER
--> No Carrier!  Trying again.
--> Sending: ATDT*99#
--> Waiting for carrier.
ATDT*99#
NO CARRIER
--> No Carrier!  Trying again.
--> Sending: ATDT*99#
--> Waiting for carrier.
ATDT*99#
NO CARRIER
--> No Carrier!  Trying again.
--> Sending: ATDT*99#
--> Waiting for carrier.
ATDT*99#
NO CARRIER
--> No Carrier!  Trying again.
--> Sending: ATDT*99#
--> Waiting for carrier.
ATDT*99#
NO CARRIER
--> No Carrier!  Trying again.
--> Sending: ATDT*99#
--> Waiting for carrier.
ATDT*99#
NO CARRIER
--> No Carrier!  Trying again.
--> Sending: ATDT*99#
--> Waiting for carrier.
ATDT*99#
NO CARRIER
--> No Carrier!  Trying again.
--> Sending: ATDT*99#
--> Waiting for carrier.
ATDT*99#
NO CARRIER
--> No Carrier!  Trying again.
--> Sending: ATDT*99#
--> Waiting for carrier.
ATDT*99#
NO CARRIER
--> No Carrier!  Trying again.
--> Sending: ATDT*99#
--> Waiting for carrier.
ATDT*99#
NO CARRIER
--> No Carrier!  Trying again.
--> Sending: ATDT*99#
--> Waiting for carrier.
ATDT*99#
NO CARRIER
--> No Carrier!  Trying again.
Caught signal 2:  Attempting to exit gracefully...
--> Disconnecting at Mon Aug  4 22:02:44 2008
erthainel@Stormwind:~$ 

--> Waiting for carrier.
ATDT*99***1#
ERROR
--> Invalid dial command.
--> Disconnecting at Mon Aug  4 21:39:51 2008
erthainel@Stormwind:~$ 

```
here!

---

### Post by GeorgeVita on 2008-08-04
We are very close because we fix the init string, the PIN lock and the APN setup, my modem after ATDT has the desired "CONNECT!"

--> Sending: AT+CGDCONT=1,"IP","internet"
AT+CGDCONT=1,"IP","internet"
OK
--> Modem initialized.
--> Sending: ATDT*99#
--> Waiting for carrier.
ATDT*99#
CONNECT 7200000
--> Carrier detected.  Starting PPP immediately.

Can you wait for me to find something else?

---

### Post by Erthainel on 2008-08-04
Yesterday, i was tryind to 2:45 am, so till that time comes, i will be here. :)

---

### Post by GeorgeVita on 2008-08-04
add after ISDN = 0 the line
New PPPD = yes

Try and I am searching...

---

### Post by Erthainel on 2008-08-04
I think i saw some option yesterday somwhere on the forum, it was something with the carrier (like ignore, but something else)

i will try it.

---

### Post by GeorgeVita on 2008-08-04
The ignore carrier command is &C0 instead of &C1 (at init2),

but i thing im must get carrier!  Are you using the XP machine to "talk" with me?

---

### Post by Erthainel on 2008-08-04
yes. i am.

---

### Post by Erthainel on 2008-08-04
no, it was something else. it was an option. not in the init, but it hed its own line. but i dont really remember

---

### Post by GeorgeVita on 2008-08-04
Do you know to set Win keep a log file, so we can see the init string that the VMC program uses? It is somewhere at modems (or connections) properties, advanced, report or log file...

If you enable it, after a connection you are openning it and see the AT commands and the results. If you take a printout you will find the &C0 or the +IFC=2,2 

BUT DONOT check all around. We will find the appropriate.

If you cannot find the log, I'll put the Vista HD on my laptop. ok?

---

### Post by Erthainel on 2008-08-04
OK, i will try. DO you have any ICQ/Jabber? This is so slow.
If its to personal for you, you dont have to.

---

### Post by GeorgeVita on 2008-08-04
the command you mentioned is

carrier check = no

(from the man wvdial.conf)

---

### Post by Erthainel on 2008-08-04
should i put it there??

and:

is this the log?
(its a little czech :) )

```

08-04-2008 22:43:12.875 - Soubor: C:\WINDOWS\system32\tapisrv.dll, verze 5.1.2600    
08-04-2008 22:43:12.875 - Soubor: C:\WINDOWS\system32\unimdm.tsp, verze 5.1.2600    
08-04-2008 22:43:12.875 - Soubor: C:\WINDOWS\system32\unimdmat.dll, verze 5.1.2600    
08-04-2008 22:43:12.875 - Soubor: C:\WINDOWS\system32\uniplat.dll, verze 5.1.2600    
08-04-2008 22:43:12.875 - Soubor: C:\WINDOWS\system32\drivers\modem.sys, verze 5.1.2600    
08-04-2008 22:43:12.875 - Soubor: C:\WINDOWS\system32\modemui.dll, verze 5.1.2600    
08-04-2008 22:43:12.875 - Soubor: C:\WINDOWS\system32\mdminst.dll, verze 5.1.2600    
08-04-2008 22:43:12.875 - Typ modemu: HUAWEI Mobile Connect - 3G Modem
08-04-2008 22:43:12.875 - Cesta k souboru INF modemu: oem24.inf
08-04-2008 22:43:12.875 - Sekce souboru INF modemu: Modem0
08-04-2008 22:43:12.875 - Odpovídající ID hardwaru: usb\vid_12d1&pid_1003&mi_00 
08-04-2008 22:43:12.921 - 460800,8,N,1, ctsfl=0, rtsctl=1
08-04-2008 22:43:12.968 - Inicializace modemu
08-04-2008 22:43:12.968 - P&#345;i inicializaci modemu je silný signál CD.
08-04-2008 22:43:12.968 - Odesláno: AT<cr>
08-04-2008 22:43:12.984 - P&#345;ijato: <cr><lf>OK<cr><lf>
08-04-2008 22:43:12.984 - Interpretovaná odezva: OK
08-04-2008 22:43:13.000 - Odesláno: AT&FE0V1X1&D2&C1S0=0<cr>
08-04-2008 22:43:13.000 - P&#345;ijato: <cr><lf>OK<cr><lf>
08-04-2008 22:43:13.000 - Interpretovaná odezva: OK
08-04-2008 22:43:13.015 - Odesláno: AT<cr>
08-04-2008 22:43:13.015 - P&#345;ijato: <cr><lf>OK<cr><lf>
08-04-2008 22:43:13.015 - Interpretovaná odezva: OK
08-04-2008 22:43:13.015 - Odesílání inicializa&#269;ního p&#345;íkazu uživatele.
08-04-2008 22:43:13.031 - Odesláno: AT+CGDCONT=16,"IP","internet";<cr>
08-04-2008 22:43:13.046 - P&#345;ijato: <cr><lf>OK<cr><lf>
08-04-2008 22:43:13.046 - Interpretovaná odezva: OK
08-04-2008 22:43:13.046 - Modem &#269;eká na hovor.
08-04-2008 22:43:13.046 - Odesláno: ATS0=0<cr>
08-04-2008 22:43:13.093 - P&#345;ijato: <cr><lf>OK<cr><lf>
08-04-2008 22:43:13.093 - Interpretovaná odezva: OK
08-04-2008 22:43:13.093 - 115200,8,N,1, ctsfl=1, rtsctl=2
08-04-2008 22:43:13.125 - Inicializace modemu
08-04-2008 22:43:13.125 - Odesláno: AT<cr>
08-04-2008 22:43:13.140 - P&#345;ijato: <cr><lf>OK<cr><lf>
08-04-2008 22:43:13.140 - Interpretovaná odezva: OK
08-04-2008 22:43:13.140 - Odesláno: AT&FE0V1X1&D2&C1S0=0<cr>
08-04-2008 22:43:13.171 - P&#345;ijato: <cr><lf>OK<cr><lf>
08-04-2008 22:43:13.171 - Interpretovaná odezva: OK
08-04-2008 22:43:13.187 - Odesláno: AT<cr>
08-04-2008 22:43:13.187 - P&#345;ijato: <cr><lf>OK<cr><lf>
08-04-2008 22:43:13.187 - Interpretovaná odezva: OK
08-04-2008 22:43:13.187 - Odesílání inicializa&#269;ního p&#345;íkazu uživatele.
08-04-2008 22:43:13.203 - Odesláno: AT+CGDCONT=16,"IP","internet";<cr>
08-04-2008 22:43:13.218 - P&#345;ijato: <cr><lf>OK<cr><lf>
08-04-2008 22:43:13.218 - Interpretovaná odezva: OK
08-04-2008 22:43:13.218 - Modem vytá&#269;í.
08-04-2008 22:43:13.218 - Odesláno: ATDT*##***###<cr>
08-04-2008 22:43:13.250 - P&#345;ijato: <cr><lf>CONNECT 236800<cr><lf>
08-04-2008 22:43:13.250 - Interpretovaná odezva: P&#345;ipojit
08-04-2008 22:43:13.250 - Navázáno p&#345;ipojení, ale signál CD byl slabý. &#268;eká se, až bude silný.
08-04-2008 22:43:13.265 - Po 20ms &#269;ekání je signál CD stále slabý.
08-04-2008 22:43:13.281 - Po 20ms &#269;ekání je signál CD stále slabý.
08-04-2008 22:43:13.296 - Signál CD byl zesílen.
08-04-2008 22:43:13.296 - P&#345;ipojení bylo navázáno rychlostí 236800 b/s.
08-04-2008 22:43:13.296 - Oprava chyb je vypnuta &#269;i neznámá.
08-04-2008 22:43:13.296 - Komprese dat je vypnuta &#269;i neznámá.

```

---

### Post by GeorgeVita on 2008-08-04
ok now try, ATDT*99***16#

---

### Post by Sealbhach on 2008-08-04
Still no luck?

Maybe you could try to download the Vodafone driver again...

[https://forge.betavine.net/frs/download.php/76/vodafone-mobile-connect-card-driver-for-linux_1.99.17_i386.deb](https://forge.betavine.net/frs/download.php/76/vodafone-mobile-connect-card-driver-for-linux_1.99.17_i386.deb)



.

---

### Post by Erthainel on 2008-08-04
Just for others, it is still not yet solved. I am open to any suggestions!!

```

erthainel@Stormwind:~$ sudo gedit /etc/wvdial.conf
[sudo] password for erthainel: 
erthainel@Stormwind:~$ sudo wvdial hspa
--> WvDial: Internet dialer version 1.60
--> Cannot get information for serial port.
--> Initializing modem.
--> Sending: ATZ
ATZ
OK
--> Sending: AT&F E1 V1 X1 &D2 &C1 S0=0
AT&F E1 V1 X1 &D2 &C1 S0=0
OK
--> Sending: AT+CPIN="1234"
AT+CPIN="1234"
OK
--> Sending: AT+CGDCONT=1,"IP","internet"
AT+CGDCONT=1,"IP","internet"
OK
--> Modem initialized.
--> Sending: ATDT*99***1#
--> Waiting for carrier.
ATDT*99***1#
NO CARRIER
--> No Carrier!  Trying again.
--> Sending: ATDT*99***1#
--> Waiting for carrier.
ATDT*99***1#
NO CARRIER
--> No Carrier!  Trying again.
--> Sending: ATDT*99***1#
--> Waiting for carrier.
ATDT*99***1#
NO CARRIER
--> No Carrier!  Trying again.
--> Sending: ATDT*99***1#
--> Waiting for carrier.
ATDT*99***1#
NO CARRIER
--> No Carrier!  Trying again.
Caught signal 2:  Attempting to exit gracefully...
--> Disconnecting at Tue Aug  5 00:01:45 2008
erthainel@Stormwind:~$

```

wvdial.conf
```

[Dialer hspa]
Modem = /dev/ttyUSB0
Modem Type = Analog Modem
ISDN = 0
New PPPD = yes
Baud = 115200
Username = user
Password = pass
Phone = *99***1#
Stupid Mode =1
Init1 = ATZ
Init2 = AT&F E1 V1 X1 &D2 &C1 S0=0
Init3 = AT+CPIN="1234"
Init4 =AT+CGDCONT=1,"IP","internet"

```

---

### Post by Sealbhach on 2008-08-04
Try adding this line to /etc/wvdial.conf

Carrier Check = no


Also you have 

Stupid Mode =1

Change it to:

Stupid Mode = 1



.

---

### Post by Sealbhach on 2008-08-04
> **Sealbhach said:**
> Try adding this line to /etc/wvdial.conf

```
Carrier Check = no
```


Got it from here:


[https://help.ubuntu.com/community/DialupModemHowto/SetUpDialer#head-277fdde88a3b04feee00e14834388d58d7add4f9](https://help.ubuntu.com/community/DialupModemHowto/SetUpDialer#head-277fdde88a3b04feee00e14834388d58d7add4f9)


>       add X3 to Init2 (means dial without waiting)
    

      add Carrier Check = no as a new line (useful for Smartlink modems)
    

      add Stupid mode = on as a new line (will start pppd immediately--required by some ISPs) 

..

---

### Post by GeorgeVita on 2008-08-05
Good Morning,

I thing that the wvdial.conf on post#56 must work!

If you have a "live" ubuntu DVD run it on the XP machine and try the changes there with your modem. I check it in my laptop, and you can do the same (terminal, sudo gedit, sudo wvdial) without altering the test machine.

---

### Post by Erthainel on 2008-08-05
I dont have the CDs with me. 
You think the .conf from the #56 must work?
I will try other combinations.
--
I finally downloaded the driver, but there are another 21 .debs to download...

---

### Post by Erthainel on 2008-08-05
> **Sealbhach said:**
> Try adding this line to /etc/wvdial.conf

Carrier Check = no


Also you have 

Stupid Mode =1

Change it to:

Stupid Mode = 1



.

No difference. Still the same.
Today at 17:00 i probably wont have the XP comp anymore...
And i really dont want to install vista on my already ubuntu mashine... I removed it with great hapiness :)

---

### Post by Sealbhach on 2008-08-05
> **Erthainel said:**
> I dont have the CDs with me. 
You think the .conf from the #56 must work?


It looks like you're very close to success.

GeorgeVita, do you think maybe it's waiting for a dial tone?


.

---

### Post by GeorgeVita on 2008-08-05
Hi, I wouldn't like to say it but "I think that this is a hardware problem!"
I mean something in the power supply. That's why I propose to Check the modem to the other laptop with LIVE CD, or even to be sure that this modem was working to the UBUNTU pc before installing 8.04.

Note: I begin involving with Ubuntu & Forums just after buying the E170 modem!  I am very happy with 8.04 and also the E170 BUT after placing external capacitors (external=without altering waranty on E170 or Laptop).

---

### Post by Erthainel on 2008-08-05
I am not sure what to try. I have no CD and I have no other connection to use. I am kind of lost.

---

### Post by Sealbhach on 2008-08-05
Hi,

This is a thread I used when I first set up my modem,

[http://www.boards.ie/vbulletin/showpost.php?p=55779679&postcount=8](http://www.boards.ie/vbulletin/showpost.php?p=55779679&postcount=8)

It might be worth giving it a try... you will obviously need to change some of the lines to your own.

Oliver.


.

---

### Post by Erthainel on 2008-08-05
ill try it

---

### Post by Erthainel on 2008-08-05
Thanks very much, but it did not make any difference.
Im getting desperate...

---

### Post by Sealbhach on 2008-08-05
> **Erthainel said:**
> Thanks very much, but it did not make any difference.
Im getting desperate...


Another thing you can try... it may work for your modem.

**Out-of-box Solution**

There is also out-of-box solution named Salutis Connect. Connect your Huawei E200 or E169G device to USB port, open Terminal and enter these installation commands: 


```
sudo -s
echo deb http://repository.salutis.sk/production ./ >> /etc/apt/sources.list
apt-get update
apt-get install salutis-connect
```

After installation click on Salutis Connect icon in Applications -> Internet menu section and enjoy. To disconnect the device, click on Salutis Connect again and the device will be disconnected. 

From: [https://help.ubuntu.com/community/DialupModemHowto/Huawei/E220](https://help.ubuntu.com/community/DialupModemHowto/Huawei/E220)




.

---

### Post by Erthainel on 2008-08-05
I am afraid i cant do that. I have no other connection to the internet available.

---

### Post by Sealbhach on 2008-08-05
> **Erthainel said:**
> I am afraid i cant do that. I have no other connection to the internet available.

I've attached it here.

---

### Post by Erthainel on 2008-08-05
doesent it have any other dependencies??

---

### Post by Sealbhach on 2008-08-05
> **Erthainel said:**
> doesent it have any other dependencies??

Have you tried installing it? Does it ask for dependencies?


.

---

### Post by Erthainel on 2008-08-05
OK, no dependencies needed, but i got no clue how to disable the pin.

---

### Post by Erthainel on 2008-08-05
PIN disabled through the phone, at least i think. so ill go try it.

---

### Post by Sealbhach on 2008-08-05
> **Erthainel said:**
> PIN disabled through the phone, at least i think. so ill go try it.

Yes, that's what they did in this thread here:

[http://ubuntuforums.org/showthread.php?t=262867&page=15](http://ubuntuforums.org/showthread.php?t=262867&page=15)


I really hope it works for you!


.

---

### Post by Erthainel on 2008-08-05
Wow! I am now writing from ubuntu!

Sealbhach, the program you sent me did not work, but i had to remove the PIN to try it. After it didnt work, i removed the init with the pin and tried dialing without the pin and "Connected 236800"!!

Thank you both. If you need anything, contact me and i will be happy to help you till 1:30 AM like you did! 

(Btw, is there any way i can see the speed or downloaded KBs?)

---

### Post by Sealbhach on 2008-08-05
> **Erthainel said:**
> 

(Btw, is there any way i can see the speed or downloaded KBs?)

Good, I'm really happy you got it going!!! :guitar:

If you right click on the Panel, you can find a network monitor which can show you download and upload speeds.

Also test it on [www.speedtest.net](www.speedtest.net)



.

---

### Post by Erthainel on 2008-08-05
on what panel? if you mean the place where wireless connection is shown, nothing is there. "No connection"

---

### Post by Sealbhach on 2008-08-05
> **Erthainel said:**
> on what panel? if you mean the place where wireless connection is shown, nothing is there. "No connection"

Sorry, I was in a hurry when I wrote that.

Right click on the panel, select Add to Panel nand then select Modem Monitor.

Happy internets to you!

.

---

### Post by GeorgeVita on 2008-08-05
Bravo, well done! It was a little bit harder but the result counts!

---

### Post by Erthainel on 2008-08-05
It doesnt work...

---

### Post by Sealbhach on 2008-08-05
> **Erthainel said:**
> It doesnt work...

You got working once, you will again. I had a LOT of pain getting my E220 working at first. But I learned a lot too - next time, you get it working, you will find that you did it an easier,faster way, you'll see!


Maybe start a new thread with your present problem, and get ideas from other people?

.

---

