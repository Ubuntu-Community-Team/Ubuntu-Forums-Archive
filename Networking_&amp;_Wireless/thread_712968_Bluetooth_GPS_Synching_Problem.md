---
title: "Bluetooth GPS Synching Problem"
date: 2008-03-02
forum: Networking &amp; Wireless
---

### Post by mikethetyro on 2008-03-02
Hi

Version is Gutsy, Laptop is Compaq Evo N620c - very problem free install and a dream to use.
Here's the problem - Using Bluetooth Manager, i encountered the bug-  "Couldn't display "obex://[00:02:00:f0:f5:99]". Unfortunately the published work-around which got my mouse and phone linking (Preferences - Services - Input Service - Add - Browse all and select the relevant device) does not work, the GUI drops straight out without error message.
The GPS is a BTGP-38 manufacturer unknown and the usb wireless dongle is made by SafeCom.

When I list all of the bluetooth devices, the GPS is listed as BTGPS and is device type "Unknown" where all others are "Phone" or "Mouse" as appropriate. Is there any chance of a fix?

Am I better off just  buying a different supply / type of GPS receiver?

Thanks

---

### Post by ecimon on 2008-03-02
Hi,

I haven't managed to connect to my BT GPS through GUI either (I'm using kubuntu/gutsy), but if you're not afraid of the command line interface then you can try doing it manually.

Open a terminal window and do the following:

Check if your GPS provides a serial port service. Run:
```
sdptool records 00:02:00:f0:f5:99
```

You should see something like:
```

Service Name: SPP
Service RecHandle: 0x10000
Service Class ID List:
  "Serial Port" (0x1101)
Protocol Descriptor List:
  "L2CAP" (0x0100)
  "RFCOMM" (0x0003)
    Channel: 1
Language Base Attr List:
  code_ISO639: 0x656e
  encoding:    0x6a
  base_offset: 0x100
```

This means we can make the serial port visible under /dev/rfcomm0. Run:
```
sudo rfcomm bind /dev/rfcomm0 00:02:00:f0:f5:99 1
```

Try reading some data from the serial port. Run:
```
cat /dev/rfcomm0 | head
```

You should see NMEA sentences which usually begin with $GPGSV,  $GPGGA ... or similar.

You'll need a NMEA parser, to extract the actual information. I know there is something called 'gpsman', but I haven't used it yet.

---

### Post by mikethetyro on 2008-03-02
Thanks, thats the first time I've got anything from the GPS, your instructions worked seamlessly!

I'm attempting to use GpsDrive ver 2.09 and am inching toward getting some results as soon as I can get my BTGPS unit out on the window ledge far enough to get a satellite link without it dropping to the road below.... 

I'm very grateful for your help

---

