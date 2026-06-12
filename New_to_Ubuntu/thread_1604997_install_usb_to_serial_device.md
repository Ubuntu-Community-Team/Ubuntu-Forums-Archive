---
title: "install usb to serial device"
date: 2010-10-24
forum: New to Ubuntu
---

### Post by jackscode on 2010-10-24
Ubuntu 10.4

dmesg
[ 5424.500332] usb 2-1: USB disconnect, address 7
[ 5492.931435] usb 2-1: new full speed USB device using uhci_hcd and address 8
[ 5493.177224] usb 2-1: configuration #1 chosen from 1 choice
 
lsusb
>Bus 002 Device 008: ID 0403:6001 Future Technology Devices International, Ltd FT232 USB-Serial (UART) IC

sudo modprobe usbserial vendor=0x0403 product=6001 
>FAT AL: Module usbserial not found.

On Ubuntu 9.10 there is not problem - device it showed as TTYUSB0 and I can used ex. minicom.
But with Ubuntu 10.4 I get "FATAL: Module usbserial not found." when using modprobe?

What can I do?

---

### Post by carl.davis on 2010-10-24
Does this bug apply to you?

[https://bugs.launchpad.net/ubuntu/+source/devicekit-power/+bug/507247](https://bugs.launchpad.net/ubuntu/+source/devicekit-power/+bug/507247)

It has a suggested workaround at the end of the bug report.

---

### Post by jackscode on 2010-10-25
[FONT=&quot]I have[/FONT][FONT=&quot] [/FONT][FONT=&quot]delete[/FONT] delete 95-uower-wup.rules, it is not working. 

I guss the problem is that the device is not showed under /dev

[FONT=&quot]Expect  something like /dev/ttyUSB0[/FONT]  [FONT=&quot][/FONT]

---

### Post by alexfish on 2010-10-25
> **jackscode said:**
> [FONT=&quot]I have[/FONT][FONT=&quot]delete[/FONT] delete 95-uower-wup.rules, it is not working. 

I guss the problem is that the device is not showed under /dev

[FONT=&quot]Expect  something like /dev/ttyUSB0[/FONT]  

hi

looking at the modprobe code 

sudo modprobe usbserial vendor=0x0403 product=6001

should be 

sudo modprobe usbserial vendor=0x0403 product=0x6001

however suggest checking the actual driver in 9.10

Code:

[COLOR=Blue]usb-devices[/COLOR]

look at the listings which indicate the device ( if posting , locate the lines which indicate the device and post only those lines)

the info will give the device ID's + the driver

then compare the same command "[COLOR=Blue]usb-devices"[/COLOR] with 10.04

to find the ttyXXX

Code:

[COLOR=Blue]ls -al /dev/serial/by-id/usb*[/COLOR]

alexfish

---

### Post by jackscode on 2010-10-25
>[QUOTE=alexfish;10025568]hi

>looking at the modprobe code 

>sudo modprobe usbserial vendor=0x0403 product=6001

>should be 

>sudo modprobe usbserial vendor=0x0403 product=0x6001

>however suggest checking the actual driver in 9.10
ok

>Code:

[COLOR=Blue]>usb-devices[/COLOR]
Ubuntu 10.4
  T:  Bus=02 Lev=01 Prnt=01 Port=00 Cnt=01 Dev#=  4 Spd=12  MxCh= 0
  D:  Ver= 1.10 Cls=00(>ifc ) Sub=00 Prot=00 MxPS= 8 #Cfgs=  1
  P:  Vendor=0403 ProdID=6001 Rev=04.00
  S:  Manufacturer=FTDI
  S:  Product=USB HS SERIAL CONVERTER
  S:  SerialNumber=FTF06SRC
  C:  #Ifs= 1 Cfg#= 1 Atr=a0 MxPwr=44mA
  I:  If#= 0 Alt= 0 #EPs= 2 Cls=ff(vend.) Sub=ff Prot=ff Driver=(none)
Ubun9.10
commando "usb-devices" not available  

lsusb:
Bus 004 Device 002: ID 0403:6001 Future Technology Devices International, Ltd FT232 USB-Serial (UART) IC
dmesg:
[  745.772258] usb 4-2: new full speed USB device using uhci_hcd and address 2
[  745.972276] usb 4-2: configuration #1 chosen from 1 choice
[  746.050649] usbcore: registered new interface driver usbserial
[  746.050664] USB Serial support registered for generic
[  746.050693] usbcore: registered new interface driver usbserial_generic
[  746.050695] usbserial: USB Serial Driver core
[  746.057148] USB Serial support registered for FTDI USB Serial Device
[  746.057217] ftdi_sio 4-2:1.0: FTDI USB Serial Device converter detected
[  746.057241] usb 4-2: Detected FT232BM
[  746.057243] usb 4-2: Number of endpoints 2
[  746.057245] usb 4-2: Endpoint 1 MaxPacketSize 64
[  746.057247] usb 4-2: Endpoint 2 MaxPacketSize 64
[  746.057249] usb 4-2: Setting MaxPacketSize 64
[  746.059276] usb 4-2: FTDI USB Serial Device converter now attached to ttyUSB0
[  746.059296] usbcore: registered new interface driver ftdi_sio
[  746.059298] ftdi_sio: v1.5.0:USB FTDI Serial Converters Driver



Ubuntu 10.4

dmesg - only data
[ 5424.500332] usb 2-1: USB disconnect, address 7
[ 5492.931435] usb 2-1: new full speed USB device using uhci_hcd and address 8
[ 5493.177224] usb 2-1: configuration #1 chosen from 1 choice


  

 >look at the listings which indicate the device ( if posting , locate the lines which >indicate the device and post only those lines)

>the info will give the device ID's + the driver

>then compare the same command "[COLOR=Blue]usb-devices"[/COLOR] with 10.04

>to find the ttyXXX

>Code:

[COLOR=Blue]>ls -al /dev/serial/by-id/usb*[/COLOR]
Ubuntu 9.10
06SRC-if00-port0 
lrwxrwxrwx 1 root root 13 2010-10-25 23:02 /dev/serial/by-id/usb-FTDI_USB_HS_SERIAL_CONVERTER_FTF06SRC-if00-port0 -> ../../ttyUSB0
this symbolic link or path /dev/serial/by-id do not exist on my 10.4 version.

---

### Post by alexfish on 2010-10-25
in 10.04 ,search on file system 

should have
 
ftdi-sio.ko
sio.h 

on 9.10

to find actual name of driver

Code:

lsusb -t

look through the listings for the driver 

then when in 10.04

try modeprobe the device with the driver module name

or to load the module

Code:

sudo modeprobe <driver module name >

ADDED have a look at this single thread , at foot of page attachments  is a script file [COLOR=Blue]usb-devices[/COLOR] 

 #[**1**]("http://ubuntuforums.org/showpost.php?p=9200750&postcount=1")

---

### Post by jackscode on 2010-10-28
Hi
>should have
 
>ftdi-sio.ko
>sio.h 

I'm missing this files on Ubuntu 10.04 version. 
Will try link 
[http://ubuntuforums.org/showthread.php?t=1327965](http://ubuntuforums.org/showthread.php?t=1327965)
for compiling of the ftdi-sio.ko driver

Thanks

---

