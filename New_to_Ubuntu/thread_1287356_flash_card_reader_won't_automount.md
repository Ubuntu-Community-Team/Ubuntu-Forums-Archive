---
title: "flash card reader won't automount"
date: 2009-10-10
forum: New to Ubuntu
---

### Post by Warlon on 2009-10-10
I have an internal compact flash reader on my computer that won't automount my cards anymore. I think the reader itself is an usb device.

This started after I ran powertop and did some of the optimizations it suggested.

Please help, how do I get that automounting back working?

---

### Post by taavikko on 2009-10-10
Terve,

You propably issued "hal-disable-polling" command that causes the issue.
try using
```
hal-disable-polling --enable-polling <device>
```
Might need sudo to work correctly.
check dmesg for proper device.

And as always, a warning, if not knowing what commands and apps do, ask.

---

### Post by Warlon on 2009-10-10
Terve,

yes, I remember issuing that disable-polling command for /dev/cdrom. Enabling that won't help with my card reader.

dmesg does not show anything about the card reader. Only bunch of lines about wlan and few about an usb stick I tested that worked fine.

---

### Post by Warlon on 2009-10-12
I also recall powertop saying that the card reader was active 100% of the time and suggested enabling interrupt mode so I enabled it.(I'm not sure what it is called in english since I'm using finnish translation).

Is there a way to undo that?:confused:

---

