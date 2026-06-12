---
title: "Dual boot won't boot"
date: 2010-08-03
forum: New to Ubuntu
---

### Post by Calais225 on 2010-08-03
Turned on my computer this evening (WinXP and Karmic Koala) and it won't boot.  I get this message on a black sceen:


"Minimal BASH-like line editing is supported.  For the first word, TAB lists possible command completions.  Anywhere else TAB lists possible device/file completions."

then this prompt appears---right after the above, without me entering anything.

"rescue:grub"

Okay, I'm flummoxed.  What do I do now?

Thanks,

Bill

---

### Post by sandyd on 2010-08-03
> **Calais225 said:**
> Turned on my computer this evening (WinXP and Karmic Koala) and it won't boot.  I get this message on a black sceen:


"Minimal BASH-like line editing is supported.  For the first word, TAB lists possible command completions.  Anywhere else TAB lists possible device/file completions."

then this prompt appears---right after the above, without me entering anything.

"rescue:grub"

Okay, I'm flummoxed.  What do I do now?

Thanks,

Bill
Means grub bootloader went bad
boot up to a livecd and run
```

wget -c http://cdnetworks-us-2.dl.sourceforge.net/project/bootinfoscript/bootinfoscript/0.55/boot_info_script055.sh
chmod 777 boot_info_script055.sh
sudo bash ./boot_info_script005.sh

```

---

### Post by Calais225 on 2010-08-04
Being such a noob, I just typed, word for word what Carlee suggested.  I suspect that each line shown needs me to press enter??? at the end of the lines she posted?

Didn't work the first time when I typed in all of her code and only pressed enter at the end.

Sorry to be so dense.

Bill

---

### Post by Calais225 on 2010-08-04
Tried the commands line by line.  Worked.  But, after the connection timing out several times, I got a 404 error.

Now what?

I do have a dvd form Linux Format Magazine with Fedora and super grub disk on it.  Plus an article from the magazine on how to repair grub etc. but I can't figure out how to get the super grub program from the dvd onto the desktop as it just wants to load fedora when i put the dvd in.


Apparently the super grub disk program should repair grub without even a live cd but I can't figure out how.

It says:sudo update-grub
and sudo install-grub

but I can't get the program off the dvd.

Maybe I should try and download it onto a usb key?

Help, please.

Bill

---

### Post by oldfred on 2010-08-04
Carlee code was meant to be copied and pasted into the terminal to avoid typing errors.

Another way:

Boot Info Script courtesy of forum member meierfra
Page with instructions and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Paste results.txt, then highlight entire file and click on # in edit panel(code tags) to make it easier to read.
Or You can generate the tags first by pressing the # icon in the post's menu and then paste the contents between the generated [ code][ /code] tags.

---

### Post by Calais225 on 2010-08-04
finally was able to do the code that Carlee suggested.

The file boot_info_script055.sh was saved.

typed chmod 777 boot_info_script055.sh

then typed sudo bash ./boot_info_script055.sh

and got  No such file or directory

Now what?

Bill

---

### Post by Calais225 on 2010-08-04
Thanks to OldFred I have found the file.

The directions said to paste the results of the txt file here to I will try that.

```

```/home/ubuntu/Desktop/RESULTS.txt

HOpe that is how I was supposed to paste it.

Bill

wondering what to do now?

---

### Post by Calais225 on 2010-08-04
or do i just paste this?

```

```                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks for 
    (UUID=7680772a-b484-4a27-89a4-7442e0ea466d)/boot/grub.
 => Windows is installed in the MBR of /dev/sdb

sda1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Dell Utility: Fat16
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 95
    Boot files/dirs:   /IO.SYS /MSDOS.SYS /COMMAND.COM

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM

sdb1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdb2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sdb5: _________________________________________________________________________

    File system:       
    Boot sector type:  -
    Boot sector info:  
    Mounting failed:
mount: unknown filesystem type ''

sdb6: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 40.0 GB, 40020664320 bytes
255 heads, 63 sectors/track, 4865 cylinders, total 78165360 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x9dc96e9e

Partition  Boot         Start           End          Size  Id System

/dev/sda1                  63        64,259        64,197  de Dell Utility
/dev/sda2    *         64,260    78,156,224    78,091,965   7 HPFS/NTFS


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders, total 234441648 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xec8ab693

Partition  Boot         Start           End          Size  Id System

/dev/sdb1                  63   181,309,589   181,309,527   7 HPFS/NTFS
/dev/sdb2         181,309,590   234,436,544    53,126,955   5 Extended
/dev/sdb5         181,309,653   232,155,314    50,845,662  83 Linux
/dev/sdb6         232,155,378   234,436,544     2,281,167  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda1        07D3-0C03                              vfat       DellUtility                   
/dev/sda2        1C885DEF885DC7C2                       ntfs                                     
/dev/sdb1        A0E8D896E8D86BD2                       ntfs       Storage                       
/dev/sdb5: ambivalent result (probably more filesystems on the device)
/dev/sdb6        808f4aa2-8284-4496-9799-42ae9addfb73   swap                                     

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sr0         /cdrom                   iso9660    (rw)
/dev/loop0       /rofs                    squashfs   (rw)


================================ sda2/boot.ini: ================================

[boot loader] 
timeout=30 
default=multi(0)disk(0)rdisk(0)partition(2)\WINDOWS 
[operating systems] 
multi(0)disk(0)rdisk(0)partition(2)\WINDOWS="Microsoft Windows XP Home Edition" /fastdetect /NoExecute=OptIn 
=======Devices which don't seem to have a corresponding hard drive==============

sdc

---

### Post by oldfred on 2010-08-04
You have a random file error that is easily corrected from a liveCD.

ambivalent result (probably more filesystems on the device)

[http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:minix](http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:minix)

---

### Post by Calais225 on 2010-08-04
Tried several of the suggestions on that page....no luck.

Reinstalled Ubuntu and things are back up and running.

Now to figure out how to removed the extra kernels.

---

