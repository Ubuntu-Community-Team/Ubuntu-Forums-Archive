---
title: "How do i edit the OS list on GRUB?"
date: 2009-07-29
forum: New to Ubuntu
---

### Post by pbateman on 2009-07-29
Hi 
I installed Ubuntu 9.04 in my laptop recently but the partition created automatically was too small for it. 
The drive is being shared with Windows, so I re-installed Ubuntu, this time manually creating the partition.
Everything is ok now except for the fact that at bootup i now get 2 instances of Ubuntu listed (the old install and the new one) plus Windows at the end. 
I know in Windows when this happens you can just edit the boot.ini file and delete one of the instances, however I do not know if this is also possible in Ubuntu?
Again its not something that's creating problems per se, but wouldn't mind editing it so as to keep it simpler.
Thanks!

---

### Post by cosmicappuccino on 2009-07-29
I believe that /boot/grub/menu.lst is the file corresponding to boot.ini. (You'll have to open it using sudo.)

If you've played with boot.ini before, you might well be able to figure out what you need to do in menu.lst. I've only played with it a little and so don't want to give you instructions, in case I'm wrong...

Hope this helps (:

---

### Post by oldfred on 2009-07-30
Normally you have several versions of Ubuntu to choose from in Grub.
Everytime a new kernal is updated the grub menu adds it as the first and a recovery version in case of problems. You start with 2 - regular and recovery and it grows to a number in menu.lst called howmany, which may be commented out with a # sign.
If you want to edit menu.lst you should make a copy/backup so an error in editing can easier be corrected by booting the cd and copying the orginal back.
To see what kernal you are using
[COLOR=DarkRed]uname -a[/COLOR]
make a copy of current menu.lst
[COLOR=DarkRed]cp /boot/grub/menu.lst /boot/grub/menu.lst.backup[/COLOR]
Use gksudo for graphical applications, edit at your own risk
[COLOR=DarkRed]gksudo gedit /boot/grub/menu.lst[/COLOR]

menu.lst is used by grub - info on grub
[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows#Recovering%20GRUB%20Manually](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows#Recovering%20GRUB%20Manually)

---

### Post by presence1960 on 2009-07-30
before you go changing anything why don't you post your menu.lst contents back here. Open a terminal and run ```
gksu gedit /boot/grub/menu.lst
``` BTW that is a lowercase L in .lst

Post the output of that command back here.

---

### Post by pbateman on 2009-07-30
Thanks guys,
I actually went ahead and did this last night. I backed up the menu.lst file, then i opened the file and saw the list of the versions I get at bootup. I had taken note of the one that was the correct one so I deleted the listings for the old version. I rebooted and worked great!
Thanks again for the help!

---

