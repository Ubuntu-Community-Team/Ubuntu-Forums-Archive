---
title: "HUAWEI ETS2556 Fixed Wireless Terminal"
date: 2006-11-20
forum: Networking &amp; Wireless
---

### Post by rozilla on 2006-11-20
i can't get my usb modem to work. this is the log i get when i type **sudo tail -f /var/log/messages** after plugging in the serial-to-usb cable. the usb part goes into my Dell OptiPlex desktop.
help please:confused:

---

### Post by rozilla on 2006-11-20
i forgot to post the log:

Nov 13 10:44:31 BlackBetty kernel: [  823.806741] usb 1-2: new full speed USB device using uhci_hcd and address 15
Nov 13 10:44:31 BlackBetty kernel: [  823.955199] ti_usb_3410_5052 1-2:1.0: TI USB 3410 1 port adapter converter detected
Nov 13 10:44:32 BlackBetty kernel: [  824.582217] usb 1-2: reset full speed USB device using uhci_hcd and address 15
Nov 13 10:44:32 BlackBetty kernel: [  824.707518] usb 1-2: device firmware changed
Nov 13 10:44:32 BlackBetty kernel: [  824.707563] ti_usb_3410_5052: probe of 1-2:1.0 failed with error -5
Nov 13 10:44:32 BlackBetty kernel: [  824.707788] usb 1-2: USB disconnect, address 15
Nov 13 10:44:32 BlackBetty kernel: [  824.810052] usb 1-2: new full speed USB device using uhci_hcd and address 16
Nov 13 10:44:32 BlackBetty kernel: [  824.980472] usb 1-2: configuration #1 chosen from 2 choices
Nov 13 10:44:32 BlackBetty kernel: [  824.982446] ti_usb_3410_5052 1-2:1.0: TI USB 3410 1 port adapter converter detected
Nov 13 10:44:32 BlackBetty kernel: [  824.982481] ti_usb_3410_5052: probe of 1-2:1.0 failed with error -5

---

### Post by rozilla on 2006-11-25
also this is what i get from **sudo lsusb -v | less**


Bus 001 Device 003: ID 0451:3410 Texas Instruments, Inc. TUSB3410 Microcontroller
Device Descriptor:
  bLength                18
  bDescriptorType         1
  bcdUSB               1.10
  bDeviceClass          255 Vendor Specific Class
  bDeviceSubClass         0 
  bDeviceProtocol         0 
  bMaxPacketSize0         8
  idVendor           0x0451 Texas Instruments, Inc.
  idProduct          0x3410 TUSB3410 Microcontroller
  bcdDevice            1.00
  iManufacturer           1 Texas Instruments
  iProduct                2 TUSB3410 Boot Device
  iSerial                 3 TUSB3410        
  bNumConfigurations      2
  Configuration Descriptor:
    bLength                 9
    bDescriptorType         2
    wTotalLength           25
    bNumInterfaces          1
    bConfigurationValue     1
    iConfiguration          0 
    bmAttributes         0x80
      (Bus Powered)
    MaxPower              100mA
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        0
      bAlternateSetting       0
      bNumEndpoints           1
      bInterfaceClass       255 Vendor Specific Class
      bInterfaceSubClass      0 
      bInterfaceProtocol      0 
      iInterface              0 
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x01  EP 1 OUT
        bmAttributes            2
          Transfer Type            Bulk
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0040  1x 64 bytes
        bInterval               0
  Configuration Descriptor:
    bLength                 9
    bDescriptorType         2
    wTotalLength           39
    bNumInterfaces          1
    bConfigurationValue     2
    iConfiguration          0 
    bmAttributes         0xa0
      (Bus Powered)
      Remote Wakeup
    MaxPower              100mA
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        0
      bAlternateSetting       0
      bNumEndpoints           3
      bInterfaceClass       255 Vendor Specific Class
      bInterfaceSubClass      0 
      bInterfaceProtocol      0 
      iInterface              0 
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x81  EP 1 IN
        bmAttributes            2
          Transfer Type            Bulk
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0040  1x 64 bytes
        bInterval               0
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x01  EP 1 OUT
        bmAttributes            2
          Transfer Type            Bulk
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0040  1x 64 bytes
        bInterval               0
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x83  EP 3 IN
        bmAttributes            3
          Transfer Type            Interrupt
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0002  1x 2 bytes
        bInterval               1
Device Status:     0x0001
  Self Powered

Bus 001 Device 001: ID 0000:0000  
Device Descriptor:
  bLength                18
  bDescriptorType         1
  bcdUSB               1.10
  bDeviceClass            9 Hub
  bDeviceSubClass         0 Unused
  bDeviceProtocol         0 
  bMaxPacketSize0        64
  idVendor           0x0000 
  idProduct          0x0000 
  bcdDevice            2.06
  iManufacturer           3 Linux 2.6.15-23-386 uhci_hcd
  iProduct                2 UHCI Host Controller
  iSerial                 1 0000:00:07.2
  bNumConfigurations      1
  Configuration Descriptor:
    bLength                 9
    bDescriptorType         2
    wTotalLength           25
    bNumInterfaces          1
    bConfigurationValue     1
    iConfiguration          0 
    bmAttributes         0xc0
      Self Powered
    MaxPower                0mA
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        0
      bAlternateSetting       0
      bNumEndpoints           1
      bInterfaceClass         9 Hub
      bInterfaceSubClass      0 Unused
      bInterfaceProtocol      0 
      iInterface              0 
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x81  EP 1 IN
        bmAttributes            3
          Transfer Type            Interrupt
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0002  1x 2 bytes
        bInterval             255
Hub Descriptor:
  bLength               9
  bDescriptorType      41
  nNbrPorts             2
  wHubCharacteristic 0x000a
    No power switching (usb 1.0)
    Per-port overcurrent protection
  bPwrOn2PwrGood        1 * 2 milli seconds
  bHubContrCurrent      0 milli Ampere
  DeviceRemovable    0xc8
  PortPwrCtrlMask    0xc0 
 Hub Port Status:
   Port 1: 0000.0100 power
   Port 2: 0000.0103 power enable connect
Device Status:     0x0001
  Self Powered

---

### Post by rozilla on 2006-12-07
i've made some progress, but i still can't get online with dapper

$ wvdialconf

> Editing `/etc/wvdial.conf'.

Scanning your serial ports for a modem.

ttyS0<*1>: ATQ0 V1 E1 -- failed with 2400 baud, next try: 9600 baud
ttyS0<*1>: ATQ0 V1 E1 -- failed with 9600 baud, next try: 115200 baud
ttyS0<*1>: ATQ0 V1 E1 -- and failed too at 115200, giving up.
ttyS1<*1>: ATQ0 V1 E1 -- failed with 2400 baud, next try: 9600 baud
ttyS1<*1>: ATQ0 V1 E1 -- failed with 9600 baud, next try: 115200 baud
ttyS1<*1>: ATQ0 V1 E1 -- and failed too at 115200, giving up.
Modem Port Scan<*1>: S2   S3   S4   S5   S6   S7   S8   S9
Modem Port Scan<*1>: S10  S11  S12  S13  S14  S15  S16  S17
Modem Port Scan<*1>: S18  S19  S20  S21  S22  S23  S24  S25
Modem Port Scan<*1>: S26  S27  S28  S29  S30  S31  S32  S33
Modem Port Scan<*1>: S34  S35  S36  S37  S38  S39  S40  S41
Modem Port Scan<*1>: S42  S43  S44  S45  S46  S47
WvModem<*1>: Cannot get information for serial port.
ttyUSB0<*1>: ATQ0 V1 E1 -- failed with 2400 baud, next try: 9600 baud
ttyUSB0<*1>: ATQ0 V1 E1 -- failed with 9600 baud, next try: 115200 baud
ttyUSB0<*1>: ATQ0 V1 E1 -- and failed too at 115200, giving up.


Sorry, no modem was detected!  Is it in use by another program?
Did you configure it properly with setserial?

Please read the FAQ at [http://open.nit.ca/wiki/?WvDial](http://open.nit.ca/wiki/?WvDial)

If you still have problems, send mail to <wvdial-list@lists.nit.ca>.



$ lsusb

> Bus 001 Device 002: ID 0451:3410 Texas Instruments, Inc. TUSB3410 Microcontroller
Bus 001 Device 001: ID 0000:0000


$ ls -al /dev/ttyU*

> crw-rw---- 1 root dialout 188, 0 2006-12-07 19:04 /dev/ttyUSB0


$ lsmod | grep ti_usb_3410

> ti_usb_3410_5052       55112  0 
usbserial              31336  1 ti_usb_3410_5052
usbcore               129668  4 ti_usb_3410_5052,usbserial,uhci_hcd



$ lsmod | grep ppp

> ppp_generic            30100  0
slhc                    7424  1 ppp_generic

there's no **ppp_async** and **ppp_deflate**. why?


there's no 'scripts' directory in /etc/udev
and also no file called 'static_devices.txt'

> drwxr-xr-x   3 root root 4096 2006-05-31 01:50 .
drwxr-xr-x 108 root root 4096 2006-12-07 20:42 ..
drwxr-xr-x   2 root root 4096 2006-11-26 19:35 rules.d
-rw-r--r--   1 root root  226 2006-05-22 15:25 udev.conf



and there's no 50-rules in /etc/udev/rules.d

> -rw-r--r-- 1 root root   262 2006-05-22 15:25 00-init.rules
-rw-r--r-- 1 root root  2264 2006-05-22 15:25 20-names.rules
-rw-r--r-- 1 root root   190 2006-05-22 15:25 25-iftab.rules
-rw-r--r-- 1 root root  3048 2006-05-22 15:25 40-permissions.rules
-rw-r--r-- 1 root root 47992 2006-05-31 01:55 45-libgphoto2.rules
-rw-r--r-- 1 root root 28262 2006-04-06 08:12 45-libsane.rules
-rw-r--r-- 1 root root  1306 2006-05-22 15:25 60-symlinks.rules
-rw-r--r-- 1 root root  2585 2006-05-22 15:25 65-persistent-disk.rules
-rw-r--r-- 1 root root   385 2006-05-22 15:25 80-programs.rules
-rw-r--r-- 1 root root   171 2006-05-29 13:03 85-alsa.rules
-rw-r--r-- 1 root root   208 2006-05-22 16:09 85-hal.rules
-rw-r--r-- 1 root root    81 2006-01-04 12:13 85-hdparm.rules
-rw-r--r-- 1 root root   126 2006-05-16 02:43 85-hwclock.rules
-rw-r--r-- 1 root root   657 2006-01-30 14:40 85-ifupdown.rules
-rw-r--r-- 1 root root  1131 2006-03-08 00:36 85-linux-wlan-ng.rules
-rw-r--r-- 1 root root   937 2006-03-23 21:40 85-pcmcia.rules
-rw-r--r-- 1 root root    82 2006-05-22 16:09 90-hal.rules
-rw-r--r-- 1 root root  2534 2006-05-22 15:25 90-modprobe.rules
-rw-r--r-- 1 root root    75 2006-05-22 15:25 99-udevmonitor.rules


i also have no path called '/etc/hotplug.d/usb/'

help please

---

### Post by mips on 2006-12-07
Do a search for huawei or ETS here as i think the topic might have been covered before.

---

### Post by maduranga on 2006-12-11
Hello..

 I'm using a HUAWEI CDMA phone and me too having the same problem.. 


 "ti_usb_3410_5052: probe of 2-2:1.0 failed with error -5"

 Thats what i used to get after the dmesg command.

---

### Post by daimengrui on 2007-12-01
I think this web page answers the question above, it is applicable also for HUAWEI ETS2556


[http://www.openpages.info/huawei.html]("http://www.openpages.info/huawei.html")

---

### Post by daimengrui on 2007-12-01
deleted*

---

