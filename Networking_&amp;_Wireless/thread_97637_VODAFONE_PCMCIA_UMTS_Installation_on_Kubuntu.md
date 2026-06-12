---
title: "VODAFONE PCMCIA UMTS Installation on Kubuntu"
date: 2005-12-01
forum: Networking &amp; Wireless
---

### Post by AndreSchaaf on 2005-12-01
Good Evening. I have bought a Datacard from Vodafone. Theyr name ist Novatel  Merlin U630. I have find and read the Howtos in the Forums but the doesn´t working. I have an Averatec Laptop with Kubuntu 5.10 as OS. 
When I type the commands from the HowTo and it happens nothing. 
Another problem is that I have no Internet in Linux. 

Can me help anybody with this problem, please ?. I have no idea what I have to do.

Thanks. 

MFG Andre Schaaf

---

### Post by mips on 2005-12-06
Double post. See [http://ubuntuforums.org/showthread.php?p=548850#post548850](http://ubuntuforums.org/showthread.php?p=548850#post548850)

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

