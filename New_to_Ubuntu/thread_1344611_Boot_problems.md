---
title: "Boot problems"
date: 2009-12-03
forum: New to Ubuntu
---

### Post by SwatKat on 2009-12-03
HI
I am trying to triple boot Win Xp, Mandriva and Ubuntu. I installed mandriva on a system which already had xp and the dual boot worked fine. But mandriva wont boot after installing ubuntu ( Xp works alright). I have an option of booting into mandriva, but when I select it, I get an error message that the file cannot be found. 
While installing ubuntu I went with the default options , so I don't think that the partition in which mandriva was installed was deleted. Could someone explain what I might have done wrong?

---

### Post by ukripper on 2009-12-03
boot into ubuntu and post output of your grub menu.lst if it is ubuntu 9.04 or lower. if karmic (9.10) post output of /etc/default/grub
and output of these commands:
```
sudo blkid
```

```
sudo fdisk -l
```

---

### Post by SwatKat on 2009-12-03
> **ukripper said:**
> boot into ubuntu and post output of your grub menu.lst if it is ubuntu 9.04 or lower. if karmic (9.10) post output of /etc/default/grub
and output of these commands:
```
sudo blkid
``````
sudo fdisk -l
```


Here you go 

swat@swat-desktop:~$ /etc/default/grub
bash: /etc/default/grub: Permission denied

swat@swat-desktop:~$ sudo blkid
[sudo] password for swat: 
/dev/sda1: UUID="2CB8AC79B8AC4366" TYPE="ntfs" 
/dev/sda5: UUID="C2043CD5043CCDE3" TYPE="ntfs" 
/dev/sda6: UUID="8214413F14413805" TYPE="ntfs" 
/dev/sda7: UUID="BC84460D8445CA9A" TYPE="ntfs" 
/dev/sda8: UUID="46A04A77A04A6E0D" TYPE="ntfs" 
/dev/sda9: UUID="75cccc51-010e-4ea8-9f61-e05e1c69f896" TYPE="ext4" 
/dev/sda10: UUID="dfa8a38b-fd68-4a3e-9577-c29593af9ec7" TYPE="swap" 
/dev/sda11: UUID="7b0f2102-174e-45b6-bb17-ab7d01469370" TYPE="ext4" 
/dev/sda12: UUID="b7bdfab0-d2c7-4015-8db9-9ead3337f7ce" TYPE="ext4" 
/dev/sda13: UUID="4fedb9f4-cac4-44d2-b616-7efbf03c90c3" TYPE="swap" 



swat@swat-desktop:~$ sudo fdisk -l

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x34a234a1

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        7649    61440561    7  HPFS/NTFS
/dev/sda2            7650       60801   426943440    f  W95 Ext'd (LBA)
/dev/sda5            7650       17210    76798701    7  HPFS/NTFS
/dev/sda6           17211       26771    76798701    7  HPFS/NTFS
/dev/sda7           26772       33178    51464196    7  HPFS/NTFS
/dev/sda8           39520       47353    62926573+   7  HPFS/NTFS
/dev/sda9           47354       48921    12594928+  83  Linux
/dev/sda10          48922       49430     4088511   82  Linux swap / Solaris
/dev/sda11          49431       60801    91337526   83  Linux
/dev/sda12          33179       39254    48805438+  83  Linux
/dev/sda13          39255       39519     2128581   82  Linux swap / Solaris

Partition table entries are not in disk order

---

### Post by ukripper on 2009-12-03
> **SwatKat said:**
> Here you go 

swat@swat-desktop:~$ /etc/default/grub
bash: /etc/default/grub: Permission denied



```
gedit /etc/default/grub
``` and post output here

---

### Post by SwatKat on 2009-12-03
> **ukripper said:**
> ```
gedit /etc/default/grub
``` and post output here


GRUB_DEFAULT=4
#GRUB_HIDDEN_TIMEOUT=0
GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_TIMEOUT=30
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
GRUB_CMDLINE_LINUX=" vga=773"

---

### Post by SwatKat on 2009-12-03
I just wanted to add that I dont mind completely clearing the partitions that donot have windows in them and reinstalling mandriva and ubuntu since they were fresh installs anyway. Am I right in understanding that the ntfs partitions are windows' and the rest is linux and 'Swap' refers to linux swap space only?

---

### Post by musarraf172 on 2009-12-03
> **SwatKat said:**
> GRUB_DEFAULT=4
#GRUB_HIDDEN_TIMEOUT=0
GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_TIMEOUT=30
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
GRUB_CMDLINE_LINUX=" vga=773"



Please give the output of the following also..

$ sudo gedit /boot/grub/grub.cfg

---

### Post by SwatKat on 2009-12-03
> **musarraf172 said:**
> Please give the output of the following also..

$ sudo gedit /boot/grub/grub.cfg


### BEGIN /etc/grub.d/00_header ###
if [ -s /boot/grub/grubenv ]; then
  have_grubenv=true
  load_env
fi
set default="4"
if [ ${prev_saved_entry} ]; then
  saved_entry=${prev_saved_entry}
  save_env saved_entry
  prev_saved_entry=
  save_env prev_saved_entry
fi
insmod ext2
set root=(hd0,12)
search --no-floppy --fs-uuid --set b7bdfab0-d2c7-4015-8db9-9ead3337f7ce
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  insmod gfxterm
  insmod vbe
  if terminal_output gfxterm ; then true ; else
    # For backward compatibility with versions of terminal.mod that don't
    # understand terminal_output
    terminal gfxterm
  fi
fi
if [ ${recordfail} = 1 ]; then
  set timeout=-1
else
  set timeout=30
fi
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/05_debian_theme ###
set menu_color_normal=white/black
set menu_color_highlight=black/white
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
menuentry "Ubuntu, Linux 2.6.31-14-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    set quiet=1
    insmod ext2
    set root=(hd0,12)
    search --no-floppy --fs-uuid --set b7bdfab0-d2c7-4015-8db9-9ead3337f7ce
    linux    /boot/vmlinuz-2.6.31-14-generic root=UUID=b7bdfab0-d2c7-4015-8db9-9ead3337f7ce ro  vga=773  quiet splash
    initrd    /boot/initrd.img-2.6.31-14-generic
}
menuentry "Ubuntu, Linux 2.6.31-14-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    insmod ext2
    set root=(hd0,12)
    search --no-floppy --fs-uuid --set b7bdfab0-d2c7-4015-8db9-9ead3337f7ce
    linux    /boot/vmlinuz-2.6.31-14-generic root=UUID=b7bdfab0-d2c7-4015-8db9-9ead3337f7ce ro single  vga=773
    initrd    /boot/initrd.img-2.6.31-14-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows XP (loader) (on /dev/sda1)" {
    insmod ntfs
    set root=(hd0,1)
    search --no-floppy --fs-uuid --set 2cb8ac79b8ac4366
    chainloader +1
}
menuentry "linux (on /dev/sda9)" {
    insmod ext2
    set root=(hd0,9)
    search --no-floppy --fs-uuid --set 75cccc51-010e-4ea8-9f61-e05e1c69f896
    linux /boot/vmlinuz BOOT_IMAGE=linux root=UUID=75cccc51-010e-4ea8-9f61-e05e1c69f896 resume=UUID=dfa8a38b-fd68-4a3e-9577-c29593af9ec7 splash=silent vga=788
    initrd (hd0,8)/boot/initrd.img
}
menuentry "failsafe (on /dev/sda9)" {
    insmod ext2
    set root=(hd0,9)
    search --no-floppy --fs-uuid --set 75cccc51-010e-4ea8-9f61-e05e1c69f896
    linux /boot/vmlinuz BOOT_IMAGE=failsafe root=UUID=75cccc51-010e-4ea8-9f61-e05e1c69f896 failsafe
    initrd (hd0,8)/boot/initrd.img
}
menuentry "linux-nonfb (on /dev/sda9)" {
    insmod ext2
    set root=(hd0,9)
    search --no-floppy --fs-uuid --set 75cccc51-010e-4ea8-9f61-e05e1c69f896
    linux /boot/vmlinuz BOOT_IMAGE=linux-nonfb root=UUID=75cccc51-010e-4ea8-9f61-e05e1c69f896 resume=UUID=dfa8a38b-fd68-4a3e-9577-c29593af9ec7
    initrd (hd0,8)/boot/initrd.img
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

So am I right in understanding that mandriva is on /dev/sda9  ? 
PS: An 8 and ) ends up being 8) on ubuntu forums when I copy and paste grub.cfg:D.


like I mentioned, I dont mind completely formatting the *linux* partitions and doing a fresh installation of mandriva and ubuntu. I just want to know what NOT to format. Thanks.

---

### Post by musarraf172 on 2009-12-03
> **SwatKat said:**
> ### BEGIN /etc/grub.d/00_header ###
if [ -s /boot/grub/grubenv ]; then
  have_grubenv=true
  load_env
fi
set default="4"
if [ ${prev_saved_entry} ]; then
  saved_entry=${prev_saved_entry}
  save_env saved_entry
  prev_saved_entry=
  save_env prev_saved_entry
fi
insmod ext2
set root=(hd0,12)
search --no-floppy --fs-uuid --set b7bdfab0-d2c7-4015-8db9-9ead3337f7ce
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  insmod gfxterm
  insmod vbe
  if terminal_output gfxterm ; then true ; else
    # For backward compatibility with versions of terminal.mod that don't
    # understand terminal_output
    terminal gfxterm
  fi
fi
if [ ${recordfail} = 1 ]; then
  set timeout=-1
else
  set timeout=30
fi
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/05_debian_theme ###
set menu_color_normal=white/black
set menu_color_highlight=black/white
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
menuentry "Ubuntu, Linux 2.6.31-14-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    set quiet=1
    insmod ext2
    set root=(hd0,12)
    search --no-floppy --fs-uuid --set b7bdfab0-d2c7-4015-8db9-9ead3337f7ce
    linux    /boot/vmlinuz-2.6.31-14-generic root=UUID=b7bdfab0-d2c7-4015-8db9-9ead3337f7ce ro  vga=773  quiet splash
    initrd    /boot/initrd.img-2.6.31-14-generic
}
menuentry "Ubuntu, Linux 2.6.31-14-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    insmod ext2
    set root=(hd0,12)
    search --no-floppy --fs-uuid --set b7bdfab0-d2c7-4015-8db9-9ead3337f7ce
    linux    /boot/vmlinuz-2.6.31-14-generic root=UUID=b7bdfab0-d2c7-4015-8db9-9ead3337f7ce ro single  vga=773
    initrd    /boot/initrd.img-2.6.31-14-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows XP (loader) (on /dev/sda1)" {
    insmod ntfs
    set root=(hd0,1)
    search --no-floppy --fs-uuid --set 2cb8ac79b8ac4366
    chainloader +1
}
menuentry "linux (on /dev/sda9)" {
    insmod ext2
    set root=(hd0,9)
    search --no-floppy --fs-uuid --set 75cccc51-010e-4ea8-9f61-e05e1c69f896
    linux /boot/vmlinuz BOOT_IMAGE=linux root=UUID=75cccc51-010e-4ea8-9f61-e05e1c69f896 resume=UUID=dfa8a38b-fd68-4a3e-9577-c29593af9ec7 splash=silent vga=788
    initrd (hd0,8)/boot/initrd.img
}
menuentry "failsafe (on /dev/sda9)" {
    insmod ext2
    set root=(hd0,9)
    search --no-floppy --fs-uuid --set 75cccc51-010e-4ea8-9f61-e05e1c69f896
    linux /boot/vmlinuz BOOT_IMAGE=failsafe root=UUID=75cccc51-010e-4ea8-9f61-e05e1c69f896 failsafe
    initrd (hd0,8)/boot/initrd.img
}
menuentry "linux-nonfb (on /dev/sda9)" {
    insmod ext2
    set root=(hd0,9)
    search --no-floppy --fs-uuid --set 75cccc51-010e-4ea8-9f61-e05e1c69f896
    linux /boot/vmlinuz BOOT_IMAGE=linux-nonfb root=UUID=75cccc51-010e-4ea8-9f61-e05e1c69f896 resume=UUID=dfa8a38b-fd68-4a3e-9577-c29593af9ec7
    initrd (hd0,8)/boot/initrd.img
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

So am I right in understanding that mandriva is on /dev/sda9  ? 
PS: An 8 and ) ends up being 8) on ubuntu forums when I copy and paste grub.cfg:D.


like I mentioned, I dont mind completely formatting the *linux* partitions and doing a fresh installation of mandriva and ubuntu. I just want to know what NOT to format. Thanks.

grub.cfg seems to be fine. Can you tell me what exact error you are getting in grub??

You may need to modify the line "initrd (hd0,8)/boot/initrd.img"

try replacing with "initrd /boot/initrd.img"

---

### Post by SwatKat on 2009-12-03
> **musarraf172 said:**
> grub.cfg seems to be fine. Can you tell me what exact error you are getting in grub??

You may need to modify the line "initrd (hd0,8)/boot/initrd.img"

try replacing with "initrd /boot/initrd.img"

I just get
error :file not found
press any key to continue...

Looks like I cant edit grub.cfg either. I get an error msg that its a read only file. I'll just take a deep breath and reinstall.

---

### Post by musarraf172 on 2009-12-03
> **SwatKat said:**
> I just get
error :file not found
press any key to continue...

Looks like I cant edit grub.cfg either. I get an error msg that its a read only file. I'll just take a deep breath and reinstall.

Did you replaced the initrd line as suggested??
[ initrd /boot/initrd.img ]

grub.cfg is a read only file. U should not edit it manually. It is being edited with the command " update-grub" the data written in it  are taken from /etc/grub.d/ and /etc/default/grub

If you wish to edit grub.cfg manually then use :

$ sudo chmod +w /boot/grub/grub.cfg
$ sudo gedit /boot/grub/grub.cfg

---

### Post by ukripper on 2009-12-03
you shouldn't edit grub.cfg in any circumstances. More info read here [http://ubuntuforums.org/showthread.php?t=1195275](http://ubuntuforums.org/showthread.php?t=1195275)

Reason - "''**grub.cfg'' is overwritten anytime there is a update, a kernel is added/removed or the user runs `update-grub`** * "

---

### Post by ukripper on 2009-12-03
@SwatKat - can you post output of this command:
```
gedit /etc/grub.d/30_os-prober
```

---

### Post by SwatKat on 2009-12-03
Thanks for the reply ukripper.Looks like you were steering me in the right direction . I guess I had to be more patient. But I took a deep breath and reinstalled after my last post, mandriva first and ubuntu last and got the same error again. I looked around a bit and found that many have trouble booting ubuntu 9.10 and mandriva 2010 side by side. It has something to do with ubuntu using grub2 and mandriva using the old legacy grub and one ends up not recognizing the other, whichever is installed first. 

I found this link
[http://forum.mandriva.com/viewtopic.php?t=119610](http://forum.mandriva.com/viewtopic.php?t=119610)

which tells me how to install mandriva second and add ubuntu to its bootloader. But I guess it'll use the older grub as the bootloader( I don't undersatnd the * install the boot loader to the root partition either. *I dont remember getting that option while installing)

I lso found this link 
[http://forums.scotsnewsletter.com/index.php?showtopic=30224](http://forums.scotsnewsletter.com/index.php?showtopic=30224)

which tells how to boot mandriva with grub 2.  But it says something about booting manually from the grub prompt  which I think is too much of a hassle.

Could somone help me please? pretty please with a cheery on top?

---

### Post by oldfred on 2009-12-04
Installing grub to the partition is the PBR instead of the MBR. There is a partition boot record like the MBR for the entire drive. Grub2 does not like to be installed to a PBR, but old grub works just fine. Old grub does not directly recognize ext4 partitions, so I would use grub2 in the MBR and install old grub to the mandriva PBR to point to the mandriva install.

**Installing GRUB to a partition:** 
To install GRUB to a partition, you would use a command like, 'setup (hd0,1), or 'setup (hd0,3)', where (hd0,1) and (hd0,3) are Linux partitions. If you do that, you'll be able to boot your operating system using the 'chainloader' command.
[http://members.iinet.net.au/~herman546/p15.html#Re-install_Grub_with_Live_CD](http://members.iinet.net.au/~herman546/p15.html#Re-install_Grub_with_Live_CD)



You then can add a simple chainboot entry (like windows chainboot) to just jump to the mandriva PBR.

Grub2 chainboot entry to add to 40_custom in grub2/ubuntu Partitions are using grub2 numbering here.
# Chainload another bootloader
menuentry "Chainload partition [COLOR=Red]3[/COLOR]" {
set root=(hd0,[COLOR=Red]3[/COLOR])
chainloader +1
}

---

### Post by SwatKat on 2009-12-04
@oldfred Thanks. Since I have wiped the partitions containing the linux distros clean and have neither of them, this is what I plan to do. I'll install mandriva first, install its grub in the mandriva root partition. Then install ubuntu and install grub in mbr. If I do this, Ubuntu would run update grub automatically and add mandriva to its boot menu, right? Or would I still have to add a chain boot entry? If yes, *where* should I add it? 

Clould you please tell me how to make them share swap space? I found out that the  /etc/fstab  entry in both of them must be the same. Is there a way to direct them to do this during installation? ( I have observed that both create a swap partition). 
Any help is much appreciated. Thanks.

---

### Post by oldfred on 2009-12-04
Grub2 usually add direct boot entries not chainboot. You can add a chainboot entry to 40_custom and turn off the osprober so you do not have 2 entries if osprober is finding you mandriva entries.

I alway use manual install where I create partitions first and then have to tell it which partition to use for what. That way I also select the same swap for all the installs. I do not know if mandriva allows that but I know Ubuntu does.

---

