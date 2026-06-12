---
title: "HOWTO: Using Option (Vodafone) 3G PCMCI card in Ubuntu PowerPC"
date: 2005-07-14
forum: Networking &amp; Wireless
---

### Post by eduardgrebe on 2005-07-14
I have been using a Vodafone-branded Option 3G (UMTS) PCMCIA modem in Mac OS X on my Powerbook G4 and had struggled to use it under Hoary PPC. I found an excellent HOWTO for using the card under linux by Tazz_Tux here: [http://mybroadband.co.za/vb/printthread.php?t=21726](http://mybroadband.co.za/vb/printthread.php?t=21726). However, his instructions didn't work immediately on hoary ppc.

I use it with the Vodacom network in South Africa, but you can just replace network-specific items with the relevant info for your network.

First, ensure that your PCMCIA services are running and that the OS is detecting the card when it's inserted. This should work automatically. 

In order for ubuntu to handle the modem correctly and create appropriate aliases you must load the serial_cs module as follows:
```
sudo modprobe serial_cs
```

Then check your syslog to make sure the card is properly initialised. Type the following:
```
sudo tail -f /var/log/syslog
```
When you insert the card, you should see something like the following:
```

Jul 14 23:53:48 localhost kernel: ohci_hcd 0001:11:00.0: OPTi Inc. 82C861 (#3)
Jul 14 23:53:48 localhost kernel: ohci_hcd 0001:11:00.0: irq 53, pci mem 0xf3000000
Jul 14 23:53:48 localhost kernel: ohci_hcd 0001:11:00.0: new USB bus registered, assigned bus number 5
Jul 14 23:53:48 localhost kernel: ohci_hcd 0001:11:00.0: WARNING: OPTi workarounds unavailable
Jul 14 23:53:48 localhost kernel: hub 5-0:1.0: USB hub found
Jul 14 23:53:48 localhost kernel: hub 5-0:1.0: 2 ports detected
Jul 14 23:53:49 localhost pci.agent[13878]:      ohci-hcd: already loaded
Jul 14 23:53:49 localhost usb.agent[13922]:      usbcore: already loaded
Jul 14 23:53:56 localhost kernel: usb 5-1: new full speed USB device using ohci_hcd and address 2
Jul 14 23:53:56 localhost kernel: usbserial_generic 5-1:1.0: Generic converter detected
Jul 14 23:53:56 localhost kernel: usb 5-1: Generic converter now attached to ttyUSB0
Jul 14 23:53:56 localhost kernel: usbserial_generic 5-1:1.1: Generic converter detected
Jul 14 23:53:56 localhost kernel: usb 5-1: Generic converter now attached to ttyUSB1
Jul 14 23:53:56 localhost kernel: usbserial_generic 5-1:1.2: Generic converter detected
Jul 14 23:53:56 localhost kernel: usb 5-1: Generic converter now attached to ttyUSB2
```

You now have a generic USB modem set up at /dev/ttyUSB0.

Let's use wvdial to handle the ppp connection. Edit/create /etc/wvdial.conf. Mine is as follows:

```

[Dialer Defaults]

Phone = *99***1#
Username = username
Password = password
Stupid Mode = 1
Dial Command = ATDT

[Dialer pin]

Init1 = AT+CPIN=1234

[Dialer option]

Modem = /dev/ttyUSB0
Baud = 460800
Init2 = ATZ
Init3 = ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
ISDN = 0
Modem Type = Analog Modem

[Dialer 2gonly]

Init4 = AT+COPS=0,0,"Vodacom-SA",0

[Dialer 3gonly]

Init4 = AT+COPS=0,0,"Vodacom-SA",2

[Dialer internet]

Init5 = AT+CGDCONT=1,"IP","internet";

[Dialer internetvpn]

Init5 = AT+CGDCONT=1,"IP","internetvpn";

[Dialer myapn]

Init5 = AT+CGDCONT=1,"IP","myapn"

[Dialer 384k]

Init6 = AT+CGEQMIN=1,4,64,384,64,384
Init7 = AT+CGEQREQ=1,4,64,384,64,384

[Dialer 144k]

Init6 = AT+CGEQMIN=1,4,64,144,64,144
Init7 = AT+CGEQREQ=1,4,64,144,64,144

[Dialer 64k]

Init6 = AT+CGEQMIN=1,4,64,64,64,64
Init7 = AT+CGEQREQ=1,4,64,64,64,64


```

You will need to change some of the settings in the file according to your local network. I think the phone number *99***1# is used by all networks for packet switched data, but check with your network. Importantly, you must replace the digits 1234 in the [pin] section with your sim card's PIN. The sections [Dialer internet], [Dialer myapn] and [Dialer myapn] sets up three APNs used by the Vodacom network. Again, check with your network, but "internet" is likely to work.

Once you've configured wvdial, you can use it to establish the ppp connection. You can call sections of wvdial.conf in the command line. 

However, here I experience an irritating problem. The Option card takes about 10 seconds or so after being passed the PIN before it is ready to dial (you can see when it's ready because the green LED will stop flashing, leaving only the blue LED flashing). My wvdial tries to dial before the modem is ready and the ppp connection fails. I therefore run the following, but must press control-C and and run the dialer again before it works.

```

wvdial pin option internet 3gonly 384k
(press ^C after the PIN has been passed to the modem, wait until green LED stops flashing)
wvdial option internet 3gonly 384k

```

Ideally, one should tell wvdial to wait 10 seconds between running the [pin] section and the rest, but I don't know how to do this. Another alternative is to run a terminal app like minicom and manually pass AT+CPIN=1234 to the modem before running wvdial (without the pin flag).

If you want to dial again later without having unplugged the modem, you can use only:

```

wvdial option internet 3gonly 384k

```

It is a good idea to switch off the card before unplugging by typing
```

sudo cardctl eject

```

---

### Post by theouys on 2007-08-05
Hi I'm having problems with the initialization of the card. I'm running on Ubuntu 7.04
When inserting the card after I've done what you guys have told me to do on this specific discussion, my system.log file have the following lines:

Aug  5 23:44:53 theo-laptop kernel: [  236.060000] PCI: Enabling device 0000:03:00.0 (0000 -> 0002)
Aug  5 23:44:53 theo-laptop kernel: [  236.060000] ACPI: PCI Interrupt 0000:03:00.0[A] -> Link [LNKE] -> GSI 11 (level, low) -> IRQ 11
Aug  5 23:44:53 theo-laptop kernel: [  236.060000] nozomi 0000:03:00.0: Nozomi driver nozomi_tty
Aug  5 23:44:53 theo-laptop NetworkManager: <debug info>^I[1186350293.281546] nm_hal_device_added (): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_1931_c'). 
Aug  5 23:44:53 theo-laptop NetworkManager: <debug info>^I[1186350293.282157] nm_hal_device_added (): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_1931_c_serial_unknown_0'). 
Aug  5 23:44:53 theo-laptop NetworkManager: <debug info>^I[1186350293.282693] nm_hal_device_added (): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_1931_c_serial_unknown_1'). 
Aug  5 23:44:53 theo-laptop NetworkManager: <debug info>^I[1186350293.283209] nm_hal_device_added (): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_1931_c_serial_unknown_2'). 
Aug  5 23:44:53 theo-laptop NetworkManager: <debug info>^I[1186350293.283782] nm_hal_device_added (): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_1931_c_serial_unknown_3'). 
Aug  5 23:44:53 theo-laptop kernel: [  236.700000] nozomi 0000:03:00.0: Version of card: 3
Aug  5 23:44:53 theo-laptop kernel: [  236.700000] nozomi 0000:03:00.0: Initialization OK!

---

