---
title: "How to remove ubuntu"
date: 2010-12-25
forum: New to Ubuntu
---

### Post by zuber786 on 2010-12-25
ok here is the story
long time ago I installed ubuntu on my lenovo laptop it has 120 GB of hard drive, so I had to make the partition I can install ubuntu separately.

so now I have 80 gb on ubuntu 
and 40 gb of vista 

when I start the computer I see Gurb thing pop up and I have option to pick ubuntu or vista but now I want to remove ubuntu and grub both totally. I want to remove it from my laptop and will install on desktop as a server after words but now I really need help removing ubuntu and grub 
thank you

---

### Post by zuber786 on 2010-12-25
can I follow this?
[http://www.youtube.com/watch?v=uUgf84bdYvg](http://www.youtube.com/watch?v=uUgf84bdYvg)

---

### Post by fatharraxman on 2010-12-25
[http://ubuntuforums.org/showthread.php?t=901383](http://ubuntuforums.org/showthread.php?t=901383)

---

### Post by ryu kun on 2010-12-25
Two options come to my mind:

1. Easy option: Backup all your data and reinstall Vista from recovery partition or from DVD if you have.

2. Tricky option: Use the instructions _**[here]("http://neosmart.net/wiki/display/EBCD/Recovering+the+Vista+Bootloader+from+the+DVD")**_ to make Vista recovery DVD if you don't have one. After you have the DVD, boot with Ubuntu Live CD. Run Gparted and remove Ubuntu partition and resize Vista partition. Then boot with your Vista recovery DVD and use the instructions explained in the link I gave above.

I should remind you that you must get full backup of all your data before you do anything.

---

### Post by fatharraxman on 2010-12-25
[http://ubuntuforums.org/showthread.php?t=574725](http://ubuntuforums.org/showthread.php?t=574725)

---

### Post by Verbeck on 2010-12-25
from vista : right click my computer>manage>disk management>delete the  ubuntu partition
then, 
> 

[LIST=1]
[*]Put the Windows Vista or Windows 7 installation disc in the disc  drive, and then start the computer.
[*]Press a key when you are  prompted.
[*]Select a language, a time, a currency, a keyboard or  an input method, and then click **Next**.
[*]Click  **Repair your computer**.
[*]Click the  operating system that you want to repair, and then click **Next**.
[*]In the **System  Recovery Options** dialog box, click **Command  Prompt**.
[*]Type **Bootrec.exe***<space>***/FixMbr**,  and then press ENTER.
[/LIST]
that would restore the vista boot loader and remove grub

---

### Post by zuber786 on 2010-12-25
Thank you all but that video fixed it
it also removed grub and ubuntu 
i had to install easybcd 
click on bootloader setup
click write MBR
after
go to run type "diskmgmt.msc"
you will see the unname disk space under volume on it right click and select "delete volume" 
after deleting it on bottom there will be green box
right click on green box and click delete partition 
after that to merge partition 
on bottom right click on C:/ box and click extend volume
and click next, next, finish. you might have to restart.
enjoy

---

