---
title: "Booting from pendrive"
date: 2009-10-30
forum: New to Ubuntu
---

### Post by Sonnyh on 2009-10-30
I installed 9.10 on to a live cd then used Ubuntu to create a bootable flash drive.  Tried it on my IBM R32 by pressing F12 and choosing the flash drive but windows starts up instead of Ubuntu.  Any help would be appreciated.  If I do get this going, will any changes I make in Ubuntu be there when I reboot?

Thanks,

---

### Post by JamesParnell on 2009-10-30
What i would do, if that method didn't work, would be to:


[LIST=1]
[*]Enter the BIOS (F2 or DEL)
[*]Find the Boot sequence (usually under the "boot" tab)
[*]Change the sequence to make the computer read from the USB first
[*][COLOR=Red]***Alternative*** [COLOR=Black]: If that doesn't work, disable all the other bootable devices altogether, so the computer has no choice of where to boot from[/COLOR][/COLOR].
[/LIST]
**EDIT: **Make sure to change the BIOS settings back to the original settings after you are done with it, or you may have problems.
**EDIT:** If the USB option is not in the BIOS, my help is useless.
 
With regards to the changes, I would think that all changes will stick, but I am an 18 year old IT student, so I'm still learning.

Hope that is clear enough and is helpful to you,

Regards, 
             * James*

---

### Post by Sonnyh on 2009-10-30
Hi,

Tried all that it did not work.  I suspect Ubuntu did not install correctly on the 2 gig pendrive.

Thanks,

---

### Post by nwadams on 2009-10-30
if you set a persistant partition when you make the bootable usb (using ubuntu's usb creator) then any changes you make will be saved.

and yes I expect that the install got screwed up somehow. or your iso was bad.

---

### Post by JamesParnell on 2009-10-30
sounds like a bad ISO, make sure you format the drive, and i would use Unetbootin for windows, to create the the ubuntu installer..if you havent already.

---

### Post by theozzlives on 2009-10-30
> **JamesParnell said:**
> sounds like a bad ISO, make sure you format the drive, and i would use Unetbootin for windows, to create the the ubuntu installer..if you havent already.

In my experience, unetbootin doesn't support persistence. Portable Linux is what I would go with.

---

### Post by oldfred on 2009-10-30
On my Jaunty install to a pen drive several months ago I thought I had the same problem. It would not boot from any of my settings for USB from my desktop, but when I tested it in my portable it worked. I went back to my desktop and tried all the USB boot - usb HD, usb cd, usb floppy, usb, nadda. Then I tried choosing Hard drive to boot for a different reason when I still had the USB pen drive in and there it was. 

t was part to the hard drive top level choice not USB hard drive choice.

---

### Post by Sonnyh on 2009-10-30
Hi,

I had ran the live cd on my desk top computer and other than the desk top had shifted to the left the os worked.  I also used the Ubunt disk creator and did not format the pen drive and install ubuntu.

I just now ran the live cd on my laptop and went to disk creator and tried to format the pendrive but got an error message "unable to mount Kingston - Dbus error - org.gtk.Private remote volume monitor not found. The given volume was not found."  I can see the Kingston on the desktop and it found it in the disk creator so what gives?  Can I format in windows xp and run disk creator?

Thanks,

---

