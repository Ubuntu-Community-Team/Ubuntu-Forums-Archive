---
title: "USB 3G has to be reconnected to be recognized"
date: 2014-04-03
forum: Networking &amp; Wireless
---

### Post by hongquan1987 on 2014-04-03
I still use my 3G USB without problem until recently, it suddenly appears an issue: Each time I want to use it, I have to disconnect and connect again.
The first time I connect, running ```
usb-devices
``` shows only usbstorage driver attached (to the device). Only when I disconnect and reconnect, I get *option* driver loaded and the model is usable.

Do you have any idea how to fix it?

---

### Post by varunendra on 2014-04-03
This kind of problem has been common with most models in my experience and its frequency has always been dependent on the ISP's service/signal quality and independent of the OS or its version (again, as per my personal experience, there may be other factors involved).

If it is just the modeswitching that you are having trouble with, have you tried manually switching its mode yet? Something like this example -
```
sudo usb_modeswitch -v 0x1c9e -p 0xf000 -M "55534243123456788000000080000606f50402527000000000000000000000"
```
Where **1c9e** is the modem's Vendor ID, **f000** is its Product ID (before mode switching) and the string after "-M" is the product specific message string which you can find by looking at the file "**1c9e:f000**" within **/usr/share/usb_modeswitch/configPack.tar.gz** archive.

Of course change the Vendor ID, Product ID and Message content as per those of your modem. If unsure, please post the outputs of -
```
lsusb
dmesg | tail -20
```
...after plugging in the modem.

---

### Post by hongquan1987 on 2014-04-04
Hi

```
dmesg | tail -n 30
[  158.025846] usb 2-1.1.1: USB disconnect, device number 7
[  164.096273] usb 2-1.1.1: new high-speed USB device number 8 using ehci-pci
[  164.431598] usb 2-1.1.1: New USB device found, idVendor=12d1, idProduct=1c05
[  164.431609] usb 2-1.1.1: New USB device strings: Mfr=2, Product=1, SerialNumber=0
[  164.431615] usb 2-1.1.1: Product: HUAWEI Mobile
[  164.431620] usb 2-1.1.1: Manufacturer: HUAWEI
[  164.434453] usb-storage 2-1.1.1:1.3: USB Mass Storage device detected
[  164.434798] scsi10 : usb-storage 2-1.1.1:1.3
[  164.435184] usb-storage 2-1.1.1:1.4: USB Mass Storage device detected
[  164.435452] scsi11 : usb-storage 2-1.1.1:1.4
[  164.511292] usbcore: registered new interface driver usbserial
[  164.511310] usbcore: registered new interface driver usbserial_generic
[  164.511324] usbserial: USB Serial support registered for generic
[  164.592789] usbcore: registered new interface driver option
[  164.592802] usbserial: USB Serial support registered for GSM modem (1-port)
[  164.592915] option 2-1.1.1:1.0: GSM modem (1-port) converter detected
[  164.593250] usb 2-1.1.1: GSM modem (1-port) converter now attached to ttyUSB0
[  164.593273] option 2-1.1.1:1.1: GSM modem (1-port) converter detected
[  164.594033] usb 2-1.1.1: GSM modem (1-port) converter now attached to ttyUSB1
[  164.594053] option 2-1.1.1:1.2: GSM modem (1-port) converter detected
[  164.594321] usb 2-1.1.1: GSM modem (1-port) converter now attached to ttyUSB2
[  165.431660] scsi 10:0:0:0: CD-ROM            HUAWEI   Mass Storage     2.31 PQ: 0 ANSI: 2
[  165.431776] scsi 11:0:0:0: Direct-Access     HUAWEI   SD Storage       2.31 PQ: 0 ANSI: 2
[  165.432007] sd 11:0:0:0: Attached scsi generic sg2 type 0
[  165.435033] sd 11:0:0:0: [sdb] Attached SCSI removable disk
[  165.441018] sr1: scsi-1 drive
[  165.441265] sr 10:0:0:0: Attached scsi CD-ROM sr1
[  165.442243] sr 10:0:0:0: Attached scsi generic sg3 type 5
[  195.113617] PPP BSD Compression module registered
[  195.197287] PPP Deflate Compression module registered
```

(I don't paste output of lsusb here because I think the log above already has what you want to see from lsub)

---

### Post by varunendra on 2014-04-05
Everything looks as it should including the loading of "option" driver in the above output. It also seems to be the very first attempt after booting the system (since the "usbserial" driver loads in the first attempt). So of course it doesn't show the problem you described in your original post.

If what you originally described happens only sometimes, I would again suspect a bad signal/service quality on the ISPs side (maybe combined with "modemmanager" service's inability to recover immediately).

By the way, the exact command to manually do the modeswitching for this device would be -
```
sudo usb_modeswitch -v 0x12d1 -p 0x1c0b -M "55534243123456780000000000000011062000000100000000000000000000"
```
(the "**1c05**" is the Product ID AFTER mode switching. Before that it should be "**1c0b**")

---

### Post by hongquan1987 on 2014-04-05
Hi,
What looks OK is after I disconnect and reconnect again.

Now I shutdown my PC and restart it, plug the USB 3G in. No "option" driver attaches. Run
```

sudo usb_modeswitch -v 0x12d1 -p 0x1c0b -M "55534243123456780000000000000011062000000100000000000000000000"
```

shows that:

```
Looking for default devices ...
   found matching product ID
   adding device
 Found device in default mode, class or configuration (1)
Accessing device 004 on bus 002 ...
Getting the current device configuration ...
 OK, got current device configuration (1)
Using first interface: 0x00
Using endpoints 0x0f (out) and 0x8f (in)
Inquiring device details; driver will be detached ...
Looking for active driver ...
 OK, driver found ("usb-storage")
 OK, driver "usb-storage" detached

SCSI inquiry data (for identification)
-------------------------
  Vendor String: HUAWEI  
   Model String: Mass Storage    
Revision String: 2.31
-------------------------

USB description data (for identification)
-------------------------
Manufacturer: HUAWEI
     Product: HUAWEI Mobile
  Serial No.: not provided
-------------------------
Setting up communication with interface 0
Using endpoint 0x0f for message sending ...
Trying to send message 1 to endpoint 0x0f ...
 OK, message successfully sent
Resetting response endpoint 0x8f
Resetting message endpoint 0x0f
-> Run lsusb to note any changes. Bye.
```

and "option" driver now attach.

The problem happens "always", but since 2 weeks ago. Before that, I didn't have to disconnect and reconnect.

---

