---
title: "Novatel Merlin U630 Connection Card problem"
date: 2007-04-01
forum: Networking &amp; Wireless
---

### Post by ianus on 2007-04-01
I've a Novatel Merlin U630 Connection Card with a Ubuntu 6.10
and my kernel is 2.6.17-11-generic .
I've tried differents how-to but without much luck.

```
:~$ tail -f /var/log/messages
Apr  1 16:41:44 myXUbuntu kernel: [ 6865.203287] pccard: PCMCIA card inserted into slot 0
Apr  1 16:41:44 myXUbuntu kernel: [ 6865.204361] pcmcia: registering new device pcmcia0.0
Apr  1 16:41:44 myXUbuntu kernel: [ 6865.247248] 0.0: ttyS0 at I/O 0x3f8 (irq = 11) is a 16550A
Apr  1 16:41:44 myXUbuntu kernel: [ 6865.247705] pcmcia: registering new device pcmcia0.1
Apr  1 16:41:44 myXUbuntu kernel: [ 6865.289928] 0.1: ttyS1 at I/O 0x2f8 (irq = 0) is a 16550A

```

I'm not sure if I'm doing right but to get it work I'm using wvdial

```
:~# wvdialconf 
Editing `/etc/wvdial.conf'.

Scanning your serial ports for a modem.

ttyS0<*1>: ATQ0 V1 E1 -- failed with 2400 baud, next try: 9600 baud
ttyS0<*1>: ATQ0 V1 E1 -- failed with 9600 baud, next try: 115200 baud
ttyS0<*1>: ATQ0 V1 E1 -- and failed too at 115200, giving up.
ttyS1<*1>: ATQ0 V1 E1 -- failed with 2400 baud, next try: 9600 baud
ttyS1<*1>: ATQ0 V1 E1 -- failed with 9600 baud, next try: 115200 baud
ttyS1<*1>: ATQ0 V1 E1 -- and failed too at 115200, giving up.
Modem Port Scan<*1>: S2   S3   

```

my wvdial.conf looks like this:
```

[Dialer pin]
Init1 = AT+CPIN=3751

[Dialer novatel_u630]
Modem = /dev/ttyS0
Baud = 460800
Init2 = ATZ
Init3 = ATE0V1&D2&C1S0=0+IFC=2,2
ISDN = 0
Modem Type = Analog Modem

[Dialer internet]
Init5 = AT+CGDCONT=1,"IP","internet"

[Dialer 3gonly]
Init4 = AT+COPS=0,0,"Vodacom-SA",2

[Dialer 384k]
Init6 = AT+CGEQMIN=1,4,64,384,64,384
Init7 = AT+CGEQREQ=1,4,64,384,64,384


```

```
:~# wvdial pin novatel_u630 internet 3gonly 384k
--> WvDial: Internet dialer version 1.56
--> Initializing modem.
--> Sending: AT+CPIN=3751
--> Sending: ATQ0
--> Re-Sending: AT+CPIN=3751
--> Modem not responding.

```

I'v already tried to change in my config ttyS0 for ttyS1 but it does the same.

I've tried to use minicom to talk with my card but I don't know what I'm doing wrong.

Thanks and sorry for my english...

---

### Post by Mach1US on 2007-04-03
Try this how-to and let me know if you have other problems
[HTML]http://ubuntuforums.org/showthread.php?p=2396333#post2396333[/HTML]

---

### Post by Carlos Santiago on 2007-06-01
I use the same modem but a different ISP

To solve the low speed problem type:
```
sudo setserial /dev/ttyS0 spd_warp low_latency
```

Notice that from ubuntu 7.04 (even maybe from 6.10), you can use UDEV rules to start your device modules and immediately connect.

The rule that I made and append to /etc/udev/rules.d/85-pcmcia.rules is:
```
ACTION=="add", KERNEL=="ttyS0", SYSFS{card_id}=="0x0276", SYSFS{manf_id}=="0x00a4", \
                RUN+="/bin/setserial /dev/ttyS0 baud_base 460800 spd_warp low_latency", \
                RUN+="/usr/bin/pon provider", GROUP="dialout"
```

You may also need to change the files /etc/ppp/peers/provider and  /etc/chatscripts/pap

Bellow, a copy of mines (adapted to vodafone!)

Note that my ISP doesnt require any authentication. I believe neither vodafone!

Feel free to send me a message if you need any more help!

-----------------------------------
$ cat /etc/ppp/peers/provider
```

# example configuration for a dialup connection authenticated with PAP or CHAP
#
# This is the default configuration used by pon(1) and poff(1).
# See the manual page pppd(8) for information on all the options.

# MUST CHANGE: replace myusername@realm with the PPP login name given to
# your by your provider.
# There should be a matching entry with the password in /etc/ppp/pap-secrets
# and/or /etc/ppp/chap-secrets.
user "myusername@realm"

# MUST CHANGE: replace ******** with the phone number of your provider.
# The /etc/chatscripts/pap chat script may be modified to change the
# modem initialization string.
connect "/usr/sbin/chat -v -f /etc/chatscripts/pap -T *99***1#"

# Serial device to which the modem is connected.
/dev/ttyS0

# Speed of the serial line.
#115200
460800

# Assumes that your IP address is allocated dynamically by the ISP.
noipdefault
# Try to get the name server addresses from the ISP.
usepeerdns
# Use this connection as the default route.
defaultroute

# Makes pppd "dial again" when the connection is lost.
persist

# Do not ask the remote to authenticate.
noauth

```

$ cat /etc/chatscripts/pap
```

# You can use this script unmodified to connect to sites which allow
# authentication via PAP, CHAP and similar protocols.
# This script can be shared among different pppd peer configurations.
# To use it, add something like this to your /etc/ppp/peers/ file:
#
# connect "/usr/sbin/chat -v -f /etc/chatscripts/pap -T PHONE-NUMBER"
# user YOUR-USERNAME-IN-PAP-SECRETS
# noauth

# Uncomment the following line to see the connect speed.
# It will be logged to stderr or to the file specified with the -r chat option.
#REPORT         CONNECT

ABORT           BUSY
ABORT           VOICE
ABORT           "NO CARRIER"
ABORT           "NO DIALTONE"
ABORT           "NO DIAL TONE"
""              ATZ
OK              'ATE1'
OK              'AT$NWRAT=0,2'
OK              'AT+COPS=0,0,"P VODAFONE",2'
OK              'AT+CGDCONT=1,"IP","myconnection","0.0.0.0",0,0'
OK              'AT+CGEQREQ=1,4,0,0,,,2,1500,"0E0","0E0",3,,0'
OK              'AT+CGEQMIN=1,4,0,0,0,0,2,1500,"0E0","0E0",3,0,0'
OK              ATDT\T
CONNECT         ""

```

---

