---
title: "Need Help with PCI Modem and Hyperterminal in Ubuntu 7"
date: 2007-07-26
forum: Networking &amp; Wireless
---

### Post by DrewbieTech on 2007-07-26
At my job I use Hyperterminal in Windows to dial into our phone system to make changes.  My computer has a PCI modem.  I recently installed Ubuntu 7, and I have not been able to figure out how to dial into our phone system.  Someone recommended C-Kermit as a replacement for hyperterminal, as well as GtkTerm.  But I can't seem to configure these apps to work with my internal modem, and then dial out.  Can anyone offer some help?

---

### Post by MrFSL on 2007-07-26
What model / manufacturer makes your modem?

**Hint** You might try:
```
lspci | grep -i modem
```


What have you tried already?

What were your specific results?

Have you looked at any of the DialUp howto's here on the forums or in the Ubuntu Documentation or online through google etc.?

---

### Post by DrewbieTech on 2007-07-26
My modem is:
03:0a.0 Communication controller: Agere Systems 56k WinModem (rev 01)

I have tried changing the settings in these programs, for instance, I know that I need to tell the app where the modem is, but I can only seem to find information on attaching the app to a serial port (an external modem, or direct cable connection).  One tutorial said to try attaching kermit to /dev/ttyS0, but that doesn't work.  I have only briefly looked at the dial up how to's.  The ones I was able to find are geared toward setting up a dial up internet connection, which is not what I need to do.  I need to talk directly to another modem, with command line access.  Google was unhelpful, though perhaps I'm not using the right terms in my searching.

Any tips would be appreciated.

---

### Post by MrFSL on 2007-07-26
Alrighty now I can help you...

You still need to use the first half of these DialUp howto's that show you how to properly configure and use your Windows-Only DialUp Modem.

/dev/ttyS0 refers the the first serial port on your computer. In the Windows world you can think of it as COM1.

When properly configured you modem IS a serial port just like an external modem and will be referenced in a similar way such as: */dev/ttySL0 or /dev/ttyACM0 or /dev/ttySL1 etc.*

Check out this link:
[https://help.ubuntu.com/community/DialupModemHowto](https://help.ubuntu.com/community/DialupModemHowto)

Once you have a driver loaded for your modem I can instruct you on how to identify where to find it in /dev/ and how to configure gtkterm. 

**NOTE** Good luck. You should be able to get a driver loaded for your modem but it can be tricky. Personally configuring Win-Modems in Linux is my least favorite configuration to every have to do!

---

### Post by DrewbieTech on 2007-07-27
Thanks for info and help.  My modem seems to be configured correctly now.  I even managed to get minicom to connect to our phone system.  The problem I'm having now is that I don't see the command prompt and such output from the server that I am connected to.  I'm sure I must be missing some important setting, but if you could offer an clues it would be great.  Thanks.

---

### Post by MrFSL on 2007-07-27
Alrighty. To make sure that your modem is configured correctly you can use the package wvdial and wvdial.conf.

If you need the package you can do:
```
sudo apt-get install wvdial
```

Then run:
```
 wvdialconf
```

This will tell you what modems are connected and how they are configured. We can then use that informtion to setup your modem for serial connections.

---

### Post by DrewbieTech on 2007-07-30
Here's the output from running wvdialconf:

[INDENT]
[Dialer Defaults]
Init1 = ATZ
Init2 = ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
Modem Type = Analog Modem
Baud = 115200
New PPPD = yes
Modem = /dev/ttyLTM0
ISDN = 0
; Phone = <Target Phone Number>
; Password = <Your Password>
; Username = <Your Login Name>[/INDENT]

---

### Post by DrewbieTech on 2007-08-02
Anyone got any advice?

---

### Post by MrFSL on 2007-08-02
When running wvdialconf you should have an output similar to this:

```
Scanning your serial ports for a modem.

Modem Port Scan<*1>: S0   S1   S2   S3   
WvModem<*1>: Cannot get information for serial port.
ttySL0<*1>: ATQ0 V1 E1 -- OK
ttySL0<*1>: ATQ0 V1 E1 Z -- OK
ttySL0<*1>: ATQ0 V1 E1 S0=0 -- OK
ttySL0<*1>: ATQ0 V1 E1 S0=0 &C1 -- OK
ttySL0<*1>: ATQ0 V1 E1 S0=0 &C1 &D2 -- OK
ttySL0<*1>: ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0 -- OK
ttySL0<*1>: Modem Identifier: ATI -- SmartLink Soft Modem
ttySL0<*1>: Speed 4800: AT -- OK
ttySL0<*1>: Speed 9600: AT -- OK
ttySL0<*1>: Speed 19200: AT -- OK
ttySL0<*1>: Speed 38400: AT -- OK
ttySL0<*1>: Speed 57600: AT -- OK
ttySL0<*1>: Speed 115200: AT -- OK
ttySL0<*1>: Speed 230400: AT -- OK
ttySL0<*1>: Speed 460800: AT -- OK
ttySL0<*1>: Max speed is 460800; that should be safe.
ttySL0<*1>: ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0 -- OK

```

please post your output

---

### Post by DrewbieTech on 2007-08-03
```
Scanning your serial ports for a modem.

ttyLTM0<*1>: ATQ0 V1 E1 -- OK
ttyLTM0<*1>: ATQ0 V1 E1 Z -- OK
ttyLTM0<*1>: ATQ0 V1 E1 S0=0 -- OK
ttyLTM0<*1>: ATQ0 V1 E1 S0=0 &C1 -- OK
ttyLTM0<*1>: ATQ0 V1 E1 S0=0 &C1 &D2 -- OK
ttyLTM0<*1>: ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0 -- OK
ttyLTM0<*1>: Modem Identifier: ATI -- LT V.92 Data+Fax Modem Version 8.31
ttyLTM0<*1>: Speed 4800: AT -- OK
ttyLTM0<*1>: Speed 9600: AT -- OK
ttyLTM0<*1>: Speed 19200: AT -- OK
ttyLTM0<*1>: Speed 38400: AT -- OK
ttyLTM0<*1>: Speed 57600: AT -- OK
ttyLTM0<*1>: Speed 115200: AT -- OK
ttyLTM0<*1>: Max speed is 115200; that should be safe.
ttyLTM0<*1>: ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0 -- OK
ttyS0<*1>: ATQ0 V1 E1 -- failed with 2400 baud, next try: 9600 baud
ttyS0<*1>: ATQ0 V1 E1 -- failed with 9600 baud, next try: 115200 baud
ttyS0<*1>: ATQ0 V1 E1 -- and failed too at 115200, giving up.
Modem Port Scan<*1>: S1   S2   S3   

Found a modem on /dev/ttyLTM0.
Modem configuration written to /etc/wvdial.conf.
ttyLTM0<Info>: Speed 115200; init "ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0"

```

---

### Post by MrFSL on 2007-08-04
Excellent:
Open gtkterm. Goto configuration > port.
Port should be set to: /dev/ttyLTM0.

Type AT and hit enter.
If you see 'OK' then you are talking to your modem.

---

### Post by helmut_hed on 2007-08-06
Hi Drewbietech,

It seems from your wvdialconf output that you are almost there.  The modem driver is responding to you and giving (mostly) sensible answers.  I'm not sure why it's trying 115200 speed; presumably 57600 (a.k.a. 56K) is the highest you could expect to achieve.  There's usually a way to limit the connection speed to a maximum and perhaps this is what you need to do.

You say you expect to see a "command prompt" - does this mean you are using minicom to talk directly to your modem (via "AT" commands) and then to a server somewhere?  This probably means you are using your modem as a direct terminal connection.  Most howtos and info out there assume you use your modem as a network interface, instead of a direct text/terminal connection.  This is done via a protocol called "ppp", and I think in that case wvdial is appropriate.  It will set everything up for you and then you can use web browsers, email tools, etc. - using your modem as the connetion to the Internet.  You can even use a terminal window to connect, through this network interface, to a server out there at your organization.

On the other hand, if you expected to use your modem only to login to a text-based system somewhere, and not use that connection to surf the net, download email, etc. then you are probably right to be using minicom.  It gives you a direct connection to your modem (which I see is /dev/LTM0 - a Lucent softmodem), and you can type commands directly to it, e.g.:

ATDT7658080

(or whatever the number is) which, after a pause and some noises, should connect you to your organization's modem concentrator, to which you can give whatever commands you like.  Maybe this "gtkterm" will do the same thing?  I'm not familiar with it.

Oh, and /dev/ttyS0 is definitely NOT the right one :)

Regards,
Jeff
(who formerly used modems in exactly that manner)

---

### Post by DrewbieTech on 2007-08-06
Hi all.  Thanks for your help.

Let me explain a little more in detail what I'm trying to do.  My company has an old analog PBX phone system.  In order to make changes to the phone system (In Windows), I have to open Hyper Terminal, and dial 199. This dials directly to a modem connected to the controller card on the phone system.  Once the modem (in my computer) is connected to the remote modem, I receive a prompt to enter the system password.  Once entered, I can make changes to the system all from a command line (in Hyper Terminal). There is no GUI interface for the system.

Problem: In Ubuntu, using both minicom and gtkterm, I am able to get my modem to dial out and connect to the remote modem, but then the screen is blank. I never get prompted for the password.  It's like I'm only communicating one-way.  Am I missing a setting somewhere?  Also, I am not familiar with "AT commands";  All the training I have with telephones I received on the job here, so I'm woefully ignorant.

Perhaps someone could suggest some general trouble shooting tips that might help me remedy my blank screen?  Thanks.

---

### Post by helmut_hed on 2007-08-06
You may need to send a "break" - ^AF in minicom, or to hit return once or twice to see a prompt.

You may also need to set your communication parameters - baud rate, parity and stop bits, etc.  This is done with ^AP in minicom.

Good luck,
Jeff
PS: you are certain the modem has dialed and connected successfully?

---

### Post by DrewbieTech on 2007-08-06
Thanks for the tips... sending the Break command did not help.

Also, I set the baud rate and parity as best as I knew how.  I set them to be the same as the settings in Hyper Terminal in Windows.

I am fairly certain that I am successfully connected.  I can hear the modem dialing and 'screaming'  Then it makes a triumphant sounding beeping pattern and I see a message that says connected.  However, I am seeing something I didn't see before.  The connection message has changed.  It now says "CONNECT 9600 NoEC".  Does that mean anything to you?

---

