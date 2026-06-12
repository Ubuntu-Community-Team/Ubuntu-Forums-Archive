---
title: "xubuntu installation-help"
date: 2009-09-09
forum: New to Ubuntu
---

### Post by raoul-newbie on 2009-09-09
I need help. I am completely newbie on ubuntu/xubuntu/linux. I got it wrong (somewhere along the way) when i first installed xubuntu on my asus laptop- S5Notebook (248Mb RAM, 1.6ghz). At first, I used the alternate CD xubuntu 8.04 i386 but hang in the process. So, I downloaded again the xubuntu 8.04 desktop. I installed it but on the partitioning of the disk, it also hang for almost 2 hours. So i decided to reinstall again my windows recovery disk to start all over again but the after the windows xp preinstallation environment, it told me to reboot. After rebooting.. 

Message:

GRUB Loading stage1.5
GRUB Loading. please wait
Error 17.


Please help me on what to do next. I wanted to install Xubuntu on this laptop.

thanks

---

### Post by Xoanan on 2009-09-09
> **raoul-newbie said:**
> I need help. I am completely newbie on ubuntu/xubuntu/linux. I got it wrong (somewhere along the way) when i first installed xubuntu on my asus laptop- S5Notebook (248Mb RAM, 1.6ghz). At first, I used the alternate CD xubuntu 8.04 i386 but hang in the process. So, I downloaded again the xubuntu 8.04 desktop. I installed it but on the partitioning of the disk, it also hang for almost 2 hours. So i decided to reinstall again my windows recovery disk to start all over again but the after the windows xp preinstallation environment, it told me to reboot. After rebooting.. 

Message:

GRUB Loading stage1.5
GRUB Loading. please wait
Error 17.


Please help me on what to do next. I wanted to install Xubuntu on this laptop.

thanks

This bit might help, but you might need the live cd for it.  According to the article, its a partitioning issue.  I had several on machine and I wound up using another harddisk.

[http://stringofthoughts.wordpress.com/2009/05/24/grub-error-17-debianubuntu/]("http://stringofthoughts.wordpress.com/2009/05/24/grub-error-17-debianubuntu/")

---

### Post by Hospadar on 2009-09-09
The problem is (I suspect) that grub got installed in the MBR (master boot record) of the disk, and for whatever reason, the windows installation didn't re-create the windows MBR.

So, what you need to do is
a) get a windows install CD - probably the recovery disk will work
b) boot off windows cd, go into recovery mode instead of installing
c) use the "fixmbr" command to restore the windows bootloader.

You can google "restore windows bootloader" to findo more info on the specifics of what to do.

---

### Post by Rob Maddison on 2009-09-09
> **Hospadar said:**
> The problem is (I suspect) that grub got installed in the MBR (master boot record) of the disk, and for whatever reason, the windows installation didn't re-create the windows MBR.

So, what you need to do is....

Now if only I'd known that when I got the Error 17 message after botching my partitions completely and ending up with about 7 of the blighters! :lolflag:

I solved it by booting to live CD and using the whole HD for Ubuntu - which now puts me on a very steep learning curve (though I had backed up to CD the only  important files I had on my new laptop after some nice person had walked away with my old one).

---

### Post by raoul-newbie on 2009-09-09
Thanks for the help. I already use a live windows cd and fixed the mbr.I am now in the process of reinstalling xubuntu. However, It goes sluggish on the partitioning process part. I choose the guided resize and it stuck up again. At first, it is reading the cd (with the light blinking on it) then after 30mins, it hangs up again.

---

### Post by Xoanan on 2009-09-09
> **raoul-newbie said:**
> Thanks for the help. I already use a live windows cd and fixed the mbr.I am now in the process of reinstalling xubuntu. However, It goes sluggish on the partitioning process part. I choose the guided resize and it stuck up again. At first, it is reading the cd (with the light blinking on it) then after 30mins, it hangs up again.
Uh oh;  Be careful on that.  I ran into that too.  I ruined the harddrive after reinstalling several times.

---

### Post by raoul-newbie on 2009-09-09
After 5 hours of grueling efforts, I manage again to reinstall my windows using windows live cd. Booting from it, typing fixMBR and fixboot at c: prompt respectively. I tried again to install Xubuntu 8.04 but to no avail, it hangs up on step 4-7. after I click on the guided partitioning 10gig for the windows and 35gig for ubuntu, it stops responding again. :confused:  I even tried the "guided-entire disk" the screen goes dots and lines... thankfully as i reset my laptop, windows xp can still run and without that grub 17 error... I think  Xubuntu is not for me. :( and im about to give up.:lolflag: 

Any idea on how to install xubuntu?

---

