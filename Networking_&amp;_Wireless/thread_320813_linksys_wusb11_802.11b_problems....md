---
title: "linksys wusb11 802.11b problems..."
date: 2006-12-17
forum: Networking &amp; Wireless
---

### Post by tedk89 on 2006-12-17
I am running the WUSB 802.11b wireless adapter from linux. I just finished a fresh install of the latest version of Ubuntu (6.10). I am not exactly sure of the problem so I will tell you what I have now....The device shows up in the device manager, and I have the network settings setup to my essid and my wep entered and such... but to get from there to a working network connection I cannot get... Forgive me I am relatively new to linux only a few days...
Ted

Edit 
please provide steps as specific as possible... Ie step one do this step two do that....

---

### Post by n00b@linux on 2006-12-18
Can you please copy and paste the output from your **lsusb** and **iwconfig** commands:
 
***Step 1: Open a Terminal to get to the command line***
Navigate with your mouse to:```
Applications > Accessories > Terminal
```and click on it to open a terminal.
 
***Step 2: Run the 'lsusb' command as root***
At the terminal prompt, type:```
sudo lsusb -v
```and press <return>. Enter your password when prompted. Then copy and paste the output of the lsusb command to this thread. FYI 'lsusb' is a simple command that lists the USB buses and any USB devices attached to them. The '-v' option means make the output of the command verbose, thereby giving you lots of information. To use -v properly, you have to run the command with root privileges, hence the prefix 'sudo'. If you run it without 'sudo' you will get a lot of 'unable to access' type messages. When using -v it's always a good idea to get into the habit of running as root (ie. with the 'sudo' prefix).
 
***Setp 3: Run the 'iwconfig' command***
At the terminal prompt, type:```
iwconfig
```and press <return>. This will list your wireless and non-wireless interfaces. You should see output for 'lo' and 'eth0' saying they're not a wireless interface. Hopefully, you'll also see output for 'wlan0' - which will be your USB wireless adapter - and this will have a whole heap of output (about 6-10 lines). If you don't see this don't worry. It probably means the kernel module for the chipset inside your USB wireless adapter has not been loaded. If this is the case, then we can fix it. However, before we go into that, please copy and paste the output of the iwconfig command to this thread.

---

### Post by tedk89 on 2006-12-18
ok I got alot of results here you go 

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
  iManufacturer           3 Linux 2.6.17-10-generic ehci_hcd
  iProduct                2 EHCI Host Controller
  iSerial                 1 0000:00:09.2
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
        bInterval              12
Hub Descriptor:
  bLength               9
  bDescriptorType      41
  nNbrPorts             4
  wHubCharacteristic 0x000a
    No power switching (usb 1.0)
    Per-port overcurrent protection
    TT think time 8 FS bits
  bPwrOn2PwrGood       10 * 2 milli seconds
  bHubContrCurrent      0 milli Ampere
  DeviceRemovable    0x00
  PortPwrCtrlMask    0xff
 Hub Port Status:
   Port 1: 0000.0100 power
   Port 2: 0000.0100 power
   Port 3: 0000.0100 power
   Port 4: 0000.0100 power
Device Status:     0x0003
  Self Powered
  Remote Wakeup Enabled

Bus 001 Device 002: ID 077b:2219 Linksys WUSB11 V2.6 802.11b Adapter
Device Descriptor:
  bLength                18
  bDescriptorType         1
  bcdUSB               1.10
  bDeviceClass          254 Application Specific Interface
  bDeviceSubClass         1 Device Firmware Update
  bDeviceProtocol         0 
  bMaxPacketSize0         8
  idVendor           0x077b Linksys
  idProduct          0x2219 WUSB11 V2.6 802.11b Adapter
  bcdDevice            1.00
  iManufacturer           0 
  iProduct                0 
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
    MaxPower              500mA
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        0
      bAlternateSetting       0
      bNumEndpoints           2
      bInterfaceClass       255 Vendor Specific Class
      bInterfaceSubClass      0 
      bInterfaceProtocol    255 
      iInterface              0 
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x85  EP 5 IN
        bmAttributes            2
          Transfer Type            Bulk
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0040  1x 64 bytes
        bInterval               0
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x02  EP 2 OUT
        bmAttributes            2
          Transfer Type            Bulk
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0040  1x 64 bytes
        bInterval               0
Device Status:     0x0000
  (Bus Powered)

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
  iManufacturer           3 Linux 2.6.17-10-generic uhci_hcd
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
  DeviceRemovable    0x00
  PortPwrCtrlMask    0xff
 Hub Port Status:
   Port 1: 0000.0100 power
   Port 2: 0000.0103 power enable connect
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
  bDeviceProtocol         0 
  bMaxPacketSize0        64
  idVendor           0x0000 
  idProduct          0x0000 
  bcdDevice            2.06
  iManufacturer           3 Linux 2.6.17-10-generic uhci_hcd
  iProduct                2 UHCI Host Controller
  iSerial                 1 0000:00:09.1
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
  bDeviceProtocol         0 
  bMaxPacketSize0        64
  idVendor           0x0000 
  idProduct          0x0000 
  bcdDevice            2.06
  iManufacturer           3 Linux 2.6.17-10-generic uhci_hcd
  iProduct                2 UHCI Host Controller
  iSerial                 1 0000:00:09.0
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
  DeviceRemovable    0x00
  PortPwrCtrlMask    0xff
 Hub Port Status:
   Port 1: 0000.0100 power
   Port 2: 0000.0100 power
Device Status:     0x0003
  Self Powered
  Remote Wakeup Enabled



wlan0     IEEE 802.11-DS  ESSID:"Kraus"  Nickname:"okuwlan"
          Mode:Managed  Frequency:2.462 GHz  Access Point: 00:0F:66:2B:6A:47   
          Bit Rate:11 Mb/s   Tx-Power=15 dBm   
          Retry limit:8   RTS thr=1536 B   Fragment thr=1536 B   
          Power Management:off
          Link Quality=0/0  Signal level=37/255  Noise level=0/0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

Both commaands were sucessful as you see and returned alot of information :) thank you for your information about the commands it helps me to understand them so I can use them in the future on my own :) so... what is the next thing you would like me to do...

---

### Post by n00b@linux on 2006-12-19
OK.  Your USB wireless adapter has been recognised - look at the output from lsusb where it starts Bus 001 Device 002.  Furthermore, your USB wireless adapter has been associated with an access point - look at the output from the iwconfig where is has 'Access Point: 00:0F:66:2B:6A:47'
 
This suggests to me everything is working.  Is 00:0F:66:2B:6A:47 not your access point/"Kraus" not your network?

---

### Post by vintendo on 2006-12-19
i cannot get mine to work :( here is what i got when i did ```
sudo lsusb -v
```
Bus 002 Device 001: ID 0000:0000  
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
  iManufacturer           3 Linux 2.6.17-10-generic uhci_hcd
  iProduct                2 UHCI Host Controller
  iSerial                 1 0000:00:04.3
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
  DeviceRemovable    0x00
  PortPwrCtrlMask    0xff
 Hub Port Status:
   Port 1: 0000.0100 power
   Port 2: 0000.0100 power
Device Status:     0x0003
  Self Powered
  Remote Wakeup Enabled

Bus 001 Device 004: ID 0443:002e Gateway, Inc. 
Device Descriptor:
  bLength                18
  bDescriptorType         1
  bcdUSB               1.10
  bDeviceClass            0 (Defined at Interface level)
  bDeviceSubClass         0 
  bDeviceProtocol         0 
  bMaxPacketSize0         8
  idVendor           0x0443 Gateway, Inc.
  idProduct          0x002e 
  bcdDevice            1.00
  iManufacturer           1 NMB
  iProduct                2 Gateway USB Hub Keyboard
  iSerial                 0 
  bNumConfigurations      1
  Configuration Descriptor:
    bLength                 9
    bDescriptorType         2
    wTotalLength           59
    bNumInterfaces          2
    bConfigurationValue     1
    iConfiguration          2 Gateway USB Hub Keyboard
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
      bInterfaceClass         3 Human Interface Devices
      bInterfaceSubClass      1 Boot Interface Subclass
      bInterfaceProtocol      1 Keyboard
      iInterface              2 Gateway USB Hub Keyboard
        HID Device Descriptor:
          bLength                 9
          bDescriptorType        33
          bcdHID               1.10
          bCountryCode            0 Not supported
          bNumDescriptors         1
          bDescriptorType        34 Report
          wDescriptorLength      65
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
        wMaxPacketSize     0x0008  1x 8 bytes
        bInterval              24
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        1
      bAlternateSetting       0
      bNumEndpoints           1
      bInterfaceClass         3 Human Interface Devices
      bInterfaceSubClass      0 No Subclass
      bInterfaceProtocol      0 None
      iInterface              2 Gateway USB Hub Keyboard
        HID Device Descriptor:
          bLength                 9
          bDescriptorType        33
          bcdHID               1.10
          bCountryCode            0 Not supported
          bNumDescriptors         1
          bDescriptorType        34 Report
          wDescriptorLength     211
         Report Descriptors: 
           ** UNAVAILABLE **
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x82  EP 2 IN
        bmAttributes            3
          Transfer Type            Interrupt
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0004  1x 4 bytes
        bInterval              48
Device Status:     0x0000
  (Bus Powered)

Bus 001 Device 003: ID 0443:002f Gateway, Inc. 
Device Descriptor:
  bLength                18
  bDescriptorType         1
  bcdUSB               1.10
  bDeviceClass            9 Hub
  bDeviceSubClass         0 Unused
  bDeviceProtocol         0 
  bMaxPacketSize0         8
  idVendor           0x0443 Gateway, Inc.
  idProduct          0x002f 
  bcdDevice            1.00
  iManufacturer           1 NMB
  iProduct                2 Gateway USB Hub Keyboard
  iSerial                 0 
  bNumConfigurations      1
  Configuration Descriptor:
    bLength                 9
    bDescriptorType         2
    wTotalLength           25
    bNumInterfaces          1
    bConfigurationValue     1
    iConfiguration          2 Gateway USB Hub Keyboard
    bmAttributes         0xa0
      (Bus Powered)
      Remote Wakeup
    MaxPower               90mA
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        0
      bAlternateSetting       0
      bNumEndpoints           1
      bInterfaceClass         9 Hub
      bInterfaceSubClass      0 Unused
      bInterfaceProtocol      0 
      iInterface              2 Gateway USB Hub Keyboard
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x81  EP 1 IN
        bmAttributes            3
          Transfer Type            Interrupt
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0001  1x 1 bytes
        bInterval             255
Hub Descriptor:
  bLength               9
  bDescriptorType      41
  nNbrPorts             3
  wHubCharacteristic 0x000d
    Per-port power switching
    Compound device
    Per-port overcurrent protection
  bPwrOn2PwrGood       50 * 2 milli seconds
  bHubContrCurrent     90 milli Ampere
  DeviceRemovable    0x02
  PortPwrCtrlMask    0xff
 Hub Port Status:
   Port 1: 0000.0103 power enable connect
   Port 2: 0000.0100 power
   Port 3: 0000.0100 power
Device Status:     0x0000
  (Bus Powered)

Bus 001 Device 002: ID 13b1:000b Linksys WUSB11 v4.0 802.11b Adapter
Device Descriptor:
  bLength                18
  bDescriptorType         1
  bcdUSB               1.10
  bDeviceClass          255 Vendor Specific Class
  bDeviceSubClass       255 Vendor Specific Subclass
  bDeviceProtocol       255 Vendor Specific Protocol
  bMaxPacketSize0         8
  idVendor           0x13b1 Linksys
  idProduct          0x000b WUSB11 v4.0 802.11b Adapter
  bcdDevice            0.01
  iManufacturer           1 ALinx Corp
  iProduct                2 USB Device
  iSerial                 0 
  bNumConfigurations      1
  Configuration Descriptor:
    bLength                 9
    bDescriptorType         2
    wTotalLength           39
    bNumInterfaces          1
    bConfigurationValue     1
    iConfiguration          0 
    bmAttributes         0x80
      (Bus Powered)
    MaxPower              200mA
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        0
      bAlternateSetting       0
      bNumEndpoints           3
      bInterfaceClass       255 Vendor Specific Class
      bInterfaceSubClass    255 Vendor Specific Subclass
      bInterfaceProtocol    255 Vendor Specific Protocol
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
        bInterval               0
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x06  EP 6 OUT
        bmAttributes            2
          Transfer Type            Bulk
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0040  1x 64 bytes
        bInterval               0
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x81  EP 1 IN
        bmAttributes            3
          Transfer Type            Interrupt
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0010  1x 16 bytes
        bInterval               1
Device Status:     0x0000
  (Bus Powered)

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
  iManufacturer           3 Linux 2.6.17-10-generic uhci_hcd
  iProduct                2 UHCI Host Controller
  iSerial                 1 0000:00:04.2
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
  DeviceRemovable    0x00
  PortPwrCtrlMask    0xff
 Hub Port Status:
   Port 1: 0000.0103 power enable connect
   Port 2: 0000.0103 power enable connect
Device Status:     0x0003
  Self Powered
  Remote Wakeup Enabled

 And for ```
iwconfig
```
lo        no wireless extensions.

eth0      no wireless extensions.

vmnet8    no wireless extensions.

vmnet1    no wireless extensions.

sit0      no wireless extensions.
:confused:

---

### Post by tedk89 on 2006-12-19
> **n00b@linux said:**
> OK.  Your USB wireless adapter has been recognised - look at the output from lsusb where it starts Bus 001 Device 002.  Furthermore, your USB wireless adapter has been associated with an access point - look at the output from the iwconfig where is has 'Access Point: 00:0F:66:2B:6A:47'
 
This suggests to me everything is working.  Is 00:0F:66:2B:6A:47 not your access point/"Kraus" not your network?

ok so now that I can see my adapter is working I see what is causing the problem  which  is why i cannot get on the interent so ... I need to change a few settings here... the first is I need to change my RTS threshhold and the Fragmentation Threshhold... I also need to chnge the security mode from open to WEP 10 digit hex key...than I think I will be on the internet :) so could you please expain how I can change those settings... thanks :)


Ted

---

### Post by n00b@linux on 2006-12-20
@tedk89:
You use the 'iwconfig' command to configure a wireless network interface. To change RTS Threshold you use the 'rts' parameter. To change Fragmentation Threshold you use the 'frag' parameter. To set the WEP key you use the 'key' parameter. For example, to:
 
a) change RTS Threshold to 1000;
b) change Fragmentation Threshold to 1200; and
c) set the WEP key to 'sample_wep_key'
 
You would issue the following command:```
sudo iwconfig wlan0 rts 1000 frag 1200 key s:sample_wep_key
```Note the 's:' prefix to the WEP key. You only need to use this prefix if you're specifying it as an ASCII string. If you specify it in hex digits you don't need the 's:' prefix. More information can be gained from the man page:```
man iwconfig
```Note: press 'q' to get out of/close down the man page once you've finished reading it.
 
Also consider physically moving your connection closer to your access point as the Signal level is low (37/255).
 
@vintendo
Your Linksys WUSB11 is version 4.0.  tedk89's is version 2.6.  It appears from comparing the 'lsusb -v' outputs that they have totally different chipsets.  This means totally different device drivers (FYI, device driver = kernel module).  Please start a new thread (specifying 'Linksys WUSB11 v4.0')and I'll answer it there ;)

---

### Post by tedk89 on 2006-12-21
thank you I am still working on it...unforchanatly I cant move any closer I am only one room away.. its weird my computer is duel boot xp pro/ ubuntu and in xp pro the signal is amazing.. I was wondering if you had any ideas why there would be a difference? 
Thanks for all your help !!! :)
Ted

Edit allso how do you get a list of available essid that you can connect to and how do you make it connect in terminal? I heard some peoples settings from the administration-network were not really applied or some so how do you get the servers and have it connect using terminal? 

Thanks again
Ted

---

### Post by tedk89 on 2006-12-21
actually for the most part disreguard the last post... my playing with some of my routers settings I have narrowed the problem down to the WEP encryption not exactly sure but when WEP is on I cant get packets recieved with the codes entered on the acecssing computer when I turn wep off on the router and off on the machine everything works fine... not sure what exactly the problem is just I know it has some thing to do with the WEP

---

### Post by tedk89 on 2006-12-21
ok on a third note I have no idea what I changed but now I have WEP encryption working well as well as a good connection... I will post back the details when I have more things figured out... Thanks again
Ted

---

### Post by n00b@linux on 2006-12-22
Hey!  Glad to hear you've got it working!   I hope you've now understood a few wireless commands so that next time you have a wireless problem (which, hopefully, you won't) you can at least do some basic troubleshooting.

As to scanning for other available access points (ie. to see a list of available ESSIDs), the 'iwlist' command is the one you want.  Check out the man page:```
man iwlist
```For example, if the name of your wireless interface is 'wlan0':```
iwlist wlan0 scan
```Or, if your interface is called 'eth1':```
iwlist eth1 scan
```By now you'll hopefully appreciate that these commands won't work until your wireless network interface card has been (a) recognised by the kernel (lspci) AND (b) the device driver (ie. 'kernel module') has been loaded (lsmod).

Once you've got the list of available ESSIDs you just use the 'iwconfig' command (prefixed with 'sudo' of course) to configure your wireless interface to connect to that ESSID.  Of course you need to read the output of 'iwlist' in detail to see which access points use encryption because you'll need to know the type of encryption and key in order to use those.  But if any of them has NO encryption you've got free wifi, LOL.  It's illegal, of course, and I don't condone doing it especially if the owner of the access point owns multiple machines and has enabled file sharing between them.  Leeching someone's bandwidth is one thing, but playing around with their file system is another thing completely.  That leads me on to another topic: encryption.

If you want encryption, use WPA1 as a minimum.  WEP is not secure.  WEP will protect you against anyone who doesn't understand wireless (90% of users) but anyone who knows the basics of wireless encryption can find out a WEP key relatively easily, discover hidden ESSIDs without a problem and spoof MAC addresses with ease.  There are linux tools in the Ubuntu repos you can download now that allow you to do it.  Of course no wireless system is completely safe - it's only as safe as its weakest link.  That's why you still need a strong password with WPA1.  I use a 63 character password made up of completely random characters.  I got it from the Security Now web site over at [www.grc.com](www.grc.com).  It's an interesting site and you can download some podcasts about wireless security to listen to.

---

### Post by tedk89 on 2006-12-22
hmm ok interesting again thank you for your good advice off to wireless security I go :)

---

### Post by rmills on 2007-01-07
Any idea what you did to get it working?  I've got it installed and it's being recognized:
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11-DS  ESSID:"dlink"  Nickname:"okuwlan"
          Mode:Managed  Frequency:2.457 GHz  Access Point: Not-Associated
          Bit Rate:11 Mb/s   Tx-Power=15 dBm
          Retry limit:8   RTS thr=1536 B   Fragment thr=1536 B
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

sit0      no wireless extensions.

ham0      no wireless extensions.


but when i kill my eth0 connection and ifup my wlan0:
ifup: interface wlan0 already configured


Granted I used the gui configuration tool in System > Administration > Networking, but it seems like I can't get an IP address from my router no matter what I try.  My ESSID and key are correct, I'm sure because I'm using it on my laptop now.  I'm using a Linksys WUSB11 v2.6 just like you.   Any suggestions?

---

