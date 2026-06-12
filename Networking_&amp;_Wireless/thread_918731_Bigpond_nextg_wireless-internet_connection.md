---
title: "Bigpond nextg wireless-internet connection"
date: 2008-09-13
forum: Networking &amp; Wireless
---

### Post by sunlover on 2008-09-13
I have Ubuntu 7.10 dual booted with Windows XP on my laptop.
I access the Net thru Windows XP using an OPTION GX 0202 pci wireless card supplied by BigPond.
I am keen to get into Ubuntu but am frustrated by lack of direct internet access. When I boot up  ubuntu I get flashing blue light on modem which leads me to believe card has detected  network(3G).
After playing around with ndiswrapper, windows drivers and  **vodaphone-mobile-connect-card- driver-for-Linux _1.99.17_i386.deb**(which would probably work if you could reconfigure it- not much documentation on this.)I ran *dmesg* command after inserting option card, as suggested in post on forums, with the following output:



[I]bruce@bruce-laptop:~$ [ 1354.888000] ohci_hcd 0000:02:00.1: new USB bus registered, assigned bus number 4 
[ 1354.888000] ohci_hcd 0000:02:00.1: irq 11, io mem 0x30001000 
[ 1354.972000] usb usb4: configuration #1 chosen from 1 choice 
[ 1354.972000] hub 4-0:1.0: USB hub found 
[ 1354.972000] hub 4-0:1.0: 1 port detected 
[ 1358.652000] usb 4-1: new full speed USB device using ohci_hcd and address 2 
[ 1358.868000] usb 4-1: configuration #1 chosen from 1 choice 
[ 1359.048000] usbcore: registered new interface driver usbserial 
[ 1359.048000] /build/buildd/linux-source-2.6.22-2.6.22/drivers/usb/serial/usb-serial.c: USB Serial support registered for generic 
[ 1359.048000] usbcore: registered new interface driver usbserial_generic 
[ 1359.048000] /build/buildd/linux-source-2.6.22-2.6.22/drivers/usb/serial/usb-serial.c: USB Serial Driver core 
[ 1359.068000] /build/buildd/linux-source-2.6.22-2.6.22/drivers/usb/serial/usb-serial.c: USB Serial support registered for GSM modem (1-port) 
[ 1359.068000] option 4-1:1.0: GSM modem (1-port) converter detected 
[ 1359.068000] usb 4-1: GSM modem (1-port) converter now attached to ttyUSB0 
[ 1359.068000] option 4-1:1.1: GSM modem (1-port) converter detected 
[ 1359.072000] usb 4-1: GSM modem (1-port) converter now attached to ttyUSB1 
[ 1359.072000] usbcore: registered new interface driver option 
[ 1359.072000] /build/buildd/linux-source-2.6.22-2.6.22/drivers/usb/serial/option.c: USB Driver for GSM modems: v0.7.1 
bruce@bruce-laptop:~$ [/I]

From other posts I should be able to configure connection but need some guidance with this.
Feel I keep coming up against brick walls but hopefully now getting closer to internet access in ubuntu.

Cheers sunlover

---

### Post by jwwishart on 2008-09-18
Hi,

From the dmesg it seems like it is considered a USB device (Please don't anyone have a go at me as I'm not all that familiar with all this... Weaning myself off Win... :) )

On Hardy I've manage to get the Broadband modem installed using eee-maxon-bp3 which is in the repositories. 

[http://quozl.linux.org.au/bp3-usb/eee.phtml]("http://quozl.linux.org.au/bp3-usb/eee.phtml")

It "may" work if you install that package...

Then from the command line type:

```
sudo bp3config
```

And enter you details when prompted.

I'm not familiar with the modem/router... Hope it may have been of some help!

Hope all goes well!

jwwishart

---

