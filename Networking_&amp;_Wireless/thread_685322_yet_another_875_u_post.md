---
title: "yet another 875 u post"
date: 2008-02-02
forum: Networking &amp; Wireless
---

### Post by kieronch3 on 2008-02-02
ok i am trying to get my aircard working and have been using all the previuous posts to check my settings.... it says it is dialing but doesnt connect here is my lsusb output


Bus 004 Device 003: ID 054c:014d Sony Corp. Memory Stick Reader/Writer
Bus 004 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 003: ID 054c:0107 Sony Corp. VCC-U01 Visual Communication Camera
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 003: ID 1199:6812 Sierra Wireless, Inc. 
Bus 001 Device 001: ID 0000:0000  


and my dmesg output

[  369.360000] usb 1-2: new full speed USB device using uhci_hcd and address 2
[  369.524000] usb 1-2: configuration #1 chosen from 1 choice
[  369.708000] usbcore: registered new interface driver usbserial
[  369.708000] /build/buildd/linux-source-2.6.22-2.6.22/drivers/usb/serial/usb-serial.c: USB Serial support registered for generic
[  369.708000] usbcore: registered new interface driver usbserial_generic
[  369.708000] /build/buildd/linux-source-2.6.22-2.6.22/drivers/usb/serial/usb-serial.c: USB Serial Driver core
[  369.724000] /build/buildd/linux-source-2.6.22-2.6.22/drivers/usb/serial/usb-serial.c: USB Serial support registered for Sierra USB modem (1 port)
[  369.724000] /build/buildd/linux-source-2.6.22-2.6.22/drivers/usb/serial/usb-serial.c: USB Serial support registered for Sierra USB modem (3 port)
[  369.724000] sierra 1-2:1.0: Sierra USB modem (3 port) converter detected
[  369.724000] usb 1-2: Sierra USB modem (3 port) converter now attached to ttyUSB0
[  369.728000] usb 1-2: Sierra USB modem (3 port) converter now attached to ttyUSB1
[  369.728000] usb 1-2: Sierra USB modem (3 port) converter now attached to ttyUSB2
[  369.728000] usbcore: registered new interface driver sierra
[  369.728000] /build/buildd/linux-source-2.6.22-2.6.22/drivers/usb/serial/sierra.c: USB Driver for Sierra Wireless USB modems: v.1.0.6
[ 1281.600000] usb 1-2: USB disconnect, address 2
[ 1281.600000] sierra3 ttyUSB0: Sierra USB modem (3 port) converter now disconnected from ttyUSB0
[ 1281.600000] sierra3 ttyUSB1: Sierra USB modem (3 port) converter now disconnected from ttyUSB1
[ 1281.600000] sierra3 ttyUSB2: Sierra USB modem (3 port) converter now disconnected from ttyUSB2
[ 1281.600000] sierra 1-2:1.0: device disconnected
[ 1287.584000] usb 1-2: new full speed USB device using uhci_hcd and address 3
[ 1287.748000] usb 1-2: configuration #1 chosen from 1 choice
[ 1287.752000] sierra 1-2:1.0: Sierra USB modem (3 port) converter detected
[ 1287.752000] usb 1-2: Sierra USB modem (3 port) converter now attached to ttyUSB0
[ 1287.752000] usb 1-2: Sierra USB modem (3 port) converter now attached to ttyUSB1
[ 1287.752000] usb 1-2: Sierra USB modem (3 port) converter now attached to ttyUSB2


and the wvdialconf output

Scanning your serial ports for a modem.

Modem Port Scan<*1>: S0   S1   S2   S3   
WvModem<*1>: Cannot get information for serial port.
ttyUSB0<*1>: ATQ0 V1 E1 -- OK
ttyUSB0<*1>: ATQ0 V1 E1 Z -- OK
ttyUSB0<*1>: ATQ0 V1 E1 S0=0 -- OK
ttyUSB0<*1>: ATQ0 V1 E1 S0=0 &C1 -- OK
ttyUSB0<*1>: ATQ0 V1 E1 S0=0 &C1 &D2 -- OK
ttyUSB0<*1>: ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0 -- OK
ttyUSB0<*1>: Modem Identifier: ATI -- MC8775
ttyUSB0<*1>: Speed 4800: AT -- OK
ttyUSB0<*1>: Speed 9600: AT -- OK
ttyUSB0<*1>: Speed 19200: AT -- OK
ttyUSB0<*1>: Speed 38400: AT -- OK
ttyUSB0<*1>: Speed 57600: AT -- OK
ttyUSB0<*1>: Speed 115200: AT -- OK
ttyUSB0<*1>: Speed 230400: AT -- OK
ttyUSB0<*1>: Speed 460800: AT -- OK
ttyUSB0<*1>: Max speed is 460800; that should be safe.
ttyUSB0<*1>: ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0 -- OK
WvModem<*1>: Cannot get information for serial port.
ttyUSB1<*1>: ATQ0 V1 E1 -- failed with 2400 baud, next try: 9600 baud
ttyUSB1<*1>: ATQ0 V1 E1 -- failed with 9600 baud, next try: 115200 baud
ttyUSB1<*1>: ATQ0 V1 E1 -- and failed too at 115200, giving up.
WvModem<*1>: Cannot get information for serial port.
ttyUSB2<*1>: ATQ0 V1 E1 -- OK
ttyUSB2<*1>: ATQ0 V1 E1 Z -- OK
ttyUSB2<*1>: ATQ0 V1 E1 S0=0 -- OK
ttyUSB2<*1>: ATQ0 V1 E1 S0=0 &C1 -- OK
ttyUSB2<*1>: ATQ0 V1 E1 S0=0 &C1 &D2 -- OK
ttyUSB2<*1>: ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0 -- OK
ttyUSB2<*1>: Modem Identifier: ATI -- Manufacturer: Sierra Wireless, Inc.
ttyUSB2<*1>: Speed 4800: AT -- OK
ttyUSB2<*1>: Speed 9600: AT -- OK
ttyUSB2<*1>: Speed 19200: AT -- OK
ttyUSB2<*1>: Speed 38400: AT -- OK
ttyUSB2<*1>: Speed 57600: AT -- OK
ttyUSB2<*1>: Speed 115200: AT -- OK
ttyUSB2<*1>: Speed 230400: AT -- OK
ttyUSB2<*1>: Speed 460800: AT -- OK
ttyUSB2<*1>: Max speed is 460800; that should be safe.
ttyUSB2<*1>: ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0 -- OK

Found a modem on /dev/ttyUSB0.
Modem configuration written to /etc/wvdial.conf.
ttyUSB0<Info>: Speed 460800; init "ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0"
ttyUSB2<Info>: Speed 460800; init "ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0"



but when i connect this is what my onnection log says,

/home/tr2ap3-admin/.wvdial.conf<Warn>: Ignoring malformed input line: ";Do NOT edit this file by hand!"
WvDial<*1>: WvDial: Internet dialer version 1.56
WvModem<*1>: Cannot get information for serial port.
WvDial<*1>: Initializing modem.
WvDial<*1>: Sending: ATX3
WvDial Modem<*1>: OK
WvDial<*1>: Sending: ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
WvDial Modem<*1>: OK
WvDial<*1>: Modem initialized.
WvDial<*1>: Sending: ATM1L3DT*99#
WvDial<*1>: Waiting for carrier.
WvDial Modem<*1>: OK
WvDial<Warn>: Timed out while dialing.  Trying again.
WvDial<Warn>: Maximum Attempts Exceeded..Aborting!!
WvDial<*1>: Disconnecting at Fri Feb  1 23:27:17 2008





hopefully someone can help

thanx in advance

---

### Post by kieronch3 on 2008-02-02
bump, 

hopefully someone notices my post, :( and has a simple answer on something i am missing :)

p.s. i apologize for the fat fingers in my last post i had a few to many:wink::wink: if something is unreadable let me know

---

### Post by kieronch3 on 2008-02-03
34 vews and not one reply darn it...

anyway over the last 19 hours i have discovered another program that eases interfacing with the sierra wireless 875u...

it is Vodafone Mobile Card Driver For Linux.


after installing, reinstalling, messing it up, removing, and finally getting it right (with latest drivers)

it launches...attempts to conect to the network, states that I am "Authenticated" and freezes...

If I disconnect my 875u program doesnt launch...

If it is connected with no network signal (like when i am in a shielded building) it skips authentication process and launches program.


If there is a signal, it attempts to authenticate, says it succeeds and stops...

i launched firefox just to test and it doesnt see any interent connection, so i am fairly sure it is not negotiating for an IP after it "authenticates"

if anyone has any ideas feel free to chime in until then i will talk to myself  :)

---

### Post by kieronch3 on 2008-02-04
ok so i called at and  t to check that the settings here are the same (my aircard says it is on celluar on dcs, which was recently bought by at and t, , they confirmed the "isp.cingular" apn info is correct.

it still doesnt connect.

at and t sent me this unsupported script to assist, when using gnome ppp it finds carrier and then the connection dies (exit code 2).

here are the at and t scripts....

7Note: Creating connection scripts and utilizing the PPPD dialer require ROOT
privileges.

Configuring:

Create a file named "gprs-connect-chat" in the directory "/etc/ppp/peers/" and copy
and paste the following information into it:
# File name: gprs-connect-chat
#
# These are the GPRS connection settings for if you wish to use CHAT to establish a
PDP context.
# See the "chat" man pages for more information.
'' AT
# Replace "proxy" with whichever APN you need to establish a PDP context.
OK AT+CGDCONT=1,"IP","proxy"
# If more than one APN is configured on the device, replace 1 with the slot
containing the settings for the 
# desired connection.
OK ATD*99***1#
# This line advises the wireless device to connect.
CONNECT ''

Create a filed named "gprs-disconnect-chat" in the directory /etc/ppp/peers/" and
copy and paste the following information into it:
# File gprs-disconnect-chat
#
# Description: This script issues the disconnect AT commands via the "chat" program
to the modem.
# See the "chat" man pages for more information.
exec /usr/sbin/chat -V -s -S \
ABORT "BUSY" \
ABORT "ERROR" \
ABORT "NO DIALTONE" \
SAY "n\Sending break to the modem\n" \
"" "\K" \
"" "\K" \
"" "\K" \
"" "+++ATH" \
"" "+++ATH" \
"" "+++ATH" \
SAY "\nPDP context detached\n"

Create a filed named "gprs-wvdial.conf" in the directory /etc/ppp/peers/" and copy
and paste the following information into it:
# File name gprs-wvdial.conf
#
# Description:
# These are the GPRS connection settings for if you wish to use WVDIAL to establish
a PDP context.
# See the wvdial man pages for more information.
# 
# Call CID=1 which activate PDP context one and perform GPRS attach:
[Dialer gprs]
# Replace /dev/rfcomm0 with the interface being used to establish the PPP connection.
Modem = /dev/rfcomm0
Init1 = ATH
Init2 = ATE1
# Replace "proxy" with whichever APN you need to establish a PDP context.
Init3 = AT+CGDCONT=1,"IP","proxy","",0,0
Dial Command = ATD
Phone = *99#
Username = user
Password = user

Create a file called "gprs" in the directory "/etc/ppp/peers/" and copy and paste
the following information into it:
# GPRS PPPD connection script.
# Filename: gprs
# Description:
# This is an extremely detailed script for tethering GPRS wireless devices using
Bluetooth, Serial, and USB. 
# Following this script will be a shorter script that can be substituted.
# See 'man pppd' for detailed option descriptions.
# Most GPRS-enabled wireless devices don't reply to LCP echo's
lcp-echo-failure 0
lcp-echo-interval 0
# Specifying 'nodetach' below allows PPPD to run interactively rather than as a
background daemon.
nodetach
# The 'debug' option is pretty self-explanatory, if you do not wish to receive debug
information 
# from PPPD comment out 'debug' below.
debug
# Show password in debug messages
show-password
# Connect script:
# You can use either "chat" or "wvdial" to pass AT commands to the wireless device.
# connect "/usr/bin/wvdial --chat --config /etc/ppp/peers/gprs-wvdial.conf gprs"
connect "/usr/sbin/chat -v -t3 -f /etc/ppp/peers/gprs-connect-chat"
# Disconnect script:
# AT commands used to terminate the GPRS session. 
# Only use this if you are connecting using the "chat" program.
disconnect /etc/ppp/peers/gprs-disconnect-chat
# Connection method used to wireless device:
# /dev/ttyS0 # Serial Port 1 (COM1 in Windows)
# /dev/ttyS1 # Serial Port 2 (COM2 in Windows)
# /dev/ircomm0 # IrDA Serial Port
# /dev/ttyUSB0 # USB Serial device
/dev/rfcomm0 # Bluetooth Serial Port 1
# /dev/rfcomm1 # Bluetooth Serial Port 2
# Serial port line speed:
# (Note: This does not affect GPRS connection speed, this affects the speed at 
# which the computer talks to the wireless device.)
#460800 # This could theoretically be needed.
#230400 # UMTS performs well here.
115200 # Fast enough for GPRS and EDGE handsets.
#57600 # Some IrDA devices don't operate full-duplex and can run only at this speed.
# Hardware flow control:
# Use hardware flow control with cable, Bluetooth and USB but not with IrDA.
crtscts # This is used for Serial, Bluetooth, USB connections.(rarely IrDA)
#nocrtscts # This is used for IrDA primarily.
# Ignore carrier detect signal from the modem:
local
# IP addresses:
# This advises the PPP accept peers idea of our local address and set address peer
as 10.0.0.1 
# (any address would do, since IPCP gives 0.0.0.0 to it)
# PPPD may reject this if you are using the 10.x.x.x range on another interface.
:10.0.0.1
# The 'noipdefault' command advises PPPD not to request a specific address of the
DHCP server.
noipdefault
# This line allows the PPPD daemon to accept DHCP assigned IPs.
ipcp-accept-local
# Add the ppp interface as default route to the IP routing table
defaultroute
# This line advises PPPD to use the DNS provided by the DHCP connection.
usepeerdns
# PPP compression options:
# (Note: These compression options are specifically addressed to the serial
connection and not the GPRS connection)
novj
nobsdcomp
novjccomp
nopcomp
noaccomp
# This disables authentication as it is not necessary when establishing a PDP
context in most
# situations. If you are using a custom PDP that requires authentication, comment
this out
# and provide the correct username below and update the username-password
combination to the 
# secrets file: /etc/ppp/pap-secrets for PAP and /etc/ppp/chap-secrets for CHAP 
# authentication. See the PPPD man pages for further information.
user "username"
# The 'persist' option will attempt to re-establish dropped GPRS connections.
persist
# The 'maxfail' option is the number of maximum reconnection attempts that will be
made.
maxfail 99
# Asyncmap:
# some phones may require this option.
# asyncmap 0xa0000
# With the 'nomagic' option, PPPD cannot detect a looped-back line.
# Uncomment this only if the PPPD connection is buggy.
# nomagic
# Require the peer to authenticate itself using PAP [Password Authentication Protocol] 
# authentication. Some wireless devices and/or APNs require this.
# require-pap 


when i run the at and t script i get a failure "uknown identifier "bluetooth"


i tried to comment out all references to blue tooth but apparently i missing something....


anyone have any suggestions it stinks being so close but unable to get a connection

---

### Post by kieronch3 on 2008-02-08
latest update, connected my samsun a707 for fun, hit lsusb, list the phone as a samsung z100 on ttyACM0, for some more entertainment i put that pirt into Gnomeppp..../dev/ttyACM0


it connects i am using it right now.... damn crap but my 875u that maps to ttyUSB0 wont work... can someone tell me if I can get the 875u to map to ttyACM0 will it work?? how do i do that??  are my questions that moronic that no one feels it deserves a responce??? guess i'll keep talkin to myself for now.... lol

---

### Post by kieronch3 on 2008-02-08
p.s. pardon the poor spelling my spell checker button is broken (lame joke) and i am tired (truth)

---

### Post by The--Captain on 2008-03-12
Your scripts worked fine (where did you find them?) for my 875u after a few changes - I'll post them here when I get the chance...

Cheers,
-Jon

---

### Post by kieronch3 on 2008-03-24
i got them from sierawireless site, at&t emails and multiple other sources, i spent quite a lot of time researching, in the end it works if i put the sim in my samsung a707 (synch) phone, but does not work when it is in the sierra wireless 875u.

i gave up trying... someone else said mandriva 2008 had better 3g device compatibility i might make the switch...

---

