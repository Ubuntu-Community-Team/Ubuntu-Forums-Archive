---
title: "The Case of the Missing Wireless Device"
date: 2008-01-14
forum: Networking &amp; Wireless
---

### Post by keylime on 2008-01-14
Here's a fun one for the group.

My faithful Toshiba Satellite A70 device that I've had for over 3 years finally is starting to croak, so for a dirt-cheap price, I got a Toshiba A205-S5804.

I dual-booted the machine and Vista, by sheer luck, is functioning decently. 7.10 tho, not so good - everything is in except the wireless. When I did the lspci command, it has NO listing, zero, zip, nada, absence of any, for the wireless card.

According to Device Manager, it has it as a Realtek 8187B USB 2.0 Adapter. Ndiswrapper doesn't work, because the device doesn't exist in the eyes of Linux.

So, what's the key to unlock this mystery? Thanks in advance!:)

---

### Post by kevdog on 2008-01-14
Those devices work via the usb bus --> southbridge, rather than the pci bus.  So issuing the command
lspci (list pci devices) is not going to work!

If you want to see whats connected via USB use:
lsusb -v

Also you probably need to use cuervo's altered drivers for your device.
[http://www.datanorth.net/~cuervo/rtl8187b/](http://www.datanorth.net/~cuervo/rtl8187b/)

---

### Post by keylime on 2008-01-14
Kevdog,

Thanks for the assist there. How do I get the entire output quoted onto here? It's A LOT of data.

I was able to extract this segment of it:

Bus 007 Device 003: ID 0bda:8197 Realtek Semiconductor Corp. 
Device Descriptor:
  bLength                18
  bDescriptorType         1
  bcdUSB               2.00
  bDeviceClass            0 (Defined at Interface level)
  bDeviceSubClass         0 
  bDeviceProtocol         0 
  bMaxPacketSize0        64
  idVendor           0x0bda Realtek Semiconductor Corp.
  idProduct          0x8197 
  bcdDevice            2.00
  iManufacturer           1 
  iProduct                2 
  iSerial                 3 
  bNumConfigurations      1
  Configuration Descriptor:
    bLength                 9
    bDescriptorType         2
    wTotalLength           81
    bNumInterfaces          1
    bConfigurationValue     1
    iConfiguration          4 
    bmAttributes         0x80
      (Bus Powered)
    MaxPower              500mA
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        0
      bAlternateSetting       0
      bNumEndpoints           9
      bInterfaceClass       255 Vendor Specific Class
      bInterfaceSubClass    255 Vendor Specific Subclass
      bInterfaceProtocol    255 Vendor Specific Protocol
      iInterface              2 
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x83  EP 3 IN
        bmAttributes            2
          Transfer Type            Bulk
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0200  1x 512 bytes
        bInterval               0
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x04  EP 4 OUT
        bmAttributes            2
          Transfer Type            Bulk
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0200  1x 512 bytes
        bInterval               0
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x05  EP 5 OUT
        bmAttributes            2
          Transfer Type            Bulk
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0200  1x 512 bytes
        bInterval               0
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x06  EP 6 OUT
        bmAttributes            2
          Transfer Type            Bulk
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0200  1x 512 bytes
        bInterval               0
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x07  EP 7 OUT
        bmAttributes            2
          Transfer Type            Bulk
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0200  1x 512 bytes
        bInterval               0
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x89  EP 9 IN
        bmAttributes            2
          Transfer Type            Bulk
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0200  1x 512 bytes
        bInterval               0
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x0a  EP 10 OUT
        bmAttributes            2
          Transfer Type            Bulk
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0200  1x 512 bytes
        bInterval               0
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x0b  EP 11 OUT
        bmAttributes            2
          Transfer Type            Bulk
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0200  1x 512 bytes
        bInterval               0
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x0c  EP 12 OUT
        bmAttributes            2
          Transfer Type            Bulk
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0200  1x 512 bytes
        bInterval               0
can't get device qualifier: Operation not permitted
can't get debug descriptor: Operation not permitted
cannot read device status, Operation not permitted (1)

---

### Post by keylime on 2008-01-14
Here's the shorthand of it:

Bus 006 Device 001: ID 0000:0000  
Bus 007 Device 003: ID 0bda:8197 Realtek Semiconductor Corp. 
Bus 007 Device 001: ID 0000:0000  
Bus 005 Device 001: ID 0000:0000  
Bus 004 Device 001: ID 0000:0000  
Bus 003 Device 002: ID 046d:c408 Logitech, Inc. Marble Mouse (4-button)
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000

---

### Post by keylime on 2008-01-14
OK an update.

I did install the drivers, and following the steps, a wlan0 is created - but when rebooting, for some reason it isn't keeping that alias. Additionally, I can't get it to see network resources. Is there a step or two I'm missing to get this to function on every boot up?

---

### Post by keylime on 2008-01-14
OK, I got the wireless working - but I dunno if after the reboot the driver will take.

---

### Post by jperez on 2008-01-18
Is it working?  I just got the EXACT same laptop at BestBuy just 3 days ago and I wanted to know if your wireless device is now working, even after reboot.  Let me know! :D

Jesse~

---

### Post by Big D ND on 2008-01-23
Just bought a Tosh A205-5804 a couple days ago.  Wanted to put Ubuntu on it, but after looking to see if theres been any hassles, I see that the wireless has had this problem.  Anyone gotten it to work??  Thanks for any feedback!!

Darrick

---

### Post by DefaultUser on 2008-02-01
Has anyone been able to reliably use any kind of wireless connectivity on the Toshiba A205-5804 laptop?  If so, would you please tell us the secret?  

I just got one also, but the box is still unopened, so that I can return it if necessary, without a hefty "re-stocking" fee.  

If wireless is not possible, then please let me know that instead, since if so, it has to go back by the end of this week.  

Thanks!

---

### Post by boyevil on 2008-02-13
Well, im n the same boat with ya. Im still a bit of a noob w/linux. Lukily im prefecent w/winslows as im stuk w/vista. if ne1 figures this 1 out please le me gno

---

### Post by gimfred on 2008-02-13
> **keylime said:**
> Kevdog,

Thanks for the assist there. How do I get the entire output quoted onto here? It's A LOT of data.
<snip>
the magic command for filtering cli commands is 'grep'. Basically you "pipe" your command through 'grep' as in:
```
lsusb -v | grep Realtek
```

here is my lsusb:
> ~$ sudo lsusb -v | grep Canon
[sudo] password for gimfred:
Bus 001 Device 005: ID 04a9:220d Canon, Inc. CanoScan N670U/N676U/LiDE 20
  idVendor           0x04a9 Canon, Inc.
  iManufacturer          64 Canon


---

### Post by mreider on 2008-03-09
I am also a Linux n00b, but I got this working as follows:

Went to [http://datanorth.net/~cuervo/rtl8187b/](http://datanorth.net/~cuervo/rtl8187b/)

And downloaded...

[http://datanorth.net/~cuervo/rtl8187b/rtl8187b-modified-dist.tar.gz](http://datanorth.net/~cuervo/rtl8187b/rtl8187b-modified-dist.tar.gz)

Unpacked it and followed the directions.

Works!

Note that the Ubuntu Wireless Signal icon remains at 30% no matter how strong the signal is, but I don't care, I can gauge the signal by how fast the browser returns pages.

Happy happy.

---

### Post by arriagga on 2008-03-26
does anyone knows if this will be correct  on Hardy, im trying the beta and it has not being fix.
i have a a205-s5804 toshiba laptop.

thanks

---

### Post by acirilo on 2008-04-05
> **arriagga said:**
> does anyone knows if this will be correct  on Hardy, im trying the beta and it has not being fix.
i have a a205-s5804 toshiba laptop.

thanks

any luck? i have the same issue with Hardy... sucks

---

### Post by ercork on 2008-04-06
I have hardy on my satellite A205-S5804 and have the wireless working perfectly thanks to ndiswrapper and a windows driver provided by realtek. See post_erasmus contribution on page 11 and mine on page 12 of this post for details:

[http://ubuntuforums.org/showthread.php?t=571046&highlight=toshiba+a205+wireless](http://ubuntuforums.org/showthread.php?t=571046&highlight=toshiba+a205+wireless)

---

### Post by rolfepope on 2008-07-11
> **Big D ND said:**
> Just bought a Tosh A205-5804 a couple days ago.  Wanted to put Ubuntu on it, but after looking to see if theres been any hassles, I see that the wireless has had this problem.  Anyone gotten it to work??  Thanks for any feedback!!

Darrick

My Toshiba U205-S5034 Satilite works with Ubuntu 8.04 without anything else.  Downloaded the DVD.  Booted and installled without problems.  Found my wireless card without any problem.  Had used a v6 of Ubuntu previously, but that version would not do WPA encryption with mu wireless.

Rolfe

---

### Post by Bobmatt on 2008-07-12
I Have a Toshiba L40-17M and i'm havimg the same problems with the internal wireless an external NetGear WG11v2 works fine.

---

### Post by onewithnature83 on 2008-07-20
Here is my solution:

[https://help.ubuntu.com/community/WifiDocs/Device/RealtekRTL8187b](https://help.ubuntu.com/community/WifiDocs/Device/RealtekRTL8187b)

--TJ (creator)

---

