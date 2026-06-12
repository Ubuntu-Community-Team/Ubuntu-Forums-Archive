---
title: "HOWTO: internet dailing using sony ericsson handphone via bluetooth"
date: 2008-02-12
forum: Networking &amp; Wireless
---

### Post by piju on 2008-02-12
today I wanna share with u how to configure internet connection using sony ericsson via bluetooth.

the step by step is includes how to check detected device, configuring the files, and dialing using wvdial, a command line dialer.

 

firstly,

is ur laptop got bluetooth ?

 

root@x-laptop:~# dmesg | grep Bluetooth

[ 34.632530] Bluetooth: Core ver 2.11

[ 34.632581] Bluetooth: HCI device and connection manager initialized

[ 34.632585] Bluetooth: HCI socket layer initialized

[ 34.677235] Bluetooth: HCI USB driver ver 2.9

[ 43.881409] Bluetooth: L2CAP ver 2.8

[ 43.881416] Bluetooth: L2CAP socket layer initialized

[ 44.006424] Bluetooth: RFCOMM socket layer initialized

[ 44.006728] Bluetooth: RFCOMM TTY layer initialized

[ 44.006733] Bluetooth: RFCOMM ver 1.8

 

got bluetooth apps installed ?

 

root@x-laptop:~# dpkg -l | grep blue

ii bluez-cups 3.19-0ubuntu3 Bluetooth printer driver for CUPS

ii bluez-gnome 0.14-0ubuntu2 Bluetooth utilities for GNOME

ii bluez-utils 3.19-0ubuntu3 Bluetooth tools and daemons

ii gnome-bluetooth 0.9.1-0ubuntu1 GNOME Bluetooth tools.

ii libbluetooth2 3.19-0ubuntu1 Library to use the BlueZ Linux Bluetooth sta

 

probe ur device, detected or not using hcitool

 

root@x-laptop:~# hcitool scan

Scanning …

00:1A:75:0A:06:63 Z610i

 

 

 

is this device supporting the internet via bluetooth ?

check it out, give me the result!

using sdptool

root@x-laptop:~# sdptool browse 00:1A:75:0A:06:63

Browsing 00:1A:75:0A:06:63 … ( result skipped )

 

the important is, ur hp must have this to enable internet via bluetooth connection

 

Service Name: Dial-up Networking

Service RecHandle: 0×10002

Service Class ID List:

“Dialup Networking” (0×1103)

“Generic Networking” (0×1201)

Protocol Descriptor List:

“L2CAP” (0×0100)

“RFCOMM” (0×0003)

Channel: 2

Profile Descriptor List:

“Dialup Networking” (0×1103)

Version: 0×0100

 

remember the channel as shown above.

then edit /etc/bluetooth/rfcomm.conf

add this

 

rfcomm0 {
bind yes;
device 00:1A:75:0A:06:63; <— replace with urs
channel 2;
comment “Z610i”; <—anything u want to
}

 

then restart the service

 

#/etc/init.d/bluetooth restart

 

great, now u can proceed to the next step,

configuring wvdial

 

edit /etc/wvdial.conf

this is my mine

 

[Dialer Z610i]

Phone = *99# <-change with urs isp

Username = maxis <-change with urs

Password = wap <-change with urs

New PPPD = yes

Dial Command = ATDT

Modem = /dev/rfcomm0

Baud = 460800

Dial Command = ATDT

Init2 = ATZ

Init3 = ATM0

Init4 = at+cgdcont=1,”ip”,”unet” <-change with urs

FlowControl = crtscts

Modem Type = Analog Modem

 

save and exit,

 

then u can start to dial using the command

 

#wvdial Z610i

this is my result

 

x@x-laptop:~# wvdial Z610i

WvDial<*1>: WvDial: Internet dialer version 1.56

WvModem<*1>: Cannot get information for serial port.

WvDial<*1>: Initializing modem.

WvDial<*1>: Sending: ATZ

WvDial Modem<*1>: ATZ

WvDial Modem<*1>: OK

WvDial<*1>: Sending: ATZ

WvDial Modem<*1>: ATZ

WvDial Modem<*1>: OK

WvDial<*1>: Sending: ATM0

WvDial Modem<*1>: ATM0

WvDial Modem<*1>: OK

WvDial<*1>: Sending: at+cgdcont=1,”ip”,”unet”

WvDial Modem<*1>: at+cgdcont=1,”ip”,”unet”

WvDial Modem<*1>: OK

WvDial<*1>: Modem initialized.

WvDial<*1>: Sending: ATDT*99#

WvDial<*1>: Waiting for carrier.

WvDial Modem<*1>: ATDT*99#

WvDial Modem<*1>: CONNECT

WvDial Modem<*1>: ~[7f]}#@!}!}!} }9}#}%B#}%}(}”}’}”}”}&} } } } }%}&~Pm7P[~

WvDial<*1>: Carrier detected. Waiting for prompt.

WvDial Modem<*1>: ~[7f]}#@!}!}”} }9}#}%B#}%}(}”}’}”}”}&} } } } }%}&~Pm7}<6~

WvDial<*1>: PPP negotiation detected.

WvDial<Notice>: Starting pppd at Tue Feb 12 02:00:46 2008

WvDial<Notice>: Pid of pppd: 9966

WvDial<*1>: Using interface ppp0

WvDial<*1>: local IP address 58.71.203.17

WvDial<*1>: remote IP address 10.64.64.64

WvDial<*1>: primary DNS address 10.213.17.1

WvDial<*1>: secondary DNS address 10.213.17.2

 

u are now connected to the internet via bluetooth!!!

 

;)

 

p/s: try using Kppp, it is more user friendly

---

### Post by crisjrvt on 2008-02-15
Thanks for this how-to..., i was already giving up search how to connect via blutooth.

Will give it a try this weekend,

I'm will be using Feisty on Abit SA6, Widcomm BT,  Nokia 6820 and Globe Philippines (my celphone network offering internet access).  Thanks .....

---

### Post by crisjrvt on 2008-02-16
Many thanks.........and more power.

---

