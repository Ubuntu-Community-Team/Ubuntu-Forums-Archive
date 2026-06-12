---
title: "Conexant USB adsl modem. HELP!!  :("
date: 2004-12-30
forum: Networking &amp; Wireless
---

### Post by charleyramm on 2004-12-30
I am using a conexant usb adsl modem. I have patched my kernel and I think that worked, but i'm having trouble running the cxstart.sh script. Does anyone know about the files /etc/ppp/options and /etc/ppp/pap-secrets or chap-secrets.
 The patch is applied to the default ubuntu kernel. 2.6.8.1 although that is not the kernel it is designed for. How can i check if it is working, other than 'the lights are flashing'?
 If you would like to see my /etc/ppp/options or any other file, i will post them. 

This is the result of running cxstart.sh
> charley@gateway:~ $ sudo cxstart.sh
Password:
>>> Inits Conexant AccessRunner <<<

time to remove modules driver cxacru
>>> Removing cxacru driver...

time to remove modules driver
>>> Loading firmware...
Conexant AccessRunner microcode upload program. 6/9/2003
Josep Comas <jcomas@gna.es>
See credits in documentation

I found ADSL modem with VendorID = 0572 & ProductID = cb00
Loading and sending /usr/sbin/cxfirm4.bin...
Firmware is sent!
Setting configuration...
Waiting ADSL line is up (until 90 seconds)...
................
ADSL line is up (Downstream 512 Kbits/s, Upstream 128 Kbits/s)
time to remove modules driver
time to remove modules driver
checking remove modules
>>> Loading driver...
Launching driver in normal mode...

/usr/sbin/cxload.sh successful
Setting PPP over ATM...
>>> Setting PPPoA <<<

>>> Loading ppp_generic...

>>> Loading pppoatm...

>>> Activating send/receive data...
Conexant AccessRunner ioctl call. 6/9/2003
Josep Comas <jcomas@gna.es>
See credits in documentation

I found ADSL modem with VendorID = 0572 & ProductID = cb00
Error in ioctl call, status = -1

---

### Post by charleyramm on 2004-12-30
chap-secrets file. 
> charley@gateway:/etc/ppp $ sudo cat /etc/ppp/chap-secrets
# Secrets for authentication using CHAP
# client        server  secret                  IP addresses
adsluser*pass*


---

### Post by charleyramm on 2004-12-30
/etc/cxacru file. 

> charley@gateway:/etc $ cat cxacru
#
# Config file for Conexant AccessRunner
#

# Driver mode
DRIVER_MODE=1  # 1 = normal, 2 = debug, 3 = normal+max speed (without ask adsl status), 4 = debug+max speed (without ask adsl status)

# Protocol
PROTOCOL_MODE=2  # 1 = RFC1483/2684 routed, 2 = PPP over ATM (pppoa), 3 = RFC1483/2684 bridged, 4 = PPP over Ethernet (pppoe)
# Paths
BINARY_PATH="/usr/sbin"
ATM_PATH=""

# ADSL
#  if OPEN_MODE is blank then cxload uses default mode acoording VID & PID
#  Values for OPEN_MODE are:
#    0 = auto selection, G.Handshake
#    1 = auto selection, T1.413
#    2 = G.Handshake
#    3 = ANSI T1.413
#    4 = ITU-T G.992.1 (G.DMT)
#    5 = ITU-T G.992.2 (G.LITE)
OPEN_MODE=

# ATM
VPI=8
VCI=32

# Specific for RFC1483/2684 routed/bridged
#  if IP_ADDRESS is blank in bridged mode then it uses DHCP to get IP
IP_ADDRESS=
NETMASK=255.255.255.0
GATEWAY=

---

