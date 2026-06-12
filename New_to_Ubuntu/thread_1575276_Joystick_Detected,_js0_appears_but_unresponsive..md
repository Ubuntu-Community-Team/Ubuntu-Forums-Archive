---
title: "Joystick Detected, js0 appears but unresponsive."
date: 2010-09-15
forum: New to Ubuntu
---

### Post by itsmeaflo on 2010-09-15
Hi guys. I've setup MAME and was excited to plug in my Mad Catz Street Fighter 4 Tournament Edition Joystick and it worked! I mapped the buttons in MAME, played a few games, unplugged the joystick and went to bed.

The next morning, I plugged in the joystick but it was unresponsive. I checked if it was detected by going to
 
```

/dev/input/ and found js0. 

```

To make sure it was the right joystick i ran 

```

jstest /dev/input/js0

```

and it returned:

```

Driver version is 2.1.0.
Joystick (MadCatz PC USB Wired Stick 8838) has 6 axes (X, Y, Z, Rz, Hat0X, Hat0Y)
and 13 buttons (BtnX, BtnY, BtnZ, BtnTL, BtnTR, BtnTL2, BtnTR2, BtnSelect, BtnStart, BtnMode, BtnThumbL, BtnThumbR, ?).
Testing ... (interrupt to exit)
...

```

The right one! but when i mashed a few buttons none of the buttons switched from off to on. (When I cat /dev/input/js0, funny characters appear but do not add any more when i press buttons). I unplugged the joystick and replugged it in again and ran dmesg and it spit this out:

```

...
[47748.593672] input: MadCatz PC USB Wired Stick 8838 as /devices/pci0000:00/0000:00:04.0/usb2/2-5/2-5:1.0/input/input20
[47748.593895] generic-usb 0003:0738:8838.0010: input,hidraw0: USB HID v1.10 Gamepad [MadCatz PC USB Wired Stick 8838] on usb-0000:00:04.0-5/input0
...

```

And finally, I ran lsusb -vv to see what's up but to my untrained eyes it looks alright to me:

```

Bus 002 Device 003: ID 0738:8838 Mad Catz, Inc. 
Device Descriptor:
  bLength                18
  bDescriptorType         1
  bcdUSB               1.10
  bDeviceClass            0 (Defined at Interface level)
  bDeviceSubClass         0 
  bDeviceProtocol         0 
  bMaxPacketSize0         8
  idVendor           0x0738 Mad Catz, Inc.
  idProduct          0x8838 
  bcdDevice            1.00
  iManufacturer           1 MadCatz
  iProduct                2 PC USB Wired Stick 8838
  iSerial                 0 
  bNumConfigurations      1
  Configuration Descriptor:
    bLength                 9
    bDescriptorType         2
    wTotalLength           41
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
      bInterfaceClass         3 Human Interface Device
      bInterfaceSubClass      0 No Subclass
      bInterfaceProtocol      0 None
      iInterface              0 
      ** UNRECOGNIZED:  09 21 10 01 00 01 22 89 00
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x81  EP 1 IN
        bmAttributes            3
          Transfer Type            Interrupt
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0040  1x 64 bytes
        bInterval              10
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x02  EP 2 OUT
        bmAttributes            3
          Transfer Type            Interrupt
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0040  1x 64 bytes
        bInterval              10
Device Status:     0x0000
  (Bus Powered)

```

I'm probably doing something really stupid but I guess i'm pretty frustrated. Any ideas?

p.s. I tested the joystick with my ps3 and it works there.

---

### Post by Sef on 2010-09-15
Moved to ABT.

---

### Post by itsmeaflo on 2010-09-18
I've reinstalled ubuntu to 10.04 and tried again. same issue. js0 appears but when jstest is run, no button inputs seem to be recognized.

---

### Post by itsmeaflo on 2010-09-20
Ok i figured it out sorta. if i run:

```
sudo modprobe uinput
```

My joystick buttons return! I dont know why this is the case. I also have CWiid installed. but it's odd that i have to do this since i have uinput in my /etc/modules already. I hope this helps anyone else.

---

