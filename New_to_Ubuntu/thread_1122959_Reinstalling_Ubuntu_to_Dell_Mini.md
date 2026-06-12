---
title: "Reinstalling Ubuntu to Dell Mini"
date: 2009-04-11
forum: New to Ubuntu
---

### Post by rifd on 2009-04-11
This is how I messed up my new Dell Mini.
1)Tried to get sound working with earphones.
2) Typed sudo apt-get --purge remove linux-sound-base alsa-base alsa-utils
3) Typed sudo apt-get install gdm **X**ubuntu-desktop
4) rebooted and found my login screen had changed to Xubuntu (of course), so
5) typed sudo apt-get **un**install gdm xubuntu-desktop
6) Rebooted and found I had only terminal
7) Typed sudo apt-get install gdm ubuntu-desktop, but get this error message:
"could not resolve 'dell-mini.archive.canonical.com'
8. Tried sudo nano "/etc/apt/sources.lst" so see if I could edit out the 'dell-mini.archive.canonical.com', but get the message nano:command not found.
9) Dell mini does not have cdrom drive, so tried downloading Ubuntu sourse code to a USB flash drive. Plugged in the drive, fired up, checked the computer bios and see the flash drive listed, but can't get the mini to boot from it.

So, tried everything I can think of, and looking for help.

---

### Post by llamabr on 2009-04-11
> **rifd said:**
> Plugged in the drive, fired up, checked the computer bios and see the flash drive listed, but can't get the mini to boot from it.


You say you see flash drive listed.  Did you make sure that it's listed ABOVE the hard disk?

---

### Post by RetchingRabbit on 2009-04-11
Source code on a usb stick isn't going to help you. 
You can create a bootable usb stick with unetbootin.
It's in the repos.

---

### Post by rifd on 2009-04-13
Many thanks to those who helped.
I found the solution at [http://www.ubuntumini.com/2008/10/make-liveusb.html]("http://www.ubuntumini.com/2008/10/make-liveusb.html") - no difficulty when I followed the instructions.

---

