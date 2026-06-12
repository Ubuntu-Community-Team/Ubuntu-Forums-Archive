---
title: "Can't blacklist islsm, etc"
date: 2007-01-22
forum: Networking &amp; Wireless
---

### Post by EnterDaMatrix on 2007-01-22
For some reason even though I have them in /etc/modprobe.d/blacklist the modules islsm_usb and islsm keep loading every boot. I have a Netgear WG111v1. After every boot I have to type this to get internet to work:

```
sudo modprobe -r islsm_usb
sudo modprobe -r islsm
sudo modprobe -r ndiswrapper
sudo modprobe ndiswrapper
```

My /etc/modprobe.d/blacklist is this:

```
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

blacklist islsm
blacklist lslsm_usb

```

Drivers work fine with ndiswrapper, just whatever I do the old drivers load no matter what...

---

### Post by EnterDaMatrix on 2007-01-22
Oh wow. Nevermind. Sorry for the waste of a thread. I just caught the mistake where I had lslsm_usb with an l. I feel dumb now. Anyway sorry again for the dumbass thread.  Please delete if you're a mod.

---

