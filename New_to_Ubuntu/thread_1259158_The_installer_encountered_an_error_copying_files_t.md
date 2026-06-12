---
title: "The installer encountered an error copying files to the hard disk"
date: 2009-09-06
forum: New to Ubuntu
---

### Post by psam3 on 2009-09-06
This is the error message I am receiving while trying to install Ubuntu.

"[B]The installer encountered and error copying files to the hard disk: [Errno 5] Input/output error.

This is often due to a faulty cd/dvd disk or drive, or a faulty hard disk.[/B]"

I had already suspected a hardware failure([http://ubuntuforums.org/showthread.php?t=1259113]("http://ubuntuforums.org/showthread.php?t=1259113")), but this really narrows it down for me. The question now is how to determine whether it is the dvd drive or the hard drive? Is their anything in the bios which might give me a clue to which one is failing or any other way to find out? 

Thanks in advance

psam3

---

### Post by pedro3005 on 2009-09-06
You could try installing ubuntu from a different media other than a CD. Try using a USB Stick ( [https://help.ubuntu.com/community/Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick) ) or maybe boot the ISO directly using grub2 ( [http://michael-prokop.at/blog/2009/05/25/boot-an-iso-via-grub2/](http://michael-prokop.at/blog/2009/05/25/boot-an-iso-via-grub2/) )

---

### Post by Jazzy_Jeff on 2009-09-06
Are you using the Live cd or the alternate install cd? I always have problems intstalling with the Live cd. The alternate cd is text based but easy to follow.

---

### Post by 3rdalbum on 2009-09-06
> **psam3 said:**
> This is the error message I am receiving while trying to install Ubuntu.

"[B]The installer encountered and error copying files to the hard disk: [Errno 5] Input/output error.

This is often due to a faulty cd/dvd disk or drive, or a faulty hard disk.[/B]"

I had already suspected a hardware failure([http://ubuntuforums.org/showthread.php?t=1259113]("http://ubuntuforums.org/showthread.php?t=1259113")), but this really narrows it down for me. The question now is how to determine whether it is the dvd drive or the hard drive? Is their anything in the bios which might give me a clue to which one is failing or any other way to find out? 

Thanks in advance

psam3

Have you tried the 'Check CD for defects' option in the CD's boot menu? This will tell you if the CD or CD drive is at fault.

---

### Post by psam3 on 2009-09-06
> **pedro3005 said:**
> You could try installing ubuntu from a different media other than a CD. Try using a USB Stick ( [https://help.ubuntu.com/community/Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick) ) or maybe boot the ISO directly using grub2 ( [http://michael-prokop.at/blog/2009/05/25/boot-an-iso-via-grub2/](http://michael-prokop.at/blog/2009/05/25/boot-an-iso-via-grub2/) )

Thanks, I will try the USB stick method first to see if it installs into the hard drive correctly and hopefully that will answer my question.

---

