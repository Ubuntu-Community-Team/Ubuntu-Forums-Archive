---
title: "Configure Airtel GPRS/EDGE via Bluetooth"
date: 2006-09-14
forum: Networking &amp; Wireless
---

### Post by mukherjee.siddhartha on 2006-09-14
[SIZE=2][COLOR=DimGray][COLOR=Blue]**I AM RE-POSTING HERE BECAUSE, I TRIED TO POST IN HOWTO SECTION, BUT IT DID NOT APPEARED, I DONT KNOW WHY!**[/COLOR]

How to configure internet access through GPRS/EDGE, using bluetooth connection with your GSM phone.

I am using ubuntu and Nokia 6630 phone with Airtel Connection, but this will work with any distribution and any bluetooth capable phone.. 

_** * Requirements:**_
  
   1) GPRS/EDGE Enabled Phone (Here Nokia 6630)
  2) GPRS Connection (Here Airtel, Kolkata, India)
  3) BlueTooth Dongle
  4) bluez-utils 
       [/COLOR][/SIZE][SIZE=2][COLOR=DimGray]> sudo apt-get install bluez-utils[/COLOR][/SIZE][SIZE=2][COLOR=DimGray]
  5) openobex 
[/COLOR][/SIZE]> [SIZE=2][COLOR=DimGray][Download here]("http://sourceforge.net/projects/openobex") and compile, 
      You need gawk and gcc, 
sudo apt-get install gawk 
sudo apt-get install gcc[/COLOR][/SIZE][SIZE=2][COLOR=DimGray]
  6) ppp
      [/COLOR][/SIZE]> [SIZE=2][COLOR=DimGray]sudo apt-get install ppp[/COLOR][/SIZE][SIZE=2][COLOR=DimGray]
  7) latest 2.6 kernel

[/COLOR]_**[COLOR=DimGray] * Now the simple easy steps:[/COLOR]**_[/SIZE][SIZE=2]
[/SIZE][SIZE=2][COLOR=DimGray]
_**Step 1.**_
Plugin The bluetooth dongle and activate the bluetooth on your mobile
_**Step 2.**_
**       Kernel Configuration** 
You may ignore this part if your hardware is recognised, Ubuntu Magic:wink:
[/COLOR][/SIZE][SIZE=2]> CONFIG_BT=y 
CONFIG_BT_L2CAP=m 
CONFIG_BT_SCO=m 
CONFIG_BT_RFCOMM=m 
CONFIG_BT_RFCOMM_TTY=y 
CONFIG_BT_BNEP=m 
CONFIG_BT_BNEP_MC_FILTER=y 
CONFIG_BT_BNEP_PROTO_FILTER=y 
CONFIG_BT_HIDP=m 
## Bluetooth device drivers 
CONFIG_BT_HCIUSB=m 
CONFIG_BT_HCIUSB_SCO=y 
CONFIG_BT_HCIUART=m 
CONFIG_BT_HCIUART_H4=y 
CONFIG_BT_HCIUART_BCSP=y 
CONFIG_BT_HCIBCM203X=m 
CONFIG_BT_HCIBPA10X=m 
CONFIG_BT_HCIBFUSB=m 
CONFIG_BT_HCIDTL1=m 
CONFIG_BT_HCIBT3C=m 
CONFIG_BT_HCIBLUECARD=m 
CONFIG_BT_HCIBTUART=m 
CONFIG_BT_HCIVHCI=m 
## PPP 
CONFIG_PPP=y 
CONFIG_PPP_ASYNC=y 
CONFIG_PPP_SYNC_TTY=m 
CONFIG_PPP_DEFLATE=m 
CONFIG_PPP_BSDCOMP=m 
CONFIG_PPP_MPPE=m [/SIZE][SIZE=2][COLOR=DimGray]    [U][B]Step 3.
[/B][/U]Issue this command
[/COLOR][/SIZE][SIZE=2]> hcitool scan It will give you an output like this
> Scanning ...
        00:11:9F:grin:1:05:A4       Nokia 6630 [COLOR=Blue]Note/Copy the address **"00:11:9F :grin:1:05:A4" **somewhere.
This is the bluetooth address of the phone.
[/COLOR]
[U][B]Step 4.
[/B][/U]Issue this command> sudo vi /etc/bluetooth/pin-helper Put this on that file and save
[/SIZE]> [SIZE=2]#!/bin/sh[/SIZE][SIZE=2]
echo -n "PIN:" cat /etc/bluetooth/pin[/SIZE][SIZE=2][COLOR=Blue]also remember to check the file "[/COLOR][COLOR=Blue]/etc/bluetooth/pin"
which should have something like this "1234", If it is not there create that files and put "1234"
[/COLOR]

[U][B]Step 5.
[/B][/U]Issue this
> sudo vi /etc/bluetooth/rfcomm.conf Put this
> rfcomm0 {
 bind yes;
 device 00:11:9F:grin:1:05:A4;
 channel 1;
 comment "Nokia";
} [/SIZE][SIZE=2][COLOR=Red]Remember to replace this "00:11:9F:grin:1:05:A4" with the address you copied in step 3. [/COLOR][/SIZE][SIZE=2] 

[U][B]Step 6.
[/B][/U]
Create a file > sudo  vi /etc/ppp/peers/airtel Put this
> /dev/rfcomm0 115200 
connect '/usr/sbin/chat -v -f /etc/ppp/chat-gprs'
crtscts
modem -detach
noccp
defaultroute
usepeerdns
noauth
ipcp-accept-remote
ipcp-accept-local
noipdefault  

**_ Step 7._**
Create a file
> sudo vi /etc/ppp/chat-gprs Put this
> '' ATZ OK 
AT+CGDCONT=1,"IP","[airtelgprs.com]("http://airtelgprs.com/")"
OK "ATD*99***1#"
CONNECT '' [/SIZE][SIZE=2][COLOR=Red]You need to ask your service provider and replace the "[ airtelgprs.com]("http://airtelgprs.com/")"
and "*99***1#", these are the IP/host name of gprs provider and dialup no.
[/COLOR][/SIZE][SIZE=2]_**Step 7.**_
**[COLOR=Red]YOU ARE DONE! THATS IT? YEAH....[/COLOR]**
just issue this command
> pppd call airtel 
Thanks..Enjoy Ubuntu.
[/SIZE]

---

### Post by mukherjee.siddhartha on 2006-09-14
Sorry for duplicate post
[http://ubuntuforums.org/showthread.php?t=257091](http://ubuntuforums.org/showthread.php?t=257091)

The moderator may delete this one.
And let it be at HOW TO section.

---

### Post by mthakur2006 on 2007-05-25
does this work on fiesty?

---

### Post by deepakprasad on 2007-08-03
hi guys, have tried every trick in the book to connect using gprs (Airtel) on nokia 9300 with bt & cable. it works fine on my winxp desktop, but am unable to do so in my laptop Ubunto 7.04. with cable i get error code 16. A modem hung up the phine and have not been able to pair my phone with laptop. pls. need help urgently. using a compaq presario c303tu, intel corfe solo, 760 mb ram .
 thanks in advance
Deepak Prasad

---

### Post by fazillatheef on 2007-09-07
In Ubuntu 7.04 just install the application gnome-bluez and before doing the command 



Just pair the device (and do that from the Phone ,that worked for me) and authorize the device.
After that

> pppd call airtel

---

### Post by suniltr77 on 2007-10-05
Give link to the bluez utilities. If there is any alternative for going the command line , describe.
I am a newbe to Linux.Just switched over from Windows.
Help me [email]Suniltr77@yahoo.com[/email]

---

### Post by sumesh on 2007-10-23
Thank u very much....dear friend...
I solved the problem...with ur help...but with a slight change....
I am using USB for connection...so first configure usb..modem with
** lsusb** first
then..
sudo /sbin/modprobe usbserial vendor=0x421 product=0x43a...
then
wvdialconf create
then
sudo gedit /etc/wvdial.conf
in that text window add ur gprs configaration
for airtel it is airtelgprs.com
thanks...
sumesh

---

### Post by sumesh on 2007-10-23
Those who are using USB and AIRTEL...try the following
Connect your phone via datacable
open terminal & type 

lsusb

now u will get the following output

owais@owais-desktop:~$ lsusb
Bus 002 Device 001: ID 0000:0000 
Bus 001 Device 004: ID 0421:0445 Nokia Mobile Phones 
Bus 001 Device 002: ID 046d:092f Logitech, Inc. 
Bus 001 Device 001: ID 0000:0000 
owais@owais-desktop:~$ 


it is on my compter,ur will not be exactly the same...

Now note the line in which NOkia Mobile Phones is written...it has two number one is 0421 & other is 0445...we'll take these numbers as 0x421 & 0x445

0421 is the Vendor ID & 0445 is the Product ID

Now enter this comand.

sudo /sbin/modprobe usbserial vendor=0x(vid) product=0x(pid)

eg, in my case::: sudo /sbin/modprobe usbserial vendor=0×421 product=0×445

Now enter this command

wvdialconf create
u'll get a long output which will be like 

Scanning your serial ports for a modem.
Port Scan: S0 S1 S2 S3
WvModem: Cannot get information for serial port.
ttyACM0: ATQ0 V1 E1 — OK
ttyACM0: ATQ0 V1 E1 Z — OK
ttyACM0: ATQ0 V1 E1 S0=0 — OK
ttyACM0: ATQ0 V1 E1 S0=0 &C1 — OK
ttyACM0: ATQ0 V1 E1 S0=0 &C1 &D2 — OK
ttyACM0: ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0 — OK
ttyACM0: Modem Identifier: ATI — Nokia
ttyACM0: Speed 4800: AT — OK
ttyACM0: Speed 9600: AT — OK
ttyACM0: Speed 19200: AT — OK
ttyACM0: Speed 38400: AT — OK
ttyACM0: Speed 57600: AT — OK
ttyACM0: Speed 115200: AT — OK
ttyACM0: Speed 230400: AT — OK
ttyACM0: Speed 460800: AT — OK
ttyACM0: Max speed is 460800; that should be safe.
ttyACM0: ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0 — OK
Found an USB modem on /dev/ttyACM0.
Modem configuration written to create.
ttyACM0: Speed 460800; init “ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0?

NOw.. notice the output says that there is a modem at /dev/ttyACM0 & max speed is 460800

now enter this command

sudo gedit /etc/wvdial.conf

A file will open in text editor...now delete everything in that file & paste the following there

It must look like this:-
[Dialer Defaults]
Init1 = ATZ
Init2 = ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
Init3 = AT+CGDCONT=1,"IP","orangeinternet"
Modem Type = USB Modem
Baud = 460800
New PPPD = yes
Modem = /dev/ttyACM0
ISDN = 0
Phone = *99 ***1#
Password = orange
Username = orange

Then launch the connection with:-
$ wvdial

And close the connection with:-
Ctrl^C

save the file & you are done


NOw whenevr u need to connect...open terminal & type wvdial,,wait till some sort of IP adress is displayed like

pppd: ?[06][06][08]` [06][08]
primary DNS address 218.248.240.135
pppd: ?[06][06][08]` [06][08]
secondary DNS address 218.248.240.79
pppd: ?[06][06][08]` [06][08]

Now you are connected....hit cntrl+c to dissconnect...:lolflag:

---

### Post by sumesh on 2007-10-23
Sorry I have posted it for orrange net work
use airtelgprs.com insted og orrange....
[Dialer Defaults]
Init1 = ATZ
Init2 = ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
Init3 = AT+CGDCONT=1,"IP","airtelgprs.com"
Modem Type = USB Modem
Baud = 460800
New PPPD = yes
Modem = /dev/ttyACM0
ISDN = 0
Phone = *991#
Password = airtel
Username = airtel

Then launch the connection with:-
$ wvdial

And close the connection with:-
Ctrl^C

Okay....:guitar::lolflag:

---

### Post by cdinz on 2007-10-25
> **sumesh said:**
> Sorry I have posted it for orrange net work
use airtelgprs.com insted og orrange....
[Dialer Defaults]
Init1 = ATZ
Init2 = ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
Init3 = AT+CGDCONT=1,"IP","airtelgprs.com"
Modem Type = USB Modem
Baud = 460800
New PPPD = yes
Modem = /dev/ttyACM0
ISDN = 0
Phone = *991#
Password = airtel
Username = airtel

Then launch the connection with:-
$ wvdial

And close the connection with:-
Ctrl^C

Okay....:guitar::lolflag:


Tried the same settings but I am not able to connect.... Its opening the port and dialing but not able to get an IP address.....:confused::confused::confused:

---

### Post by pigbig842001 on 2007-10-30
> **cdinz said:**
> Tried the same settings but I am not able to connect.... Its opening the port and dialing but not able to get an IP address.....:confused::confused::confused:
```

[Dialer Defaults]
Init1 = ATZ
Init2 = ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
Init3 = AT+CGDCONT=1,"IP","airtelgprs.com"
Modem Type = USB Modem
Baud = 460800
New PPPD = yes
Modem = /dev/ttyACM0
ISDN = 0
Phone = *99***1#
Password = a
Username = b

```
 
These lines should help you. Because I believe that **it would work definitely.**

---

### Post by pigbig842001 on 2007-10-30
This is what I get when dialed.
```

nitro@Nitrous-Fumes:~$ sudo wvdial
[sudo] password for nitro:
WvDial<*1>: WvDial: Internet dialer version 1.56
WvModem<*1>: Cannot get information for serial port.
WvDial<*1>: Initializing modem.
WvDial<*1>: Sending: ATZ
WvDial Modem<*1>: ATZ
WvDial Modem<*1>: OK
WvDial<*1>: Sending: ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
WvDial Modem<*1>: ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
WvDial Modem<*1>: OK
WvDial<*1>: Sending: AT+CGDCONT=1,"IP","internet"
WvDial Modem<*1>: AT+CGDCONT=1,"IP","internet"
WvDial Modem<*1>: OK
WvDial<*1>: Modem initialized.
WvDial<*1>: Sending: ATDT*99***1#
WvDial<*1>: Waiting for carrier.
WvDial Modem<*1>: ATDT*99***1#
WvDial Modem<*1>: CONNECT
WvDial Modem<*1>: ~[7f]}#@!}!} } }2}#}$@#}!}$}%\}"}&} }*} } g}%~
WvDial<*1>: Carrier detected.  Waiting for prompt.
WvDial Modem<*1>: ~[7f]}#@!}!} } }2}#}$@#}!}$}%\}"}&} }*} } g}%~
WvDial<*1>: PPP negotiation detected.
WvDial<Notice>: Starting pppd at Tue Oct 30 22:15:25 2007
WvDial<Notice>: Pid of pppd: 8143
WvDial<*1>: Using interface ppp0
WvDial<*1>: pppd: 
WvDial<*1>: pppd: 
WvDial<*1>: pppd: 
WvDial<*1>: pppd: 
WvDial<*1>: local  IP address 10.8.248.87
WvDial<*1>: pppd: 
WvDial<*1>: remote IP address 10.6.6.6
WvDial<*1>: pppd: 
WvDial<*1>: primary   DNS address 202.56.250.5
WvDial<*1>: pppd: 
WvDial<*1>: secondary DNS address 202.56.250.6
WvDial<*1>: pppd: 

```


And the connection is stable too. Didn't get a disconnection till now. Too Good.

---

### Post by vasantcs on 2008-01-23
:) The wvdial for usb cable worked for my n72 as well. thank you very much for the help...

---

### Post by ptamdagr8 on 2008-03-01
I've tried those and according to the instruction u've given, i should probably be surfing the net now (I think). these are what i get

while trying to connect through USB serial cable (m using nokia 5300)

[root@localhost ~]# wvdial

--> WvDial: Internet dialer version 1.54.0
--> Cannot get information for serial port.
--> Initializing modem.

--> Sending: ATZ
ATZ
OK

--> Sending: ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
OK

--> Sending: AT+CGDCONT=1,"IP","airtelgprs.com"
AT+CGDCONT=1,"IP","airtelgprs.com"
OK

--> Modem initialized.

--> Sending: ATDT*99#

--> Waiting for carrier.
ATDT*99#
CONNECT
~[7f]}#@!}!} } }2}#}$@#}!}$}%\}"}&} }*} } g}%~

--> Carrier detected.  Starting PPP immediately.

--> Starting pppd at Sat Mar  1 18:03:09 2008

--> pid of pppd: 3101

--> Using interface ppp0

--> local  IP address 117.96.23.226

--> remote IP address 10.6.6.6

--> primary   DNS address 202.56.250.5

--> secondary DNS address 202.56.250.6




WHILE dialing using BLUETOOTH


[root@localhost ~]# wvdial airtel

--> WvDial: Internet dialer version 1.54.0

--> Cannot get information for serial port.

--> Initializing modem.

--> Sending: ATZ
ATZ
OK

--> Sending: ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
OK
--> Sending: AT+CGDCONT=1,"IP","airtelgprs.com"
AT+CGDCONT=1,"IP","airtelgprs.com"
OK

--> Modem initialized.

--> Sending: ATDT*99#

--> Waiting for carrier.
ATDT*99#
CONNECT
~[7f]}#@!}!} } }2}#}$@#}!}$}%\}"}&} }*} } g}%~

--> Carrier detected.  Starting PPP immediately.

--> Starting pppd at Sat Mar  1 18:08:07 2008

--> pid of pppd: 3304

--> Using interface ppp0

--> local  IP address 117.96.14.129
--> remote IP address 10.6.6.6

--> primary   DNS address 202.56.250.5

--> secondary DNS address 202.56.250.6





AND this is my wvdial.conf


[Dialer airtel]

Init1 = ATZ

Init2 = ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0

Init3 = AT+CGDCONT=1,"IP","airtelgprs.com"

stupid mode = 1

Modem Type = DUN Modem

Baud = 460800

New PPPD = yes

Modem = /dev/ttyACM0

ISDN = 0

Phone = *99#

Password = airtel

Username = airtel



[Dialer Defaults]

Init1 = ATZ

Init2 = ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0

Init3 = AT+CGDCONT=1,"IP","airtelgprs.com"

Modem Type = USB Modem
Baud = 460800

New PPPD = yes

Modem = /dev/ttyACM0

ISDN = 0
Phone = *99#

Password = airtel

Username = airtel

Stupid Mode = 1



And this is the  rfcomm.conf


#
# RFCOMM configuration file.
#



rfcomm0 {

	#
	# Automatically bind the device at startup
		bind yes;

	#
	
#	

	# Bluetooth address of the device
		device 00:1B:AF:23:B9:7B;
	
#
#	
	# RFCOMM channel for the connection
		channel	1;
	
#
#	
	# Description of the connection
	comment 	"Dial Up";

#
}


As far as I know, the network should be working but i still couldnt browse any site even after i get those while i dial through wvdial. Is there something else i need to complete. Can anybody help me??

and 1 more thing, after using the command 'wvdial', i pressed "ctrl+z". after that how do i disconnected the gprs. I mean using 'ctrl+c" works only before u use 'ctrl+z'

---

### Post by alanzkorner on 2008-06-23
Hello ,

Well  I tried to connect my airtel gprs with datacable . I followed 
the steps given to connect with datacable , initially I was getting an error when I typed the command 

wvdialconf create

I got the out put till 

Scanning your serial ports for a modem.
Port Scan: S0 S1 S2 S3
WvModem: Cannot get information for serial port.
ttyACM0: ATQ0 V1 E1 — OK
ttyACM0: ATQ0 V1 E1 Z — OK
ttyACM0: ATQ0 V1 E1 S0=0 — OK
ttyACM0: ATQ0 V1 E1 S0=0 &C1 — OK
ttyACM0: ATQ0 V1 E1 S0=0 &C1 &D2 — OK
ttyACM0: ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0 — OK
ttyACM0: Modem Identifier: ATI — Nokia
ttyACM0: Speed 4800: AT — OK
ttyACM0: Speed 9600: AT — OK
ttyACM0: Speed 19200: AT — OK
ttyACM0: Speed 38400: AT — OK
ttyACM0: Speed 57600: AT — OK
ttyACM0: Speed 115200: AT — OK
ttyACM0: Speed 230400: AT — OK
ttyACM0: Speed 460800: AT — OK
ttyACM0: Max speed is 460800; that should be safe.
ttyACM0: ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0 — OK
Found an USB modem on /dev/ttyACM0.

after this instead of getting the listing that 
added to create , I got the error that unable to 
add to create , file or directory does not exist . 

and after following the further steps I was not able to 
get connected . So I tried the step 

wvdialconf create
 2 or 3 times which was giving the same error but with a 
modification unable to open create.tmp but in the next attempt the error disappeared but when I dial I am not getting connected 

this is the error that I got 

alanjohn@alanjohn-desktop:~$ wvdial
WvDial<*1>: WvDial: Internet dialer version 1.56

WvModem<*1>: Cannot get information for serial port.
WvDial<*1>: Initializing modem.

WvDial<*1>: Sending: ATZ
WvDial Modem<*1>: ATZ
WvDial Modem<*1>: OK
WvDial<*1>: Sending: ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
WvDial Modem<*1>: ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
WvDial Modem<*1>: OK
WvDial<*1>: Sending: AT+CGDCONT=1,"IP","airtelgprs.com"
WvDial Modem<*1>: AT+CGDCONT=1,"IP","airtelgprs.com"
WvDial Modem<*1>: OK
WvDial<*1>: Modem initialized.
WvDial<*1>: Sending: ATDT*991#
WvDial<*1>: Waiting for carrier.
WvDial Modem<*1>: ATDT*991#
WvDial Modem<*1>: ERROR
WvDial<Err>: Invalid dial command.
WvDial<*1>: Disconnecting at Mon Jun 23 11:47:47 2008



Could any one help  me to get this resolved :(:(

Alan

---

