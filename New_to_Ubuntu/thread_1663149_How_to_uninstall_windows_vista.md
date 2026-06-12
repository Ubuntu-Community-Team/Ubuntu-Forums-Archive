---
title: "How to uninstall windows vista"
date: 2011-01-09
forum: New to Ubuntu
---

### Post by Thundersheep on 2011-01-09
Well i'm new to this forums and well new to ubuntu i've just installed it today :D. So is there anychance i can make it reboot my entire harddrive. what i mean is how can i unistall windows vista on my computer and just have ubuntu alone. The method i used to install it was Wubi.exe, if there is a method to unistall windows with keeping Ubuntu i'll be happy if anyone were to tell me and is there an chance that i can remove the other program files stored on vista.


Any help would be greated appreciated.
And yes im thinkig of making some programs for ubuntu to enhance some programming knowledge aswell :).
The computer i am using is very old aswell it has 512MB ram and is a Emachines  620. That ran on XP but i tried installing vista on there but it couldn't handle it... so i gave unbuntu a run and its so smooth and user friendly.

---

### Post by venicequeen7706 on 2011-01-09
I don't know anything about wubi but i'll try to help. go to system>administration>disk utility click on your hard drive and check how many partitions you have and what they are called. if wubi created a separate partition for ubuntu I should be able to help

---

### Post by Rubi1200 on 2011-01-09
If this is a Wubi install then removing Windows will remove Wubi.

In Ubuntu, go to Applications > Accessories > Terminal and run the following command:

```
sudo parted -l
```

(lowercase L not 1)

Copy/paste the output here and then we can advise you on the best method to achieve what you want.

---

### Post by CaptainMark on 2011-01-09
The least complicated way if you dont any windows left and you havent made any major changes to your wubi install of ubuntu is to back up your documents and boot a live cd and start with a fresh install, this will only be ideal if you want to start over with ubuntu completely, if not keep us posted for better advice on how top seperate your ubuntu install from windows

---

### Post by MartyBuntu on 2011-01-09
> **CaptainMark said:**
> ...back up your documents and boot a live cd and start with a fresh install...

True.

If you only installed Ubuntu today and you have no further use for Vista, start over with a real, full install.

---

### Post by Thundersheep on 2011-01-09
> **Rubi1200 said:**
> If this is a Wubi install then removing Windows will remove Wubi.

In Ubuntu, go to Applications > Accessories > Terminal and run the following command:

```
sudo parted -l
```(lowercase L not 1)

Copy/paste the output here and then we can advise you on the best method to achieve what you want.


[FONT=monospace]
[LIST=1]
[*]Model: ATA WDC WD800EB-00DJ (scsi)
[*]Disk /dev/sda: 80.0GB
[*]Sector size (logical/physical): 512B/512B
[*]Partition Table: msdos
[*] 
[*]Number  Start   End     Size    Type     File system  Flags
[*] 1      32.3kB  80.0GB  80.0GB  primary  ntfs         boot
[/LIST]
[/FONT]
Done

---

### Post by Rubi1200 on 2011-01-09
Thanks for posting the output.

The decision is really yours to make as to what you want.

There is a way to migrate a Wubi install to the drive, but since you want to get rid of Windows it might be better just to go for a fresh start with a clean install from the CD.

I would suggest you make backups of any important data from Windows and if you don't have one, get hold of the installation/recovery CD; you never know.

The other option is to dual-boot both operating systems.

There is no right or wrong way to do this; it depends on your needs.

---

### Post by Thundersheep on 2011-01-09
Well the problem is that I installed it on a diff PC that has a broken CD drive so I cannot boot from a disk.

---

### Post by Merk42 on 2011-01-09
Can you boot from USB? You could reinstall Ubuntu that way.
You'd still have to make backups as reinstalling Ubuntu you'd lose everything either way

---

### Post by fossil93 on 2011-01-09
> **Thundersheep said:**
> Well i'm new to this forums and well new to ubuntu i've just installed it today :D. So is there anychance i can make it reboot my entire harddrive. what i mean is how can i unistall windows vista on my computer and just have ubuntu alone. The method i used to install it was Wubi.exe, if there is a method to unistall windows with keeping Ubuntu i'll be happy if anyone were to tell me and is there an chance that i can remove the other program files stored on vista.


Any help would be greated appreciated.
And yes im thinkig of making some programs for ubuntu to enhance some programming knowledge aswell :).
The computer i am using is very old aswell it has 512MB ram and is a Emachines  620. That ran on XP but i tried installing vista on there but it couldn't handle it... so i gave unbuntu a run and its so smooth and user friendly.

*   *   *   *   *   *   *   *   *

I'm a newbie too & I had problems installing Ubuntu 10.1  But the Ubuntu install CD gave me the option to totally erase Windoze XP which I did accidentally. Then I tried to do a "clean" install on only HALF of the empty hard drive. But Ubuntu ONLY wanted (far as I saw) to use the WHOLE hard drive for Linux. So then I put Windoze back on that hard drive all over again. When I had a Windows partition on the hard drive - Ubuntu would THEN allow my to select only a *portion* of that hard drive to use for Linux. (Ain't that fun???) 

Using the Ubuntu 10.1 CD from the "On Disk" Linux dealers, that CD *would* easily erase Windows off the hard drive. Also, those Linux distro CDs which the "On Disk" company are selling are *super* cheap. So if you would buy one of those CDs you should be able to easily erase your Windows by using the Ubuntu CD. 

I'd heard it's possible to make Windows *erase* itself by telling it to format C: drive. You possibly could (??) do that by going into the "My Computer" screen and right-clicking on the C: drive icon. Then you would just select the "Format C Drive" option in the new menu box. But whenever I did that, my WinXP kept saying it could *not* format C: drive because (some function) of Windoze was "in use". So then I tried to make sure every application in Windows WAS totally off, but still could not make Windows reformat C: Drive.

In the end I had to do whole new installation of Windows which erased everything else on the hard drive. To achieve that I first manually erased many, many Windows files - especially files in the "System 32" sub-directory of the Windows folder. By doing that a New Install of Windows was then permitted, because the previous Windows copy was so damaged the new install was then permissible. 

Then I did a *new* install of Windows XP. When I put in the new Windows I made SURE that the WHOLE hard drive DID get formatted. Earlier I'd formatted only a part of that hard drive for Windows. But then the Ubuntu installation REFUSED to "see" the portion of that large hard drive that HAD NOT been formatted by Windows! This Ubuntu installation just COULD NOT "see" the half of my hard drive which was NOT yet formatted - by Windows in this case.   

After I installed the *new* copy of Window - whenever I was later installing Ubuntu 10.1, that Ubuntu "install" then gave the option to use ALL of the hard drive if I wanted to - by erasing part of all of the Windows partition.     

Maybe that info will help you some - or maybe it's gobbledegook.

---

### Post by wojox on 2011-01-09
> **fossil93 said:**
> or maybe it's gobbledegook.

No offense. :P

---

### Post by Thundersheep on 2011-01-10
It is a really OLD computer that i don't think it can be booted by USB i've tried that

---

### Post by cgroza on 2011-01-10
I would just backup and do a fresh install. It is much faster and it saves you some time. The sooner you start, the sooner you will be done.

---

