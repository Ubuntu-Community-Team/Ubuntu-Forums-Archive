---
title: "[SOLVED] Trying to use my mobile phone as a modem (with no success)"
date: 2008-04-04
forum: Networking &amp; Wireless
---

### Post by vdalmonte on 2008-04-04
I'm using Gutsy (7.10). After trying several guides to connect to the Internet using my mobile phone as a modem, I tried this one: 
[http://wiki.ubuntu-it.org/Hardware/Modem/CellulareGprsUmtsUsb](http://wiki.ubuntu-it.org/Hardware/Modem/CellulareGprsUmtsUsb)
and I finally got to something: My phone no longer complains about settings being wrong and according to the wvdial messages I 'should be' connected to the Internet
It's not in English but the commands are the same by the way. I think there's an equivalent in the English documentation.
By the way, I followed the above guide step-by-step.
This is the wvdial "log":

WvDial<*1>: WvDial: Internet dialer version 1.56
WvModem<*1>: Cannot get information for serial port.
WvDial<*1>: Initializing modem.
WvDial<*1>: Sending: AT+CGDCONT=1,"IP","internet.wind","",0,0
WvDial Modem<*1>: AT+CGDCONT=1,"IP","internet.wind","",0,0
WvDial Modem<*1>: OK
WvDial<*1>: Modem initialized.
WvDial<*1>: Sending: ATDT*99***1#
WvDial<*1>: Waiting for carrier.
WvDial Modem<*1>: ATDT*99***1#
WvDial Modem<*1>: CONNECT
WvDial Modem<*1>: ~[7f]}#@!}!}!} }8}#}$@#}(}"}'}"}"}&} } } } }%}&>m=}?[12]w~
WvDial<*1>: Carrier detected.  Waiting for prompt.
WvDial Modem<*1>: ~[7f]}#@!}!}"} }8}#}$@#}(}"}'}"}"}&} } } } }%}&>m=}?Xe~
WvDial<*1>: PPP negotiation detected.
WvDial<Notice>: Starting pppd at Fri Apr  4 06:42:03 2008
WvDial<Notice>: Pid of pppd: 5871
WvDial<*1>: Using interface ppp0
WvDial<*1>: local  IP address 151.83.3.7
WvDial<*1>: remote IP address 10.64.64.64
WvDial<*1>: primary   DNS address 193.70.152.25
WvDial<*1>: secondary DNS address 193.70.192.25

When I type in any web site's address, in Firefox's bar I can read "Looking up" followed by the web site's address and the page won't run. I tried to wait a while, for the connection to get "stabilized" as it's suggested in the guide but pages won't just load.
What else can I do?
Furthermore I noticed when I'm using a wireless or ethernet connection and I plug in the USB phone cable my wireless/ethernet connection is lost until I unplug it and reboot
Can someone help?
I'm totally new to Ubuntu

---

### Post by firedrow on 2008-04-04
Well, what kind of phone for you have and who is your service provider.  I am using a Samsung Blackjack with WM6 from AT&T.  Mine tethers just fine.  In fact I use it when I am on a service call and can't jack into customers networks.  I can use wvdial in console, or I also have gnome-ppp configured.  Let me post my WVDIAL.CONF config:

```
[Dialer pulse]
Dial Command = ATDP

[Dialer shh]
Init3 = ATM0

[Dialer Defaults]
Init1 = ATZ
Init2 = ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
Init3 = AT+CGDCONT=1,"IP"."WAP.CINGULAR"
Phone = *99#
Modem Type = USB Modem
Stupid Mode = on
Auto DNS = 1
Baud = 115200
Modem = /dev/ttyACM0
Init = ATZ
ISDN = 0
Username = WAP@CINGULARGPRS.COM
Password = CINGULAR1
Carrier Check = no
Auto Reconnect = on
```

Also, here are my Gnome-PPP settings:

Username: [email]WAP@CINGULARGPRS.COM[/email]
Password: CINGULAR1
Phone Number *99#
Device: /dev/ttyACM0
Type: USB Modem
Speed: 115200
Phone Line: Tone
Volume: High
For the INIT strings, use the ones from the WVDIAL.CONF

Also, you might go through [[COLOR="DarkOrange"]this thread[/COLOR]]("http://ubuntuforums.org/showthread.php?t=343989&page=3").  It's where I got all the info I needed to get my BlackJack working.  It's got things on lots of the big companies, Sprint, AT&T, Verizon, etc.

---

### Post by vdalmonte on 2008-04-05
Phone is SonyEricsson K618i and provider is Wind (Italy). In Windows I don't have to add any particular commands, besides no username and no password (blank) (may that cause problems?) and, just if I didn't set it up in the phone, I may add the ONLY Init string AT+CGDCONT=1,"internet.wind","",0,0
Also the phone number I used in Windows is *99***1#

after typing wvdial the phone acts like it 's connected or so it seems.

wvdial.conf

[Dialer defaults]
Modem = /dev/ttyUSB0 # I tried the USB as with ACM0 my phone said wrong configuration etc.
Baud = 115200
Init = AT+CGDCONT=1,"internet.wind","",0,0
Carrier check = no
Phone = *99***1#
Username = ininfluent
Password = ininfluent

---

### Post by firedrow on 2008-04-05
Bring up a console/terminal window, plugin your phone and then type 'dmesg'.  Send me the last 5 lines or so of that output.

Try this in your wvdial.conf:

```

[Dialer Defaults]
Modem = /dev/ttyACM0
Baud = 460800
Init = ATZ0
Init2 = AT Q0 V1 E0 S0=0 &C1 &D2 +FCLASS=0
Init3 = AT+CGDCONT=1,"IP","internet.wind","",0,0
Modem Type = Analog Modem
Carrier Check = no
Phone = *99***1#
Username = ininfluente
Password = ininfluente

```


Also, I was reading over your original post.  You shouldn't have a wired or wireless connection when you try to use your phone as a modem.  Otherwise your run into a problem of multiple default gateways, which maybe why you're not able to get online once the phone seems connected.  Try killing all internet connections then run your phone as a modem.  See if that makes a difference.

---

### Post by vdalmonte on 2008-04-05
-I added a # in the /etc/modprobe.d/options file so that it looks like this now:

```
options hostap_pci iw_mode=2
options hostap_cs iw_mode=2

#options usbserial vendor=0x0fce product=0xdo46
```

-removed the blacklist for the cdc_acm driver in the /etc/modprobe.d/blacklist file

```
#blacklist cdc_acm
```

-rebooted the computer

in order to be able to use ttyACM0 again instead of ttyUSB0.

I modified the wvdial.conf as suggested

[EDIT] plugged the phone in and typed dmesg[/EDIT]

These are the last lines of the dmesg output now

```
[   24.132000] apm: BIOS not found.
[   24.652000] Bluetooth: Core ver 2.11
[   24.652000] NET: Registered protocol family 31
[   24.652000] Bluetooth: HCI device and connection manager initialized
[   24.652000] Bluetooth: HCI socket layer initialized
[   24.672000] Bluetooth: L2CAP ver 2.8
[   24.672000] Bluetooth: L2CAP socket layer initialized
[   24.840000] Bluetooth: RFCOMM socket layer initialized
[   24.840000] Bluetooth: RFCOMM TTY layer initialized
[   24.840000] Bluetooth: RFCOMM ver 1.8
[   28.036000] [drm] Initialized drm 1.1.0 20060810
[   28.040000] ACPI: PCI Interrupt 0000:00:02.0[A] -> GSI 16 (level, low) -> IRQ 21
[   28.044000] [drm] Initialized i915 1.6.0 20060119 on minor 0
[  447.720000] usb 1-2: new full speed USB device using uhci_hcd and address 2
[  447.900000] usb 1-2: configuration #3 chosen from 1 choice
[  448.812000] cdc_acm 1-2:3.1: ttyACM0: USB ACM device
[  448.812000] cdc_acm 1-2:3.3: ttyACM1: USB ACM device
[  448.816000] usbcore: registered new interface driver cdc_acm
[  448.816000] /build/buildd/linux-source-2.6.22-2.6.22/drivers/usb/class/cdc-acm.c: v0.25:USB Abstract Control Model driver for USB modems and ISDN adapters
[  448.924000] usb0: register 'cdc_ether' at usb-0000:00:1d.0-2, CDC Ethernet Device, 02:80:37:05:03:00
[  448.924000] usbcore: registered new interface driver cdc_ether
```

[EDIT]
I also tried running wvdial and these are the messages I got:

```
WvDial<*1>: WvDial: Internet dialer version 1.56
WvModem<*1>: Cannot get information for serial port.
WvDial<*1>: Initializing modem.
WvDial<*1>: Sending: ATZ0
WvDial Modem<*1>: ATZ0
WvDial Modem<*1>: ERROR
WvDial<Err>: Bad init string.
WvModem<*1>: Cannot get information for serial port.
WvDial<*1>: Initializing modem.
WvDial<*1>: Sending: ATZ0
WvDial Modem<*1>: ATZ0
WvDial Modem<*1>: ERROR
WvDial<Err>: Bad init string.
WvModem<*1>: Cannot get information for serial port.
WvDial<*1>: Initializing modem.
WvDial<*1>: Sending: ATZ0
WvDial Modem<*1>: ATZ0
WvDial Modem<*1>: ERROR
WvDial<Err>: Bad init string.
```

Obviously at this time the phone didn't react at all.

Just to make sure the phone works I connected to the Internet using it in Windows.

[/EDIT]

---

### Post by firedrow on 2008-04-08
> **vdalmonte said:**
> 

These are the last lines of the dmesg output now

```
[   24.132000] apm: BIOS not found.
[   24.652000] Bluetooth: Core ver 2.11
[   24.652000] NET: Registered protocol family 31
[   24.652000] Bluetooth: HCI device and connection manager initialized
[   24.652000] Bluetooth: HCI socket layer initialized
[   24.672000] Bluetooth: L2CAP ver 2.8
[   24.672000] Bluetooth: L2CAP socket layer initialized
[   24.840000] Bluetooth: RFCOMM socket layer initialized
[   24.840000] Bluetooth: RFCOMM TTY layer initialized
[   24.840000] Bluetooth: RFCOMM ver 1.8
[   28.036000] [drm] Initialized drm 1.1.0 20060810
[   28.040000] ACPI: PCI Interrupt 0000:00:02.0[A] -> GSI 16 (level, low) -> IRQ 21
[   28.044000] [drm] Initialized i915 1.6.0 20060119 on minor 0
[  447.720000] usb 1-2: new full speed USB device using uhci_hcd and address 2
[  447.900000] usb 1-2: configuration #3 chosen from 1 choice
[  448.812000] cdc_acm 1-2:3.1:[COLOR="Red"] ttyACM0[/COLOR]: USB ACM device
[  448.812000] cdc_acm 1-2:3.3:[COLOR="Red"] ttyACM1[/COLOR]: USB ACM device
[  448.816000] usbcore: registered new interface driver cdc_acm
[  448.816000] /build/buildd/linux-source-2.6.22-2.6.22/drivers/usb/class/cdc-acm.c: v0.25:USB Abstract Control Model driver for USB modems and ISDN adapters
[  448.924000] usb0: register 'cdc_ether' at usb-0000:00:1d.0-2, CDC Ethernet Device, 02:80:37:05:03:00
[  448.924000] usbcore: registered new interface driver cdc_ether
```


Ok, well dmesg shows ACM0 and ACM1 as new devices.  So based on your messages that the ATZ0 init string doesn't work, lets remove that string and Init2.  Make Init3 your Init once again.  In otherwords, go back to your original config but with ttyACM0.  If it doesn't work, try changing the modem to ttyACM1 also.

```

[Dialer defaults]
Modem = /dev/ttyACM0
Baud = 115200
Init = AT+CGDCONT=1,"internet.wind","",0,0
Carrier check = no
Phone = *99***1#
Username = ininfluent
Password = ininfluent

```

Out of curiousity, why didn't you put Init or Init2 in the original config?  Your site you had listed had an Init and Init2 string, but you only had Init3 listed as your Init string.

---

### Post by vdalmonte on 2008-04-09
I used the Inits as reported in the guide but my phone/modem doesn't react to ATZ0

by the way, I don't know exactly how but after changing wvdial.conf to this

```
[Dialer Defaults]
Modem = /dev/ttyACM0
Baud = 460800
Init = AT S7=45 S0=0 V1 X4 &c1 E0
Init2 = AT+CGDCONT=1,"IP","internet.wind","",0,0
Modem Type = Analog Modem
Carrier Check = no
Phone = *99***1#
Username = whatever	
Password = whatever
```

and opening a console/terminal then typing wvdial now it works

A friend of mine had suggested to install KMobileTools
After I installed it I realized it had nothing to do with my problem;
although after selecting my phone brand from within KMobileTools I got
the initialization string AT S7=45 S0=0 V1 X4 &c1 E0
So I said to myself "why not?" and that's it

---

