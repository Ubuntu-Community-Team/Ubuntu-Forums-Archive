---
title: "Getting a Sierra Wireless MC8720 module to work (need help)"
date: 2007-12-23
forum: Networking &amp; Wireless
---

### Post by ranpha on 2007-12-23
Ok so i saw the bug report for the umts module for x61. Appertnly i got a better module the 8720

so it was just fixing a extra hardcode (6832) and voila it appears in DMESG en de module sierra is loaded.

So far i think everthing is installed okay. Now comes the part where i'm lost.

I tried wvdial with a wvdial-pin.conf

gcom -d /dev/ttyUSB0 info
##### GlobeTrotter Configuration #####
Manufacturer Text:      gcom 20:10:36 -> -- Error Report --
gcom 20:10:36 -> ---->                     ^
gcom 20:10:36 -> Error @190, line 8, Could not write to COM device. (1)

 wvdial --config /etc/wvdial-pin.conf
WvDial<*1>: WvDial: Internet dialer version 1.56
WvModem<*1>: Cannot get information for serial port.
WvDial<*1>: Initializing modem.
WvDial<*1>: Sending: ATZ
WvDial<*1>: Sending: ATQ0
WvDial<*1>: Re-Sending: ATZ
WvDial<Err>: Modem not responding.



Wvdial.conf is something like this. No clue if it is right
[ModemUMTS]
Modem = /dev/umts
Baud = 460800
SetVolume = 0
Dial Command = ATDT
Init1 = ATZ
Init2 = ATM0
Init3 = ATM0
FlowControl = NOFLOW
[Dialer umts]
Username = VFD2
Password = WAP
Phone = *99***1#
Stupid Mode = 1
Init1 = ATZ
Init2 = ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
Init3 = AT+CGDCONT=1,"IP","internet"
Inherits = ModemUMTS

Wvdial-pin enters the pin .


So the problem now is that i need to enter a PIN and then connect. Can somebody help me with this

---

### Post by ranpha on 2007-12-24
update

for some unknown reason the modem works and responds to AT commands.

but i still can't enter a pin with gcom.

i get the enter PIN but than it says it's not correct (and yes i did fill in the correct numbers)

it's driving me crazy but slowly we are getting there

---

### Post by ranpha on 2007-12-26
In my wiki entry (scroll down for the last part)

is my instruction how i did things. I still doesn't work but it's a start

---

