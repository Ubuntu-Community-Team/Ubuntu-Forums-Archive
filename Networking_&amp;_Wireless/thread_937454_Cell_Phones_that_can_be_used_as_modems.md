---
title: "Cell Phones that can be used as modems"
date: 2008-10-03
forum: Networking &amp; Wireless
---

### Post by evilgold on 2008-10-03
By pretty much random chance i ended up finding out that my girlfriends crappy $40 cell phone could easily be used as a modem with both ubuntu and debian sid (probably lenny too). 

I ended up coming across a usb cable that happed to fit the phone her phone while i was at freegeek the other day...after throwing down a whole 10 cents for it (im sure they cost more online), I got it home and just used it as an extra charger for probably a good 2 weeks before i even thought "i wonder if i can do anything else with this thing"... so i check dmesg after plugging it in one day and i notice:

```

[90831.676147] usb 4-2: new full speed USB device using uhci_hcd and address 6
[90831.877300] usb 4-2: configuration #2 chosen from 1 choice
[90831.887411] cdc_acm 4-2:2.1: ttyACM0: USB ACM device
[90831.896009] usb 4-2: New USB device found, idVendor=04e8, idProduct=663e
[90831.896017] usb 4-2: New USB device strings: Mfr=1, Product=2, SerialNumber=3
[90831.896017] usb 4-2: Product: SAMSUNG Mobile USB Modem
[90831.896017] usb 4-2: Manufacturer: Samsung
[90831.896017] usb 4-2: SerialNumber: 357771-01-219975

```

Specifically the part about "SAMSUNG Mobile USB Modem"

So since happend to have access to a test dial up account, i loaded up wvdial, and sure enough i was able to connect without any problems. I also tested it with gnome-ppp which also worked.

Anywho, the model of the phone is T219S. It was the cheapest one they had at the store which we ended up getting because her previous phone had  broken. So for $40 we ended up with a Linux compatible hardware modem as well as an okay cell phone.

Does anyone else know of other (preferably cheap) models that may do this? Or a good resource for finding this information?

---

### Post by andocmdo on 2009-02-09
Words cannot express my gratitude to you my friend! I've just been searching all over the internet for a good phone to use as a modem, and low and behold, didn't even think of searching for the one that I own, and has a cracked screen! Thank you a million times for posting this!

---

### Post by evilgold on 2009-02-09
> **andocmdo said:**
> Words cannot express my gratitude to you my friend! I've just been searching all over the internet for a good phone to use as a modem, and low and behold, didn't even think of searching for the one that I own, and has a cracked screen! Thank you a million times for posting this!

Glad to hear it :-D

---

### Post by andocmdo on 2009-02-10
Now that I'm searching for the cable, do you have any suggestions as to which usb cable to use? Do you know which one you have? I've found quite a few different ones so far, but I'm not too sure which would be best. Any help would be greatly appreciated. Thanks again.

perhaps this one?
[http://www.susteen.com/productdetail/302/producthl/Notempty]("http://www.susteen.com/productdetail/302/producthl/Notempty")

---

### Post by evilgold on 2009-02-10
> **andocmdo said:**
> Now that I'm searching for the cable, do you have any suggestions as to which usb cable to use? Do you know which one you have? I've found quite a few different ones so far, but I'm not too sure which would be best. Any help would be greatly appreciated. Thanks again.

perhaps this one?
[http://www.susteen.com/productdetail/302/producthl/Notempty]("http://www.susteen.com/productdetail/302/producthl/Notempty")

Well i got mine at the local FreeGeek, just by luck i happended to be recycling cables and noticed one that fit the phone. The one you found looks like it would work. I think as long as its the right size for the phone it should be fine.

---

### Post by andocmdo on 2009-02-10
Thanks for all the help!

---

