---
title: "Grub Loading stage 1.5, Grub loading - Error 22, won't boot from bootdisk"
date: 2010-12-06
forum: New to Ubuntu
---

### Post by susancorless on 2010-12-06
Hello,

I am new to Linux and have to admit I know nothing. My ex was trying to convert me to Linux and installed Ubuntu on my laptop + partitioned it. He never finished it and he's not around now.

So I thought (here's where my in experience comes in!) how hard can it be to just remove the partition! Well using his partition wizard I was able to delete the partition easy enough, and thought it would just flip back to auto loading windows (I've had a grub to use for the past I don't know how many months and it auto loaded Ubuntu after about 15 secs if I didn't select the one which would load windows).

How wrong was I (I see you shake your head!) Now I get the following error on screen

GRUB Loading Stage 1.5.

GRUB Loading, please wait...
Error 22

I've searched for the error and found loads of stuff and instructions on what to do, only issue is I've downloaded a bootdisk (I'm using Vista 32 bit) but I can't boot from it. I can't get into my BIOS, I don't have a Vista CD and I really don't know what to do next.

Can anyone help?

Thanks
Susan

---

### Post by oldfred on 2010-12-06
Assuming your Vista is ok.

From Ubuntu liveCD (if you do this before deleting Ubuntu then you do not have any issues):
Restore basic windows boot loader - universe enabled
sudo apt-get install lilo
sudo lilo -M /dev/sda mbr
May show error messages about the rest of lilo missing, ignore, we just want MBR

The windows way:
How to use the Bootrec.exe tool in the Windows Recovery Environment to troubleshoot and repair startup issues in Windows
[http://support.microsoft.com/kb/927392](http://support.microsoft.com/kb/927392)
[http://www.sevenforums.com/tutorials/20864-mbr-restore-windows-7-master-boot-record.html](http://www.sevenforums.com/tutorials/20864-mbr-restore-windows-7-master-boot-record.html)
[http://windows7ultimate.windowsreinstall.com/repairwin7startup/indexthumbs.ht](http://windows7ultimate.windowsreinstall.com/repairwin7startup/indexthumbs.ht)

Above links summarized, see links if more detail desired
You will need to boot with your Vista/Windows 7 installation disk or repair disk. Hit Enter at the language selection prompt then hit "R" to get to the repair section. You can then select the automatic boot repair tool, but it often will not do any good. Then select the command prompt (console) and type in the following commands:
BootRec.exe /fixmbr   #updates MBR master boot record  do not run if you still want grub
chkdsk C: /r /f (may have to run /r or /f as separate entries) rerun until no errors

If your PC did not come with a complete Vista or Win7 installation CD, you can download a Recovery Disc at the following links:
Windows Vista/7 Recovery Disc - for repairs only
[http://neosmart.net/blog/2008/windows-vista-recovery-disc-download/](http://neosmart.net/blog/2008/windows-vista-recovery-disc-download/)
[http://neosmart.net/blog/2009/windows-7-system-repair-discs/](http://neosmart.net/blog/2009/windows-7-system-repair-discs/)
Vista/7 will not repair XP (they create the boot sectors differently) but can run chkdsk.
[http://support.microsoft.com/kb/927392](http://support.microsoft.com/kb/927392)

You need to be able to get into BIOS to change boot order to boot the CD. Most systems show the BIOS sceen for a few seconds and at the bottom will say hit f2 or Del key to enter BIOS. Often another key like f12 (on my system) lets you choose a one time alternate boot which should also work.

---

### Post by susancorless on 2010-12-06
You are amazing!!! It's come back to live :)

I managed to go down the windows way using Bootrec.exe, the location you gave for the bootdisk worked, I must have had a dud download before or something.

The \fixmbr worked and now when I turn on my laptop it comes up with 'welcome to the partition wizard' and then windows loads :).  I don't however get any option to get into BIOS before this loads?

---

### Post by oldfred on 2010-12-06
Glad it worked.

I do not know why you would get welcome to partition wizard unless somehow the BIOS default screen is loading the wrong graphic??

It seems you may have figured out how to boot CD?

On computers that I did not know what key to use for BIOS, I would just start hitting keys. Often del, f2 or f10. One time boot key is often f12. When that did not work as you only have a few seconds before it is done with BIOS and starts booting, just hit keys. Your computer manual should say or you can search Internet.

---

### Post by susancorless on 2010-12-06
ok I'll see if I can get into BIOS to make that change, but it's good that it's working now anyway!

---

