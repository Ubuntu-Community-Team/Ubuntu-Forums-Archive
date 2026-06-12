---
title: "hotsync w/ palm treo 700p?"
date: 2010-02-19
forum: New to Ubuntu
---

### Post by hortstu on 2010-02-19
I followed this tutorial I found during a search but I'm still not getting a sync with jpilot.  

[https://help.ubuntu.com/community/PalmDeviceSetup](https://help.ubuntu.com/community/PalmDeviceSetup)

Should I be trying something other than jpilot? Is there anything more similar to outlooks address book?

Anyway I followed the directions through number 5 but I'm still not syncing.  This part at the end here has me confused... not quite sure what to do with it...

> 

See if newer "PalmOne", Handspring, or Treo devices have different product names, requiring more lines in the file.


See if ttyUSB* is good enough for the majority, or if we need to use ttyUSB[13579]. 

---

### Post by hortstu on 2010-02-19
really trying to dump windows all together.

I still have xp but only on rarely used desktop.  Getting this phone to sync in linux will get me one step closer.

Even a suggestion of a better place to ask this question will be great.

---

### Post by NUboon2Age on 2010-06-22
It appears I've got it working.  Details:

Lucid, Palm 700p, USB cable/cradle

1) **Purged** (aka Synaptic "completely remove") **modemmanager** package (because otherwise I was getting continous Palm resets (see Bug #421673).
2) **Removed visor from /etc/module file** (not there by default, I'd added when experimenting earlier) 
Note the visor module conflicts with libusb  which appears to have been available from Jaunty onward.

My settings in **gnome-pilot**:

- Devices tab:
  - Name: Cable, you may choose what you like.
  - **Type: USB**
  - Timeout: 2 
  - **Device: usb: **
  - Speed: 115200 (not default -- don't know if this is vital, but it worked for me)

---

