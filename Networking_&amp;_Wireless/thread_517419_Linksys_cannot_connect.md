---
title: "Linksys cannot connect"
date: 2007-08-04
forum: Networking &amp; Wireless
---

### Post by Khan-din on 2007-08-04
I am totally clueless about this linksys on Ubuntu Feisty.  I have installed Feisty on two different 4 year old computers that could both connect.  The computer I am trying now is an x86 Dell Dimension 2400 with a USB connected linksys card.  I put autorun.inf, rt73.inf, and rt73.sys on the desktop, but ubuntu cannot open it because "No application suitable for automatic installation is available for handling this kind of file."  I think it's a Linux-Windows incompatibility issue.  I have thought of using WINE, but this can't connect to the internet, so that is not an option.
Other people have had problems with linksys on Ubuntu, but I didn't see anything there that relates to this.
Help?

---

### Post by MrFSL on 2007-08-04
what is the output of:

```
sudo lsusb
```

---

### Post by Khan-din on 2007-08-04
```

Bus 004 Device 005:  ID 13b1:0020 Linksys
Bus 004 Device 001:  ID 0000:0000
Bus 003 Device 001:  ID 0000:0000
Bus 002 Device 001:  ID 0000:0000
Bus 001 Device 003:  ID 046d:c00e Logitech, Inc. M-BJ69 Optical Wheel Mouse
Bus 001 Device 001:  ID 0000:0000

```

---

### Post by MrFSL on 2007-08-04
Well that certainly is not much helpful information. How about:
```
sudo lsusb -v
```

---

### Post by Khan-din on 2007-08-04
```

Bus 004 Device 009: ID 04b4:6830 Cypress Semiconductor Corp. USB-2.0 IDE Adapter 
Device Descriptor: 
  bLength                18 
  bDescriptorType         1 
  bcdUSB               2.00 
  bDeviceClass            0 (Defined at Interface level) 
  bDeviceSubClass         0 
  bDeviceProtocol         0 
  bMaxPacketSize0        64 
  idVendor           0x04b4 Cypress Semiconductor Corp. 
  idProduct          0x6830 USB-2.0 IDE Adapter 
  bcdDevice            0.01 
  iManufacturer          56 Cypress Semiconductor 
  iProduct               78 USB2.0 Storage Device 
  iSerial               100 DEF10CBDF21F 
  bNumConfigurations      1 
  Configuration Descriptor: 
    bLength                 9 
    bDescriptorType         2 
    wTotalLength           32 
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
      bNumEndpoints           2 
      bInterfaceClass         8 Mass Storage 
      bInterfaceSubClass      6 SCSI 
      bInterfaceProtocol     80 Bulk (Zip) 
      iInterface              0 
      Endpoint Descriptor: 
        bLength                 7 
        bDescriptorType         5 
        bEndpointAddress     0x02  EP 2 OUT 
        bmAttributes            2 
          Transfer Type            Bulk 
          Synch Type               None 
          Usage Type               Data 
        wMaxPacketSize     0x0200  1x 512 bytes 
        bInterval               0 
      Endpoint Descriptor: 
        bLength                 7 
        bDescriptorType         5 
        bEndpointAddress     0x86  EP 6 IN 
        bmAttributes            2 
          Transfer Type            Bulk 
          Synch Type               None 
          Usage Type               Data 
        wMaxPacketSize     0x0200  1x 512 bytes 
        bInterval               0 
Device Qualifier (for other device speed): 
  bLength                10 
  bDescriptorType         6 
  bcdUSB               2.00 
  bDeviceClass            0 (Defined at Interface level) 
  bDeviceSubClass         0 
  bDeviceProtocol         0 
  bMaxPacketSize0        64 
  bNumConfigurations      1 
Device Status:     0x0001 
  Self Powered 

Bus 004 Device 005: ID 13b1:0020 Linksys 
Device Descriptor: 
  bLength                18 
  bDescriptorType         1 
  bcdUSB               2.00 
  bDeviceClass            0 (Defined at Interface level) 
  bDeviceSubClass         0 
  bDeviceProtocol         0 
  bMaxPacketSize0        64 
  idVendor           0x13b1 Linksys 
  idProduct          0x0020 
  bcdDevice            0.01 
  iManufacturer           1 Cisco-Linksys 
  iProduct                2 Compact Wireless-G USB Adapter 
  iSerial                 0 
  bNumConfigurations      1 
  Configuration Descriptor: 
    bLength                 9 
    bDescriptorType         2 
    wTotalLength           32 
    bNumInterfaces          1 
    bConfigurationValue     1 
    iConfiguration          0 
    bmAttributes         0x80 
      (Bus Powered) 
    MaxPower              300mA 
    Interface Descriptor: 
      bLength                 9 
      bDescriptorType         4 
      bInterfaceNumber        0 
      bAlternateSetting       0 
      bNumEndpoints           2 
      bInterfaceClass       255 Vendor Specific Class 
      bInterfaceSubClass    255 Vendor Specific Subclass 
      bInterfaceProtocol    255 Vendor Specific Protocol 
      iInterface              0 
      Endpoint Descriptor: 
        bLength                 7 
        bDescriptorType         5 
        bEndpointAddress     0x81  EP 1 IN 
        bmAttributes            2 
          Transfer Type            Bulk 
          Synch Type               None 
          Usage Type               Data 
        wMaxPacketSize     0x0200  1x 512 bytes 
        bInterval               0 
      Endpoint Descriptor: 
        bLength                 7 
        bDescriptorType         5 
        bEndpointAddress     0x01  EP 1 OUT 
        bmAttributes            2 
          Transfer Type            Bulk 
          Synch Type               None 
          Usage Type               Data 
        wMaxPacketSize     0x0200  1x 512 bytes 
        bInterval               0 
Device Qualifier (for other device speed): 
  bLength                10 
  bDescriptorType         6 
  bcdUSB               2.00 
  bDeviceClass            0 (Defined at Interface level) 
  bDeviceSubClass         0 
  bDeviceProtocol         0 
  bMaxPacketSize0        64 
  bNumConfigurations      1 
Device Status:     0x0000 
  (Bus Powered) 

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
  iManufacturer           3 Linux 2.6.20-15-generic ehci_hcd 
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
      bInterfaceProtocol      0 Full speed hub 
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
  bLength               9 
  bDescriptorType      41 
  nNbrPorts             6 
  wHubCharacteristic 0x000a 
    No power switching (usb 1.0) 
    Per-port overcurrent protection 
    TT think time 8 FS bits 
  bPwrOn2PwrGood       10 * 2 milli seconds 
  bHubContrCurrent      0 milli Ampere 
  DeviceRemovable    0x00 
  PortPwrCtrlMask    0xff 
 Hub Port Status: 
   Port 1: 0000.0000 
   Port 2: 0000.0100 power 
   Port 3: 0000.0100 power 
   Port 4: 0000.0100 power 
   Port 5: 0000.0503 highspeed power enable connect 
   Port 6: 0000.0503 highspeed power enable connect 
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
  bDeviceProtocol         0 Full speed hub 
  bMaxPacketSize0        64 
  idVendor           0x0000 
  idProduct          0x0000 
  bcdDevice            2.06 
  iManufacturer           3 Linux 2.6.20-15-generic uhci_hcd 
  iProduct                2 UHCI Host Controller 
  iSerial                 1 0000:00:1d.2 
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
      bInterfaceProtocol      0 Full speed hub 
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
  bDeviceProtocol         0 Full speed hub 
  bMaxPacketSize0        64 
  idVendor           0x0000 
  idProduct          0x0000 
  bcdDevice            2.06 
  iManufacturer           3 Linux 2.6.20-15-generic uhci_hcd 
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
      bInterfaceProtocol      0 Full speed hub 
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

Bus 001 Device 003: ID 046d:c00e Logitech, Inc. M-BJ69 Optical Wheel Mouse 
Device Descriptor: 
  bLength                18 
  bDescriptorType         1 
  bcdUSB               2.00 
  bDeviceClass            0 (Defined at Interface level) 
  bDeviceSubClass         0 
  bDeviceProtocol         0 
  bMaxPacketSize0         8 
  idVendor           0x046d Logitech, Inc. 
  idProduct          0xc00e M-BJ69 Optical Wheel Mouse 
  bcdDevice           11.10 
  iManufacturer           1 Logitech 
  iProduct                2 USB-PS/2 Optical Mouse 
  iSerial                 0 
  bNumConfigurations      1 
  Configuration Descriptor: 
    bLength                 9 
    bDescriptorType         2 
    wTotalLength           34 
    bNumInterfaces          1 
    bConfigurationValue     1 
    iConfiguration          0 
    bmAttributes         0xa0 
      (Bus Powered) 
      Remote Wakeup 
    MaxPower               98mA 
    Interface Descriptor: 
      bLength                 9 
      bDescriptorType         4 
      bInterfaceNumber        0 
      bAlternateSetting       0 
      bNumEndpoints           1 
      bInterfaceClass         3 Human Interface Devices 
      bInterfaceSubClass      1 Boot Interface Subclass 
      bInterfaceProtocol      2 Mouse 
      iInterface              0 
        HID Device Descriptor: 
          bLength                 9 
          bDescriptorType        33 
          bcdHID               1.10 
          bCountryCode            0 Not supported 
          bNumDescriptors         1 
          bDescriptorType        34 Report 
          wDescriptorLength      52 
         Report Descriptors: 
           ** UNAVAILABLE ** 
      Endpoint Descriptor: 
        bLength                 7 
        bDescriptorType         5 
        bEndpointAddress     0x81  EP 1 IN 
        bmAttributes            3 
          Transfer Type            Interrupt 
          Synch Type               None 
          Usage Type               Data 
        wMaxPacketSize     0x0004  1x 4 bytes 
        bInterval              10 
Device Status:     0x0000 
  (Bus Powered) 

Bus 001 Device 001: ID 0000:0000  
Device Descriptor: 
  bLength                18 
  bDescriptorType         1 
  bcdUSB               1.10 
  bDeviceClass            9 Hub 
  bDeviceSubClass         0 Unused 
  bDeviceProtocol         0 Full speed hub 
  bMaxPacketSize0        64 
  idVendor           0x0000 
  idProduct          0x0000 
  bcdDevice            2.06 
  iManufacturer           3 Linux 2.6.20-15-generic uhci_hcd 
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
      bInterfaceProtocol      0 Full speed hub 
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
   Port 1: 0000.0303 lowspeed power enable connect 
   Port 2: 0000.0100 power 
Device Status:     0x0003 
  Self Powered 
  Remote Wakeup Enabled 
```
I appreciate the help!

---

### Post by MrFSL on 2007-08-04
well it looks like it has been properly identified. How about the output of:

```
sudo iwconfig
```

---

### Post by Khan-din on 2007-08-04
it says:
```
matt@matt-desktop:~$ sudo iwconfig 
Password: 
lo        no wireless extensions. 

eth0      no wireless extensions. 

wmaster0  IEEE 802.11g  Frequency:2.412 GHz  
          RTS thr:off   Fragment thr=2346 B   
          
wlan0     IEEE 802.11g  ESSID:"linksys"  
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated   
          RTS thr:off   Fragment thr=2346 B   
          Encryption key:off 
          Link Quality:0  Signal level:0  Noise level:0 
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0 
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0 

```
I am totally clueless.  My knowledge of BASH is very limited.

---

### Post by noob12 on 2007-08-04
Ubuntu Feisty ships with older rt73usb drivers that don't work right.  

Can you do 

```

sudo lshw -C network

```

to confirm these are the drivers that you have associated?

I'd recommend that you follow the instructions in the following thread to get up and running.  

[http://ubuntuforums.org/showthread.php?t=400236](http://ubuntuforums.org/showthread.php?t=400236)

People on the forum can help you follow them and help you troubleshoot

---

### Post by noob12 on 2007-08-04
We can also try to get you set up with ndiswrapper and the windows driver, but we'll have to pull ndiswrapper 1.47 and build it.  Let me know if you want help with this route.

---

### Post by noob12 on 2007-08-05
This might be of interest to you: [http://ubuntuforums.org/showthread.php?t=516649](http://ubuntuforums.org/showthread.php?t=516649)

---

