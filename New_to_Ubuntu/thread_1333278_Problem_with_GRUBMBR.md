---
title: "Problem with GRUB/MBR"
date: 2009-11-21
forum: New to Ubuntu
---

### Post by jmundinger on 2009-11-21
I successfully installed Ubuntu 9.10 to an 8gb pen drive.  When I did, I used the "advanced" option to install GRUB to the pen drive.  That apparently worked correctly because I noticed no change to GRUB on my desktop (a dual booted computer) and I was able to boot into Ubuntu from the pen drive with the pen drive installed on my laptop (a Windows XP computer).

Now, the problem!  While running Ubuntu from the pen drive on the laptop, I updated the installation.  That update also included an update to GRUB.  I selected the default option about what to do about GRUB.  When I rebooted to complete the update, I noticed that the GRUB menu had changed, including an option to boot into windows.  Apparently, that change also altered the MBR because I am no longer able to boot the laptop into Windows unless the pen drive is installed.

Is there an easy way to repair the MBR?

thanks

---

### Post by jmundinger on 2009-11-21
Now I am really confused!  I had booted into XP from the GRUB on the pen drive.  Then, after doing some internet research, I decided to try to run fixmbr from the recovery console.  So, I turned the computer on, selected the boot menu, inserted the recovery cd  But, when prompted whether I wanted to boot the cd, I wasn't quick enough with the "enter" and the computer then defaulted to boot from the first hard disk and booted normally into Windows.

So, what happened?  I wouldn't think that a problem with the MBR would have self-corrected.  But, is there something about GRUB2 that might have reset after I booted from GRUB into Windows?

---

