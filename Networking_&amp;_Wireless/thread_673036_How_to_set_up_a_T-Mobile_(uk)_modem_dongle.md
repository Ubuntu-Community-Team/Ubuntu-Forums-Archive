---
title: "How to set up a T-Mobile (uk) modem dongle"
date: 2008-01-20
forum: Networking &amp; Wireless
---

### Post by roycocup on 2008-01-20
Hello all, 
Here's what I did in 2 laptops that were connecting to the internet through an T-Mobile huwaei 220 modem.

You must create 2 files

1.
The first file will be called "provider" and it will be copied to the /etc/ppp/peers/... There will be a Provider file there already that you must rename or otherwise overwrite.
In the file "provider" copy/paste the following:

```

# example configuration for a dialup connection authenticated with PAP or CHAP
#
# This is the default configuration used by pon(1) and poff(1).
# See the manual page pppd(8) for information on all the options.

# MUST CHANGE: replace myusername@realm with the PPP login name given to
# your by your provider.
# There should be a matching entry with the password in /etc/ppp/pap-secrets
# and/or /etc/ppp/chap-secrets.
user "T-Mobile"

# MUST CHANGE: replace ******** with the phone number of your provider.
# The /etc/chatscripts/pap chat script may be modified to change the
# modem initialization string.
connect "/usr/sbin/chat -v -f /etc/chatscripts/pap -T *99#"

# Serial device to which the modem is connected.
/dev/ttyUSB0

# Speed of the serial line.
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

updetach
novj
novjccomp
nopcomp
nodeflate
replacedefaultroute
holdoff 5

```

2. create a file named "pap" that will go into the /etc/chatscripts/ directory

copy paste the following:
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
#REPORT		CONNECT

ABORT		BUSY
ABORT		VOICE
ABORT		"NO CARRIER"
ABORT		"NO DIALTONE"
ABORT		"NO DIAL TONE"
""		ATZ
OK 		ATE0V1&D2&C1S0=0+IFC=2,2
OK 		AT+CGDCONT=1,"IP","general.t-mobile.uk"
OK 		ATDT*99#
CONNECT		""

```

after putting those 2 files in place, you can try opening a console and typing "pon" for connecting and "poff" to disconnect.

if you get any errors, try rebooting and try again.

make sure you always disconnect the modem with "poff" before you reboot. Sometimes it wont connect on the next session.

Having the usb modem always pluged in is optional... you can start linux with the modem pluged or not.... as long as it has a blue or green light flashing every 5 seconds....

those lights have a meaning too: 
green flash twice: usb detected, no carrier to connect
green flash time to time: usb detected, carrier present in gsm (very slow connection)
green still: usb detected, internet connection on, gsm speed
blue flash: usb detected, ready for use in umts band
blue still: connected alright in umts.

have fun.
pon for on. poff for off.

---

