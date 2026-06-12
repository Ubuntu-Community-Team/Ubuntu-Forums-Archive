---
title: "Novatel Ovation U727 Device Assignment"
date: 2008-10-28
forum: Networking &amp; Wireless
---

### Post by ba_rich on 2008-10-28
I've got a PC with two Novatel U727 USB cards. If the cards are plugged in when the PC is booted, each of the U727s create multiple ttyUSBxx devices:

  First U727 - ttyUSB0 through ttyUSB11
  Second U727 - ttyUSB12 through ttyUSB23

Is this normal? Will it always be 12 devices?

The related dmesg entries follow:

[   61.941956] usb-storage: device found at 4
[   61.941962] usb-storage: waiting for device to settle before scanning
[   61.942356] scsi5 : SCSI emulation for USB Mass Storage devices
[   61.942786] usbcore: registered new interface driver usb-storage
[   61.942794] USB Mass Storage support registered.
[   61.943003] usb-storage: device found at 5
[   61.943007] usb-storage: waiting for device to settle before scanning
[   66.931380] usb-storage: device scan complete
[   66.931501] usb-storage: device scan complete
[   66.934360] scsi 5:0:0:0: Direct-Access     Novatel  MMC Storage      2.31 PQ: 0 ANSI: 2
[   66.934370] scsi 4:0:0:0: Direct-Access     Novatel  MMC Storage      2.31 PQ: 0 ANSI: 2
[   66.940379] sd 5:0:0:0: [sdb] Attached SCSI removable disk
[   66.940425] sd 5:0:0:0: Attached scsi generic sg2 type 0
[   66.945364] sd 4:0:0:0: [sdc] Attached SCSI removable disk
[   66.945408] sd 4:0:0:0: Attached scsi generic sg3 type 0

[   76.010117] usbcore: registered new interface driver usbserial
[   76.010190] /build/buildd/linux-2.6.24/drivers/usb/serial/usb-serial.c: USB Serial support registered for generic
[   76.010383] usbcore: registered new interface driver usbserial_generic
[   76.010390] /build/buildd/linux-2.6.24/drivers/usb/serial/usb-serial.c: USB Serial Driver core
[   76.050132] /build/buildd/linux-2.6.24/drivers/usb/serial/usb-serial.c: USB Serial support registered for airprime
[   76.050204] airprime 3-1:1.0: airprime converter detected
[   76.050467] usb 3-1: airprime converter now attached to ttyUSB0
[   76.050633] usb 3-1: airprime converter now attached to ttyUSB1
[   76.050793] usb 3-1: airprime converter now attached to ttyUSB2
[   76.050813] airprime 3-1:1.1: airprime converter detected
[   76.051007] usb 3-1: airprime converter now attached to ttyUSB3
[   76.051189] usb 3-1: airprime converter now attached to ttyUSB4
[   76.051342] usb 3-1: airprime converter now attached to ttyUSB5
[   76.051361] airprime 3-1:1.2: airprime converter detected
[   76.051519] usb 3-1: airprime converter now attached to ttyUSB6
[   76.051692] usb 3-1: airprime converter now attached to ttyUSB7
[   76.051844] usb 3-1: airprime converter now attached to ttyUSB8
[   76.051864] airprime 3-1:1.3: airprime converter detected
[   76.052025] usb 3-1: airprime converter now attached to ttyUSB9
[   76.052177] usb 3-1: airprime converter now attached to ttyUSB10
[   76.052330] usb 3-1: airprime converter now attached to ttyUSB11
[   76.052352] airprime 3-2:1.0: airprime converter detected
[   76.052547] usb 3-2: airprime converter now attached to ttyUSB12
[   76.052694] usb 3-2: airprime converter now attached to ttyUSB13
[   76.052850] usb 3-2: airprime converter now attached to ttyUSB14
[   76.052869] airprime 3-2:1.1: airprime converter detected
[   76.053031] usb 3-2: airprime converter now attached to ttyUSB15
[   76.053184] usb 3-2: airprime converter now attached to ttyUSB16
[   76.053346] usb 3-2: airprime converter now attached to ttyUSB17
[   76.053366] airprime 3-2:1.2: airprime converter detected
[   76.053526] usb 3-2: airprime converter now attached to ttyUSB18
[   76.053705] usb 3-2: airprime converter now attached to ttyUSB19
[   76.053867] usb 3-2: airprime converter now attached to ttyUSB20
[   76.053886] airprime 3-2:1.3: airprime converter detected
[   76.054074] usb 3-2: airprime converter now attached to ttyUSB21
[   76.054230] usb 3-2: airprime converter now attached to ttyUSB22
[   76.054384] usb 3-2: airprime converter now attached to ttyUSB23
[   76.054408] usbcore: registered new interface driver airprime
[   76.103408] /build/buildd/linux-2.6.24/drivers/usb/serial/usb-serial.c: USB Serial support registered for GSM modem (1-port)
[   76.103541] usbcore: registered new interface driver option
[   76.103547] /build/buildd/linux-2.6.24/drivers/usb/serial/option.c: USB Driver for GSM modems: v0.7.1

---

### Post by skullY Dazed on 2008-10-29
> **ba_rich said:**
> I've got a PC with two Novatel U727 USB cards. If the cards are plugged in when the PC is booted, each of the U727s create multiple ttyUSBxx devices:

  First U727 - ttyUSB0 through ttyUSB11
  Second U727 - ttyUSB12 through ttyUSB23

Is this normal? Will it always be 12 devices?


I don't know if it's "normal" but I just setup my U727 under hardy (which involved upgrading the kernel from git - not fun) and I got the same thing. In my case I have ttyUSB2 - ttyUSB14, because I have a different device on ttyUSB0 and ttyUSB1.

I pointed pppd at ttyUSB2 and everything seems to work. Got 746k down on a speedtest, which is better than the 500k I was seeing when I was still using the usbserial module directly.

-Zach

---

### Post by cozmicharlie on 2008-10-30
I don't know if that is normal or not either.  However, when I boot with my U727 plugged in it mounts as a cdrom device and I have to sudo eject /dev/scd1.  Then it mounts and connects.  My dmesg output is below:

usbcore: registered new interface driver usbserial_generic
[  769.532296] usbserial: USB Serial Driver core
[  769.554982] usbserial: USB Serial support registered for GSM modem (1-port)
[  769.555062] option 2-5:1.0: GSM modem (1-port) converter detected
[  769.555562] usb 2-5: GSM modem (1-port) converter now attached to ttyUSB0
[  769.555602] option 2-5:1.1: GSM modem (1-port) converter detected
[  769.555785] usb 2-5: GSM modem (1-port) converter now attached to ttyUSB1
[  769.555821] option 2-5:1.2: GSM modem (1-port) converter detected
[  769.555998] usb 2-5: GSM modem (1-port) converter now attached to ttyUSB2
[  769.556033] option 2-5:1.3: GSM modem (1-port) converter detected
[  769.556213] usb 2-5: GSM modem (1-port) converter now attached to ttyUSB3
[  769.556259] usbcore: registered new interface driver option
[  769.556271] option: USB Driver for GSM modems: v0.7.2
[  774.189598] usb-storage: device scan complete
[  774.194579] scsi 5:0:0:0: Direct-Access     Novatel  MMC Storage      2.31 PQ: 0 ANSI: 2

---

### Post by ba_rich on 2008-10-30
Yes. If I plug the USB devices in after booting, I also have to eject the CD-ROM device to make it work. In this case, there are 4 ttyUSB devices.

If I plug in the devices before booting, I don't have to eject the CD-ROM and there are 12 ttyUSB devices.

---

