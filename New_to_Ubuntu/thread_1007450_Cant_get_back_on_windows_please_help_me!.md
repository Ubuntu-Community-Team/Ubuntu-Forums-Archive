---
title: "Cant get back on windows please help me!"
date: 2008-12-10
forum: New to Ubuntu
---

### Post by yalgret on 2008-12-10
this has been posted before but none of it helped

I have just installed ubuntu on a windows computer and now i cant go back on it just goes on to ubuntu i kinda rushed the partitions and i might have gone wrong there

i would be grateful if anyone can help

please ask if you need any details on my computer

btw i got the standard installatoin you get on the ubuntu homepage
:confused:

---

### Post by halitech on 2008-12-10
open a terminal and post the results of
```
sudo fdisk -l
```

---

### Post by ukulele_ninja on 2008-12-10
Were you careful not to install Ubuntu on top of your sindows partition? I wouldnt worry to much as likely all you will need to do is reinstall GRUB.

---

### Post by fooman on 2008-12-10
do you not see the grub menu when you boot?  ...or is there no windows entry in grub?

if you do not see the grub menu,  then as you boot there should be a prompt to "press esc to display grub menu" (or something similar)...when you see that prompt,  press "esc" and see if windows is listed.

---

### Post by yalgret on 2008-12-10
Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x2aa12aa1

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       30025   241175781   83  Linux
/dev/sda2           30026       30401     3020220    5  Extended
/dev/sda5           30026       30401     3020188+  82  Linux swap / Solaris
yannick@yannick-desktop:~$ 
yannick@yannick-desktop:~$

---

### Post by halitech on 2008-12-10
hope you didn't have anything in windows that you can't replace because your windows install is gone, adios, bye bye.

---

### Post by Michael.Godawski on 2008-12-10
Your Windows partitions are not there so your Windows is nuked...

Probably you have chosen the use entire disk option during the Ubuntu installation.

I hope you have done some back-ups...

---

### Post by Titan8990 on 2008-12-10
This is why "Guided" partitioning should be removed from the installer IMO.

Lot more clicking to manually delete your Windows drive then to have it automatically done with a pre-selected option just waiting for you to hit next....

---

### Post by yalgret on 2008-12-10
> **fooman said:**
> do you not see the grub menu when you boot?  ...or is there no windows entry in grub?

if you do not see the grub menu,  then as you boot there should be a prompt to "press esc to display grub menu" (or something similar)...when you see that prompt,  press "esc" and see if windows is listed.
well i put 

title		Windows XP
lock
root		(hd0,1)
savedefault
makeactive
chainloader	+1


at the end of the menue thingy and when i press esc it gives me 4 optoins three are ubuntu and one is windows xp, when i go on xp it gives me an error.

does that help?

thanx for the reply though

---

### Post by yalgret on 2008-12-10
> **halitech said:**
> hope you didn't have anything in windows that you can't replace because your windows install is gone, adios, bye bye.
sh*t

---

### Post by Titan8990 on 2008-12-10
> **yalgret said:**
> well i put 

title		Windows XP
lock
root		(hd0,1)
savedefault
makeactive
chainloader	+1


at the end of the menue thingy and when i press esc it gives me 4 optoins three are ubuntu and one is windows xp, when i go on xp it gives me an error.

does that help?

thanx for the reply though


Maybe you didn't fully understand halitech's post. Everything Windows related on your machine is **gone**.

---

### Post by halitech on 2008-12-10
> **yalgret said:**
> sh*t

I take it from that response that you had things there you can't replace.

---

### Post by Titan8990 on 2008-12-10
> **halitech said:**
> I take it from that response that you had things there you can't replace.


Most people (including myself) learn the value of regular backups the hard way.

---

### Post by halitech on 2008-12-10
been there myself

---

### Post by Michael.Godawski on 2008-12-10
Moralizing after the damage is done is to no avail....

But for the future yalgret do not rush through an installation process. Read the provided info and ask on the forums for guidance.
Sorry for the lost data though**.** I hope you do not lose heart and you stay with Ubuntu.

---

### Post by halitech on 2008-12-10
> **Michael.Godawski said:**
> 
But for the future yalgret do not rush through an installation process. Read the provided info and ask on the forums for guidance.
Sorry for the lost data though**.** I hope you do not lose heart and you stay with Ubuntu.

good advice for anyone :)

---

### Post by dragos_iliescu_2005 on 2008-12-10
I don't know if this will work but... use Live CD and run testdisk from there. I expect it will recover the files deleted even after formatting. If you are not familiar with testdisk, you can google for another file recover option.

N.B. From now on you must back-up you system.

---

### Post by Michael.Godawski on 2008-12-10
I do not want destroy your hopes, but I remember that recovering files from a drive which was formatted to ext3 is extremely difficult and likely doomed to failure.

---

### Post by halitech on 2008-12-10
> **dragos_iliescu_2005 said:**
> I don't know if this will work but... use Live CD and run testdisk from there. I expect it will recover the files deleted even after formatting. If you are not familiar with testdisk, you can google for another file recover option.

N.B. From now on you must back-up you system.

> **Michael.Godawski said:**
> I do not want destroy your hopes, but I remember that recovering files from a drive which was formatted to ext3 is extremely difficult and likely doomed to failure.

if the partition types were the same, testdesk or photorec might have a chance but an NTFS drive thats been formatted ext3, I wouldn't want to give odds on the success of getting anything back. not to mention, depending where the files were on the drive, they may have been over written as well.

---

### Post by waspbr on 2008-12-10
that's really sucks but what you can learn from this is the golden rule of tweaking/installing any operating system: back up your files before you do anything.

---

