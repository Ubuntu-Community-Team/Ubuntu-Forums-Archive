---
title: "Internet Connection"
date: 2009-04-02
forum: New to Ubuntu
---

### Post by paul77 on 2009-04-02
Hi, 
   I've just installed ubantu on my PC and need to setup the
internet connection (tiscali adsl broadband). Can someone inform
what I need to do to achieve this - I assume its a case of using the network settings icon.

Thanks

---

### Post by superprash2003 on 2009-04-02
in windows did you require a dialer to connect to the internet? in your terminal type ifconfig and post output here..

---

### Post by paul77 on 2009-04-02
Yes I believe windows uses a dialler to connect to the tiscali
broadband. I have a shortcut its target location is Network
Connections and in here is the dialler.

The properties of the dialler in the general tab says it
'Connects using'
ISDN channel - USB ADSL WAN Adapter

Phone Number: x,y


My ifconfig is as follows:

lo   Link encap: Local Loopback
     inet addr: w.x.y.z   Mask: 255.0.0.0
     UP LOOP BACK RUNNING MTU:16426 Metric:1
     RX packets:0 errors:0 dropped:0 overruns:0 frame:0
     TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
     collisions:0 txqueuelen:0
     RX bytes:0 (0.0b) TX bytes:0 (0.0b)

---

### Post by superprash2003 on 2009-04-03
are you sure this is ADSL? cause ADSL doesnt require any telephone number> Phone Number: x,y

---

### Post by paul77 on 2009-04-03
Yes the dialler refers to ADSL and specifies a telephone number.
ADSL is a broadband over copper wire - presumably the telephone
number identifies the service required.

The modem is Sagem Fast 800 E3 - I've found a ubuntu source identifying it as a USB ADSL modem (Analog Devices Inc. eagle-usb I, II or III chipset)

---

### Post by paul77 on 2009-04-03
I've found the following link:-

[https://help.ubuntu.com/7.04/internet/C/connect-to-internet.html#modems-adsl-usb](https://help.ubuntu.com/7.04/internet/C/connect-to-internet.html#modems-adsl-usb)

Under the section USB ADSL modems

and under item:

2. Modems using the Analog Devices Inc. eagle-usb I, II or III chipset (such as Sagem Fast 800, Comtrend ct 350 etc.)

in link UsbAdslModem/EagleUsb

it says:

The ueagle-atm driver is built into Linux 2.6.16.

As I'm running 2.6.22-14-generic ubuntu (from uname -r) I'm assuming that there is a device driver for the Sagem modem in my kernel and it should be just a case of configuring the network settings.

---

### Post by paul77 on 2009-04-03
If the device driver is present in my kernel - will it still
need installing?

---

### Post by paul77 on 2009-04-03
It looks like I should be able to go striaght to:-

sudo eagleconfig

---

### Post by halitech on 2009-04-03
whats the output of```
lsusb
```

---

### Post by paul77 on 2009-04-03
lsusb's output:-


Bus 005 Device 001: ID 0000:0000
Bus 004 Device 001: ID 0000:0000
Bus 003 Device 001: ID 0000:0000
Bus 002 Device 001: ID 0000:0000
Bus 001 Device 002: ID 1110:9031 Analog Devices Canada Ltd       
                                                (Allied Telesyn)
Bus 001 Device 001: ID 0000:0000


typing:
sudo eagleconfig

outputs:
command not found


I also noticed that when ubuntu comes up there's the following 
output:

eagle_atm requesting firmware. Error failed 2

---

### Post by paul77 on 2009-04-04
So it looks like I have the eagle-atm device driver already installed.

In the help page mentioned above it says the following:

"There are problems with the eagle-usb packages included in Dapper and Breezy (and maybe earlier releases), but the source obtained here works well. It is highly recommended that you use the ueagle-atm driver instead if you are running Edgy or newer, and it is encouraged that you use that in Dapper as well." 

This seems to say that the eagle-atm will support usb based adsl
so I ought to have the approapriate device driver already.

But as its failing to connect to the modem maybe I should install
eagle-usb.

---

### Post by paul77 on 2009-04-04
Had a look at the eagle-usb download link 

[http://dev.eagle-usb.org/wakka.php?wiki=EagleUsb230](http://dev.eagle-usb.org/wakka.php?wiki=EagleUsb230)

and found this info:

"Eagle-usb-2.3.3
Release date : March 1st 2006
You should use ueagle-atm driver (interwiki) if you have a kernel >= 2.6.16
eagle-usb will no longer be properly maintained as ueagle-atm is now included in the linux kernel"


Eagle-usb 2.3.3 was the last release. I'm running 2.6.16-generic
ubuntu so I should be able to use the eagle-atm already in my
linux kernel. But its not connecting. Is ueagle-atm different
from eagle-atm?

---

### Post by paul77 on 2009-04-04
Its 2.6.22-14-generic ubuntu not 2.6.16 as stated so I should
not need eagle-usb.

---

### Post by paul77 on 2009-04-04
lsmod | grep "eagle"

gives the following:-


ueagle_atm 27176  0
usbatm     20864  1 ueagle_atm
usbcore    138632 6 ueagle_atm, usbatm, ethci, hcd, ohci_hcd,
                                                          uhci_hcd 

The modem's power light is on but not the adsl light.
(Under Windows both lights are on.)



typing:

sudo modprobe ueagle-atm

has no effect on the lights on the modem

---

### Post by paul77 on 2009-04-04
I should be able to configure the connection as per the link
above:-

gksudo gedit /etc/ppp/peers/ueagle-atm

And in this file put:

user "<your username>"
password "<your password>"
plugin pppoatm.so <VP>.<VC>
noipdefault
usepeerdns
defaultroute
persist
noauth


But the tiscali password is hidden in the windows internet options connection settings. Is there anyway of determining the password without contacting the provider?

---

