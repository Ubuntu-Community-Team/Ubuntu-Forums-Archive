---
title: "Usb Linux Help....."
date: 2009-10-31
forum: New to Ubuntu
---

### Post by shaifymehtadnn on 2009-10-31
heelo....

i have a usb pendrive in which ubuntu (linux) is installed and on my hard disk window vista is installed....

but when i put the pendrive and boot it only only linux will boot up...

means 

menu must be shown like this which window u want to run...

1) window vista

2) linux

help..??????

how to use boot loader ....

if i have unbuntu in usb and window vista in harddisk....

---

### Post by Matt__ on 2009-10-31
So you have bios set to boot from USB first?

Hit F12 (usually this key) to choose from the list of boot options.

Boot list options will only appear automatically if Ubuntu is installed on the hard drive, otherwise it defaults to BIOS settings.

---

### Post by yeats on 2009-10-31
If I'm understanding you correctly,

> but when i put the pendrive and boot it only only linux will boot up...

This is expected behavior if only Ubuntu is on the pendrive and your BIOS is configured to boot from the pendrive (when present)

> menu must be shown like this which window u want to run...

1) window vista

2) linux


If you want to choose on bootup which operating system to boot to, you have to use GRUB as your bootloader.  This is better if you have both OSs installed on the hard drive, though.

---

### Post by shaifymehtadnn on 2009-10-31
> **chrissharp123 said:**
> If I'm understanding you correctly,



This is expected behavior if only Ubuntu is on the pendrive and your BIOS is configured to boot from the pendrive (when present)



If you want to choose on bootup which operating system to boot to, you have to use GRUB as your bootloader.  This is better if you have both OSs installed on the hard drive, though.

tell me how to use GRUB...command

---

### Post by shaifymehtadnn on 2009-10-31
how to use boot loader ....

if i have unbuntu in usb and window vista in harddisk....

---

