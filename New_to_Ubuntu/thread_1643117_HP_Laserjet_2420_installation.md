---
title: "HP Laserjet 2420 installation"
date: 2010-12-11
forum: New to Ubuntu
---

### Post by lake59 on 2010-12-11
I installed Ubuntu about 6 weeks ago and have been impressed with the functionality and GUIness  I have decided to continue this adventure leaving my desire for Windows 7 in the dust.

Here is my current challenge:  Ubuntu 10.10 automatically installed my HP Laserjet 2420 printer without problem and I began to use it.  Well done!  Unfortunately i shortly found that some functionality was missing.  I found hplip 3.10.9 that lists my missing functionality as being fixed!  But when i installed 3.10.9, I received an error indicating 6 missing dependencies.  I embraced the opportunity to learn more about Ubuntu!  After many hours of fishing and trial/error, i now am only missing 4 dependencies.  But the joy for learning opportunities is waning and so am compelled to ask for help (if i wasn't so hard-headed, I would have asked some days ago).  Here is the current error (below).  Your advice/encouragement will be hugely appreciated!
[INDENT]warning: There are 4 missing REQUIRED dependencies.
note: Installation of dependencies requires an active internet connection.
warning: Missing REQUIRED dependency: libusb (libusb - USB library)
warning: This installer cannot install 'libusb' for your distro/OS and/or version.
error: Installation cannot continue without this dependency. Please manually install this dependency and re-run this installer.
[/INDENT]

---

### Post by khelben1979 on 2010-12-11
[libusb - available source code]("http://sourceforge.net/projects/libusb/files/libusb-1.0/").

[libusb packages - packages.ubuntu.com]("http://packages.ubuntu.com/search?keywords=libusb&searchon=names&suite=lucid&section=all").

By this you either can choose to download the source code and install that into the system (not to recommend for newbies!) or get the packages by the Ubuntu system (recommended!).

Packages can sometimes have a version number attached to the packages you're looking for. Use [Ubuntu Software Center]("http://en.wikipedia.org/wiki/Ubuntu_Software_Center") to find what you're looking for.

---

### Post by lake59 on 2010-12-11
Thanks Lenny!  Since I *am* a newbie, i selected the second link.  But how do I know which version to use?  And why can't I find libusb in the "Ubuntu Software Center"?  Thanks!

---

### Post by Geoff918 on 2010-12-11
I would try "System -> Administration -> Synaptic Package Manager" enter your password, and then search for libusb.

Another option is to use the terminal ("Applications -> Accessories -> Terminal") and type in sudo apt-get install libusb (and then the version number--I'm using 10.04 and the one listed in my archives is libusb-1.0.0). I'm not sure of your error, you may also need libusb-1.0.0-dev

I hope this may help.

---

### Post by lake59 on 2010-12-12
Well, I found and installed libusb-1.0.0-dev but still returns the same error listed above.  Terminal reports that libusb-1.0.0 & libusb-1.0.0-dev are already the newest versions

---

### Post by lake59 on 2010-12-12
I went back to synaptic package manager and installed anything similiar to libsub and that worked taking me to only missing 3 dependencies.  Again installed anything close to what was asked and eventually got hplip to install.  Seems like a very difficult process to just install a printer.  Anyway, the new print driver does not address the issue I originally had, leaving me unable to go forward....

The issue i was trying to address is the ability to print envelopes.  The printer tray for envelopes is in the center of the feed tray but the ubuntu driver wants to print on the left side of the feed tray.  Any thoughts on this would be awesome!

---

### Post by khelben1979 on 2010-12-13
From my experience, you should be able to change your settings in the software which you're using. Maybe it's a bug in that software and not in the printer driver?

---

### Post by case79 on 2011-05-10
```

sudo apt-get install libusb++-dev

```
worked for me.

---

