---
title: "help BootMGR problem"
date: 2010-12-18
forum: New to Ubuntu
---

### Post by idavid on 2010-12-18
Having this problem already try to do this running windows vista 
command prompt
bootrec /rebuildbcd 
not working!!!
as it know working with the ubuntu live cd thanks God but really need to recover my information.
after installing ubuntu 10.04, already check gparted and it says  
path: dev/sda1
status : not mounted
already try to do this to...
sudo mkdir /media/windows/
after that sudo mount 
plz any body!!!Help me out.!! sure it's something that can be fix!!

---

### Post by cipherboy_loc on 2010-12-18
Try running the boot script that is in my signature from the LiveCD. Post the results.txt as an attachment.


Cipherboy

---

### Post by idavid on 2010-12-18
Here is the attachment,

---

### Post by idavid on 2010-12-18
thanks for your reply, here it's.

---

### Post by cipherboy_loc on 2010-12-18
Try this:

[http://neosmart.net/dl.php?id=1](http://neosmart.net/dl.php?id=1)

---

### Post by Rubi1200 on 2010-12-18
@[cipherboy_loc]("http://ubuntuforums.org/member.php?u=1066963")

> Try this:

[http://neosmart.net/dl.php?id=1](http://neosmart.net/dl.php?id=1)

Are you sure? Have you looked at the results?

```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Windows is installed in the MBR of /dev/sda

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /ubuntu/disks/swap.disk

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders, total 156301488 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x00000080

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63   156,280,319   156,280,257   7 HPFS/NTFS


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda1        B030B3F930B3C51E                       ntfs                                     

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

rootfs           /                        rootfs     (rw)
/dev/scd0        /cdrom                   iso9660    (ro,noatime)
/dev/loop0       /rofs                    squashfs   (ro,noatime)

```

---

### Post by idavid on 2010-12-18
Hey that's an .exe file i'm working on livecd can't install that !!

---

### Post by wilee-nilee on 2010-12-18
Your description is confusing and the script is showing a fairly messed up setup.

What is supposed to be on the HD and what do you want?

---

### Post by wilee-nilee on 2010-12-18
> **cipherboy_loc said:**
> Try this:

[http://neosmart.net/dl.php?id=1](http://neosmart.net/dl.php?id=1)

Please read the scripts and don't push easybcd this is a Linux forum easybcd is a last ditch for most people and wont work here. There is no Ubuntu install showing in the script.

---

### Post by idavid on 2010-12-18
I install ubuntu using wubi it took 10Gb of th HD and left the 70Gb to vista, after that i was trying to have access to my vista files/ so i did this!.

sudo mkdir /media/windows/
sudo mount 

after that work with the files and turn off the pc, now when i'm trying to load again ubuntu it showme BootMGR is missing!
is that clear?

---

### Post by idavid on 2010-12-18
> **wilee-nilee said:**
> Your description is confusing and the script is showing a fairly messed up setup.

What is supposed to be on the HD and what do you want?

This is what i did to install it!

[http://www.ubuntu.com/desktop/get-ubuntu/windows-installer](http://www.ubuntu.com/desktop/get-ubuntu/windows-installer)

---

### Post by wilee-nilee on 2010-12-18
> **idavid said:**
> I install ubuntu using wubi it took 10Gb of th HD and left the 70Gb to vista, after that i was trying to have access to my vista files/ so i did this!.

sudo mkdir /media/windows/
sudo mount 

after that work with the files and turn off the pc, now when i'm trying to load again ubuntu it showme BootMGR is missing!
is that clear?

The script does not show a wubi install and is missing files needed to boot Vista does it boot?

If you had Vista working it would look like this. The hignlighted is missing and shows Linux there instead.

sda1: __________________________________________________ ________
File system: ntfs
Boot sector type: Windows Vista
Boot sector info: No errors found in the Boot Parameter Block.
Operating System: Windows Vista
Boot files/dirs: **/bootmgr /Boot/BCD /Windows/System32/winload.exe**


A wubi install would show this.

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /bootmgr /Boot/BCD /Windows/System32/winload.exe 
                       /wubildr.mbr /ubuntu/winboot/wubildr.mbr /wubildr 
                       /ubuntu/winboot/wubildr /ubuntu/disks/root.disk 
                       /ubuntu/disks/swap.disk

sda1/Wubi: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu maverick (development 
                       branch)
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab


Your missing the full wubi reference in the script and no Vista boot files.

---

### Post by Rubi1200 on 2010-12-18
idavid,
what wilee-nilee is trying to say is that whatever you tried to do did not work, at least not according to the results of the script.

You have the failed remnants of a Wubi install and no Windows boot files.

> File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
[COLOR=Red]    Operating System:  [/COLOR]
    Boot files/dirs:   [COLOR=Red]/ubuntu/disks/swap.disk[/COLOR]You need to tell us the following things now:
Do you have a Windows installation/recovery disk?
Did you make backups of your important data?

EDIT: sorry wilee-nilee, you explained it better than me.

---

### Post by wilee-nilee on 2010-12-18
> **Rubi1200 said:**
> idavid,
what wilee-nilee is trying to say is that whatever you tried to do did not work, at least not according to the results of the script.

You have the failed remnants of a Wubi install and no Windows boot files.

You need to tell us the following things now:
Do you have a Windows installation/recovery disk?
Did you make backups of your important data?

EDIT: sorry wilee-nilee, you explained it better than me.

Thanks sometimes I need a translator and a closer look at the script.;)

---

### Post by idavid on 2010-12-18
> **Rubi1200 said:**
> idavid,
what wilee-nilee is trying to say is that whatever you tried to do did not work, at least not according to the results of the script.

You have the failed remnants of a Wubi install and no Windows boot files.

You need to tell us the following things now:
Do you have a Windows installation/recovery disk?
Did you make backups of your important data?

EDIT: sorry wilee-nilee, you explained it better than me.

I do have a windows disk! an i already try to do this..
[http://www.howtogeek.com/howto/windows-vista/fixing-bootmgr-is-missing-error-while-trying-to-boot-windows-vista/](http://www.howtogeek.com/howto/windows-vista/fixing-bootmgr-is-missing-error-while-trying-to-boot-windows-vista/)

using system recovery and command prompt.

Sadly i don't have a backup of my data!. ... i know ... !! :(
**if you need me to run another scripts.. let me know... the script that i upload it's what the 1st guy told me to do!.**

---

### Post by wilee-nilee on 2010-12-18
OP so you need a install Vista disc or a recovery, here is a recovery link and the commands needed to hopefully get Vista back in shape. Notice the W7 http lnk that along with the instructions gets you to the command line on the recovery disc.
[http://neosmart.net/blog/2008/windows-vista-recovery-disc-download/](http://neosmart.net/blog/2008/windows-vista-recovery-disc-download/)

1) Boot with your Vista/Windows 7 installation disk. Hit <Enter> at the language selection prompt then hit <R> for Repair to get to the Repair section. 
2) Select the command prompt (console) and type in the following commands:
BootRec.exe /fixmbr (#updates MBR master boot record...do not run if you still want grub)
chkdsk /r
BootRec.exe /FixBoot (#updates PBR partition boot)
BootRec.exe /ScanOs
BootRec.exe /RebuildBcd
[http://www.sevenforums.com/tutorials/20864-mbr-restore-windows-7-master-boot-record.html](http://www.sevenforums.com/tutorials/20864-mbr-restore-windows-7-master-boot-record.html)

---

### Post by cipherboy_loc on 2010-12-18
> **wilee-nilee said:**
> Please read the scripts and don't push easybcd this is a Linux forum easybcd is a last ditch for most people and wont work here. There is no Ubuntu install showing in the script.

Sorry about that. Is there any tool that runs on Linux that you would recommend to restore the Windows boot loader, or would that be a violation of bootloader's license? 


Thanks for correcting me,
Cipherboy

---

### Post by wilee-nilee on 2010-12-18
> **cipherboy_loc said:**
> Sorry about that. Is there any tool that runs on Linux that you would recommend to restore the Windows boot loader, or would that be a violation of bootloader's license? 


Thanks for correcting me,
Cipherboy

No its not against any rules. Lilo will restore the bootloader and boot MS. Here are the commands for you if needed from a Live Ubuntu cd.

Restore basic windows boot loader - universe enabled
sudo apt-get install lilo
sudo lilo -M /dev/sda mbr
May show error messages about the rest of lilo missing, ignore, we just want MBR.

This is if the HD is sda, if another like sdb use accordingly.

---

