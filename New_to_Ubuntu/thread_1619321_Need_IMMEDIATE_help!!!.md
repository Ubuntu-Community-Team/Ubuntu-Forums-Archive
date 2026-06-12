---
title: "Need IMMEDIATE help!!!"
date: 2010-11-11
forum: New to Ubuntu
---

### Post by UnknownFear on 2010-11-11
I had Ubuntu and Windows 7 dual-booted. I decided to simply delete Ubuntu via Windows 7 in the partition manager, which was stupid because now, because Ubuntu automatically makes itself the default boot, I can not boot into Windows. Says grub: boot error or something. I know I didn't delete Windows by accident cause I can still see it in gparted. Can someone please tell me how to boot Windows?

I have tried updating grub, but nothing seems to work.

---

### Post by nm_geo on 2010-11-11
Sound like you need to restore your MBR for WinDoz 7. I was reading about that earlier and will let an someone who knows more than I explain.

---

### Post by UnknownFear on 2010-11-11
> **nm_geo said:**
> Sound like you need to restore your MBR for WinDoz 7. I was reading about that earlier and will let an someone who knows more than I explain.

Found it:

[http://ubuntuforums.org/showthread.php?t=622828](http://ubuntuforums.org/showthread.php?t=622828)

Going to try it now. PLEASE WORK!!!!!

---

### Post by nm_geo on 2010-11-11
It will I bet.

---

### Post by kroq-gar78 on 2010-11-11
you have to remove the ubuntu boot entries in grub.

you have to boot into a live cd
then, go to "Places" and mount the harddrive (just click on it; should be say "80GB" disk or something...)
then, go to command prompt (Applications -> Accessories -> Terminal) and then type this:
```
cd /media/
```press enter, and then
```
ls
``` and press enter
if you did the first part correctly, there should be something that was output (might be something that looks like "random" letters and numbers)
then, type a quotation mark
select the output of the "ls" part with your mouse (drag mouse)
do CTRL-SHIFT-C
do CTRL-SHIFT-V
and then type another quotation mark

now, you're in your computer's system
run (type & hit enter) this:
```
cd /boot/grub
```then
```
sudo nano grub.cfg
```this is the thing where the entries are stored.
I am a little fuzzy on this, so google "edit grub entries" and follow the tutorials there on how to delete them. Because I might mess up your computer, I won't tell you of how I THINK how to do it.

UPDATE: just do nm_geo's way

---

### Post by hansdown on 2010-11-11
Hi UnknownFear.

A super grub disk live cd will fix the mbr.

[http://en.kioskea.net/faq/2677-super-grub-disk-live-cd](http://en.kioskea.net/faq/2677-super-grub-disk-live-cd)

---

### Post by beew on 2010-11-11
I don't know if this is the same in Windoze 7, but in XP all you need to do is to stick the XP install disk into the CD drive and boot from it and then go to the repair option and type```
fixmbr
``` and reboot (remove the CD of course)

Now if you don't have a Windoze CD you would have to get advice from more advanced users. :)

---

### Post by wilee-nilee on 2010-11-11
It is real straight forward. If all you have is Windows 7 download this recovery and run the command I highlighted the rest are just other options from the command line repair.
[http://neosmart.net/blog/2009/windows-7-system-repair-discs/](http://neosmart.net/blog/2009/windows-7-system-repair-discs/)

1) Boot with your Vista/Windows 7 installation disk. Hit <Enter> at the language selection prompt then hit <R> for Repair to get to the Repair section. 
2) Select the command prompt (console) and type in the following commands:
**BootRec.exe /fixmbr** (#updates MBR master boot record...do not run if you still want grub)
chkdsk /r
BootRec.exe /FixBoot (#updates PBR partition boot)
BootRec.exe /ScanOs
BootRec.exe /RebuildBcd
[http://www.sevenforums.com/tutorials/20864-mbr-restore-windows-7-master-boot-record.html](http://www.sevenforums.com/tutorials/20864-mbr-restore-windows-7-master-boot-record.html)

fixmbr alone wont fix anything but XP, you have to have the correct command.

Really I would suggest posting the bootscript in my signature before doing any thing. In code tags as described in the signature. This will give us a better picture of the whole setup

---

