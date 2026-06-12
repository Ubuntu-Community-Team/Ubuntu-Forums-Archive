---
title: "can anyone help me get linux to recognize a plug in?"
date: 2010-01-29
forum: New to Ubuntu
---

### Post by natedogg23 on 2010-01-29
my new mp3 player isnt recognized for some reason and im wondering if theres some kind of update i need to do? i tried it at a friends house on vista and it worked great but no luck for me. i use 9.10 and heres the dmesg | tail;[132111.309337] usb 1-3: configuration #85 chosen from 1 choice
[132111.313213] scsi8 : SCSI emulation for USB Mass Storage devices
[132111.313699] usb-storage: device found at 16
[132111.313704] usb-storage: waiting for device to settle before scanning
[132116.313854] usb-storage: device scan complete
[132137.176145] usb 1-3: reset full speed USB device using ohci_hcd and address 16
[132147.556119] usb 1-3: reset full speed USB device using ohci_hcd and address 16
[132152.936082] usb 1-3: reset full speed USB device using ohci_hcd and address 16
[132163.316077] usb 1-3: reset full speed USB device using ohci_hcd and address 16
[132163.522296] scsi 8:0:0:0: Device offlined - not ready after error recovery
its from hong kong and theres no brand name on it.
any help would be great. thanks

---

### Post by Psumi on 2010-01-29
After you plug it in, what is the output of... **lsusb**?

---

### Post by natedogg23 on 2010-02-01
sorry i took so long....
Bus 002 Device 003: ID 07b2:5101 Motorola BCS, Inc. SurfBoard SB5101 Cable Modem
Bus 002 Device 002: ID 046d:c00e Logitech, Inc. M-BJ58/M-BJ69 Optical Wheel Mouse
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 005: ID 1e74:3111  <---------this is it
Bus 001 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

---

### Post by niffcreature on 2010-02-01
there might be a setting on the device itself for "automatic sync" instead of "data transfer"
try all of them if there are more than two. 
also maybe try some software like rhythmbox or amarok.
im just listing these because they will be a lot easier than anything related to a bigger problem. and id guess you wont be able to get it to work if there is no driver for it. good luck

---

### Post by natedogg23 on 2010-02-01
there is a driver disc for windoze that reads but cant get it to bring up anything for the mp3. is there a way to get rythymbox to recognize it? since it knows theres something in a port is there some way to do a driver search or update?

---

