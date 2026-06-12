---
title: "Bluetooth on Dell D630 with Ubuntu 7.10 cannot see any other devices"
date: 2008-01-04
forum: Networking &amp; Wireless
---

### Post by dminor1958 on 2008-01-04
Greetings,

I've read through the posts on activating the internal Bluetooth card on a Dell D630 with 7.10 and I have a slightly different problem.  I can see the internal card, but nothing can connect to it.  Here's the details:

lsusb -v
Bus 002 Device 002: ID 413c:8140 Dell Computer Corp.
Device Descriptor:
  bLength                18
  bDescriptorType         1
  bcdUSB               2.00
  bDeviceClass          224 Wireless
  bDeviceSubClass         1 Radio Frequency
  bDeviceProtocol         1 Bluetooth
  bMaxPacketSize0        64
  idVendor           0x413c Dell Computer Corp.
  idProduct          0x8140
  bcdDevice           43.15
  iManufacturer           0
  iProduct                0
  iSerial                 0
  bNumConfigurations      1

hciconfig -a
hci0:   Type: USB
        BD Address: 00:1A:6B:3D:17:4C ACL MTU: 310:10 SCO MTU: 64:8
        UP RUNNING PSCAN ISCAN 
        RX bytes:13256 acl:0 sco:0 events:263 errors:0
        TX bytes:2505 acl:0 sco:0 commands:238 errors:0
        Features: 0xff 0xff 0x8f 0xfe 0x9b 0xf9 0x00 0x80
        Packet type: DM1 DM3 DM5 DH1 DH3 DH5 HV1 HV2 HV3 
        Link policy: RSWITCH HOLD SNIFF PARK 
        Link mode: SLAVE ACCEPT 
        Name: 'samewise-0'
        Class: 0x08010c
        Service Classes: Capturing
        Device Class: Computer, Laptop
        HCI Ver: 2.0 (0x3) HCI Rev: 0x10db LMP Ver: 2.0 (0x3) LMP Subver: 0x10db
        Manufacturer: Cambridge Silicon Radio (10)

But when I execute hcitool scan or hidd --search, they both report nothing found.  I have a Dell keyboard and Dell mouse, along with a Blackberry 8830 that cannot see the laptop no seen by the laptop.  (The bb did see the keyboard).  These (they keyboard and mouse) both worked fine when I was running XP on this laptop.

Any suggestions would be appreciated.  Also I have EVDO card at 413c/8133 that I THINK is working fine, but I'm in a rural area right now and can't really test it.

Thanks,
-David Minor

---

### Post by roblloyd on 2008-02-15
If your laptop came with Vista preinstalled, the bluetooth firmware will be incompatible with linux... the only way to get round this that i have found is to either install or find a way to boot into xp. at this point you can downgrade the bluetooth drivers and when you boot back into linux everything sould be fine... personally im just trying to work out a way of booting into xp without destroying my linux install. I hope this helps!

Rob

---

### Post by prasenp on 2008-04-12
Got it working through VMWare.

I had the exact same problem on Suse 10.3. The bluetooth device was recognized by the linux driver but coudn't communicate. The bluetooth LED on the laptop would also not light up.

Instead of trying to repartition the disk and install XP, I just fired up my XP VMWare image and the XP recognized a new device and prompted for the driver location. I got the driver from the Dell site and as soon as it was installed the bluetooth light came on. 

I am now able to use 100% of the bluetooth functions through linux without the VMWare running XP.

Hope this helps you.

Regards,
Prasen.

---

