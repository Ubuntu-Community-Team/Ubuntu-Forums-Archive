---
title: "I need help with a huawei ets2056 on ubuntu herdy heron"
date: 2008-08-18
forum: Networking &amp; Wireless
---

### Post by madra on 2008-08-18
Hi iam trying to get a  HUAWIE ETS2056 Modem installed on a DELL OPTIPLEX 330 DUAL CORE with UBUNTU 8.04 LTS....i have tried everying on the internet and i have finally managed to get it read as ttyUSB0...problem is the thing has refused to dial up
This is the verbose
root@dra:~# wvdial dra
--> WvDial: Internet dialer version 1.60
--> Cannot get information for serial port.
--> Initializing modem.
--> Sending: ATZ
--> Sending: ATQ0
--> Re-Sending: ATZ
--> Modem not responding.

///This is ths wvdial.conf file

[Dialer dra]
Modem= /dev/ttyUSB0
Baud= 230400
SetVolume= 0
DialCommand=ATDT
Init=ATZ
Init2=AT+CRM=1;$LGPKT=3
Dial Command = ATDT
Init1 = ATZ
Init3 = ATM0
FlowControl= OFF
Username = 22XXXXXXXX
Password = 22XXXXXXXX
Phone = #777
Stupid Mode = 1
Inherits = Dialer dra

root@dra:~# ls -l /dev/ttyUSB0
crw-rw---- 1 root dialout 188, 0 2008-08-10 20:22 /dev/ttyUSB0

root@dra:~# wvdialconf /ect/wvdial.conf
Editing `/ect/wvdial.conf'.

Scanning your serial ports for a modem.

WvModem<*1>: Cannot get information for serial port.
ttyS0<*1>: ATQ0 V1 E1 -- failed with 2400 baud, next try: 9600 baud
ttyS0<*1>: ATQ0 V1 E1 -- failed with 9600 baud, next try: 9600 baud
ttyS0<*1>: ATQ0 V1 E1 -- and failed too at 115200, giving up.
Modem Port Scan<*1>: S1 S2 S3
WvModem<*1>: Cannot get information for serial port.
ttyUSB0<*1>: ATQ0 V1 E1 -- failed with 2400 baud, next try: 9600 baud
ttyUSB0<*1>: ATQ0 V1 E1 -- failed with 9600 baud, next try: 9600 baud
ttyUSB0<*1>: ATQ0 V1 E1 -- and failed too at 115200, giving up.

Sorry, no modem was detected! Is it in use by another program?
Did you configure it properly with setserial?

root@dra:~# setserial /dev/ttyUSB0
Cannot get serial info: Invalid argument
root@dra:~# setserial -a /dev/ttyUSB0
Cannot get serial info: Invalid argument
root@dra:~# setserial -g /dev/ttyUSB0
Cannot get serial info: Invalid argument
root@dra:~# ls -l /dev/ttyUSB0

dmesg grep
[ 96.872524] usbcore: registered new interface driver usbserial
[ 96.872543] /build/buildd/linux-2.6.24/drivers/usb/serial/usb-serial.c: USB Serial support registered for generic
[ 96.872561] usbcore: registered new interface driver usbserial_generic
[ 96.872563] /build/buildd/linux-2.6.24/drivers/usb/serial/usb-serial.c: USB Serial Driver core
[ 100.203784] usb 4-1: new full speed USB device using uhci_hcd and address 2
[ 100.396703] usb 4-1: configuration #1 chosen from 1 choice
[ 100.400610] usbserial_generic 4-1:1.0: generic converter detected
[ 100.400719] usb 4-1: generic converter now attached to ttyUSB0
[ 100.464698] /build/buildd/linux-2.6.24/drivers/usb/serial/usb-serial.c: USB Serial support registered for TI USB 3410 1 port adapter
[ 100.464719] /build/buildd/linux-2.6.24/drivers/usb/serial/usb-serial.c: USB Serial support registered for TI USB 5052 2 port adapter
[ 100.464746] usbcore: registered new interface driver ti_usb_3410_5052
[ 100.464748] /build/buildd/linux-2.6.24/drivers/usb/serial/ti_usb_3410_5052.c: TI USB 3410/5052 Serial Driver v0.9
[ 233.946722] end_request: I/O error, dev fd0, sector 0

 lsusb -v

Bus 004 Device 002: ID 0451:3410 Texas Instruments, Inc. TUSB3410 Microcontroller
Device Descriptor:
  bLength 18
  bDescriptorType 1
  bcdUSB 1.10
  bDeviceClass 255 Vendor Specific Class
  bDeviceSubClass 0
  bDeviceProtocol 0
  bMaxPacketSize0 8
  idVendor 0x0451 Texas Instruments, Inc.
  idProduct 0x3410 TUSB3410 Microcontroller
  bcdDevice 1.00
  iManufacturer 1 Texas Instruments
  iProduct 2 TUSB3410 Boot Device
  iSerial 3 TUSB3410
  bNumConfigurations 1
  Configuration Descriptor:
    bLength 9
    bDescriptorType 2
    wTotalLength 25
    bNumInterfaces 1
    bConfigurationValue 1
    iConfiguration 0
    bmAttributes 0x80
      (Bus Powered)
    MaxPower 100mA
    Interface Descriptor:
      bLength 9
      bDescriptorType 4
      bInterfaceNumber 0
      bAlternateSetting 0
      bNumEndpoints 1
      bInterfaceClass 255 Vendor Specific Class
      bInterfaceSubClass 0
      bInterfaceProtocol 0
      iInterface 0
      Endpoint Descriptor:
        bLength 7
        bDescriptorType 5
        bEndpointAddress 0x01 EP 1 OUT
        bmAttributes 2
          Transfer Type Bulk
          Synch Type None
          Usage Type Data
        wMaxPacketSize 0x0040 1x 64 bytes
        bInterval 0
Device Status: 0x0000
  (Bus Powered)

i need your help people,i have been at this for like a week and iam losing sleep cos iam not the kind of person to give up...especially when it comes to my computer

---

### Post by itix on 2008-08-19
Don't know if it will help you, but this thread seam to regard your problem: [http://www.linuxquestions.org/questions/linux-hardware-18/huawei-ets2056-being-reported-as-a-loopback-serial-493212/](http://www.linuxquestions.org/questions/linux-hardware-18/huawei-ets2056-being-reported-as-a-loopback-serial-493212/)

---

