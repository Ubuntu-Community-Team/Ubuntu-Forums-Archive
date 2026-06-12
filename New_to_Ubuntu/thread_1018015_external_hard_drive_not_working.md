---
title: "external hard drive not working"
date: 2008-12-21
forum: New to Ubuntu
---

### Post by catface on 2008-12-21
hi,

i just installed Ubuntu 8.10 this evening onto a second drive in my computer, so that i could dual boot Ubuntu and Windows XP. My problem is that for most of my files (since my internal drives are very small) i have a 320gb iomega external hard drive, which seems to dissapear after about a minute or so of use.

if i turn it off and on again, i can see the folders of the main directory fine, but if i try to go into another folder (or i leave it a minute or so) the window will turn grey and the drive will dissapear. i never had a similar problem with XP.

can anyone help me?

(if it helps, i'm pretty sure it's formatted to FAT32)

---

### Post by empthollow on 2008-12-21
i just bought an external hard drive and am using intrepid.  Mine would work for a while and randomly i would not be able to access it.  For me, the problem was in my bios.  I had apm (advanced power management) truned on.  Once i turned it off the problem went away.  Hardware is controled by acpi these days.  I think it was a conflict.  I still can't boot my computer without unplugging the hard drive though.  I think the bios is looking for a boot sector or something even though i told it to not boot from usb.  Hope this helps.

---

### Post by catface on 2008-12-21
> **empthollow said:**
> i just bought an external hard drive and am using intrepid.  Mine would work for a while and randomly i would not be able to access it.  For me, the problem was in my bios.  I had apm (advanced power management) truned on.  Once i turned it off the problem went away.  Hardware is controled by acpi these days.  I think it was a conflict.  I still can't boot my computer without unplugging the hard drive though.  I think the bios is looking for a boot sector or something even though i told it to not boot from usb.  Hope this helps.

i tried going into the bios and setting it to the fail-safe defaults and then ensuring that the external was turned off when booting up the computer, but now the external isn't seen by the system at all :#

thanks for trying though mate

---

### Post by catface on 2008-12-22
anyone else got any ideas? i might as well just uninstall ubuntu if i can't access any of my files with it ;(

---

### Post by SlidingHorn on 2008-12-22
I don't have an answer, but I wanted to let you know this isn't exactly a "peak hour" for people being on the forums.  Give it some time and more people will be available

---

### Post by dellboy on 2008-12-22
do you  have usb 2.0 ports ?

---

