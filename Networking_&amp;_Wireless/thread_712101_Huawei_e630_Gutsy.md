---
title: "Huawei e630 Gutsy"
date: 2008-03-01
forum: Networking &amp; Wireless
---

### Post by kiomarin on 2008-03-01
Hello Everyone,

i've been looking for solution for 3 weeks now, and I also need to say, that i'm really noob in linux. However, i want to make my computer fully "compatible" with Ubuntu. I have HP 6510 laptop, and all the HW is working just great, all drivers seems to be working without problems. The only problem i have, and i was not able to solve it is my data card Huawei e630. I've tried to use all guides that i was able to find ([http://ubuntuforums.org/showthread.php?t=327682](http://ubuntuforums.org/showthread.php?t=327682), guides at mybroadband, comgt, Vodafone datacard driver pack), and nothing helped me. I'm not really sure what info i should enclude to my post, but this is what i saw on other posts:

When i connect my card, the output of tail -f /var/log/messages looks like this:

Feb 24 08:37:48 klayman kernel: [ 612.548000] pccard: CardBus card inserted into slot 0
Feb 24 08:37:48 klayman kernel: [ 612.712000] PCI: Enabling device 0000:03:00.0 (0000 -> 0002)
Feb 24 08:37:48 klayman kernel: [ 612.712000] ACPI: PCI Interrupt 0000:03:00.0[A] -> GSI 16 (level, low) -> IRQ 16
Feb 24 08:37:48 klayman kernel: [ 612.712000] ohci_hcd 0000:03:00.0: OHCI Host Controller
Feb 24 08:37:48 klayman kernel: [ 612.712000] ohci_hcd 0000:03:00.0: new USB bus registered, assigned bus number 8
Feb 24 08:37:48 klayman kernel: [ 612.712000] ohci_hcd 0000:03:00.0: irq 16, io mem 0x8c000000
Feb 24 08:37:49 klayman kernel: [ 612.796000] usb usb8: configuration #1 chosen from 1 choice
Feb 24 08:37:49 klayman kernel: [ 612.796000] hub 8-0:1.0: USB hub found
Feb 24 08:37:49 klayman kernel: [ 612.796000] hub 8-0:1.0: 1 port detected
Feb 24 08:37:49 klayman kernel: [ 612.900000] PCI: Enabling device 0000:03:00.1 (0000 -> 0002)
Feb 24 08:37:49 klayman kernel: [ 612.900000] ACPI: PCI Interrupt 0000:03:00.1[B] -> GSI 16 (level, low) -> IRQ 16
Feb 24 08:37:49 klayman kernel: [ 612.900000] ohci_hcd 0000:03:00.1: OHCI Host Controller
Feb 24 08:37:49 klayman kernel: [ 612.900000] ohci_hcd 0000:03:00.1: new USB bus registered, assigned bus number 9
Feb 24 08:37:49 klayman kernel: [ 612.900000] ohci_hcd 0000:03:00.1: irq 16, io mem 0x8c001000
Feb 24 08:37:49 klayman kernel: [ 612.984000] usb usb9: configuration #1 chosen from 1 choice
Feb 24 08:37:49 klayman kernel: [ 612.984000] hub 9-0:1.0: USB hub found
Feb 24 08:37:49 klayman kernel: [ 612.984000] hub 9-0:1.0: 1 port detected
Feb 24 08:37:59 klayman kernel: [ 623.648000] usb 8-1: new full speed USB device using ohci_hcd and address 2
Feb 24 08:38:00 klayman kernel: [ 623.860000] usb 8-1: configuration #1 chosen from 1 choice
Feb 24 08:38:00 klayman kernel: [ 623.860000] scsi4 : SCSI emulation for USB Mass Storage devices
Feb 24 08:38:00 klayman kernel: [ 624.028000] usbcore: registered new interface driver usbserial
Feb 24 08:38:00 klayman kernel: [ 624.028000] /build/buildd/linux-source-2.6.22-2.6.22/drivers/usb/serial/usb-serial.c: USB Serial support registered for generic
Feb 24 08:38:00 klayman kernel: [ 624.028000] usbcore: registered new interface driver usbserial_generic
Feb 24 08:38:00 klayman kernel: [ 624.028000] /build/buildd/linux-source-2.6.22-2.6.22/drivers/usb/serial/usb-serial.c: USB Serial Driver core
Feb 24 08:38:00 klayman kernel: [ 624.040000] /build/buildd/linux-source-2.6.22-2.6.22/drivers/usb/serial/usb-serial.c: USB Serial support registered for GSM modem (1-port)
Feb 24 08:38:00 klayman kernel: [ 624.040000] usbcore: registered new interface driver option
Feb 24 08:38:00 klayman kernel: [ 624.040000] /build/buildd/linux-source-2.6.22-2.6.22/drivers/usb/serial/option.c: USB Driver for GSM modems: v0.7.1
Feb 24 08:38:05 klayman kernel: [ 628.868000] scsi 4:0:0:0: CD-ROM HUAWEI Mass Storage 2.31 PQ: 0 ANSI: 2
Feb 24 08:38:05 klayman kernel: [ 628.940000] sr1: scsi-1 drive
Feb 24 08:38:05 klayman kernel: [ 628.940000] sr 4:0:0:0: Attached scsi generic sg3 type 5
Feb 24 08:38:13 klayman kernel: [ 637.524000] sr: Sense Key : No Sense [current] 
Feb 24 08:38:13 klayman kernel: [ 637.524000] sr: Add. Sense: No additional sense information
Feb 24 08:38:14 klayman kernel: [ 638.052000] sr: Sense Key : No Sense [current] 
Feb 24 08:38:14 klayman kernel: [ 638.052000] sr: Add. Sense: No additional sense information
Feb 24 08:38:14 klayman kernel: [ 638.068000] sr: Sense Key : No Sense [current] 
Feb 24 08:38:14 klayman kernel: [ 638.068000] sr: Add. Sense: No additional sense information
Feb 24 08:38:14 klayman kernel: [ 638.088000] sr: Sense Key : No Sense [current] 
Feb 24 08:38:14 klayman kernel: [ 638.088000] sr: Add. Sense: No additional sense information
Feb 24 08:38:14 klayman kernel: [ 638.128000] sr: Sense Key : No Sense [current] 
Feb 24 08:38:14 klayman kernel: [ 638.128000] sr: Add. Sense: No additional sense information

When i was trying to use vodafone data card application, it came back with an error that i need to have at least two serial ports registered with the kernel (but this card always registers with only one port: dev/ttyUSB0, except what i've pasted above; that is when i've installed pcmciautils using synaptic package manager). And of course the output of the gnome-ppp is then similar:

mako@klayman:~$ gnome-ppp
WVCONF: /home/mako/.wvdial.conf
GNOME PPP: STDOUT: Editing `/dev/null'.
GNOME PPP: STDOUT: 
GNOME PPP: STDOUT: Scanning your serial ports for a modem.
GNOME PPP: STDOUT: 
GNOME PPP: STDERR: Modem Port Scan<*1>: S0 S1 S2 S3 
GNOME PPP: STDOUT: 
GNOME PPP: STDOUT: 
GNOME PPP: STDOUT: Sorry, no modem was detected! Is it in use by another program?
GNOME PPP: STDOUT: Did you configure it properly with setserial?
GNOME PPP: STDOUT: 
GNOME PPP: STDOUT: Please read the FAQ at [http://open.nit.ca/wiki/?WvDial](http://open.nit.ca/wiki/?WvDial)
GNOME PPP: STDOUT: 
GNOME PPP: STDOUT: If you still have problems, send mail to <wvdial-list@lists.nit.ca>.

I'm also including logs, that i've seen in multiple threads an it seems needed:

lspci -v | grep subordinate
Bus: primary=00, secondary=08, subordinate=08, sec-latency=0
Bus: primary=00, secondary=10, subordinate=10, sec-latency=0
Bus: primary=00, secondary=18, subordinate=18, sec-latency=0
Bus: primary=00, secondary=28, subordinate=28, sec-latency=0
Bus: primary=00, secondary=02, subordinate=06, sec-latency=32
Bus: primary=02, secondary=03, subordinate=06, sec-latency=176

lsusb
Bus 009 Device 001: ID 0000:0000 
Bus 008 Device 002: ID 12d1:1003 ->this is Huawei card 
Bus 008 Device 001: ID 0000:0000 
Bus 007 Device 001: ID 0000:0000 
Bus 006 Device 001: ID 0000:0000 
Bus 004 Device 001: ID 0000:0000 
Bus 003 Device 001: ID 0000:0000 
Bus 003 Device 002: ID 03f0:171d Hewlett-Packard 
Bus 005 Device 001: ID 0000:0000 
Bus 005 Device 003: ID 08ff:2580 AuthenTec, Inc. 
Bus 005 Device 002: ID 062a:0000 Creative Labs Optical Mouse
Bus 001 Device 001: ID 0000:0000 
Bus 002 Device 004: ID 0d49:7250 Maxtor 
Bus 002 Device 001: ID 0000:0000 

uname -a
Linux klayman 2.6.22-14-generic #1 SMP Tue Feb 12 07:42:25 UTC 2008 i686 GNU/Linux

i was also trying to usu comgt application (that should enable the communication with card), at the time my card was showing up correctly as /dev/ttyUSB0, and the message i've got was that my SIM is not there, or i need to input a pin (it was there, and PIN check was disabled). Sorry i don't have this message.

Thanks in advance to everyone glad to help.
-M.

---

### Post by kiomarin on 2008-03-05
Guys, 

i can see that about 50 people already seen this post, no one really knows about this anything more? Please at least point me to forums, if you know about any, that can point me to the right direction, i will be very grateful for every tip.

Thanks a lot,
-M.

---

