---
title: "start a serial connection"
date: 2006-10-12
forum: Networking &amp; Wireless
---

### Post by danbyte on 2006-10-12
Looks like ubuntu has detected my Keyspan USB to serial adapter without problems, part of the dmesg output below:

[17182265.520000] usb 2-1: new full speed USB device using uhci_hcd and address 3
[17182265.736000] usb 2-1: configuration #1 chosen from 2 choices
[17182265.960000] usbcore: registered new driver usbserial
[17182265.960000] drivers/usb/serial/usb-serial.c: USB Serial support registered for generic
[17182265.960000] usbcore: registered new driver usbserial_generic
[17182265.960000] drivers/usb/serial/usb-serial.c: USB Serial Driver core
[17182265.972000] drivers/usb/serial/usb-serial.c: USB Serial support registered for Keyspan - (without firmware)
[17182265.972000] drivers/usb/serial/usb-serial.c: USB Serial support registered for Keyspan 1 port adapter
[17182265.972000] drivers/usb/serial/usb-serial.c: USB Serial support registered for Keyspan 2 port adapter
[17182265.972000] drivers/usb/serial/usb-serial.c: USB Serial support registered for Keyspan 4 port adapter
[17182265.972000] keyspan 2-1:1.0: Keyspan 1 port adapter converter detected
[17182265.972000] usb 2-1: Keyspan 1 port adapter converter now attached to ttyUSB0
[17182265.976000] usbcore: registered new driver keyspan
[17182265.976000] drivers/usb/serial/keyspan.c: v1.1.4:Keyspan USB to Serial Converter Driver
[17182324.776000] ISO 9660 Extensions: Microsoft Joliet Level 1



How can I start using the adapter? I want to establish a connection with the console port on a HP server but don't know how to start a serial connection in Linux and configure things like BAUD rate or parity. ](*,)

---

### Post by A. J. Rimmer on 2006-10-12
OK, I know this isn't going to be of much help, but perhaps it will get you started in the right direction.

I'm stuck with dial-up out here, and there don't seem to be any appropriate drivers for the Conexant internal modem on my laptop.  So, I am using an IoGear USB to Serial adapter to connect to a serial modem.  After a bit of poking around in /dev I discovered that the adapter is identified as /dev/ttyUSB0, so I went into the Network panel, set the modem address to /dev/ttyUSB0 and I can dial out and connect OK.

I know that doesn't help with COM port settings, but may at least help you identify the USB-serial adapter on your system.  You might try:

cd /dev
ls ttyU*

Good luck!

---

### Post by donsalo on 2007-05-07
I'm a newbie.  I just wanted to thank you for your help.

I installed Putty and the default Serial Line came up to /dev/ttys0, which allowed me to attempt to connect, but did not function.  I tried other ports, like ttyS1, ttyS2, but they failed immediately.  I read a note on the Keyspan site that indicated ubuntu only partially supports their drivers, etc, etc, and I would need to compile a new kernel, etc.  I didn't feel like getting into it that deeply.

I read this post, changed the Serial Line to /dev/ttyUSB0 and it worked perfectly.

Thanks.

Don

---

### Post by A. J. Rimmer on 2007-05-09
Thanks for the note.  First time I was actually able to help someone else!

---

