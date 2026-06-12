---
title: "[SOLVED] BT Voyager 1055 USB wireless adapter"
date: 2008-05-19
forum: Networking &amp; Wireless
---

### Post by RegUB on 2008-05-19
I have a BT Voyager 1055 wireless adapter which works fine under Windows, but I can't get it working under Ubuntu (7.10). Following the advice in previous threads, I have -
- Created /etc/udev/rules.d/99-custom.rules
- Copied the Windows .sys files to /etc/ndiswrapper/bcmrndis
- Installed Windows drivers using ndiswrapper -i, depmode -a, modprobe ndiswrapper
 
However no joy, it doesn't even show a wireless connection as being present.

Below in no particular order is the output of some relevant commands - can anyone suggest anything that might be wrong here?

> ndiswrapper -l
bcmrndis : driver installed
        device (1690:0715) present

> cat   /etc/udev/rules.d/99-custom.rules
#START**
BUS=="usb", SYSFS{idProduct}=="0715", SYSFS{idVendor}=="1690", RUN+="/bin/sh -c 'echo 1 > /sys/$devpath/device/bConfigurationValue'"
#END**

> iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

> ls -l /etc/ndiswrapper/bcmrndis
total 84
-rw-r--r-- 1 root root   752 2008-04-29 23:51 1690:0715.F.conf
-rw-r--r-- 1 root root 31185 2008-04-29 23:51 bcmrndis.inf
-rw-r--r-- 1 root root 30080 2008-04-29 23:53 rndismp.sys
-rw-r--r-- 1 root root 12672 2008-04-29 23:53 usb8023.sys

> ndiswrapper -v
utils version: 1.9
driver filename:       /lib/modules/2.6.22-14-generic/ubuntu/misc/ndiswrapper/ndiswrapper.ko
version:        1.45
vermagic:       2.6.22-14-generic SMP mod_unload 586 

> iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

> sudo ifup wlan0
Ignoring unknown interface wlan0=wlan0.

> ifconfig
eth0      Link encap:Ethernet  HWaddr 00:17:31:EB:4F:4F  
          inet addr:192.168.1.64  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::217:31ff:feeb:4f4f/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1855 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1292 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1777429 (1.6 MB)  TX bytes:142068 (138.7 KB)
          Interrupt:20 Base address:0xd000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

> cat /etc/network/interfaces
auto lo
iface lo inet loopback

> lsusb
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  
Bus 004 Device 001: ID 0000:0000  
Bus 005 Device 002: ID 1690:0715 Askey Computer Corp. [hex] 
Bus 005 Device 001: ID 0000:0000  
Bus 005 Device 004: ID 0bda:0111 Realtek Semiconductor Corp. 
Bus 001 Device 004: ID 0461:0340 Primax Electronics, Ltd Colorado 9600 Scanner
Bus 001 Device 001: ID 0000:0000

> dmesg|grep -i usb
[   27.125812] usbcore: registered new interface driver usbfs
[   27.125865] usbcore: registered new interface driver hub
[   27.125906] usbcore: registered new device driver usb
[   27.127403] USB Universal Host Controller Interface driver v3.0
[   29.734894] uhci_hcd 0000:00:10.0: new USB bus registered, assigned bus number 1
[   29.735123] usb usb1: configuration #1 chosen from 1 choice
[   29.735179] hub 1-0:1.0: USB hub found
[   29.836104] uhci_hcd 0000:00:10.1: new USB bus registered, assigned bus number 2
[   29.836298] usb usb2: configuration #1 chosen from 1 choice
[   29.836340] hub 2-0:1.0: USB hub found
[   29.939864] uhci_hcd 0000:00:10.2: new USB bus registered, assigned bus number 3
[   29.940058] usb usb3: configuration #1 chosen from 1 choice
[   29.940101] hub 3-0:1.0: USB hub found
[   30.043714] uhci_hcd 0000:00:10.3: new USB bus registered, assigned bus number 4
[   30.043909] usb usb4: configuration #1 chosen from 1 choice
[   30.043952] hub 4-0:1.0: USB hub found
[   30.075351] usb 1-1: new full speed USB device using uhci_hcd and address 2
[   30.243968] usb 1-1: configuration #1 chosen from 1 choice
[   30.486463] usb 1-2: new full speed USB device using uhci_hcd and address 3
[   30.651073] usb 1-2: configuration #1 chosen from 1 choice
[   31.408492] usb 4-1: new full speed USB device using uhci_hcd and address 2
[   31.589496] usb 4-1: configuration #1 chosen from 1 choice
[   31.771882] ehci_hcd 0000:00:10.4: new USB bus registered, assigned bus number 5
[   31.771952] ehci_hcd 0000:00:10.4: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[   31.772104] usb usb5: configuration #1 chosen from 1 choice
[   31.772138] hub 5-0:1.0: USB hub found
[   31.855544] usb 1-1: USB disconnect, address 2
[   31.983292] usb 1-2: USB disconnect, address 3
[   32.350636] usb 5-1: new high speed USB device using ehci_hcd and address 2
[   32.484953] usb 5-1: configuration #1 chosen from 1 choice
[   32.961117] usb 5-7: new high speed USB device using ehci_hcd and address 4
[   33.109655] usb 5-7: configuration #1 chosen from 1 choice
[   33.110906] usb 4-1: USB disconnect, address 2
[   33.476014] usb 1-2: new full speed USB device using uhci_hcd and address 4
[   33.640448] usb 1-2: configuration #1 chosen from 1 choice
[   38.245522] usbcore: registered new interface driver libusual
[   38.262653] Initializing USB Mass Storage driver...
[   38.262797] scsi6 : SCSI emulation for USB Mass Storage devices
[   38.262924] usbcore: registered new interface driver usb-storage
[   38.262929] USB Mass Storage support registered.
[   38.263078] usb-storage: device found at 4
[   38.263081] usb-storage: waiting for device to settle before scanning
[   38.305696] usbcore: registered new interface driver cdc_ether
[   38.318102] usb 5-1: bad CDC descriptors
[   38.318133] usbcore: registered new interface driver rndis_host
[   43.251130] usb-storage: device scan complete

> lsusb -v -d 1690:0715

Bus 005 Device 002: ID 1690:0715 Askey Computer Corp. [hex] 
Device Descriptor:
  bLength                18
  bDescriptorType         1
  bcdUSB               2.00
  bDeviceClass            2 Communications
  bDeviceSubClass         0 
  bDeviceProtocol         0 
  bMaxPacketSize0        64
  idVendor           0x1690 Askey Computer Corp. [hex]
  idProduct          0x0715 
  bcdDevice            0.06
  iManufacturer           1 
  iProduct                2 
  iSerial                 3 
  bNumConfigurations      1
  Configuration Descriptor:
    bLength                 9
    bDescriptorType         2
    wTotalLength           48
    bNumInterfaces          2
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
      bNumEndpoints           1
      bInterfaceClass         2 Communications
      bInterfaceSubClass      2 Abstract (modem)
      bInterfaceProtocol    255 Vendor Specific (MSFT RNDIS?)
      iInterface              0 
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x81  EP 1 IN
        bmAttributes            3
          Transfer Type            Interrupt
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0010  1x 16 bytes
        bInterval               4
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
        wMaxPacketSize     0x0200  1x 512 bytes
        bInterval               0
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x03  EP 3 OUT
        bmAttributes            2
          Transfer Type            Bulk
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0200  1x 512 bytes
        bInterval               1
can't get device qualifier: Operation not permitted
can't get debug descriptor: Operation not permitted
cannot read device status, Operation not permitted (1)

---

### Post by mapes12 on 2008-05-19
I'm assuming the USB adapter is plugged into your laptop/desktop?

What wifi broadband router do you have? Is it a BTHomehub?

---

### Post by RegUB on 2008-05-19
Yes to both questions

---

### Post by mapes12 on 2008-05-19
I can only share with you how I solved my problem. Others may have an alternative solution.

I too have a BTHomehub router. My desktop has an ethernet cable connection and works fine (Ubuntu OS). My laptop caused the problem. The laptop originally had a Linksys PCMCIA wifi card that did not have the support of native Linux drivers. Therefore, I configured the Linksys XP driver via ndiswrappper. Intialy, everything worked OK but after a few days the configuration broke down. I was spending more time fixing it than doing anything else. It was driving me nuts. Since then I have discovered that a ndiswrapper solution has flaws.

So I decided to get me a linix natively supported PCMCIA card from these guys:

[http://www.linuxemporium.co.uk/products/wireless/#pidR26799](http://www.linuxemporium.co.uk/products/wireless/#pidR26799)

OK, it cost me a tenner for a new piece of kit but it works straight out of the box, I didn't have to configure a thing, and it's been running flawlessly for weeks now.

Hope this may help.

Best wishes.

Mark

EDIT: Forgot to mention that from what I have read on the forums BT do not support open source drivers,

---

### Post by RegUB on 2008-05-20
Thanks, that may be useful as a last resort, but I really would like to get this USB adapter working if possible. It obviously can be done, see the following thread - [http://ubuntuforums.org/showthread.php?t=367448](http://ubuntuforums.org/showthread.php?t=367448) - post #6 more or less describes what I've tried. But I think there is something more basic wrong - for instance, are the 'Bad CDC descriptors' message in the dmesg output, or the 'can't get device qualifier: Operation not permitted' in the lsusb output, significant?

---

### Post by geezerone on 2008-07-27
Take a look at my post [_here_]("http://ubuntuforums.org/showthread.php?p=5467407#post5467407").

HTH :)

---

