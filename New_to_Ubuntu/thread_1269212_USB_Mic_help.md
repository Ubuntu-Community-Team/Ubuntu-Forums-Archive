---
title: "USB Mic help?"
date: 2009-09-18
forum: New to Ubuntu
---

### Post by Steelsteve on 2009-09-18
ok, i just bought a Dynex DX-USBMIC USB microphone and i know it says that it's compatible with windows NTFS version OSs and Macs, but what about linux? is there some nessicary ackages i need to install to allow for USB microphones to be used?

---

### Post by Steelsteve on 2009-09-18
post for attention..

---

### Post by Bölvaður on 2009-09-18
hmm yes I guess 15 hours is on a gray zone between wite (ok to bump) or black (too soon to bump). But it is on the darker side I would guess.


I cannot see why any usb micraphone wouldnt work out of the box. If you have more mics you might want to use *pulse device chooser* to select which program uses which mic.

It is not obvious how this program works so ask if you need help (if google didnt tell you the answer already)

---

### Post by Steelsteve on 2009-09-27
ok, you're right, pulseaudio does not help at all... anyone else have an idea?

---

### Post by Belizeian on 2010-02-02
I got one as well and can't get it to work
if I disconect and reconect I get following when I run dmesg


[11217.267276] usb 2-3: USB disconnect, address 2
[11228.582548] usb 2-3: new full speed USB device using ohci_hcd and address 7
[11228.809422] usb 2-3: configuration #1 chosen from 1 choice

---

### Post by CitizenJimserac on 2012-08-31
Same problem, Dynex mike with USB interface on Ubuntu studio 12.04 - but after some experimenting, the following, typed in a terminal box, DOES work:

arecord -f cd -D plughw:1,0 -d 20 test.ogg

whereas this did NOT...

arecord -f cd -D hw:1,0 -d 20 test.ogg

---

### Post by oldos2er on 2012-08-31
Please start a new thread, this one's three years old.

---

