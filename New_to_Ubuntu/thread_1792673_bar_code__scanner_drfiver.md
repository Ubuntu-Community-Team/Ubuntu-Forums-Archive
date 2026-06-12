---
title: "bar code  scanner drfiver"
date: 2011-06-28
forum: New to Ubuntu
---

### Post by helphelp on 2011-06-28
Hi,
Does anyone know where i can download the driver for a usb bar code  reader.
I am using Ubuntu 11 04. 
Thanks

---

### Post by An Sanct on 2011-06-28
Normally Bar code readers just simulate a keyboard ... What typ of scanner are you using?

---

### Post by helphelp on 2011-06-28
opticon

---

### Post by An Sanct on 2011-06-28
And the model/number?

---

### Post by An Sanct on 2011-06-28
Opticons are "USB (HID)Plug and Play Interface" - which should make them PlugNPlay, without any drivers needed...

---

### Post by helphelp on 2011-06-28
OPN -2001 
sn 040150

---

### Post by helphelp on 2011-06-28
Hi
USB (HID)Plug and Play Interface.
I'm a novice at this so please elaborate. 
Thanks

---

### Post by An Sanct on 2011-06-28
Before, since I did not know the brand/make of your scanner, I assumed, that it is a "normal" scanner, that is plugged in all the time of use...

> **helphelp said:**
> OPN -2001

This actually is a "*data collector*", a device, you scan with and then later plug to your computer and download the data...

Here is [something]("http://majid.info/blog/a-python-driver-for-the-symbol-cs-1504-bar-code-scanner/") I found [here]("http://forums.gentoo.org/viewtopic-t-719954.html")

also

[This]("http://wiki.opticon.com/index.php/Installing_the_Linux_USB-VCP_driver") is what I found on the official Opticon site wiki (installing the Linux driver)
Have you tried to use it with WINE? Download the windows program from [this location]("http://old.opticon.com/software.aspx") and it might work normally under WINE.

edit: HID is Human Interface Device (keyboard, mouse, trackball, ....)

---

### Post by helphelp on 2011-06-28
Thanks for that .  
No joy as jet

---

