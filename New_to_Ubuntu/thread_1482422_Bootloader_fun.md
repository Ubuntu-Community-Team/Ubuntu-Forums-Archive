---
title: "Bootloader fun"
date: 2010-05-13
forum: New to Ubuntu
---

### Post by SquidLord on 2010-05-13
So I had a pretty fun setup with Windows 7 Pro x64 on one side and Ubuntu 10.04 on the other, I was using Grub and enjoying it. I reinstalled Windows and I was stuck with the Windows bootloader; alright, I'll just add an entry for Ubuntu right? Wrong, "grub rescue>" Ok....I didn't really have anything installed or setup, just video drivers, dropbox and gnome-do. So I reinstalled and got Grub back, so it should be like before where I could just use Grub to switch between the two? nope, selecting the found Windows loader loops back to grub. Now I'm back in the same position [with the windows loader and "grub rescue>" after using "bootrec /fixmbr" from the windows disc. How can I get these two coexist again? Preferably booting from Grub.

tl;dr
One bootloader refuses to see the other allowing only one bootable OS on my partitioned HDD. Ideas?

---

### Post by ubunterooster on 2010-05-13
after booting into ubuntu ```
sudo update-grub
```

---

### Post by SquidLord on 2010-05-13
Possible via Live USB/CD?

---

### Post by ShadowMage on 2010-05-13
Hey there,

In a multi-boot system using GRUB, there is exactly one "primary OS" which is the one that controls GRUB. It is from this OS that you would need to run the update-grub command as root, hence in Ubuntu:

```
sudo update-grub
```

What this command does is it recreates the GRUB 2 menu config by running the scripts that generate it. One of these scripts is the "OS Prober" which looks for other operating systems on your hard drive and generates menu entries for those that are detected.

So, to answer your question, no I don't think doing this from a Live CD would do anything useful.

Are you able to boot into your primary OS currently? I imagine this would be your Ubuntu installation because AFAIK Windows doesn't "know" what GRUB is.

---

### Post by SquidLord on 2010-05-13
> **ShadowMage said:**
> Hey there,

In a multi-boot system using GRUB, there is exactly one "primary OS" which is the one that controls GRUB. It is from this OS that you would need to run the update-grub command as root, hence in Ubuntu:

```
sudo update-grub
```

What this command does is it recreates the GRUB 2 menu config by running the scripts that generate it. One of these scripts is the "OS Prober" which looks for other operating systems on your hard drive and generates menu entries for those that are detected.

So, to answer your question, no I don't think doing this from a Live CD would do anything useful.

Are you able to boot into your primary OS currently? I imagine this would be your Ubuntu installation because AFAIK Windows doesn't "know" what GRUB is.

No, sadly I can't boot into 10.04 currently. I can get as far as "grub rescue>" after I add an entry to the Windows loader for Ubuntu. The only commands that work in that mode is "ls"

---

### Post by ubunterooster on 2010-05-13
Do the grub rescue again so you can get into Ubuntu first

---

### Post by cap10Ibraim on 2010-05-13
Get the super grub disk 
[http://www.supergrubdisk.org/](http://www.supergrubdisk.org/) burn it to a CD 
boot this CD you should see all your systems boot to Ubuntu and fix your issue

---

### Post by SquidLord on 2010-05-14
> **ubunterooster said:**
> Do the grub rescue again so you can get into Ubuntu first

I can't get by the grub rescue as I have no clue what to do since only the "ls" command works ["ls /" doesn't work]...that's the problem; I should have made that a little more clear from the start.

> **cap10Ibraim said:**
> Get the super grub disk 
[http://www.supergrubdisk.org/](http://www.supergrubdisk.org/) burn it to a CD 
boot this CD you should see all your systems boot to Ubuntu and fix your issue

Alrighty, I have another solution suggested to me via a friend, but I will definitely try this disk and see where it takes me.

---

### Post by wilee-nilee on 2010-05-14
> **SquidLord said:**
> I can't get by the grub rescue as I have no clue what to do since only the "ls" command works ["ls /" doesn't work]...that's the problem; I should have made that a little more clear from the start.



Alrighty, I have another solution suggested to me via a friend, but I will definitely try this disk and see where it takes me.
You don't need the super grub disc for this although having it is a good thing generally; follow the # 11 in this link to reload grub to the MBR. When Ubuntu boots run ```
sudo update-grub
```
[https://help.ubuntu.com/community/Grub2#Upgrading](https://help.ubuntu.com/community/Grub2#Upgrading)

---

### Post by ubunterooster on 2010-05-14
he can't boot ubuntu right now.

---

### Post by wilee-nilee on 2010-05-14
> **ubunterooster said:**
> he can't boot ubuntu right now.

If your responding to me, this is done with a live cd you know that.
Really we should be looking at the boot script.

Thread starter lets get to the bottom of whats going on, post this boot script in code tags, just paste it into a reply highlight the text and click on the # in the reply panel.
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

---

### Post by ubunterooster on 2010-05-14
I assumed that Squid was using Windows at the time.

---

### Post by wilee-nilee on 2010-05-14
> **ubunterooster said:**
> I assumed that Squid was using Windows at the time.

I suspect 2 scenarios either grub wasn't loaded correctly and/or possibly put in the Windows partition or the boot flag is still on windows. The boot flag is problematic with some computers, even though if you have grub loaded it should find all boots, theoretically. ;)

---

### Post by SquidLord on 2010-05-14
The loader found in sda1 is from the Windows 7 beta(s) and RC from when I  was testing Win7 along side Vista [sda1 is also my Storage HDD, sdb* is  my main HDD]

```
                Boot Info Script 0.55    dated February 15th, 2010                     

============================= Boot Info Summary:  ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks for 
    (UUID=a4a72c01-4f10-4410-919a-76500e26b770)/boot/grub.
 => Windows is installed in the MBR of /dev/sdb

sda1:  _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Boot file info:     BootPart in the file /NST/nst_grub.mbr is trying  to 
                       chain load sector #894724173 on boot drive #1
    Operating System:  
    Boot files/dirs:   /bootmgr /Boot/BCD

sdb1:  _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Boot file info:     BootPart in the file 
                        /NST/nst_grub-E3CE933FFB150C36BA71C935175B0D13.mbr is 
                       trying to chain load sector #973314153 on boot  drive 
                       #2 BootPart in the file /NST/nst_grub.mbr is  trying to 
                       chain load sector #973314153 on boot drive #2
    Operating System:  Windows 7
    Boot files/dirs:   /bootmgr /Boot/BCD /Windows/System32/winload.exe

sdb2:  _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sdb5:  _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdb6:  _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.04 LTS
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab  /boot/grub/core.img

sdc:  _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Fat32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info:  =============================

Drive: sda ___________________  _____________________________________________________

Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63 1,953,520,064 1,953,520,002   7 HPFS/NTFS


Drive: sdb ___________________  _____________________________________________________

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *             63   894,852,629   894,852,567   7 HPFS/NTFS
/dev/sdb2         894,853,118   976,768,064    81,914,947   5 Extended
/dev/sdb5         973,314,153   976,768,064     3,453,912  82 Linux swap  / Solaris
/dev/sdb6         894,853,120   973,314,047    78,460,928  83 Linux


blkid -c /dev/null:  ____________________________________________________________

Device           UUID                                   TYPE       LABEL                          

/dev/loop0                                              squashfs                                  
/dev/loop1       e94b4e54-da87-764e-bc7d-ac8af15f9e3d   ext2                                      
/dev/sda1        042AEE3A2AEE27FE                       ntfs        STORAGE                       
/dev/sda: PTTYPE="dos" 
/dev/sdb1        1E6C761F6C75F23F                       ntfs                                      
/dev/sdb2: PTTYPE="dos" 
/dev/sdb5        944dc140-f759-49ef-9f6c-83fe047f2911   swap                                      
/dev/sdb6        7e4a7d00-d020-4134-b0d2-074bbcc4301c   ext4                                      
/dev/sdb: PTTYPE="dos" 
/dev/sdc         126A-A92C                              vfat        MYLINUXLIVE                   

============================ "mount | grep ^/dev  output:  ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sdc         /cdrom                   vfat        (rw,relatime,fmask=0022,dmask=0022,codepage=cp437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro)
/dev/loop0       /rofs                    squashfs   (ro,noatime)


=========================== sdb6/boot/grub/grub.cfg:  ===========================

#
# DO NOT EDIT THIS FILE
#
# It is automatically generated by /usr/sbin/grub-mkconfig using  templates
# from /etc/grub.d and settings from /etc/default/grub
#

### BEGIN /etc/grub.d/00_header ###
if [ -s $prefix/grubenv ]; then
  load_env
fi
set default="0"
if [ ${prev_saved_entry} ]; then
  set saved_entry=${prev_saved_entry}
  save_env saved_entry
  set prev_saved_entry=
  save_env prev_saved_entry
  set boot_once=true
fi

function savedefault {
  if [ -z ${boot_once} ]; then
    saved_entry=${chosen}
    save_env saved_entry
  fi
}

function recordfail {
  set recordfail=1
  if [ -n ${have_grubenv} ]; then if [ -z ${boot_once} ]; then save_env  recordfail; fi; fi
}
insmod ext2
set root='(hd1,6)'
search --no-floppy --fs-uuid --set 7e4a7d00-d020-4134-b0d2-074bbcc4301c
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  insmod gfxterm
  insmod vbe
  if terminal_output gfxterm ; then true ; else
    # For backward compatibility with versions of terminal.mod that  don't
    # understand terminal_output
    terminal gfxterm
  fi
fi
insmod ext2
set root='(hd1,6)'
search --no-floppy --fs-uuid --set 7e4a7d00-d020-4134-b0d2-074bbcc4301c
set locale_dir=($root)/boot/grub/locale
set lang=en
insmod gettext
if [ ${recordfail} = 1 ]; then
  set timeout=-1
else
  set timeout=10
fi
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/05_debian_theme ###
set menu_color_normal=white/black
set menu_color_highlight=black/light-gray
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
menuentry 'Ubuntu, with Linux 2.6.32-21-generic' --class ubuntu --class  gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd1,6)'
    search --no-floppy --fs-uuid --set  7e4a7d00-d020-4134-b0d2-074bbcc4301c
    linux    /boot/vmlinuz-2.6.32-21-generic  root=UUID=7e4a7d00-d020-4134-b0d2-074bbcc4301c ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-21-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-21-generic (recovery mode)' --class  ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd1,6)'
    search --no-floppy --fs-uuid --set  7e4a7d00-d020-4134-b0d2-074bbcc4301c
    echo    'Loading Linux 2.6.32-21-generic ...'
    linux    /boot/vmlinuz-2.6.32-21-generic  root=UUID=7e4a7d00-d020-4134-b0d2-074bbcc4301c ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-21-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod ext2
    set root='(hd1,6)'
    search --no-floppy --fs-uuid --set  7e4a7d00-d020-4134-b0d2-074bbcc4301c
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod ext2
    set root='(hd1,6)'
    search --no-floppy --fs-uuid --set  7e4a7d00-d020-4134-b0d2-074bbcc4301c
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sda1)" {
    insmod ntfs
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 042aee3a2aee27fe
    chainloader +1
}
menuentry "Windows 7 (loader) (on /dev/sdb1)" {
    insmod ntfs
    set root='(hd1,1)'
    search --no-floppy --fs-uuid --set 1e6c761f6c75f23f
    chainloader +1
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply  type the
# menu entries you want to add after this comment.  Be careful not to  change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

=============================== sdb6/etc/fstab:  ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique  identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>   <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sdb6 during installation
UUID=7e4a7d00-d020-4134-b0d2-074bbcc4301c /               ext4     errors=remount-ro 0       1
# swap was on /dev/sdb5 during installation
UUID=944dc140-f759-49ef-9f6c-83fe047f2911 none            swap    sw               0       0

=================== sdb6: Location of files loaded by Grub:  ===================


 471.2GB: boot/grub/core.img
 473.4GB: boot/grub/grub.cfg
 471.3GB: boot/initrd.img-2.6.32-21-generic
 471.1GB: boot/vmlinuz-2.6.32-21-generic
 471.3GB: initrd.img
 471.1GB: vmlinuz

```


> **ubunterooster said:**
> I assumed that Squid was using Windows at the time.

I am using Windows, but I do have a LiveUSB for 10.04, which apparently works in this situation.

---

### Post by ubunterooster on 2010-05-14
Can't you just tell the mobo to start to sdb (The mobo should tell you which button to press to boot to a different drive) and then do  sudo update-grub?

---

### Post by SquidLord on 2010-05-14
> **ubunterooster said:**
> Can't you just tell the mobo to start to sdb (The mobo should tell you which button to press to boot to a different drive) and then do  sudo update-grub?

Both Windows and Ubuntu are on the same drive; Windows should be starting at sdb1 and Ubuntu at sdb6.

---

### Post by wilee-nilee on 2010-05-16
> **SquidLord said:**
> Both Windows and Ubuntu are on the same drive; Windows should be starting at sdb1 and Ubuntu atsdb6.

So tell us what are sda and sdb?

---

### Post by SquidLord on 2010-05-16
> **wilee-nilee said:**
> So tell us what are sda and sdb?

sda is a 1TB Storage HDD, and sdb is a 500GB drive that I use for work and play; basically the OS drive that harbors my Win7 and 10.04 install.

I do have a spare 500GB drive that hasn't been used before if it'd be easier to separate the OS's and loaders [though I can't see myself using 500GB with Ubuntu what with the lack of 8GB-14GB games].

---

### Post by wilee-nilee on 2010-05-16
Having separate bootloaders just makes things complicated, at least it would be for me. So if you hit f12 to have a choice of hard drives to boot from what happens if you choose sdb? The problem seams to be that you have grub installed in the 1st sda which doesn't contain Ubuntu. So as a first try just change the HD boot from sdb first and see it if loads windows as it should. If this works I would just load grub into the MBR of sdb which means bootloader=sdb only via the grub2 page step 11, and then move it to the first in the HD to be read.
[https://help.ubuntu.com/community/Grub2#Upgrading](https://help.ubuntu.com/community/Grub2#Upgrading)

Also sda and sdb are set as boot, I would turn off the boot flag on sda with gparted as well.

There are probably, better and other ways to fix this,if it was me I would just reinstall everything, but I know how to get the setups I need very quickly. I would have the master HD with Windows first Ubuntu second and use the second drive without any bootloaders in the MBR as storage. I am a serial reinstaller though if it takes longer to fix then reinstalling I reinstall. I also have everything saved off my computer on a HD.

---

### Post by wilee-nilee on 2010-05-17
So what has happened is that you have a windows bootloader in sda I don't know if this was a previous install or running the auto fix on the wrong HD. When you reinstalled Ubuntu you didn't hit the advanced button in the last gui that shows where grub was being put it should have been sdb.

Here is a link to dual booting with 2 HD's
[http://members.iinet.net.au/~herman546/p24.html](http://members.iinet.net.au/~herman546/p24.html)

If none of the suggested answer work, then a little more information is needed, such as are both of these HD's mounted inside the computer. And how did the MS bootoader get into sda.

---

### Post by SquidLord on 2010-05-17
sda isn't set to boot via BIOS selection, I have the CD drive booting first and then sdb. The Windows loader on sda is from the Windows 7 beta's / release candidate [I use to just have Vista on sdb and tested Windows 7 on a 40GB partition on sda]. Grub was installed on sdb6; upon launching linux from the Windows Loader "insert system disc and press any key to continue" it then tries to load grub and goes to "grub rescue>"

I will attempt to reinstall Grub after this post.

---

### Post by wilee-nilee on 2010-05-17
> **SquidLord said:**
> sda isn't set to boot via BIOS selection, I have the CD drive booting first and then sdb. The Windows loader on sda is from the Windows 7 beta's / release candidate [I use to just have Vista on sdb and tested Windows 7 on a 40GB partition on sda]. Grub was installed on sdb6; upon launching linux from the Windows Loader "insert system disc and press any key to continue" it then tries to load grub and goes to "grub rescue>"

I will attempt to reinstall Grub after this post.

I wouldn't have the cd drive 1st that is a accident waiting to happen. sda has a boot flag on it remove it with gparted and put sdb 1st in the list. Load grub to sdb
with a live cd
```
sudo mount /dev/sdb6 /mnt
```
then again,
```
sudo grub-install --root-directory=/mnt/ /dev/sdb
```
Then if you get into Ubuntu run ```
sudo update-grub
```
If sdb6 is the main Ubuntu partition still.

I would also look into how to remove the mbr in sda.
The mbr in sda has grub still there and is probably chainloading the windows boot from who knows whether it is sda or sdb

The setup you have is rather messed up in the the HD order and where you have things installed and both HD have bootloaders.

---

### Post by SquidLord on 2010-05-19
Ok, sorry for the delay, but I made sure the settings in the BIOS were correct again, removed the boot flag from sda1, and moved the boot flag from sdb1 to sdb6 and reinstalled grub. Grub loaded and was able to launch both 10.04 and Windows 7.

Now, all I need to do is remove the entry in the Windows loader that I made for 10.04 since I don't need it; I think EasyBCD is going to restore the windows loader...

Since we're here, would you know how to remove the MBR in sda? I recall looking a long while back and not finding anything.

---

### Post by ubunterooster on 2010-05-19
remove the win7-containing drive, boot, and run ```
sudo update-grub
```

---

### Post by SquidLord on 2010-05-20
> **ubunterooster said:**
> remove the win7-containing drive, boot, and run ```
sudo update-grub
```

That wouldn't fix the windows loader.

Though, now I'm back to Windows not loading from grub, it just loops back to grub *sigh* and two Ubuntu's are detected :-/ I am disappoint...

---

