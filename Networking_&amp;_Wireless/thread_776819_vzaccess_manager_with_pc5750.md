---
title: "vzaccess manager with pc5750"
date: 2008-05-01
forum: Networking &amp; Wireless
---

### Post by vladZam on 2008-05-01
Hello,

I've run into a problem using PC5750VW after re-installing 8.04 on my laptop. Prior to re-installation it did recognized as ttyACM0 and now it shows as following 

[ 2517.044187] pccard: CardBus card inserted into slot 0
[ 2517.044565] PCI: Enabling device 0000:03:00.0 (0000 -> 0002)
[ 2517.044581] ACPI: PCI Interrupt 0000:03:00.0[A] -> Link [LNKD] -> GSI 11 (level, low) -> IRQ 11
[ 2517.044614] PCI: Setting latency timer of device 0000:03:00.0 to 64
[ 2517.044623] ohci_hcd 0000:03:00.0: OHCI Host Controller
[ 2517.044694] ohci_hcd 0000:03:00.0: new USB bus registered, assigned bus number 5
[ 2517.044723] ohci_hcd 0000:03:00.0: irq 11, io mem 0x90000000
[  719.206361] usb usb5: configuration #1 chosen from 1 choice
[  719.208744] hub 5-0:1.0: USB hub found
[  719.209128] hub 5-0:1.0: 1 port detected
[  719.310218] PCI: Enabling device 0000:03:00.1 (0000 -> 0002)
[  719.310230] ACPI: PCI Interrupt 0000:03:00.1[B] -> Link [LNKD] -> GSI 11 (level, low) -> IRQ 11
[  719.310251] PCI: Setting latency timer of device 0000:03:00.1 to 64
[  719.310255] ohci_hcd 0000:03:00.1: OHCI Host Controller
[  719.310278] ohci_hcd 0000:03:00.1: new USB bus registered, assigned bus number 6
[  719.310292] ohci_hcd 0000:03:00.1: irq 11, io mem 0x90001000
[  719.396312] usb usb6: configuration #1 chosen from 1 choice
[  719.396709] hub 6-0:1.0: USB hub found
[  719.396916] hub 6-0:1.0: 1 port detected
[ 2520.763029] usb 5-1: new full speed USB device using ohci_hcd and address 2
[  720.399340] usb 5-1: configuration #1 chosen from 1 choice
[  720.405123] airprime 5-1:1.0: airprime converter detected
[  720.405278] usb 5-1: airprime converter now attached to ttyUSB0
[  720.405320] usb 5-1: airprime converter now attached to ttyUSB1
[  720.405363] usb 5-1: airprime converter now attached to ttyUSB2
[  720.405418] airprime 5-1:1.1: airprime converter detected
[  720.405463] usb 5-1: airprime converter now attached to ttyUSB3
[  720.405505] usb 5-1: airprime converter now attached to ttyUSB4
[  720.405548] usb 5-1: airprime converter now attached to ttyUSB5
[  720.407310] airprime 5-1:1.2: airprime converter detected
[  720.407364] usb 5-1: airprime converter now attached to ttyUSB6
[  720.407410] usb 5-1: airprime converter now attached to ttyUSB7
[  720.407451] usb 5-1: airprime converter now attached to ttyUSB8

so wvdialconf does generate /etc/wvdial.conf with such entries 

Editing `/etc/wvdial.conf'.

Scanning your serial ports for a modem.

ttyS0<*1>: ATQ0 V1 E1 -- failed with 2400 baud, next try: 9600 baud
ttyS0<*1>: ATQ0 V1 E1 -- failed with 9600 baud, next try: 115200 baud
ttyS0<*1>: ATQ0 V1 E1 -- and failed too at 115200, giving up.
Modem Port Scan<*1>: S1   S2   S3   
ttyACM0<Info>: Inappropriate ioctl for device
Modem Port Scan<*1>: ACM0 
ttyUSB0<Info>: Exec format error
Modem Port Scan<*1>: USB0 
ttyUSB1<Info>: Exec format error
Modem Port Scan<*1>: USB1 
ttyUSB2<Info>: Exec format error
Modem Port Scan<*1>: USB2 
WvModem<*1>: Cannot get information for serial port.
ttyUSB3<*1>: ATQ0 V1 E1 -- OK
ttyUSB3<*1>: ATQ0 V1 E1 Z -- OK
ttyUSB3<*1>: ATQ0 V1 E1 S0=0 -- OK
ttyUSB3<*1>: ATQ0 V1 E1 S0=0 &C1 -- OK
ttyUSB3<*1>: ATQ0 V1 E1 S0=0 &C1 &D2 -- OK
ttyUSB3<*1>: ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0 -- OK
ttyUSB3<*1>: Modem Identifier: ATI -- Manufacturer: UTStarcom communication Inc.
ttyUSB3<*1>: Speed 9600: AT -- OK
ttyUSB3<*1>: Max speed is 9600; that should be safe.
ttyUSB3<*1>: ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0 -- OK
ttyUSB4<Info>: Exec format error
ttyUSB5<Info>: Exec format error
Modem Port Scan<*1>: USB5 
WvModem<*1>: Cannot get information for serial port.
ttyUSB6<*1>: ATQ0 V1 E1 -- failed with 2400 baud, next try: 9600 baud
ttyUSB6<*1>: ATQ0 V1 E1 -- failed with 9600 baud, next try: 9600 baud
ttyUSB6<*1>: ATQ0 V1 E1 -- and failed too at 115200, giving up.
ttyUSB7<Info>: Exec format error
Modem Port Scan<*1>: USB7 
ttyUSB8<Info>: Exec format error
Modem Port Scan<*1>: USB8 

Found a modem on /dev/ttyUSB3.
Modem configuration written to /etc/wvdial.conf.
ttyUSB3<Info>: Speed 9600; init "ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0"



[Dialer Defaults]
Init1 = ATZ
Init2 = ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
Modem Type = Analog Modem
; Phone = <Target Phone Number>
ISDN = 0
; Password = <Your Password>
; Username = <Your Login Name>
Modem = /dev/ttyUSB3
Baud = 9600


which is not what I would expect ...

Any attempts to get connected (with proper #777 phone number, usernam and password to VZW )  fails.

I have tried to offloca ohci-hcd and usbserial but the latter one would not go off. Any idea what had happened? I've used same media and same steps during first and successfull installation and re-installed and current?

-vzv

---

