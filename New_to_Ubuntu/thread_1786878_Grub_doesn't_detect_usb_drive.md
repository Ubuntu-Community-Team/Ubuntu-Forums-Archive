---
title: "Grub doesn't detect usb drive?"
date: 2011-06-20
forum: New to Ubuntu
---

### Post by anaa on 2011-06-20
I wanted to boot ubuntu live cd from a usb stick, but my computer is a bit old and
usb boot is not supported, but I thought that once grub is installed, it will be possible,
however this does not seem to be the case as also grub doesn't see the usb
disk. Any suggestions?

---

### Post by arochester on 2011-06-20
"Boot From a USB Drive Even if your BIOS Won&#8217;t Let You" - [http://www.howtogeek.com/howto/16822/boot-from-a-usb-drive-even-if-your-bios-wont-let-you/](http://www.howtogeek.com/howto/16822/boot-from-a-usb-drive-even-if-your-bios-wont-let-you/)

---

### Post by anaa on 2011-06-20
I see. But is this the only way? I am already booted from grub, why am I still not
able to 'ls' the usb drive from grub?

---

### Post by amjjawad on 2011-06-20
Hello and Welcome, Anaa :)

First of all, have a look at this: [http://en.wikipedia.org/wiki/GNU_GRUB](http://en.wikipedia.org/wiki/GNU_GRUB)

I'm not sure what exactly do you mean?
If you want to boot a LiveUSB for Ubuntu, what GRUB has to do with this? as - to begin with - it has to do with your machine whether it supports booting from USB or not?

If you want to install Ubuntu on an USB Drive, then that's totally something else. In my signature, there is a link for such thing.

No offense but please try to explain more so that we can help you :)

Sorry if I'm talking about something else :)

---

### Post by Rex Bouwense on 2011-06-20
Welcome anaa. I have a suggestion for you.  I have an old Dell Inspiron that did not want to boot from a flash drive but I discovered something that I have shared on these forums before.  In some cases the computer will not recognize the flash drive as a flash drive but rather another hard drive.  I happened to notice when I went into the boot order that there was a plus sign by the hard drive so I went into it and I was pleasantly surprised to find my flash drive recognized as another hard drive.  I merely changed the order of the "hard drives" and bingo bango I installed Ubuntu with no further problems.  Check yours.  It may be the same.

---

