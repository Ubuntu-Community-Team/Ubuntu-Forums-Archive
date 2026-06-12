---
title: "[HELP] Can't boot Ubuntu from USB"
date: 2009-10-07
forum: New to Ubuntu
---

### Post by Letterbomb05 on 2009-10-07
Hi,

I'd like to partition my hard disk to install ubuntu in a new partition, which from what I know requires the hard drive to be totally out of use. So, I loaded the .iso onto my USB stick, configured my BIOS to boot from USB, however it still boots from windows. I've also noticed that the LED on my USB stick doesn't come on until the PC has already booted into windows... Can anyone help?

Regards,
Aaron.

---

### Post by Mighty_Joe on 2009-10-07
> **Letterbomb05 said:**
> So, I loaded the .iso onto my USB stick, 

How did you "load" the ISO onto the drive?

---

### Post by Letterbomb05 on 2009-10-07
Drop and drag, thought I might have done something different last time I did it since last time the drive appeared in windows as "Ubuntu blabla" rather than just normal removeable media or whatever it is.

I did format the disk before hand if thats anything.

---

### Post by Mighty_Joe on 2009-10-07
Takes some more work than that.  There's [several ways to do it]("http://ubuntuforums.org/showthread.php?t=1193680"), the easiest being [the Ubuntu Live USB Creator]("http://en.wikipedia.org/wiki/Ubuntu_Live_USB_creator"), which can be found on the Live CD.  
You could try [unetbootin]("http://unetbootin.sourceforge.net/") from inside Windows, but I've seen lots of complaints about it (I haven't had good luck with it either).

---

### Post by Letterbomb05 on 2009-10-07
Ah yes I believe I used Unetbootin before, sorry I forgot all about that!

Thanks for your help, I'll go try out Unetbootin now.

---

### Post by Bölvaður on 2009-10-07
I recommend using the ubuntu live usb stick creator thingy.

System &#8594; Administration &#8594; USB startup disk creator

---

### Post by Arla on 2009-10-07
Also depends if the USB drive is acutally able to boot on the particular combination of hardware you have, my old laptop would happily boot from a USB stick I have, my new laptop refuses to see the drive as a bootable option (but allows me to try to boot from an IPOD, go figure)

---

### Post by Mighty_Joe on 2009-10-07
> **Arla said:**
> my new laptop refuses to see the drive as a bootable option (but allows me to try to boot from an IPOD, go figure)

Double-check your BIOS settings.  [This guy]("http://ubuntuforums.org/showpost.php?p=8004221&postcount=22") went around in circles for 3 pages trying to blame flash drives and Ubuntu for what was actually his error in selecting the correct BIOS option ("USB memory stick" vs "USB hard drive").
Another problem I've seen is that some USB drives don't have partition tables by default.  The USB creator doesn't show an error, but the drive is not bootable ([Bug 277865]("https://bugs.launchpad.net/ubuntu/+source/usb-creator/+bug/277865"))

---

### Post by Letterbomb05 on 2009-10-07
Ok thanks everyone very much for your feedback.

I've loaded the disk image onto the USB via Unetbootin, this is the way I've done it before for my laptop. However, for some reason the problem still persists.

I have checked my BIOS boot settings, I've got 
1. USB FDD
2. USB ZIP
3. USB HDD

I am assuming USB FDD will be my flash drive, someone please correct me if I'm wrong, I'm pretty sure there was no other USB options.

Regards,
Aaron.

---

### Post by Mighty_Joe on 2009-10-08
> **Letterbomb05 said:**
> 
I am assuming USB FDD will be my flash drive,

USB flash drives are hard drives (HDD), not Floppy Disk Drives (FDD).

---

