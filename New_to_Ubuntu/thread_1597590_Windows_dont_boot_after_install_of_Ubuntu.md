---
title: "Windows dont boot after install of Ubuntu"
date: 2010-10-15
forum: New to Ubuntu
---

### Post by vagelism on 2010-10-15
Hello to all!
I just installed the ubuntu version 10 to my pc and i did all the installation with the default options in order not to remove the windows installation and have dual boot.
I see on the first boot screen my windows there but when i try to boot them i got a blue screen.
Any help please?
My ubuntu works great!
Thank you in advance

---

### Post by Chesamo on 2010-10-15
Which version of Windows?

---

### Post by vagelism on 2010-10-15
windows xp sp3

---

### Post by muteXe on 2010-10-15
Do a 'sudo fdisk -l' from a terminal. That's a small L not a one. 

How many times did you defrag your windows disk before installing?

---

### Post by vagelism on 2010-10-15
i didnt defrag it at all!!! it was almost fresh installation also!

---

### Post by muteXe on 2010-10-15
You should defrag a few times first. Your win files might be scattered over your disk, which might not be good if your ubuntu's doing the partitioning. 

Did you run that command?

Oh, and when you say "blue screen" is there any text?

---

### Post by wilee-nilee on 2010-10-15
> **vagelism said:**
> i didnt defrag it at all!!! it was almost fresh installation also!

If you let the Ubuntu installer resize XP it might need a chkdsk /f/r run. You can do this from the command terminal in a safe mode or from a XP install cd. The safe mode would be reached with the f8 prompt at choosing XP at the grub screen. 

You could also post the bootscript in my signature, it is helpful in finding what is where. Post it in code tags as described in my signature or click on the # in the reply and paste the text in between.,

---

### Post by vagelism on 2010-10-15
> **wilee-nilee said:**
> If you let the Ubuntu installer resize XP it might need a chkdsk /f/r run. You can do this from the command terminal in a safe mode or from a XP install cd. The safe mode would be reached with the f8 prompt at choosing XP at the grub screen. 

You could also post the bootscript in my signature, it is helpful in finding what is where. Post it in code tags as described in my signature or click on the # in the reply and paste the text in between.,

Disk /dev/sda: 40.0 GB, 40007761920 bytes
255 heads, 63 sectors/track, 4864 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000001

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        2569    20633759+   7  HPFS/NTFS
/dev/sda2            2569        4864    18435073    5  Extended
/dev/sda5            2569        4763    17618944   83  Linux
/dev/sda6            4763        4864      815104   82  Linux swap / Solaris
administrator@administrator-ThinkPad-X31:

---

### Post by vagelism on 2010-10-15
> **wilee-nilee said:**
> If you let the Ubuntu installer resize XP it might need a chkdsk /f/r run. You can do this from the command terminal in a safe mode or from a XP install cd. The safe mode would be reached with the f8 prompt at choosing XP at the grub screen. 

You could also post the bootscript in my signature, it is helpful in finding what is where. Post it in code tags as described in my signature or click on the # in the reply and paste the text in between.,

I can not do this command
it says the disk is not valid....

---

### Post by wilee-nilee on 2010-10-15
> **vagelism said:**
> I can not do this command
it says the disk is not valid....

Can you describe the process you did to get to that message.

---

### Post by vagelism on 2010-10-15
Put the cd of windows restart the pc...load from cd and ask recovery!
Then I was in c: but i could not run the chckdsk! Thats all!

---

### Post by wilee-nilee on 2010-10-15
> **vagelism said:**
> Put the cd of windows restart the pc...load from cd and ask recovery!
Then I was in c: but i could not run the chckdsk! Thats all!

Here is a link, just to make sure you are doing it correctly, I don't know I'm not there.;)
[http://kb.wisc.edu/helpdesk/page.php?id=5097](http://kb.wisc.edu/helpdesk/page.php?id=5097)

You also might get with the spirit that we are trying to help you by posting the bootscript, we don't do magic here, we need solid information.

Here is a link to another XP download.
[http://www.aspireoneguide.com/xpinstallu3.html](http://www.aspireoneguide.com/xpinstallu3.html)

---

### Post by vagelism on 2010-10-15
yes I do this. one the blue screen I take only some giblish!!!nothing understandable!

---

### Post by vagelism on 2010-10-15
i tried to fix it like that
[http://www.arsgeek.com/2008/01/15/how-to-fix-your-windows-mbr-with-an-ubuntu-livecd/](http://www.arsgeek.com/2008/01/15/how-to-fix-your-windows-mbr-with-an-ubuntu-livecd/)

Now I have the xp booting and not the ubuntu..but still the xp is always on blue screen!!!

---

