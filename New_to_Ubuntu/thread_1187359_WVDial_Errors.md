---
title: "WVDial Errors"
date: 2009-06-14
forum: New to Ubuntu
---

### Post by chome4 on 2009-06-14
Having struggled to get it working in Jaunty, I now get the errors shown. At least I'm nearly there!

Can anyone point me in the right direction based on the error?

=====================================================

john@john-desktop:~$ sudo wvdialconf
Editing `/etc/wvdial.conf'.

Scanning your serial ports for a modem.

ttyS0<*1>: ATQ0 V1 E1 -- failed with 2400 baud, next try: 9600 baud
ttyS0<*1>: ATQ0 V1 E1 -- failed with 9600 baud, next try: 115200 baud
**[COLOR=Red]ttyS0<*1>: ATQ0 V1 E1 -- and failed too at 115200, giving up.[/COLOR]**
Modem Port Scan<*1>: S1   S2   S3   
**[COLOR=Red]WvModem<*1>: Cannot get information for serial port.[/COLOR]**
ttyUSB0<*1>: ATQ0 V1 E1 -- OK
ttyUSB0<*1>: ATQ0 V1 E1 Z -- OK
ttyUSB0<*1>: ATQ0 V1 E1 S0=0 -- OK
ttyUSB0<*1>: ATQ0 V1 E1 S0=0 &C1 -- OK
ttyUSB0<*1>: ATQ0 V1 E1 S0=0 &C1 &D2 -- OK
ttyUSB0<*1>: ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0 -- OK
ttyUSB0<*1>: Modem Identifier: ATI -- Manufacturer: huawei
ttyUSB0<*1>: Speed 9600: AT -- OK
ttyUSB0<*1>: Max speed is 9600; that should be safe.
ttyUSB0<*1>: ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0 -- OK
**[COLOR=Red]WvModem<*1>: Cannot get information for serial port.[/COLOR]**
ttyUSB1<*1>: ATQ0 V1 E1 -- OK
ttyUSB1<*1>: ATQ0 V1 E1 Z -- OK
ttyUSB1<*1>: ATQ0 V1 E1 S0=0 -- OK
ttyUSB1<*1>: ATQ0 V1 E1 S0=0 &C1 -- OK
ttyUSB1<*1>: ATQ0 V1 E1 S0=0 &C1 &D2 -- OK
ttyUSB1<*1>: ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0 -- OK
ttyUSB1<*1>: Modem Identifier: ATI -- Manufacturer: huawei
ttyUSB1<*1>: Speed 9600: AT -- OK
ttyUSB1<*1>: Max speed is 9600; that should be safe.
ttyUSB1<*1>: ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0 -- OK

Found a modem on /dev/ttyUSB0.
Modem configuration written to /etc/wvdial.conf.
ttyUSB0<Info>: Speed 9600; init "ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0"
ttyUSB1<Info>: Speed 9600; init "ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0"
john@john-desktop:~$ 
===================================================================
[B][COLOR=Black]
[/COLOR][COLOR=Black][SIZE=3]*Contents of wvdial.conf*[/SIZE][/COLOR][/B]

[Dialer Defaults]
Init1 = ATZ
Init2 = ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
Modem Type = Analog Modem
ISDN = 0
New PPPD = yes
Phone = *99#
Modem = /dev/ttyUSB0
Stupid Mode = yes                             (**[COLOR=Black]this was added as it was mentioned by someone[/COLOR]**)
Username = Anything                   (**used 'three' for a username, too**)
Password = Anything                      (**used 'three' for a password, too**)
Baud = 9600
===================================================================
john@john-desktop:~$ wvdial defaults

--> WvDial: Internet dialer version 1.60
[COLOR=Red]**--> Cannot get information for serial port.**[/COLOR]
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
[B][COLOR=Red]ERROR
--> Invalid dial command.[/COLOR][/B]
--> Disconnecting at Sun Jun 14 14:19:41 2009

john@john-desktop:~$ 
=============================================[COLOR=Black]

I went into the BIOS and shut the serial ports, COM1 and COM2, down but that caused even more problems.

Any help appreciated.

The above was done after a fresh installed of Jaunty. WVDial installed without any errors.
[/COLOR]

---

### Post by lkraemer on 2009-06-14
In your /etc/wvdial.conf

the phone number should be the local dialed number for your ISP.
Phone = 3211234

Your Username should be:
Username = [email]yourloginname@isp.net[/email]

Your Password should be:
Password = yourloginpassword

They MUST match a USER for your ISP.

You might want to go to locate and run pppconfig.
It will setup your pap-secrets or your chap-secrets file
Those files are at /etc/ppp

lkraemer

---

### Post by GeorgeVita on 2009-06-14
Hi **chome4**,

Can you please give more info about your modem: Huawei which model?
Dialling methods and programs (as wvdial) can be used for any type of modem/connection. Your are using Mobile internet or a standard Dial Up connection? In case of a dial up **ikraemer** is your best advisor!

A note for the system "errors" reported in your post (from my point of view & not technically "approved"):
System assigns a communication port for every attached serial device (especially modems). This is done using some tables/definitions inside kernel/systemfiles and additional info gained by the USB peripheral negotiation. The communication port created can be found listing the directory tree:
**ls /dev/ttyS* /dev/ttyU* /dev/ttyA* /tty/devH***

In the above command we can omit /dev/ttyS* as these are the standard com ports, always existed and defined as /dev/ttyS0 (com1) /dev/ttyS1 (com2) /dev/ttyS2 (com3) /dev/ttyS4 (com4)
If you have a motherboard with comX connectors you can use them directly as above.

A USB port is usbserial-ized to become a serial port. System usually assigns a /dev/ttyUSBx where x is the first free available number. For your case your modem took /dev/ttyUSB0 and /dev/ttyUSB1 as there is no other serial peripheral to your system.

**wvdialconf** found these ports but unfortunately uses low speed (9600 baud). I am sure that you can use at least 115200 Baud which is the "typical" for modems (after 1990-5). Although it found 2 ports it uses the first one.

Usually wvdial must be run with superuser privileges: **sudo wvdial**
If you have parameters under a label other than "[Dialer Defaults]" you should state it (ex. "sudo wvdial 3Gconn"). The parameters inside /etc/wvdial.conf are merged (see: **man wvdial**, **man wvdial.conf**

The following shows that you have not connected anything to ttyS0 (com1) port
> ttyS0<*1>: ATQ0 V1 E1 -- and failed too at 115200, giving up.

Ignore next error, as always shown to a USB serialized port:
> WvModem<*1>: Cannot get information for serial port.
--> Cannot get information for serial port.-

And finally this is the error to fix (with lkraemer note on Phone/user/pass).
> ATDT*99#
ERROR
--> Invalid dial command.

Regards
George

---

### Post by chome4 on 2009-06-15
I've spoken to my ISP, three.co.uk, who supply the USB modem and they can't give me logon details as they don't support Linux systems.
 
I'm looking at getting a regular broadband account which is double the cost but wired internet connections seem to be supported better. 
 
I may try and install the previous version of Ubuntu as that seems to have supported 'plug and play' for these modems. (Huawei E220 otherwise known as Huawei E156G on the box it came in.)
 
Thanks for your input, lkraemer and George.

---

### Post by mbaas on 2009-06-15
Hi,

Here's a working wvdial conf as used with the Dutch provider KPN. It uses several provider specific settings:

<code>
[Dialer kpn]
Init1 = ATZ
Init2 = ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
Init3 = AT+CGDCONT=1,"IP","yourapngoeshere"
Stupid Mode = 1
Phone = *99#
Modem = /dev/ttyUSB0
Username = username
Password = password
</code>

Replace yourapngoeshere with the correct APN from your wireless provider, if needed enter a username / password. (My provider doesnt use a user / pass, but i have to enter one anyway to stop wvdial complaining). This was tested with the Huawei e160, e180, e220, e270, e620, e630 and e870.

Regards,

Mikey

---

### Post by chome4 on 2009-06-15
> **mbaas said:**
> Hi,
 
Here's a working wvdial conf as used with the Dutch provider KPN. It uses several provider specific settings:
 
<code>
[Dialer kpn]
Init1 = ATZ
Init2 = ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
Init3 = AT+CGDCONT=1,"IP","yourapngoeshere"
Stupid Mode = 1
Phone = *99#
Modem = /dev/ttyUSB0
Username = username
Password = password
</code>
 
Replace yourapngoeshere with the correct APN from your wireless provider, if needed enter a username / password. (My provider doesnt use a user / pass, but i have to enter one anyway to stop wvdial complaining). This was tested with the Huawei e160, e180, e220, e270, e620, e630 and e870.
 
Regards,
 
Mikey
 
Thank you very much I'll give it a try later....

---

### Post by GeorgeVita on 2009-06-15
Hi again,
please inform us about exact model of modem you have.

Most **Huawei** modems work directly via **Network Manager on 9.04**

If you would like to try it:

- Boot without the modem
- Delete any existing Mobile Broadband connection
(right click Network Manager icon, Edit Connections, Mobile Broadband, click on any existing and Delete it, close)
- Attach your modem and wait for 1 minute maximum time
- If your modem recognised a Wizard must start
- Then add your Mobile Broadband connection: UK, 3 and possibly UK 3 handsets (?), close
- Click on Network Manager icon and then on "3" or "3 handsets"

In any way it is better to ask about **APN**. Sometimes they charge differently (the cost could be higher!). APN is the name of their service and it is used on smart phones also. It is not Operating System depended.

For **3-UK** there are 2x **APN** selections to try at **/etc/wvdial.conf**:

**Init3 = AT+CGDCONT=1,"IP","3internet"**
or
**Init3 = AT+CGDCONT=1,"IP","three.co.uk"**

[COLOR="Blue"]**EDIT: remove also the SIM PIN check using a mobile phone!**[/COLOR]

Regards,
George

---

### Post by chome4 on 2009-06-15
> **GeorgeVita said:**
> Hi again,
please inform us about exact model of modem you have.

Most **Huawei** modems work directly via **Network Manager on 9.04**

If you would like to try it:

- Boot without the modem
- Delete any existing Mobile Broadband connection
(right click Network Manager icon, Edit Connections, Mobile Broadband, click on any existing and Delete it, close)
- Attach your modem and wait for 1 minute maximum time
- If your modem recognised a Wizard must start
- Then add your Mobile Broadband connection: UK, 3 and possibly UK 3 handsets (?), close
- Click on Network Manager icon and then on "3" or "3 handsets"

In any way it is better to ask about **APN**. Sometimes they charge differently (the cost could be higher!). APN is the name of their service and it is used on smart phones also. It is not Operating System depended.

For **3-UK** there are 2x **APN** selections to try at **/etc/wvdial.conf**:

**Init3 = AT+CGDCONT=1,"IP","3internet"**
or
**Init3 = AT+CGDCONT=1,"IP","three.co.uk"**

Regards,
George

Hey George,

The modem is a Huawei E165G 

lsusb reveals:

Bus 001 Device 003: ID 12d1:1003 Huawei Technologies Co., Ltd. E220 HSDPA Modem / E270 HSDPA/HSUPA Modem

I'll try the stuff above when I'm next in front of the computer.

Thanks.

---

