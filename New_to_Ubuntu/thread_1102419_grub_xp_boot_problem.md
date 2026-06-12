---
title: "grub xp boot problem"
date: 2009-03-21
forum: New to Ubuntu
---

### Post by superalanliu on 2009-03-21
Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       88217   708603021   83  Linux
/dev/sda2           88218       91201    23968980    5  Extended
/dev/sda5           88218       91201    23968948+  82  Linux swap / Solaris

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x2e612e62

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1       60801   488384001    7  HPFS/NTFS

Disk /dev/sdc: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x2e142e14

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *           1       60800   488375968+   7  HPFS/NTFS
superalanliu@superalanliu-desktop:~$ cat /boot/grub/menu.lst
hiddenmenu
default 0
timeout 5

### BEGIN AUTOMAGIC KERNELS LIST
## lines between the AUTOMAGIC KERNELS LIST markers will be modified
## by the debian update-grub script except for the default options below

## DO NOT UNCOMMENT THEM, Just edit them to your needs

## ## Start Default Options ##
## default kernel options
## default kernel options for automagic boot options
## If you want special options for specific kernels use kopt_x_y_z
## where x.y.z is kernel version. Minor versions can be omitted.
## e.g. kopt=root=/dev/hda1 ro
##      kopt_2_6_8=root=/dev/hdc1 ro
##      kopt_2_6_8_2_686=root=/dev/hdc2 ro
# kopt=root=UUID=df94d33d-f3bf-4939-91b9-735207ab6f3d ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=df94d33d-f3bf-4939-91b9-735207ab6f3d

## should update-grub create alternative automagic boot options
## e.g. alternative=true
##      alternative=false
# alternative=true

## should update-grub lock alternative automagic boot options
## e.g. lockalternative=true
##      lockalternative=false
# lockalternative=false

## additional options to use with the default boot option, but not with the
## alternatives
## e.g. defoptions=vga=791 resume=/dev/hda5
# defoptions=quiet splash

## should update-grub lock old automagic boot options
## e.g. lockold=false
##      lockold=true
# lockold=false

## Xen hypervisor options to use with the default Xen boot option
# xenhopt=

## Xen Linux kernel options to use with the default Xen boot option
# xenkopt=console=tty0

## altoption boot targets option
## multiple altoptions lines are allowed
## e.g. altoptions=(extra menu suffix) extra boot options
##      altoptions=(recovery) single
# altoptions=(recovery mode) single

## controls how many kernels should be put into the menu.lst
## only counts the first occurence of a kernel, not the
## alternative kernel options
## e.g. howmany=all
##      howmany=7
# howmany=all

## should update-grub create memtest86 boot option
## e.g. memtest86=true
##      memtest86=false
# memtest86=true

## should update-grub adjust the value of the default booted system
## can be true or false
# updatedefaultentry=false

## should update-grub add savedefault to the default options
## can be true or false
# savedefault=false

## ## End Default Options ##

title Ubuntu 8.10, kernel 2.6.27-11-generic
kernel /boot/vmlinuz-2.6.27-11-generic root=UUID=df94d33d-f3bf-4939-91b9-735207ab6f3d ro quiet splash
initrd /boot/initrd.img-2.6.27-11-generic

title Windows XP Professional
root (hd1,0)
makeactive
chainloader +1

title Ubuntu 8.10, kernel 2.6.27-11-generic (recovery mode)
kernel /boot/vmlinuz-2.6.27-11-generic root=UUID=df94d33d-f3bf-4939-91b9-735207ab6f3d ro  single
initrd /boot/initrd.img-2.6.27-11-generic

title Ubuntu 8.10, kernel 2.6.27-7-generic
kernel /boot/vmlinuz-2.6.27-7-generic root=UUID=df94d33d-f3bf-4939-91b9-735207ab6f3d ro quiet splash
initrd /boot/initrd.img-2.6.27-7-generic

title Ubuntu 8.10, kernel 2.6.27-7-generic (recovery mode)
kernel /boot/vmlinuz-2.6.27-7-generic root=UUID=df94d33d-f3bf-4939-91b9-735207ab6f3d ro  single
initrd /boot/initrd.img-2.6.27-7-generic

title Ubuntu 8.10, memtest86+
kernel /boot/memtest86+.bin

### END DEBIAN AUTOMAGIC KERNELS LIST

Included the relevant info. I tried searching for a whole day to no avail. I bet someone experienced can probably figure it out in like 10 minutes. Thanks for the help in advance!

---

### Post by yeats on 2009-03-21
> Included the relevant info. I tried searching for a whole day to no avail. I bet someone experienced can probably figure it out in like 10 minutes. Thanks for the help in advance!

Maybe I'm missing something here, but what is the problem you're having? :-)

---

### Post by RetchingRabbit on 2009-03-21
Try modifying your windows section so it looks like this:

```
title Windows XP
root (hd1,0)
makeactive
map (hd0) (hd1)
map (hd1) (hd0)
chainloader +1
```

I think that will do it...
The trouble is that windows REALLY wants to be the first and only system ....

---

### Post by superalanliu on 2009-03-21
> **RetchingRabbit said:**
> Try modifying your windows section so it looks like this:

```
title Windows XP
root (hd1,0)
makeactive
map (hd0) (hd1)
map (hd1) (hd0)
chainloader +1
```

I think that will do it...
The trouble is that windows REALLY wants to be the first and only system ....

Tried it, gave me "NTLDR is missing" and then press alt ctrl del for reboot. The original problem is that my screen would say loading and do nothing. Now its the NTLDR is missing problem. Help please! Missing my windows gaming. :(

---

### Post by meierfra. on 2009-03-21
Try 

title Windows XP
root (hd0,0)
chainloader +1


Also you should put your Windows item either above the line

### BEGIN AUTOMAGIC KERNELS LIST

or below the line

### END DEBIAN AUTOMAGIC KERNELS LIST

(Otherwise your Windows item will disappear during the next kernel update)

**If this did not work:**

In order to get a clearer picture of your setup, I suggest to boot into  Ubuntu  and  download the Boot Info Script to  your desktop:

[https://sourceforge.net/projects/bootinfoscript/]("https://sourceforge.net/projects/bootinfoscript/")

Then open a terminal (Applications > Accessories > Terminal) and type:

```
sudo bash ~/Desktop/boot_info_script*.sh
```

That will create a "RESULTS.txt" file in the same directory from where the script is run, namely your desktop; please copy/paste the contents of the RESULTS.txt file to your next post, highlight the copied text, and click the pound/hash sign "#" graphic button in the Ubuntu forum message box so that the text will get "code" tags put around it. The results of that script will help clarify your setup and hopefully what the solution to your booting problem might be.

---

### Post by superalanliu on 2009-03-21
here are the results

```
============================= Boot Info Summary: ==============================

 => Grub0.97 is installed in the MBR of /dev/sda and looks on the same drive 
    in partition #1 for /boot/grub/stage2 and /boot/grub/menu.lst.
 => No boot loader is installed in the MBR of /dev/sdb
 => Windows is installed in the MBR of /dev/sdc

sda1: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 8.10
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab

sda2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdb1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdc1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 750.1 GB, 750156374016 bytes
255 heads, 63 sectors/track, 91201 cylinders, total 1465149168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x46f146f0

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63 1,417,206,104 1,417,206,042  83 Linux
/dev/sda2       1,417,206,105 1,465,144,064    47,937,960   5 Extended
/dev/sda5       1,417,206,168 1,465,144,064    47,937,897  82 Linux swap / Solaris


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x2e612e62

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *             63   976,768,064   976,768,002   7 HPFS/NTFS


Drive: sdc ___________________ _____________________________________________________

Disk /dev/sdc: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x2e142e14

Partition  Boot         Start           End          Size  Id System

/dev/sdc1    *             63   976,751,999   976,751,937   7 HPFS/NTFS


blkid -c /dev/null: ____________________________________________________________

/dev/sda1: UUID="df94d33d-f3bf-4939-91b9-735207ab6f3d" TYPE="ext3" 
/dev/sda5: UUID="964dc7eb-6624-4217-b2a4-d15d00c9fb89" TYPE="swap" 
/dev/sdb1: UUID="AAF83418F833E0ED" LABEL="Jdrama & Anime" TYPE="ntfs" 
/dev/sdc1: UUID="14F09BFAF09BE072" LABEL="Programs" TYPE="ntfs" 

=============================== "mount" output: ===============================

/dev/sda1 on / type ext3 (rw,relatime,errors=remount-ro)
tmpfs on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
/proc on /proc type proc (rw,noexec,nosuid,nodev)
sysfs on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,nosuid,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
tmpfs on /dev/shm type tmpfs (rw,nosuid,nodev)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=620)
fusectl on /sys/fs/fuse/connections type fusectl (rw)
lrm on /lib/modules/2.6.27-11-generic/volatile type tmpfs (rw,mode=755)
securityfs on /sys/kernel/security type securityfs (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/superalanliu/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=superalanliu)


=========================== sda1/boot/grub/menu.lst: ===========================

hiddenmenu
default 1
timeout 30

title Windows XP
root (hd1,0)
makeactive
map (hd0) (hd1)
map (hd1) (hd0)
chainloader +1

### BEGIN AUTOMAGIC KERNELS LIST
## lines between the AUTOMAGIC KERNELS LIST markers will be modified
## by the debian update-grub script except for the default options below

## DO NOT UNCOMMENT THEM, Just edit them to your needs

## ## Start Default Options ##
## default kernel options
## default kernel options for automagic boot options
## If you want special options for specific kernels use kopt_x_y_z
## where x.y.z is kernel version. Minor versions can be omitted.
## e.g. kopt=root=/dev/hda1 ro
##      kopt_2_6_8=root=/dev/hdc1 ro
##      kopt_2_6_8_2_686=root=/dev/hdc2 ro
# kopt=root=UUID=df94d33d-f3bf-4939-91b9-735207ab6f3d ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=df94d33d-f3bf-4939-91b9-735207ab6f3d

## should update-grub create alternative automagic boot options
## e.g. alternative=true
##      alternative=false
# alternative=true

## should update-grub lock alternative automagic boot options
## e.g. lockalternative=true
##      lockalternative=false
# lockalternative=false

## additional options to use with the default boot option, but not with the
## alternatives
## e.g. defoptions=vga=791 resume=/dev/hda5
# defoptions=quiet splash

## should update-grub lock old automagic boot options
## e.g. lockold=false
##      lockold=true
# lockold=false

## Xen hypervisor options to use with the default Xen boot option
# xenhopt=

## Xen Linux kernel options to use with the default Xen boot option
# xenkopt=console=tty0

## altoption boot targets option
## multiple altoptions lines are allowed
## e.g. altoptions=(extra menu suffix) extra boot options
##      altoptions=(recovery) single
# altoptions=(recovery mode) single

## controls how many kernels should be put into the menu.lst
## only counts the first occurence of a kernel, not the
## alternative kernel options
## e.g. howmany=all
##      howmany=7
# howmany=all

## should update-grub create memtest86 boot option
## e.g. memtest86=true
##      memtest86=false
# memtest86=true

## should update-grub adjust the value of the default booted system
## can be true or false
# updatedefaultentry=false

## should update-grub add savedefault to the default options
## can be true or false
# savedefault=false

## ## End Default Options ##

title Ubuntu 8.10, kernel 2.6.27-11-generic
kernel /boot/vmlinuz-2.6.27-11-generic root=UUID=df94d33d-f3bf-4939-91b9-735207ab6f3d ro quiet splash
initrd /boot/initrd.img-2.6.27-11-generic

title Ubuntu 8.10, kernel 2.6.27-11-generic (recovery mode)
kernel /boot/vmlinuz-2.6.27-11-generic root=UUID=df94d33d-f3bf-4939-91b9-735207ab6f3d ro  single
initrd /boot/initrd.img-2.6.27-11-generic

title Ubuntu 8.10, kernel 2.6.27-7-generic
kernel /boot/vmlinuz-2.6.27-7-generic root=UUID=df94d33d-f3bf-4939-91b9-735207ab6f3d ro quiet splash
initrd /boot/initrd.img-2.6.27-7-generic

title Ubuntu 8.10, kernel 2.6.27-7-generic (recovery mode)
kernel /boot/vmlinuz-2.6.27-7-generic root=UUID=df94d33d-f3bf-4939-91b9-735207ab6f3d ro  single
initrd /boot/initrd.img-2.6.27-7-generic

title Ubuntu 8.10, memtest86+
kernel /boot/memtest86+.bin

### END DEBIAN AUTOMAGIC KERNELS LIST


=============================== sda1/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=df94d33d-f3bf-4939-91b9-735207ab6f3d /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda5
UUID=964dc7eb-6624-4217-b2a4-d15d00c9fb89 none            swap    sw              0       0

=================== sda1: Location of files loaded by Grub: ===================


 283.4GB: boot/grub/menu.lst
 283.5GB: boot/grub/stage2
 283.4GB: boot/initrd.img-2.6.27-11-generic
 283.5GB: boot/initrd.img-2.6.27-7-generic
 283.5GB: boot/vmlinuz-2.6.27-11-generic
 283.5GB: boot/vmlinuz-2.6.27-7-generic
 283.4GB: initrd.img
 283.5GB: initrd.img.old
 283.5GB: vmlinuz
 283.5GB: vmlinuz.old
```

Thanks for the help!

I noticed that XP was on the 3rd drive so I already tried: 

{

title Windows XP
root (hd2,0)
chainloader +1

}

*stuck on loading and does nothing

as well as 
{
title Windows XP
root (hd1,0)
makeactive
map (hd0) (hd1)
map (hd1) (hd0)
chainloader +1
}

*Gives me the NTLDR thing

---

### Post by meierfra. on 2009-03-21
Well, your "ntldr" is really missing (as well as a couple of other files). Did you delete or format any partitions when you installed Ubuntu?
To get your boot files back:

Download this file: [http://ubuntuforums.org/attachment.php?attachmentid=73056&d=1212690573](http://ubuntuforums.org/attachment.php?attachmentid=73056&d=1212690573)
and save it to your Desktop. Then

```

sudo mount /dev/sdc1 /mnt
cd /mnt
sudo tar -xvzf ~/Desktop/Archive.tar.gz
ls /mnt

```

The last command lists all the files in  the root directory of your Windows partition.  Make sure that you have  now of the files "boot.ini", "NTLDR" and "NTDETECT.COM". 
From what you said, and from RESULTS.txt, it seems that XP is on the third hard drive (/dev/sdc1). You should double check on  that. If XP is actually  on /dev/sdb1  you would have to use "/dev/sdb1" in the above "mount" command.



Add the following to the very end of menu.lst

title Windows XP  (hd1)
root (hd1,0)
makeactive
map (hd0) (hd1)
map (hd1) (hd0)
chainloader +1

title Windows XP  (hd2)
root (hd2,0)
makeactive
map (hd0) (hd2)
map (hd2) (hd0)
chainloader +1


Reboot and try both entries. If one  of the works, you can delete the other from menu.lst. If none of them works, report all error messages you got.

---

### Post by superalanliu on 2009-03-21
Yep, I think its confirmed that windows in on HD2. It displays a different error now so I think we're getting closer. :)

It says something along the lines of: windows failed to load because
/system32/ntoskrnl.exe is missing. O.O

---

### Post by meierfra. on 2009-03-21
> Yep, I think its confirmed that windows in on HD2
??? Did you mean HD3? 
 If you aren't sure, just put the three boot files on  /dev/sdb1 and on  /dev/sdc1

> /system32/ntoskrnl.exe is missing
There is a bug in grub, which sometimes is causing this messsage. Or  the file is really missing.

To check whether the file is missing:

```
sudo mount /dev/sdc1 /mnt
ls  -l /mnt/system32/
sudo umount /mnt
sudo mount /dev/sdb1 /mnt
ls  -l /mnt/system32/

```


Also, lets see whether you can boot into XP without Grub: Set your bios to boot from the XP drive. Then you  should be able to  boot directly into XP.

---

### Post by superalanliu on 2009-03-21
Tried booting via bios: my computer beeps really fast continuously. I don't think there even IS a system32 folder anymore in my windows drive. I'm guessing that I'll need to repair windows with the installation disc, but won't that kill of my ubuntu and grub? Should I unplug my sata connection to my ubuntu HD before fixing windows?

found the file.. my system32 folder is in: drive/WINDOWS/system32. O.O. The ntoskrnl.exe is still there! What's wrong with the boot? :(

---

### Post by meierfra. on 2009-03-21
> /WINDOWS/system32

My bad. I knew that and should have   given you the correct path.

> Tried booting via bios: my computer beeps really fast continuously. 

Are you sure you are booting from the Windows drive?  Try booting from the other drive.

---

### Post by superalanliu on 2009-03-21
yeah, the long beep came from the wrong drive. Anyways, it gave the same error as grub! missing the ntosknl.exe even though I see the file when I mount my drive. Are we getting close now that grub/bios is displaying the same error?

Thanks for all your help meierfra!

---

### Post by meierfra. on 2009-03-22
> Are we getting close now that grub/bios is displaying the same error?
It means that it is a plain Windows problem and unrelated to grub.

Maybe the boot files I gave you got corrupted somehow.
Could you attach the boot.ini file to your next post. Mount your windows partition as before. Then you can find boot.ini in the folder /mnt.
I need the file as an attachment, since I want to make sure that the line breaks are correct.

Also check  out this link:

[http://support.microsoft.com/kb/314477]("http://support.microsoft.com/kb/314477")

It has various suggestions how to fix the "missing Ntoskrnl.exe" problem.

---

### Post by killerdogg77 on 2009-03-22
Check your windows boot.ini file make sure it loads to the right hd

---

### Post by killerdogg77 on 2009-03-22
Check your windows boot.ini file make sure it loads to the right hd.

---

### Post by superalanliu on 2009-03-22
boot ini file attached. I can't make sense of the boot file

---

### Post by meierfra. on 2009-03-22
There does not seem to be anything wrong with "boot.ini".  Did you put the boot files on /dev/sdb1 and /dev/sdc1 by now? 

Let me know if you need  help with the instruction from  the link in my last post.

---

### Post by superalanliu on 2009-03-22
I'll repair windows later today, just wondering. If I unplug my ubuntu HD, will grub be safe?

---

### Post by killerdogg77 on 2009-03-22
If your windows partion is on hd3 its tring to boot to the wrong hd,Try changing the partion number in boot file to 3


sorry for the double post

---

### Post by meierfra. on 2009-03-22
> If I unplug my ubuntu HD, will grub be safe?

Yes.

---

### Post by superalanliu on 2009-03-23
Fixed windows: it boots via the bios
Fixed grub: I can load into ubuntu

Still not working: dual boot.

---

### Post by meierfra. on 2009-03-23
Deleted. did not see your edit.

---

### Post by meierfra. on 2009-03-23
What  Windows item are you using in menu.lst?

One of these two should work:

title Windows XP (hd1)
rootnoverify (hd1,0)
map (hd0) (hd1)
map (hd1) (hd0)
chainloader +1

title Windows XP (hd2)
rootnoverify (hd2,0)
map (hd0) (hd2)
map (hd2) (hd0)
chainloader +1


If none of those two works, report any error messages you got.
Also  run the boot info script again and post the new RESULTS.txt (actually if you still have the old one, the new one will  be called RESULTS1.txt)

---

### Post by superalanliu on 2009-03-23
I shall try it tomorrow night. As I tried to dual boot into windows.. it caused instability. After attempting to boot into windows through grub, my computer crashed 2 times before it successfully booted into ubuntu again. Need to finish a major assignment for tomorrow so I don't want to risk my computer dying. Thanks for all your help meierfra!

---

### Post by superalanliu on 2009-03-25
Love you meierfra!

title Windows XP (hd1)
rootnoverify (hd1,0)
map (hd0) (hd1)
map (hd1) (hd0)
chainloader +1

Did the trick! Thanks for all your help!

---

### Post by meierfra. on 2009-03-25
> Did the trick! 

Great. Have fun with XP and Ubuntu.

---

