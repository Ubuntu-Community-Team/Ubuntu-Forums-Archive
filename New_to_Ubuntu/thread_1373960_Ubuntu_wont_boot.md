---
title: "Ubuntu wont boot"
date: 2010-01-06
forum: New to Ubuntu
---

### Post by Duck86 on 2010-01-06
I just tried installing ubuntu 8.04 from CD over my 9.04 system (I need to install 8.04 instead because 9.04 wont support my graphics card). I went into the BIOS and told it to boot from CD instead of the Hard disk and restarted with the CD in the drive.
 
It wont boot.
 
Either of them. 9.04 wont boot from the hard disk, and 8.04 wont boot from the CD.
 
I went back into BIOS and restored the old settings, but it still wont work. All I'm getting is 'strike F1 key to retry boot, F2 for setup utility'
 
Help!!!

---

### Post by adam814 on 2010-01-06
That's unusual that a newer distro would lose support for a graphics card.  Is it by any chance an ATI or nVidia that needs a proprietary driver?

Anyway, is there any chance your 8.04 CD has errors?  I've been one of the lucky ones and never had trouble with that, but a lot of people on the forums have trouble with either junk blank CDs or burn errors causing install problems.

So you didn't do anything to the hard drive?  You weren't in an install that failed, just tried to boot the LiveCD and now it won't boot?

---

### Post by Duck86 on 2010-01-06
Its an onboard Intel chipset. Already found out that there's problems with those in the v9 releases. Someone else on here is running the exact same computer as me in 8.10 though so I figure the rollback will be fine.
 
Didn't do anything at all to the HDD. Changed the Boot sequence to 
 
1. IDE CD
2. HDD
3. Diskette
 
from 
 
1. HDD
2. Diskette
3. IDE CD
 
I also switched 'OS Install' to 'on' when I was booting the CD with 8.04.
 
All those config are back to normal now.
 
Im getting nothing. Should I try downloading 8.04 from scratch again?

---

### Post by adam814 on 2010-01-06
What do you mean you switched "OS install" to "on" with the CD?  You started the installer?

There should be an option on the CD like "Check media for errors."  That should suffice, you shouldn't need to download it again unless it finds errors.

---

### Post by Duck86 on 2010-01-06
In the BIOS there's an 'OS installer mode', which was switched to 'off'. I switched it on.
 
I figured the problem though. There is a problem with the ISO recording software I used to burn the CD. Its rectified, and I'm downloading and burning from scratch. I'm hoping that that will solve the problem that I have and that I'll be able to boot from the CD.
 
Thanks!

---

