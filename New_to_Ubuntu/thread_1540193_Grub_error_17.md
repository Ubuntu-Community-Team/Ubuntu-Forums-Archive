---
title: "Grub error 17"
date: 2010-07-27
forum: New to Ubuntu
---

### Post by lbug on 2010-07-27
Let me preface this by stating that I know I did wrong and I deserve what's coming to me.

I uninstalled 10.4 by deleting its partition from my dual-booting Sony Vaio VGN-TX7450p. Unfortunately, in addition to GRUB, I seem to have also deleted the recovery partition. As a result, I'm getting GRUB error 17 and can't boot to either an Ubuntu install disc or the Sony recovery disks, despite all manner of manipulation to BIOS.

So I have a bricked Vaio. Yay me!

I have a networked Mac and an external HD that I am willing to sacrifice. Can I install Ubuntu to the HD using the Mac (but in language the Vaio will understand), tell BIOS to boot to the HD, and then initiate some sort of recovery?

Any other ideas?

I know, I'm an idiot.

---

### Post by SaaTeeVaaGreen on 2010-07-27
you should be able to boot from a ubuntu LiveCD and sort things out from there. you may first need to change the boot order in your bios to boot from the cd drive first. first step should be check boot order, set to boot from cd first,then try booting from the ubuntu LiveCD and see how you get on from there.

---

### Post by stlsaint on 2010-07-27
You need to remove grub from the MBR of the harddrive and it back over to windows bootloader, which (if you didnt touch windows when you removed ubuntu) you should be able to boot into windows just fine. Now for the harddrive issue im not sure how that has come to be affected. I would suggest using other system to download windows recovery disc and use that MAC system to burn the cd then try in the vaio.
If that doesnt work than use the MAC to install ubuntu to a usb drive and try booting that on the vaio. If you can boot into the usb drive than from there you can remove grub.

---

### Post by lbug on 2010-07-27
> **SaaTeeVaaGreen said:**
> you should be able to boot from a ubuntu LiveCD and sort things out from there. you may first need to change the boot order in your bios to boot from the cd drive first. first step should be check boot order, set to boot from cd first,then try booting from the ubuntu LiveCD and see how you get on from there.

I made a LiveCD on my Mac (don't have the original install disc), made sure BIOS was set to the optical drive, but no luck booting.

---

### Post by lbug on 2010-07-27
> **stlsaint said:**
> You need to remove grub from the MBR of the harddrive and it back over to windows bootloader, 

Can you point me to instructions? I can only access the BIOS; I can't seem to get to a recovery console or similar window.


[QUOTE=stlsaint;9644250If that doesnt work than use the MAC to install ubuntu to a usb drive and try booting that on the vaio. If you can boot into the usb drive than from there you can remove grub.[/QUOTE]

Unfortunately, my BIOS doesn't give me the option to boot from a USB.

---

### Post by oldfred on 2010-07-27
You can use any linux liveCD to install a windows style boot loader. Many rescueCDs include lilo's boot loader as standard.

Restore basic windows boot loader - universe enabled from Ubuntu or liveCD
sudo apt-get install lilo
sudo lilo -M /dev/sda mbr
May show error messages about the rest of lilo missing, ignore, we just want MBR

If your windows is XP, run a tepair from it and run fixboot.

If you have Vista or & download this:
If your PC did not come with a complete Vista or Win7 installation CD, you can download a Recovery Disc at the following links:
Windows Vista/7 Recovery Disc - for repairs only
[http://neosmart.net/blog/2008/windows-vista-recovery-disc-download/](http://neosmart.net/blog/2008/windows-vista-recovery-disc-download/)
[http://neosmart.net/blog/2009/windows-7-system-repair-discs/](http://neosmart.net/blog/2009/windows-7-system-repair-discs/)
Vista will not repair XP (they create the boot sectors differently) but can run chkdsk.
[http://support.microsoft.com/kb/927392](http://support.microsoft.com/kb/927392)

How to use the Bootrec.exe tool in the Windows Recovery Environment to troubleshoot and repair startup issues in Windows
[http://support.microsoft.com/kb/927392](http://support.microsoft.com/kb/927392)
[http://www.sevenforums.com/tutorials/20864-mbr-restore-windows-7-master-boot-record.html](http://www.sevenforums.com/tutorials/20864-mbr-restore-windows-7-master-boot-record.html)
[http://windows7ultimate.windowsreinstall.com/repairwin7startup/indexthumbs.ht](http://windows7ultimate.windowsreinstall.com/repairwin7startup/indexthumbs.ht)

Above links summarized, see links if more detail desired
You will need to boot with your Vista/Windows 7 installation disk or repair disk. Hit Enter at the language selection prompt then hit "R" to get to the repair section. You can then select the automatic boot repair tool, but it often will not do any good. Then select the command prompt (console) and type in the following commands:
BootRec.exe /fixmbr   #updates MBR master boot record  do not run if you still want grub
chkdsk C: /r /f (may have to run /r or /f as separate entries) rerun until no errors
BootRec.exe /FixBoot  #updates PBR partition boot sector
BootRec.exe /ScanOs
BootRec.exe /RebuildBcd

---

