---
title: "USB Belkin wireless? Which FAQ do I follow in Feisty?"
date: 2007-04-16
forum: Networking &amp; Wireless
---

### Post by drifting on 2007-04-16
I am a little confused, I originally tried this with 6.10 but gave up! Know with Feisty it can see the USB Belkin wireless pen fine, I can use wireless radar and see loads of ap's. I have even managed to to get it to connect with Radar. However not when I start the machine up? I use WPA, and it keeps asking for a keyring password?
Also it only connects at 11Mbits rather than the 54 it should be?

Anyone point me at the relevant how to? As I would prefer a direct connection without messing with the Radar program.

Paul.

---

### Post by joeally on 2007-04-16
Follow this tutorial.
[http://ubuntuforums.org/showthread.php?t=400236]("http://ubuntuforums.org/showthread.php?t=400236")

the second page has the bit about wpa on I havn't tried it yet(I use WEP even if it is hackable)

Hope I have helped

---

### Post by drifting on 2007-04-16
Thanks, read the thread, but not sure what I need to put in for driver on teh wpa-driver part?            

lshw produced this: -

  *-usb
                   description: Generic USB device
                   product: USB2.0 WLAN
                   vendor: Belkin
                   physical id: 5
                   bus info: usb@5:5
                   version: 48.10
                   capabilities: usb-2.00
                   configuration: driver=zd1211rw maxpower=500mA speed=480.0MB/s

So I entered wpa-driver zd1211rw ?

Think I have lost the plot here, and the will to live :(

Paul.

---

### Post by Floppyjoe on 2007-04-16
> **drifting said:**
> Thanks, read the thread, but not sure what I need to put in for driver on teh wpa-driver part?            

lshw produced this: -

  *-usb
                   description: Generic USB device
                   product: USB2.0 WLAN
                   vendor: Belkin
                   physical id: 5
                   bus info: usb@5:5
                   version: 48.10
                   capabilities: usb-2.00
                   configuration: driver=zd1211rw maxpower=500mA speed=480.0MB/s

So I entered wpa-driver zd1211rw ?

Think I have lost the plot here, and the will to live :(

Paul.
This is a list of drivers that WPA Supplicant uses:
> drivers:
  hostap = Host AP driver (Intersil Prism2/2.5/3)
  madwifi = MADWIFI 802.11 support (Atheros, etc.)
  atmel = ATMEL AT76C5XXx (USB, PCMCIA)
  wext = Linux wireless extensions (generic)
  ndiswrapper = Linux ndiswrapper
  ipw = Intel ipw2100/2200 driver
  wired = wpa_supplicant wired Ethernet driver
  test = wpa_supplicant test driver


---

### Post by drifting on 2007-04-17
> **Floppyjoe said:**
> This is a list of drivers that WPA Supplicant uses:

Ok......So which do I use with the Belkin USB?

Paul.

---

