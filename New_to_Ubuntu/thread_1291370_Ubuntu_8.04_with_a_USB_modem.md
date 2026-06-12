---
title: "Ubuntu 8.04 with a USB modem"
date: 2009-10-14
forum: New to Ubuntu
---

### Post by ericeclifford on 2009-10-14
Hi I have a USB modem, but I can't figure out how to get the computer to see it.

The make is a rosewill, and I heard reports it worked on 8.10 and 9.04, but Could not get how to it to work on 8.04.

From research people say it should show up on /dev/ttyACM0 but I do not see that, nor do I see a /dev/modem when I do wvdial.

Any help?

---

### Post by Kaizzer on 2009-10-14
Hi ..im no expert in modems or linux for all that matters but  i do have a similar problem with an USB modem ( in fact with two..) 
from what i've learned...you should consider doing a search of with the Modem Model and you would find (with luck) more than one thread related to it. 

looks like there is more than one way to do everything on linux :) .. good luck .. 

regards..

---

### Post by laidback on 2009-10-14
My advice is to get a Router/hub. I had a modem to start with and although I did get it going it was a pain whenever I upgraded. Since I moved to a router I've had no problems, mine was only £30 and has proved reliable for several years now.

---

### Post by zero-n on 2009-10-14
i had some problems with my usb modem too, but i have solved  

Can you give us the output of :
```
sudo lsusb -v
```

maybe i can help you with this

---

### Post by beastrace91 on 2009-10-15
Many USB modems are "multiple usb" devices and require "flipping" before you can use the modem part of them - give [this a try](http://www.draisberghof.de/usb_modeswitch/) if this may be your issue.

~Jeff

---

### Post by lkraemer on 2009-10-15
A quick search finds this posting (Post #3)
[http://ubuntuforums.org/showthread.php?t=1148376&highlight=wvdialconf](http://ubuntuforums.org/showthread.php?t=1148376&highlight=wvdialconf)

You should ALWAYS configure wvdial, and during the configuration it searches
for all available modems.  It should locate your USB Modem......

And once wvdial has located the USB Modem you are going to need a guide to set
up a few other things:
Ref: Posting #4 starting at: If you don't have a serial port, or want to use a
USB port check out the following:

[http://ubuntuforums.org/showthread.php?t=1100310&highlight=wvdialconf](http://ubuntuforums.org/showthread.php?t=1100310&highlight=wvdialconf)

Finally, when everything is working download Gnome-PPP and set it up for easy
GUI Dialup connecting.

LK

---

### Post by ericeclifford on 2009-10-16
Thank you guys for your support, I will try all these steps and repost, once I get to my lin comp.

---

### Post by ericeclifford on 2009-10-16
```
ubuntu@ubuntu:~$ sudo lsusb -v

Bus 004 Device 001: ID 0000:0000  
Device Descriptor:
  bLength                18
  bDescriptorType         1
  bcdUSB               2.00
  bDeviceClass            9 Hub
  bDeviceSubClass         0 Unused
  bDeviceProtocol         1 Single TT
  bMaxPacketSize0        64
  idVendor           0x0000 
  idProduct          0x0000 
  bcdDevice            2.06
  iManufacturer           3 Linux 2.6.24-23-generic ehci_hcd
  iProduct                2 EHCI Host Controller
  iSerial                 1 0000:00:1d.7
  bNumConfigurations      1
  Configuration Descriptor:
    bLength                 9
    bDescriptorType         2
    wTotalLength           25
    bNumInterfaces          1
    bConfigurationValue     1
    iConfiguration          0 
    bmAttributes         0xe0
      Self Powered
      Remote Wakeup
    MaxPower                0mA
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        0
      bAlternateSetting       0
      bNumEndpoints           1
      bInterfaceClass         9 Hub
      bInterfaceSubClass      0 Unused
      bInterfaceProtocol      0 Full speed (or root) hub
      iInterface              0 
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x81  EP 1 IN
        bmAttributes            3
          Transfer Type            Interrupt
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0004  1x 4 bytes
        bInterval              12
Hub Descriptor:
  bLength              11
  bDescriptorType      41
  nNbrPorts             8
  wHubCharacteristic 0x000a
    No power switching (usb 1.0)
    Per-port overcurrent protection
    TT think time 8 FS bits
  bPwrOn2PwrGood       10 * 2 milli seconds
  bHubContrCurrent      0 milli Ampere
  DeviceRemovable    0x00 0x00
  PortPwrCtrlMask    0xff 0xff
 Hub Port Status:
   Port 1: 0000.0100 power
   Port 2: 0000.0100 power
   Port 3: 0000.0100 power
   Port 4: 0000.0100 power
   Port 5: 0000.0100 power
   Port 6: 0000.0100 power
   Port 7: 0000.0100 power
   Port 8: 0000.0100 power
Device Status:     0x0003
  Self Powered
  Remote Wakeup Enabled

Bus 003 Device 001: ID 0000:0000  
Device Descriptor:
  bLength                18
  bDescriptorType         1
  bcdUSB               1.10
  bDeviceClass            9 Hub
  bDeviceSubClass         0 Unused
  bDeviceProtocol         0 Full speed (or root) hub
  bMaxPacketSize0        64
  idVendor           0x0000 
  idProduct          0x0000 
  bcdDevice            2.06
  iManufacturer           3 Linux 2.6.24-23-generic uhci_hcd
  iProduct                2 UHCI Host Controller
  iSerial                 1 0000:00:1d.3
  bNumConfigurations      1
  Configuration Descriptor:
    bLength                 9
    bDescriptorType         2
    wTotalLength           25
    bNumInterfaces          1
    bConfigurationValue     1
    iConfiguration          0 
    bmAttributes         0xe0
      Self Powered
      Remote Wakeup
    MaxPower                0mA
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        0
      bAlternateSetting       0
      bNumEndpoints           1
      bInterfaceClass         9 Hub
      bInterfaceSubClass      0 Unused
      bInterfaceProtocol      0 Full speed (or root) hub
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
  DeviceRemovable    0x00
  PortPwrCtrlMask    0xff
 Hub Port Status:
   Port 1: 0000.0100 power
   Port 2: 0000.0100 power
Device Status:     0x0003
  Self Powered
  Remote Wakeup Enabled

Bus 002 Device 001: ID 0000:0000  
Device Descriptor:
  bLength                18
  bDescriptorType         1
  bcdUSB               1.10
  bDeviceClass            9 Hub
  bDeviceSubClass         0 Unused
  bDeviceProtocol         0 Full speed (or root) hub
  bMaxPacketSize0        64
  idVendor           0x0000 
  idProduct          0x0000 
  bcdDevice            2.06
  iManufacturer           3 Linux 2.6.24-23-generic uhci_hcd
  iProduct                2 UHCI Host Controller
  iSerial                 1 0000:00:1d.1
  bNumConfigurations      1
  Configuration Descriptor:
    bLength                 9
    bDescriptorType         2
    wTotalLength           25
    bNumInterfaces          1
    bConfigurationValue     1
    iConfiguration          0 
    bmAttributes         0xe0
      Self Powered
      Remote Wakeup
    MaxPower                0mA
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        0
      bAlternateSetting       0
      bNumEndpoints           1
      bInterfaceClass         9 Hub
      bInterfaceSubClass      0 Unused
      bInterfaceProtocol      0 Full speed (or root) hub
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
  DeviceRemovable    0x00
  PortPwrCtrlMask    0xff
 Hub Port Status:
   Port 1: 0000.0100 power
   Port 2: 0000.0100 power
Device Status:     0x0003
  Self Powered
  Remote Wakeup Enabled

Bus 001 Device 003: ID 0572:1321 Conexant Systems (Rockwell), Inc. 
Device Descriptor:
  bLength                18
  bDescriptorType         1
  bcdUSB               1.10
  bDeviceClass            2 Communications
  bDeviceSubClass         0 
  bDeviceProtocol         0 
  bMaxPacketSize0        64
  idVendor           0x0572 Conexant Systems (Rockwell), Inc.
  idProduct          0x1321 
  bcdDevice            1.00
  iManufacturer           1 Conexant
  iProduct                2 USB Modem
  iSerial                 3 24680246
  bNumConfigurations      2
  Configuration Descriptor:
    bLength                 9
    bDescriptorType         2
    wTotalLength           73
    bNumInterfaces          2
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
      bInterfaceClass         2 Communications
      bInterfaceSubClass      2 Abstract (modem)
      bInterfaceProtocol      1 AT-commands (v.25ter)
      iInterface              0 
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x81  EP 1 IN
        bmAttributes            3
          Transfer Type            Interrupt
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0040  1x 64 bytes
        bInterval             128
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        1
      bAlternateSetting       0
      bNumEndpoints           2
      bInterfaceClass        10 CDC Data
      bInterfaceSubClass      0 Unused
      bInterfaceProtocol      0 
      iInterface              0 
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x82  EP 2 IN
        bmAttributes            2
          Transfer Type            Bulk
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0040  1x 64 bytes
        bInterval               1
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x02  EP 2 OUT
        bmAttributes            2
          Transfer Type            Bulk
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0040  1x 64 bytes
        bInterval               1
      CDC Header:
        bcdCDC               1.10
      CDC Call Management:
        bmCapabilities       0x03
          call management
          use DataInterface
        bDataInterface          1
      CDC ACM:
        bmCapabilities       0x07
          sends break
          line coding and serial state
          get/set/clear comm features
      CDC Union:
        bMasterInterface        0
        bSlaveInterface         1 
      Country Selection:
        iCountryCodeRelDate        4 04052004
        wCountryCode          0x4803
  Configuration Descriptor:
    bLength                 9
    bDescriptorType         2
    wTotalLength           96
    bNumInterfaces          3
    bConfigurationValue     2
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
      bInterfaceClass         2 Communications
      bInterfaceSubClass      2 Abstract (modem)
      bInterfaceProtocol      1 AT-commands (v.25ter)
      iInterface              0 
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x81  EP 1 IN
        bmAttributes            3
          Transfer Type            Interrupt
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0040  1x 64 bytes
        bInterval             128
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        1
      bAlternateSetting       0
      bNumEndpoints           2
      bInterfaceClass        10 CDC Data
      bInterfaceSubClass      0 Unused
      bInterfaceProtocol      0 
      iInterface              0 
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x82  EP 2 IN
        bmAttributes            2
          Transfer Type            Bulk
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0040  1x 64 bytes
        bInterval              10
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x02  EP 2 OUT
        bmAttributes            2
          Transfer Type            Bulk
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0040  1x 64 bytes
        bInterval              10
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        2
      bAlternateSetting       0
      bNumEndpoints           2
      bInterfaceClass        10 CDC Data
      bInterfaceSubClass      0 Unused
      bInterfaceProtocol      0 
      iInterface              0 
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x83  EP 3 IN
        bmAttributes            2
          Transfer Type            Bulk
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0040  1x 64 bytes
        bInterval               1
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x03  EP 3 OUT
        bmAttributes            2
          Transfer Type            Bulk
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0040  1x 64 bytes
        bInterval               1
      CDC Header:
        bcdCDC               1.10
      CDC Call Management:
        bmCapabilities       0x03
          call management
          use DataInterface
        bDataInterface          1
      CDC ACM:
        bmCapabilities       0x07
          sends break
          line coding and serial state
          get/set/clear comm features
      CDC Union:
        bMasterInterface        0
        bSlaveInterface         1 
      Country Selection:
        iCountryCodeRelDate        4 04052004
        wCountryCode          0x4803
Device Status:     0x0000
  (Bus Powered)

Bus 001 Device 001: ID 0000:0000  
Device Descriptor:
  bLength                18
  bDescriptorType         1
  bcdUSB               1.10
  bDeviceClass            9 Hub
  bDeviceSubClass         0 Unused
  bDeviceProtocol         0 Full speed (or root) hub
  bMaxPacketSize0        64
  idVendor           0x0000 
  idProduct          0x0000 
  bcdDevice            2.06
  iManufacturer           3 Linux 2.6.24-23-generic uhci_hcd
  iProduct                2 UHCI Host Controller
  iSerial                 1 0000:00:1d.0
  bNumConfigurations      1
  Configuration Descriptor:
    bLength                 9
    bDescriptorType         2
    wTotalLength           25
    bNumInterfaces          1
    bConfigurationValue     1
    iConfiguration          0 
    bmAttributes         0xe0
      Self Powered
      Remote Wakeup
    MaxPower                0mA
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        0
      bAlternateSetting       0
      bNumEndpoints           1
      bInterfaceClass         9 Hub
      bInterfaceSubClass      0 Unused
      bInterfaceProtocol      0 Full speed (or root) hub
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
  DeviceRemovable    0x00
  PortPwrCtrlMask    0xff
 Hub Port Status:
   Port 1: 0000.0103 power enable connect
   Port 2: 0000.0100 power
Device Status:     0x0003
  Self Powered
  Remote Wakeup Enabled

```


This is the output of the lsusb -v

Also the modem is detected in 9.04 but not 8.04.

It is a RNX-56USB Rosewill Modem

---

### Post by ericeclifford on 2009-10-16
Ya I still can not figure out how to do this, it is a real pain.

I edited my above reply with more details, in case anyone has more luck then me.

I tried configuring wvdial, usbmodeswitch, still nothing.

---

### Post by lkraemer on 2009-10-16
Post the contents of:
/etc/wvdial.conf

lk

---

### Post by ericeclifford on 2009-10-19
well I was going to use something like this, but I could not even detect my modem yet so I have not signed up to a provider...

[Dialer Defaults]
Init1 = ATZ
Init2 = ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
Init3 = AT+CGDCONT=1,”IP”,”gpinternet”
Modem Type = USB Modem
Baud = 460800
New PPPD = yes
Modem = /dev/ttyACM0
ISDN = 0
Phone = *99***1#
Username = gp
Password = gp

This being an example on a site I found that uses a USb modem in 8.04.



But I also did this
lsusb got me this.


ubuntu@ubuntu:~$ sudo lsusb
Bus 004 Device 004: ID 13fe:1f00 Kingston Technology Company Inc. 
Bus 004 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 004: ID 0572:1321 Conexant Systems (Rockwell), Inc. 
Bus 001 Device 001: ID 0000:0000



Do not quiet sure what it means exactly, but the conexant Systems should be my USB modem, but I am not quiet sure what the BUS/Device stuff means, I am going to do more research, just thought I would update.

---

### Post by ericeclifford on 2009-10-19
Any more advice guys, thanks again for the support thus far.

---

### Post by anewguy on 2009-10-19
I would suspect that before you can actually use that USB modem, you are going to have to install a driver for it first.  If you have a Windows driver or disk for it, let us know.  In the mean time, I'll go hunting for some sort of driver.

Dave :)

---

### Post by anewguy on 2009-10-19
A quick google search on the USB vendor/product id (the 0572:1321 on the lsusb line that shows your modem) turned up this page:

[http://www.linuxant.com/drivers/dgc/index.php]("http://www.linuxant.com/drivers/dgc/index.php")

If you have a way (direct connect) to be on the net with the computer while looking at this site, be sure your USB modem is connected and proceed to the download.  It has an option there to download an automatic installer.  Be sure to read the installation instructions, and keep in mind that Ubuntu is debian based, so follow the instructions for that.

If you have any problems/questions or anything at all, just post back.

You'll need the driver before things like wvdial can actually see the modem.

Dave :)

---

### Post by ericeclifford on 2009-10-20
But in 9.04 it automatically sees it, does that mean 9.04 has the driver installed by default?

---

### Post by ericeclifford on 2009-10-20
This worked, thank you, it finally sees my modem $$ :0

---

### Post by anewguy on 2009-10-20
If 9.04 automatically sees your modem, then yes, it has the driver or at least a driver, with it.

Glad you got things working in 8.04.

A small side note to others who may have been following this:

A USB modem is normally going to be a "Winmodem", meaning that it is not a stand alone modem so a lot of the processing has to happen in software (the driver).  In this instance, the driver had to be installed before the modem could be used.  Yes, lsusb (list the known USB devices) showed the device - this simply means it recognized the hardware, *NOT* that the hardware will work just out of the box.

A lot of non-serial (serial modems are stand alone modems that plug into your computer via a serial cable) are "Winmodems" and require software to make them work.  There are lists on the net of modems that are known to work with Ubuntu and Linux in general and if a driver is needed.  This topic has been covered many times before, but just to reiterate - check the online lists for supported modems (or buy a completely stand alone hardware modem) before buying a modem for use in Ubuntu, and in Linux in general.

Dave :)

---

