---
title: "Onboard sound help"
date: 2009-01-29
forum: New to Ubuntu
---

### Post by Irishbmx on 2009-01-29
Hello hopefully this will be my last problem :)

The sound works but I get allot of static and fuzzy sound esp when playing eve online.

It's onboard sound for the xfx 8200 mb amd 64 x2 4500+ I haven't changed anything with the sound from default cause I can't find a good answer on what to do anywhere and I am extremely nub to ubuntu.

If you have any Ideas can you please be as detailed as possible :) I'm dumb.

And thank you for your time.

---

### Post by cwsnyder on 2009-01-29
'Static and fuzzy sound' points to a problem with the speakers or connections rather than the computer/sound card/software.

---

### Post by cariboo on 2009-01-29
I would suggest you check and see if the PC speaker is black listed. Press Alt-F2 and type:

---

### Post by cariboo on 2009-01-29
I would suggest you check and see if the PC speaker is black listed. Press Alt-F2 and type:

```
gksu gedit /etc/modprobe.d/blacklist
```

at the bottom of the file you should see something like this:

```
# low-quality, just noise when being used for sound playback, causes
# hangs at desktop session start (Ubuntu: #246969)
blacklist snd_pcsp
```

If it isn't there add it to the bottom of the file.

Jim

---

### Post by Irishbmx on 2009-01-29
> **cariboo907 said:**
> I would suggest you check and see if the PC speaker is black listed. Press Alt-F2 and type:

```
gksu gedit /etc/modprobe.d/blacklist
```

at the bottom of the file you should see something like this:

```
# low-quality, just noise when being used for sound playback, causes
# hangs at desktop session start (Ubuntu: #246969)
blacklist snd_pcsp
```

If it isn't there add it to the bottom of the file.

Jim
# This file lists those modules which we don't want to be loaded by
# alias expansion, usually so some other driver will be loaded for the
# device instead.

# evbug is a debug tool that should be loaded explicitly
blacklist evbug

# these drivers are very simple, the HID drivers are usually preferred
blacklist usbmouse
blacklist usbkbd

# replaced by e100
blacklist eepro100

# replaced by tulip
blacklist de4x5

# causes no end of confusion by creating unexpected network interfaces
blacklist eth1394

# snd_intel8x0m can interfere with snd_intel8x0, doesn't seem to support much
# hardware on its own (Ubuntu bug #2011, #6810)
blacklist snd_intel8x0m

# causes failure to suspend on HP compaq nc6000 (Ubuntu: #10306)
blacklist i2c_i801

# replaced by p54pci
blacklist prism54

# replaced by b43 and ssb.
blacklist bcm43xx

# most apps now use garmin usb driver directly (Ubuntu: #114565)
blacklist garmin_gps

# replaced by asus-laptop (Ubuntu: #184721)
blacklist asus_acpi
 Is what I got I don't understand any of it lol

Anyway it's a headset not speakers but I tryd another headset and my speakers it does it on all of them it's not constant static or fuzz it's only when I'm doing something like playing eve online ect and it's choppy as well sound gets fuzzy then cuts out for a split sec.

also sometimes gets fuzz on vent but not really bad, and my mic doesn't work :(

---

### Post by Irishbmx on 2009-02-05
anyone else have any Ideas? Tryd a different headset and a couple different speakers. The sound works it just gets choppy when I play eve and sometimes when I play music ect and the mic doesn't work.

---

