---
title: "Gutsy and zd1211rw driver"
date: 2008-03-05
forum: Networking &amp; Wireless
---

### Post by SeiShonagon on 2008-03-05
Hi, I've just bought a zd1211rw based usb wifi receiver (Air Live brand)
Plugged it in my 7.04 distro, worked "out of the box", like a charm.
Ubuntu offered to upgrade to 7.10, I said yes, and now ... no network.

The device is recognized in System/Preference/Hardware Information as a usb2.0 wlan device  from ZyDAS

lsusb gives me 
Bus 001 Device 007 ID 0ace:1215 ZyDas

lsmod gives me
usbcore    136088   11 zd1211rw ...

lshw doesn't give any results

and wicd says

that there is no "Wireless Interface"

iwconfig yields : 
lo   no wireless extension
eth0 no wireless extension


I don't know what to do ... can any body help?

THanks

---

### Post by jeffus_il on 2008-03-05
what does dmesg have to say?

---

### Post by SeiShonagon on 2008-03-05
When I reconnect the usb antenna and do dmesg, it tells me : 

usb 1-5: Could not load firmware file zd1211/zd1211b_ub. Error number -2
zd1211rw 1-5:1.0: couldn't load firmware. Error number -2
uusb 1-5: reset high speed usb device using ehci_hcd and address 10
zd1211rw: probe of 1-5:1.0 failed with error number -2



Doesn't look good, does it ?
Should I try to recompile the zd1211 drivers from source ?

Thnx

---

### Post by jeffus_il on 2008-03-06
You are missing firmware for the driver. Will get back to you later about how to find and install it. You can try in the meantime to google "zd1211rw firmware ubuntu", Also you can do ```
sudo updatedb
``` and then ```
locate zd1211rw
``` to find the firmware which may be on your machine but installed in an older kernel version. This file has to them be copied to the current kernel's firmware directory.

---

### Post by SeiShonagon on 2008-03-06
thx,

did a little rooting around, and found zd1211 firmware updates on sourceforge, untarred them into the /lib/firmware/zd1211 directory

rebooted, no joy

copied to /lib/firmware/2.6.22-14-386/zd1211
rebooted, no joy

found somewhere else something about using the rt image, installed those packages, no joy

and the locate command does give me some results inside "drivers" directories.

hmm...

---

### Post by jeffus_il on 2008-03-06
I would double check 2 things:
[LIST=1]
[*]If the version of the firmware you have installed matches the version of the driver you have, the best thing may be to try to find a package that contains the driver and matching firmware.
[*]The location of the firmware folder, that is is this the folder the system searches in for the firmware.[/LIST]

---

### Post by SeiShonagon on 2008-03-20
Sorry to come back late, was away.
I'm not sure how to check those two things. Where would I find said package? and how can I make sure the firmware folder is correct ?

---

