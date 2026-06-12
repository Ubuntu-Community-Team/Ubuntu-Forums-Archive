---
title: "wlan0 not in list.. why?"
date: 2007-03-22
forum: Networking &amp; Wireless
---

### Post by Bogus83 on 2007-03-22
Ok, I've been on a quest to get my WG111T Netgear USB adapter to work.

For the specific device I needed to use ndiswrapper 1.23 or higher.  So, I completely removed the existing version (1.22) and compiled and installed 1.38.  That worked.  I then installed the drivers for the wireless adapter.  That also appears to have worked.

The adapter shows up in "sudo lsusb -v":

> Bus 003 Device 004: ID 1385:4251  
Device Descriptor:
  bLength                18
  bDescriptorType         1
  bcdUSB               2.00
  bDeviceClass          255 Vendor Specific Class
  bDeviceSubClass         0 
  bDeviceProtocol         0 
  bMaxPacketSize0        64
  idVendor           0x1385 
  idProduct          0x4251 
  bcdDevice            0.01
  iManufacturer           1 Atheros Communications Inc
  iProduct                2 WG111T
  iSerial                 3 1.0
  bNumConfigurations      1
  Configuration Descriptor:
    bLength                 9
    bDescriptorType         2
    wTotalLength           46
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
      bNumEndpoints           4
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
        bEndpointAddress     0x02  EP 2 OUT
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
  bDeviceClass          255 Vendor Specific Class
  bDeviceSubClass         0 
  bDeviceProtocol         0 
  bMaxPacketSize0        64
  bNumConfigurations      1
Device Status:     0x0000
  (Bus Powered)



ndiswrapper -v displays this:

utils version: 1.9
driver version:        1.38
vermagic:       2.6.17-11-generic SMP mod_unload 586 REGPARM gcc-4.1

and ndiswrapper -l:

athfmwdl : driver installed
        device (1385:4251) present
netwg11t : driver install

However, sudo dhclient wlan0 shows:

There is already a pid file /var/run/dhclient.pid with pid 134993416
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

SIOCSIFADDR: No such device
wlan0: ERROR while getting interface flags: No such device
wlan0: ERROR while getting interface flags: No such device
Bind socket to interface: No such device

Also, iwconfig

lo        no wireless extensions.

eth0      no wireless extensions.

eth1      no wireless extensions.

sit0      no wireless extensions.



I'm at a loss for what to do next.  I've blacklisted ath_pci and ath_hal, I've added ndiswrapper to modules, but the system doesn't even acknowledge that a wlan0 exists.  I haven't even tried tackling WPA yet, I'd like to see some indication that the device is working first.  Please, can anyone help me?

---

### Post by spd106 on 2007-03-22
To see if ndiswrapper is being loaded, check ```
lsmod
``` 

You could also try ```
sudo lshw -class network
```

---

### Post by magnetictechy on 2007-03-23
What version of linux are you using ubuntu, fedora, redhat,etc?  The reason is because each distro has a different way of configuring stuff.  

Under Ubuntu Edgy, I got my wifi card working under rausb0 instead of wlan0!  If you upgraded to Edgy via dapper, then you probably need to erase what you blacklisted in dapper.  In /etc/modprobe.d/blacklist  For instance if you had to blacklist say rt2570, then you would just gedit /etc/modprobe.d/blacklist and put a # next to blacklist rt2570, then reboot and you should see the wireless adapter in network manager!!

   Since you already have ndiswrapper installed and it is accepting the hardware, then you should be able to edit your essid via network manager and get on the internet!!

That's what I did and it is what I am using right now!!!

---

### Post by Bogus83 on 2007-03-23
I'm using Ubuntu Edgy.  Currently, I have a bigger problem- I can't get Ubuntu started!  Booting up my pc gets me to Grub error 18.  I've booted to the XP cd, and FIXMBR'd, which got me back into Windows.  I've reformatted the drive Ubuntu was on and reinstalled completely, but I get Error 18 every time.

My system has two Hard Drives- the primary is a 160GB, partitioned into two pieces.  The slave is a 30GB drive.  Ubuntu goes on the slave, and I've gone so far as to completely delete all partitions on it, reformat it in NTFS, and then format it in Ext through the Ubuntu installation process.  Does anyone know why I get that error every time I fix the boot record and reinstall?

---

