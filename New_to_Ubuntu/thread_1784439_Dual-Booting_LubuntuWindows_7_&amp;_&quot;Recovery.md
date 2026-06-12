---
title: "Dual-Booting Lubuntu/Windows 7 &amp; &quot;Recovery&quot; Partition"
date: 2011-06-16
forum: New to Ubuntu
---

### Post by lareynatortura on 2011-06-16
Hi all, 

I have a Toshiba Satellite A505-S6009 that runs Windows 7, and I would like to dual-boot with Windows 7.  If I go through the process of installing Lubuntu alongside Windows 7, will my "recovery" partition be deleted?


(I don't know very much about partitions yet. Usually, when I install an OS, I choose the recommended settings, instead of the advanced settings. . as I am not advanced yet!  :-D)

---

### Post by idoitprone on 2011-06-16
well, if you deleted or told the install to override the entire disk then you lose the recovery partition


go to windows and resize your partition. If you cant go any farer defrag and resize

remember this unix priciple
"UNIX was not designed to stop its users from doing stupid things, as that would also stop them from doing clever things."

---

### Post by lareynatortura on 2011-06-17
> **idoitprone said:**
> well, if you deleted or told the install to override the entire disk then you lose the recovery partition


go to windows and resize your partition. If you cant go any farer defrag and resize



Thank you, idoitprone

You confirmed my suspicion--that the recovery partition would not be deleted unless I installed Lubuntu on the entire hard disk--but, I am glad I asked, because I'm still figuring all this stuff out.

> **idoitprone said:**
> 

remember this unix priciple
"UNIX was not designed to stop its users from doing stupid things, as that would also stop them from doing clever things."



Oh?  Heh heh!  That's awesome. I will keep that in mind. : )

---

### Post by wildmanne39 on 2011-06-17
> **lareynatortura said:**
> Thank you, idoitprone

You confirmed my suspicion--that the recovery partition would not be deleted unless I installed Lubuntu on the entire hard disk--but, I am glad I asked, because I'm still figuring all this stuff out.



Oh?  Heh heh!  That's awesome. I will keep that in mind. : )Hi, you need to be very careful with installing, if you are using 11.04 ubuntu you can choose to have ubuntu installed along side and that is the easiest for a new person and it will split the disk in have.

---

### Post by lareynatortura on 2011-06-17
> **wildmanne39 said:**
> Hi, you need to be very careful with installing, if you are using 11.04 ubuntu you can choose to have ubuntu installed along side and that is the easiest for a new person and it will split the disk in have.


Thank you, wildmanne39

---

### Post by jtarin on 2011-06-17
There's an alternative when installing to keep Ubuntu from overwriting the MBR, it's in my signature. You install Grub to the partition Ubuntu is on then you install EasyBCD in Win7 and use Win Bootloader to chainload Grub.

---

### Post by lareynatortura on 2011-06-18
> **jtarin said:**
> There's an alternative when installing to keep Ubuntu from overwriting the MBR, it's in my signature. You install Grub to the partition Ubuntu is on then you install EasyBCD in Win7 and use Win Bootloader to chainload Grub.

jtarin,

You're awesome!  But. . I may have a little problem. . 

I just got finished installing lubuntu.  I'm a little nervous about it because I think the installation did not go as smoothly as my other dual-boot on my notebook.  Here's why I think this dual-boot did not go quite as well:

-After I disconnected my pendrive and pressed enter at the end of the installation, nothing happenend.  The computer did nothing.  I waited a minute or two, then pressed ctrl+alt+delete.  The computer responded to this, but did not re-boot.  I waited again.  Nothing happened, so I decided to just power off the machine.  After I selected the Linux partition, the screen went black and had a sort of band at the top of the screen.  It looked pixelated and was of different colors.  This kind of alarmed me--I've never seen it before.  Lubuntu eventually loaded and brought me to the logon screen.  (Things went okay on the Linux partition, after that).

-After I re-booted and selected the Windows partition, it immediately ran a disk check.  I got up for a minute to wait for it to finish, and when I came back, the computer displayed the lubuntu login screen. (I figure the computer re-booted after the disk check was finished, and then it took me into the Linux partition because I was not there to select which one I wanted).  I've been wondering why it restarted after the disk check.

-Lastly, after I got into the Windows partition, everything loaded fine, until it got to the logon screen.  The screen was blank for a long time. Then, the cursor finally came up; and slowly, the Windows logon was displayed.

This is probably nothing. . but it seemed a little weird to me, so it makes me wonder if perhaps I had corrupted something when I powered the computer off.

Is that possible?

Given the information that you told me--the alternative dual-boot--do you suggest that I re-do the process?

---

### Post by jtarin on 2011-06-18
> **lareynatortura said:**
> 
This is probably nothing. . but it seemed a little weird to me, so it makes me wonder if perhaps I had corrupted something when I powered the computer off.

Is that possible?It's possible but also I have seen this after using a partition tool and then installing an OS. It usually straightens itself out after awhile.

> **lareynatortura said:**
> Given the information that you told me--the alternative dual-boot--do you suggest that I re-do the process?Give it sometime and see what it does and the post back when your ready.

---

