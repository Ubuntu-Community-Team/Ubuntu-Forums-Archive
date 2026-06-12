---
title: "Zte mf 190 usb_modeswitch issue"
date: 2015-07-16
forum: Networking &amp; Wireless
---

### Post by Gajanana on 2015-07-16
I am trying to connect ZTE MF 190 in Linux based OS. But the problem is it is automatically modeswitching without entering any USB Modeswitch command and I am not able to mode switch after that 

 >    38.534134] usb 5-1: new high-speed USB device number 2 using ehci-platform[   38.690298] option 5-1:1.0: GSM modem (1-port) converter detected
[   38.696950] usb 5-1: GSM modem (1-port) converter now attached to ttyUSB0
[   38.704917] option 5-1:1.1: GSM modem (1-port) converter detected
[   38.711253] usb 5-1: GSM modem (1-port) converter now attached to ttyUSB1
[   38.718571] option 5-1:1.2: GSM modem (1-port) converter detected
[   38.725027] usb 5-1: GSM modem (1-port) converter now attached to ttyUSB2
[   38.732070] option 5-1:1.3: GSM modem (1-port) converter detected
[   38.738608] usb 5-1: GSM modem (1-port) converter now attached to ttyUSB3
[   38.745787] usb-storage 5-1:1.4: USB Mass Storage device detected
[   38.753414] scsi0 : usb-storage 5-1:1.4
[   38.759113] scsi 0:0:0:0: CD-ROM            ZTE      USB SCSI CD-ROM  2.31 PQ: 0 ANSI: 2
[   38.767561] scsi 0:0:0:0: Attached scsi generic sg0 type 5
[   38.773647] scsi 0:0:0:1: Direct-Access     ZTE      MMC Storage      2.31 PQ: 0 ANSI: 2
[   38.782199] sd 0:0:0:1: Attached scsi generic sg1 type 0
[   38.789221] sd 0:0:0:1: [sda] Attached SCSI removable disk

This message appears as soon as i connect Dongle without any need of any usb modeswitch command and only ttyUSB3 works for sending AT commands . Other Ports are not working at all
lsusb shows below output
> Bus 001 Device 002: ID 043e:3100Bus 003 Device 002: ID 0461:4d81
Bus 005 Device 002: ID 19d2:2003
Bus 001 Device 001: ID 1d6b:0002
Bus 002 Device 001: ID 1d6b:0003
Bus 003 Device 001: ID 1d6b:0002
Bus 004 Device 001: ID 1d6b:0003
Bus 005 Device 001: ID 1d6b:0002
Bus 006 Device 001: ID 1d6b:0002
Bus 007 Device 001: ID 1d6b:0001
Bus 008 Device 001: ID 1d6b:0001

I tried using below modeswitch command as soon as i connect dongle 
> usb_modeswitch -v 0x19d2 -p 0x2000 -V 0x19d2 -P 0x2003 -s 20 -M 55534243123456702000000080000c85010101180101010101000000000000
 
But no use since its switched already.

I tried sending below AT commands for disabling CD-ROM Mode and convert to modem mode
> AT+ZOPRT=5
AT+ZCDRUN=8

But beahviour is same . Please let me know if there is any method to make This dongle work

---

