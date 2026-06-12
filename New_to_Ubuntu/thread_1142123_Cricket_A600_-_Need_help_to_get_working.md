---
title: "Cricket A600 - Need help to get working"
date: 2009-04-28
forum: New to Ubuntu
---

### Post by beastrace91 on 2009-04-28
Does anyone know if the Cricket A600 works with Ubuntu? I recently purchased one and I don't want to have to install Windows to make it work. I have Ubuntu 8.10 64bit and 9.04 Netbook remix on my two laptops - but it does not appear to simply plug in and work on either of them. Is there a way I can get this working? I have 2 days to return it for most of my money back if I can't so any help asap would be great.

~Jeff

---

### Post by Praxicoide on 2009-04-28
Type the following into the terminal (Aplications---->Accesories----->Terminal):

```
lsusb
```

And paste the outcome here.

---

### Post by beastrace91 on 2009-04-28
> jeff@lintop:~$ lsusb
Bus 007 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 003: ID 0b05:1726 ASUSTek Computer, Inc. Laptop OLED Display
Bus 003 Device 002: ID 04f2:b012 Chicony Electronics Co., Ltd 1.3 MPixel UVC webcam
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 002: ID 0b05:1712 ASUSTek Computer, Inc. BT-183 Bluetooth 2.0+EDR adapter
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 003: ID 1f28:0021  
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub


I don't think I see it there... when I plug it in it detects it as an auto run medium, when pluggin it into a Windows system it appears to display as a CDrom drive in the way the software auto launches. Let me know if you need any other information, I've been crawling Google for a couple of hours now and can't find anything useful.

~Jeff

---

### Post by beastrace91 on 2009-04-28
Huzzah! It looks like I simply had to install the software on my Windows VM and then activate the stupid thing... Once it was activated it is simply plug and play like everything else on Ubuntu! :)

~Jeff

---

### Post by beastrace91 on 2009-04-28
Ok this is a really strange issue... When I simply plug in the Modem it does not detect it... how ever if I assign control of the device to my Windows VM and then un-assign it THEN it shows in my network manager. Any idea why this might be? Its a great work around for my stronger laptop but my EEE cannot run a VM so doing this is not an option for it. Any help would  be fantastic.

~Jeff

---

### Post by beastrace91 on 2009-04-28
I *think* (and this is slightly a stab in the dark here) that the issue is linked to how the auto setup wizard tries to run when I plug in the device. When I first plug it into Ubuntu it reads the device as a drive and put it into /media along with cdroms and other thumb drives, once it has been connected/disconnected from my VM how ever it no longer displays in the /media directory but it does then display in my network manager as a broadband modem. Any ideas how I might go about getting it to detect the way I need/want it to with out first having to connect to my VM?

~Jeff

---

### Post by Praxicoide on 2009-04-28
I was about to comment that I had an EVDO card, and what I had to do was to activate it using Windows.

It looks like it will work, when assigned correctly. You will have to do that with Udev.

---

### Post by Praxicoide on 2009-04-28
Check how the device is assigned by lsusb -v, first as a media drive, then when it is correctly recognized by the Network manager.

If it still doesn't show, reboot with the device plugged in. After you log in run

dmesg | grep usb

...and that should tell you how the system recognized it upon start up.

The point is to then use Udev to fix the usb port assignments (or at least that one, I don't remember if you can do this), granting it the characteristics of when the card is correctly recognized.

---

### Post by beastrace91 on 2009-04-28
> **Praxicoide said:**
> It looks like it will work, when assigned correctly. You will have to do that with Udev.

How would I go about doing this? And how exactly does the VM assign it after it releases it that is the "correct" manner?

~Jeff

---

### Post by beastrace91 on 2009-04-28
Here is the output from the device when it is correct recognised by the network manager: ```
Bus 005 Device 015: ID 1f28:0020  
Device Descriptor:
  bLength                18
  bDescriptorType         1
  bcdUSB               1.10
  bDeviceClass            2 Communications
  bDeviceSubClass         0 
  bDeviceProtocol         0 
  bMaxPacketSize0        64
  idVendor           0x1f28 
  idProduct          0x0020 
  bcdDevice            0.00
  iManufacturer           1 Cal-comp E&CC Limited 
  iProduct                2 Cal-comp CDMA USB Modem A600  
  iSerial                 0 
  bNumConfigurations      1
  Configuration Descriptor:
    bLength                 9
    bDescriptorType         2
    wTotalLength          189
    bNumInterfaces          7
    bConfigurationValue     1
    iConfiguration          0 
    bmAttributes         0xa0
      (Bus Powered)
      Remote Wakeup
    MaxPower              500mA
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        0
      bAlternateSetting       0
      bNumEndpoints           1
      bInterfaceClass         2 Communications
      bInterfaceSubClass      2 Abstract (modem)
      bInterfaceProtocol      1 AT-commands (v.25ter)
      iInterface              3 Data Interface
      CDC Header:
        bcdCDC               1.09
      CDC Call Management:
        bmCapabilities       0x03
          call management
          use DataInterface
        bDataInterface          1
      CDC ACM:
        bmCapabilities       0x0f
          connection notifications
          sends break
          line coding and serial state
          get/set/clear comm features
      CDC Union:
        bMasterInterface        0
        bSlaveInterface         1 
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x81  EP 1 IN
        bmAttributes            3
          Transfer Type            Interrupt
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0010  1x 16 bytes
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
      iInterface              3 Data Interface
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
        bEndpointAddress     0x02  EP 2 OUT
        bmAttributes            2
          Transfer Type            Bulk
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0040  1x 64 bytes
        bInterval               0
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        2
      bAlternateSetting       0
      bNumEndpoints           2
      bInterfaceClass       255 Vendor Specific Class
      bInterfaceSubClass    255 Vendor Specific Subclass
      bInterfaceProtocol    255 Vendor Specific Protocol
      iInterface              3 Data Interface
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x89  EP 9 IN
        bmAttributes            2
          Transfer Type            Bulk
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0040  1x 64 bytes
        bInterval               0
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x09  EP 9 OUT
        bmAttributes            2
          Transfer Type            Bulk
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0040  1x 64 bytes
        bInterval               0
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        3
      bAlternateSetting       0
      bNumEndpoints           2
      bInterfaceClass       255 Vendor Specific Class
      bInterfaceSubClass    255 Vendor Specific Subclass
      bInterfaceProtocol    255 Vendor Specific Protocol
      iInterface              3 Data Interface
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x86  EP 6 IN
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
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        4
      bAlternateSetting       0
      bNumEndpoints           3
      bInterfaceClass       255 Vendor Specific Class
      bInterfaceSubClass    255 Vendor Specific Subclass
      bInterfaceProtocol    255 Vendor Specific Protocol
      iInterface              3 Data Interface
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x85  EP 5 IN
        bmAttributes            3
          Transfer Type            Interrupt
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0010  1x 16 bytes
        bInterval               8
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x83  EP 3 IN
        bmAttributes            2
          Transfer Type            Bulk
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0040  1x 64 bytes
        bInterval               0
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x03  EP 3 OUT
        bmAttributes            2
          Transfer Type            Bulk
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0040  1x 64 bytes
        bInterval               0
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        5
      bAlternateSetting       0
      bNumEndpoints           2
      bInterfaceClass       255 Vendor Specific Class
      bInterfaceSubClass    255 Vendor Specific Subclass
      bInterfaceProtocol    255 Vendor Specific Protocol
      iInterface              3 Data Interface
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x84  EP 4 IN
        bmAttributes            2
          Transfer Type            Bulk
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0040  1x 64 bytes
        bInterval               0
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x04  EP 4 OUT
        bmAttributes            2
          Transfer Type            Bulk
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0040  1x 64 bytes
        bInterval               0
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        6
      bAlternateSetting       0
      bNumEndpoints           2
      bInterfaceClass         8 Mass Storage
      bInterfaceSubClass      6 SCSI
      bInterfaceProtocol     80 Bulk (Zip)
      iInterface              3 Data Interface
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x87  EP 7 IN
        bmAttributes            2
          Transfer Type            Bulk
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0040  1x 64 bytes
        bInterval               0
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x08  EP 8 OUT
        bmAttributes            2
          Transfer Type            Bulk
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0040  1x 64 bytes
        bInterval               0
Device Status:     0x0002
  (Bus Powered)
  Remote Wakeup Enabled

```

And the output when it is not properly assigned: ```
Bus 005 Device 016: ID 1f28:0021  
Device Descriptor:
  bLength                18
  bDescriptorType         1
  bcdUSB               1.10
  bDeviceClass            0 (Defined at Interface level)
  bDeviceSubClass         0 
  bDeviceProtocol         0 
  bMaxPacketSize0        64
  idVendor           0x1f28 
  idProduct          0x0021 
  bcdDevice            0.00
  iManufacturer           1 Cal-comp E&CC Limited 
  iProduct                2 USB Micro SD Storage
  iSerial                 3 215568498100
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
    MaxPower              100mA
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
        bEndpointAddress     0x87  EP 7 IN
        bmAttributes            2
          Transfer Type            Bulk
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0040  1x 64 bytes
        bInterval               0
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x08  EP 8 OUT
        bmAttributes            2
          Transfer Type            Bulk
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0040  1x 64 bytes
        bInterval               0
Device Status:     0x0000
  (Bus Powered)

``` It is obviously alot shorter when it is improperly working... how can I assign it to work in the first manner which I need?

~Jeff

---

### Post by Praxicoide on 2009-04-28
Hey, check it out: [someone automated this](http://www.draisberghof.de/usb_modeswitch/).

I don't know if it will work, but it is worth a look.

---

### Post by beastrace91 on 2009-04-29
Urg... my A600 is not included in the list of devices it "flips". Any idea how I can go about manually changing it so it works properly?

~Jeff

---

### Post by anewguy on 2009-04-29
That link looks promising.  I was going to mention this is a multiple-device USB device.  That is evident by the following:  The device ID when you have it recognized by network manager is 21 - obviously the modem device.  When it is not recognized by network manager the device ID is 20 - and is pointing to SD card device.  I would suspect the switcher in the link above might just do the trick - you need to change from device 20 (the SD card that looks like a disk) to device 21 (the modem).

Depending on how things go, you may also still need to add something to the udev rules, but before getting to there try the above link.

Dave :)

---

### Post by Praxicoide on 2009-04-29
Well, my guess is that you would need to force udev to recognize it as a network device, as I said. This would mean no switching, though. Udev is made to work with the rules established under /etc/dev/rules.d

Beneath this folder you should have some (I assume) empty files on persistent behavior. You write down the rules under which a usb would be persistently assigned a device.

They way I understand it, you use the device's serial (the "iserial" it gave you with lsusb -v), but your device is oddly giving a 0, so you will have to use another criteria (EDIT: The device ID, as anewguy is correctly saying). Check out the manual for udev on the synthax and on the ways to establish these rules.

---

### Post by beastrace91 on 2009-04-29
I looked through the above link, it does look promising (it is the exact issue I am having) how ever it does not support the card I am trying to use, and maybe I am just stupid but I cannot figure out how to register for their forums... (I cannot find the answer to the stupid "anti spam" question they have posted to register.) Ideas on how I might get my device to work with those that this program "flips"? Because it has an automated feature which would be nice to have...

~Jeff

---

### Post by lkraemer on 2009-04-29
Please search the forum for Cricket.  I got information on the
Cricket for a neighbor a few months back.  It was supposed to
be easy to setup and use according to the information on the
post.

Good Luck.

lkraemer

---

### Post by beastrace91 on 2009-04-29
Thanks for the help thus far! I will check out the manual for udev come morning heading to sleep now. Will report back my finding later tomorrow afternoon/evening.

~Jeff

---

### Post by Praxicoide on 2009-04-29
You can try sending him an "old fashioned" (lol!) e-mail.

Or you can register in the forum. The answer is easy, I can't post it here, but for a bigger hint, look [here](http://www.option.com/).

---

### Post by JK3mp on 2009-04-29
Yea i've seen posts plenty of time about cricket on the forums, search it up. And good luck ! :D

---

### Post by beastrace91 on 2009-04-29
@JK3 and ikr Most all of the other posts about getting cricket devices working on these boards are pertaining to older models of cricket USB modems, not the A600 which they now sell.

I've posted on these boards and a couple of others looking for help setting up the udev rules so it will detect it in the correct manner, anyone have any idea how I can go about doing this or if there is an easier way to get this working? Basically I need to tell it when I plug in the device to use the proper ID # the first time, anyone have any idea how VirtualBox assigns USB devices after it releases them it is then correct, then maybe I can replicate this with out having to turn on a VM

~Jeff

---

### Post by rotoghost on 2009-05-01
I'm having the exact issue it seems.  

So, I'm very very new to Linux, a complete newb if you will - but so far I think I'm understanding the problem (that the device is being assigned one way by Windows, and another way by Linux).  If I cold boot into Ubuntu the Cricket A600 doesn't seem to do anything but blink at me - whereas if I load XP, get online for a moment, and then reboot into Ubuntu everything is peachy.

So far it's the only issue I've had at all since initially installing, coming from a lifetime of using Windows, this is actually a shockingly polished and well done OS!

---

### Post by beastrace91 on 2009-05-01
Hey there,

I have been [working hard](http://www.draisberghof.de/usb_modeswitch/bb/viewtopic.php?p=631) the last couple of days to get usb_modeswitch working with the Cricket A600. I'll be sure to post in this thread/write a howto for the device once I get it fully working under Ubuntu with out having to boot into windows/use a VM

~Jeff

---

### Post by beastrace91 on 2009-05-02
I have it up and running howto posted [here](http://ubuntuforums.org/showthread.php?p=7197740#post7197740)

~Jeff

---

### Post by orcaman42 on 2011-04-03
Ok so I installed 10.10 it's sees my a600 in the network manager when I try to connect to it, it waits 3 seconds then disconnects. It auto installed flip flop (that was kinda cool). But it's not working... Ideas?

---

