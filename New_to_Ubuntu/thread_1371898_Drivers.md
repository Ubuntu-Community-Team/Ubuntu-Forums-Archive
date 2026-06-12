---
title: "Drivers"
date: 2010-01-03
forum: New to Ubuntu
---

### Post by Jackzor on 2010-01-03
What command line could I run to figure out whether or not ALL of my devices are Working and installed correctly?

---

### Post by markjensen on 2010-01-03
To be honest, I can't think of how any command would tell you if something was working right.

I mean, it could show you it detects a certain webcam, but it doesn't mean that it works properly. Or you might see a scanner, but does it scan at the proper resolution and color depth?

You will need to check these things out yourself, I am afraid.


EDIT: There is a command, **lshw** that can be used to dump the detected hardware listing and some information about each piece.  It can also be told to do so in HTML formatted goodness for looking at with a browser, should you choose.

---

### Post by Temposs on 2010-01-03
You can do System->Administration->System Testing to do what you wish. But that's not from the command line.

---

### Post by HermanAB on 2010-01-03
lspci, lsusb, lsmod...

---

### Post by Jackzor on 2010-01-04
Edit. Sorry, I bumped not knowing anyone replied. Damn my girlfriends slow internet

---

### Post by anewguy on 2010-01-04
> **HermanAB said:**
> lspci, lsusb, lsmod...

The first 2 will not show if something is working (e.g., accessable) only that Ubuntu knows about the hardware.  The driver could be missing, making the device unusable, but it would still show in those lists.

I thought lsmod only showed kernel modules loaded - I didn't think this said anything about a device actually working either.

If I'm wrong about this please let me know.

Dave :)

---

