---
title: "airtel grps on hardy giving error while connecting"
date: 2008-10-02
forum: Networking &amp; Wireless
---

### Post by pratiks19 on 2008-10-02
i use a motorola L9 mobile,
also the OS used by me is ubuntu 8.04

my problem:
i'm not able to connect to airtel gprs via bluetooth.

for connecting i typed:
1) hcitool scan
2) sdptool browse <mac addr>
3) sudo rfcomm bind 1 <mac addr>
4) sudo wvdial GPRS

at the terminal.

i get the error as :
**cannot open /dev/rfcomm1: connection refused**

the bluetooth modem is at channel 1.

chk out the **wvdial.conf**:

[Modem0]
Modem = /dev/rfcomm1
Baud = 230400
SetVolume = 0
DialCommand = ATDT
FlowControl = Hardware(CRTSCTS)
[Modem1]
Modem = /dev/ttyACM0
Baud = 230400
SetVolume = 0
DialCommand = ATDT
FlowControl = Hardware(CRTSCTS)
[Dialer GPRS]
Username = <>
Password = <>
Phone = *99***1#
Mode = 1
Inherits = Modem0
[Dialer DATA]
Username = <>
Password = <>
Phone = *99***1#
Mode = 1
Inherits = Modem1
[Dialer Defaults]
Modem = /dev/rfcomm1
Baud = 230400
Init1 = ATZ
Init2 = ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
Init3 = AT+CGDCONT=1,"IP","airtelgprs.com"
ISDN = 0
Modem Type = Analog Modem
Area Code =
Phone = *99***1#
Username = <>
Password = <>
Ask Password = 0
Dial Command = ATDT
Stupid Mode = 1
Compuserve = 0
Force Address =
Idle Seconds = 3600
DialMessage1 =
DialMessage2 =
ISDN = 0
Auto DNS = 1

**rfcomm.conf**:
#
# RFCOMM configuration file.
#

#rfcomm0 {
# # Automatically bind the device at startup
# bind no;
#
# # Bluetooth address of the device
# device 00:17:E6:BE:CD:11;
#
# # RFCOMM channel for the connection
# channel 1;
#
# # Description of the connection
# comment "Example Bluetooth device";
#}


**hcid.conf**:
#
# HCI daemon configuration file.
#

# HCId options
options {
# Automatically initialize new devices
autoinit yes;

# Security Manager mode
# none - Security manager disabled
# auto - Use local PIN for incoming connections
# user - Always ask user for a PIN
#
security user;

# Pairing mode
# none - Pairing disabled
# multi - Allow pairing with already paired devices
# once - Pair once and deny successive attempts
pairing multi;

# Default PIN code for incoming connections
passkey "1234";
}

# Default settings for HCI devices
device {
# Local device name
# %d - device id
# %h - host name
name "%h-%d";

# Local device class
class 0x000100;

# Default packet type
#pkt_type DH1,DM1,HV1;

# Inquiry and Page scan
iscan enable; pscan enable;
discovto 0;

# Default link mode
# none - no specific policy
# accept - always accept incoming connections
# master - become master on incoming connections,
# deny role switch on outgoing connections
lm accept;

# Default link policy
# none - no specific policy
# rswitch - allow role switch
# hold - allow hold mode
# sniff - allow sniff mode
# park - allow park mode
lp rswitch,hold,sniff,park;
}


This problem started when i installed win XP on my system( when ubuntu was already present). I lost grub, so
I reinstalled the grub.I had to change the partition numbers for booting ubuntu from the grub.
After this the GPRS would not connect, it gave the above mentioned error.

---

### Post by pratiks19 on 2008-10-02
**[COLOR="Red"]plz help me asap !!![/COLOR]**

---

