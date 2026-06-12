---
title: "I installed windows, and now I can't boot to Ubuntu"
date: 2009-01-14
forum: New to Ubuntu
---

### Post by cnhoffma on 2009-01-14
Here' the full story. I had Ubuntu and Windows XP living together on my computer. I decided I wanted to do a system restore. I re-installed windows and that went successful and normal. I installed Ubuntu, but by accident (and ignorance) I over-wrote the window OS by choosing Ubuntu to be installed on the one and only partition I had on my hard drive.

I then created a new partition for Windows and installed windows onto that partition. The install was successful, but now the boot OS Choice menu gives me two choices

Microsoft Windows XP Home Edition
Microsoft Windows XP Home Edition

Now I know that Ubuntu is on there still. I managed to mount my linux partition and I can that everything is there. For whatever reason, the OS choice menu no longer gives me the chance to boot to Ubuntu. I know that I can boot to Ubuntu, I just have to enable it somehow (somehow is where you guys come in). Where is the file that I must edit to enable booting to Ubuntu and who should I edit it?

---

### Post by theRightNee on 2009-01-14
well you would have to modify the menu.lst file, which would tell the grub bootloader which OS to boot. i am sure you can do this from windows, i just dont remember exactly how you do it...check the grub site for more information

after you manage to find the menu.lst file, add in the ubuntu partition, and it should work.

sorry to be so vague, booting isn't my forte =]
best of luck

---

### Post by handydan918 on 2009-01-14
Please post the output of ```
fdisk -l
``` This will give an idea of where you installed everything.

---

### Post by jemate18 on 2009-01-14
YOur windows install might have modified the MBR in which GRUB was installed.

Search the forum for "restoring GRUB after windows install"

---

### Post by cariboo on 2009-01-14
That is the Windows boot menu that is giving you the choice of XP home twice. To get rid of one of the entries you will have to edit c:\boot.ini.

To be able to boot in to Ubuntu, boot from the LiveCD and follow the instructions [here]("http://ubuntuforums.org/showthread.php?t=224351").

---

