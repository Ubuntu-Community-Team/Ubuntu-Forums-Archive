---
title: "can't install Ubuntu - multi boot"
date: 2011-06-22
forum: New to Ubuntu
---

### Post by bk60544 on 2011-06-22
Still a newbie. Have Win7 on partition1, XP on partition 2, and want to install Ubuntu on 3rd. Have tried installing 10.4 and 10.10 but no success.  At startup I get "Error: unknown filesystem. Grub rescue>".  This should NOT be **so** difficult.  Appreciation in advance!

---

### Post by Mr Stoozer on 2011-06-22
Are you still able to boot into Windows?

---

### Post by drs305 on 2011-06-22
If you can boot the Ubuntu LiveCD, please go to [http://bootinfoscript.sourceforge.net]("http://bootinfoscript.sourceforge.net"), download and extract the boot info script, and run it. Instructions are on the site.

It will produce a file called RESULTS.txt. Posting the contents of the file will show us the status of your boot files and perhaps provide the reason you are getting the rescue prompt.

---

### Post by bk60544 on 2011-06-22
I went back to "pre-problem" state where I can boot into either XP or Win7, and balance of drive is "unallocated".  Need (better) direction on installing (either 10.4 or 10.10) since the last 4 attempts have been unsuccessful. Thanks!

---

### Post by mike555 on 2011-06-22
Use the live cd and Gparted to make the extra partition ext4 ... that should do it ,then you should be able to install , be careful to pick the right option .

---

### Post by oldfred on 2011-06-22
How many partitions do you have? You want to create an extened partition so you can have additional logical partitions in the extended. Otherwise you are trapped into the 4 partition limit. Or did you create additional partitions in windows and it converted to dynamic (big problem)?

Boot script will still be helpful as drs305 suggested. We may be able to make better suggestions on how to install.

---

### Post by bk60544 on 2011-06-22
Mike-your advice "pick the right option" is too vague. remember this is the Absolute Beginner Forum.

---

### Post by bk60544 on 2011-06-22
Oldfred-"Better suggestions" is what I need.  4 previous installs were unsuccessful.  There are 2 partitions [xp and Win 7] and another "unallocated" to use for Ubuntu. Thanks.

---

### Post by kidknapp on 2011-06-22
When you are going through the install screens one of them should ask you "Where do you want to put Ubuntu?" and there should be an option to "Specify Partitions Manually(Advanced)." Choose this option and you will then need to create a EXT4 partition in the dead space(the space your windows partitions aren't using) you have left and a much smaller 'swap' partition - so save at least 2 GB for that or more depending upon the size of your EXT4 Partition. ONLY CHECK THE PARTITION YOU WANT TO INSTALL UBUNTU ON FOR 'Format?". It should check the necessary box for you when you created the partition. At this point you should able to continue fine or you can post what it is holding you up on....:o

---

### Post by bk60544 on 2011-06-22
Kid- In the past unsuccessful installs I chose "primary", est4, and "/" mount point. What should i do differently NOW?

---

### Post by kidknapp on 2011-06-22
Otherwise you may be having problems with your Install disk....Have you tried using another? 

When you are at the console can you login with your spcecified username and password - type your username then ENTER then your password and then ENTER. 
Then type: ```
sudo start gdm
```

Does this get you anywhere?

If not I would first make sure you have a copy of Ubuntu Desktop and not server and that it is appropriate to your computers processor architecture and the version you want to run. Burn a new disc and see if it helps....

I know it can be frustrating, but there are a lot of people here who are willing to help......:P

---

### Post by bk60544 on 2011-06-22
Kid, have used these same disks previously [on simple installs] so highly doubt that media is the issue, so again I need to ask: what should i do differently this time?

---

### Post by kidknapp on 2011-06-22
I already said to use a different disc. What version are you trying to install with? - and yes discs do wear over time so....It at least eliminates the possibility....

---

### Post by bk60544 on 2011-06-22
Kid, Yes I've used 2 different 10.4 disks and 2 different 10.10 disks, all resulted in same result: "Error: unknown filesystem. Grub rescue>". I am in process of installing 10.4 again. Choice is where to install- #1 side-by-side, #2 erase entire disk [not acceptable], #3 largest contiguous, #4 manually [have used previously-choosing "primary", "ext4", and '/"].  any thoughts?

---

### Post by kidknapp on 2011-06-22
your primary partion allows ubuntu to be created within it as / being your main mount point that you formatted as ext4 but you also need to define a "swap" partition...

---

### Post by oldfred on 2011-06-22
Are you getting any error messages on the install of the grub2 boot loader to the MBR at the end of your install?

This will not help your grub rescue issue but is my standard recommendation on how to partition a new install. You need to use manual install and choose the same drive as you  install Ubuntu to as the place for grub2's boot loader (usually sda). Do not install to partitions (like sda1, sda2 etc).

For the Total space you want for Ubuntu:
Ubuntu's standard install is just / (root) & swap, but it is better to add another partition for /home:
1. 10-20 GB Mountpoint / primary or logical beginning ext4(or ext3)
2. all but 2 GB Mountpoint /home logical beginning ext4(or ext3)
3. 2 GB Mountpoint swap logical

Depending on how much memory you have you may not absolutely need swap but having some is still recommended. I do not hibernate (boots fast enough for me) but if hibernating then you need swap equal to RAM in GiB not GB. And if dual booting with windows a shared NTFS partition is also recommended. But you usually cannot create that as part of the install, just leave some space. Or partition in advance (recommended).
One advantage of partitioning in advance is that the installer will use the swap space to speed up the install. Thanks Herman for the tip.

Then if it does not boot, run the boot script recommended above.
and/or:
Grub Rescue Prompt Megathread - drs305
[http://ubuntuforums.org/showthread.php?t=1594052](http://ubuntuforums.org/showthread.php?t=1594052)
Reinstall grub2 - Short version & full chroot version
[https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB%202]("https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB%202")

---

### Post by kidknapp on 2011-06-22
Thanks, oldfred!:)

---

### Post by bk60544 on 2011-06-23
> **oldfred said:**
> Are you getting any error messages on the install of the grub2 boot loader to the MBR at the end of your install?

This will not help your grub rescue issue but is my standard recommendation on how to partition a new install. You need to use manual install and choose the same drive as you  install Ubuntu to as the place for grub2's boot loader (usually sda). Do not install to partitions (like sda1, sda2 etc).

For the Total space you want for Ubuntu:
Ubuntu's standard install is just / (root) & swap, but it is better to add another partition for /home:
1. 10-20 GB Mountpoint / primary or logical beginning ext4(or ext3)
2. all but 2 GB Mountpoint /home logical beginning ext4(or ext3)
3. 2 GB Mountpoint swap logical

Depending on how much memory you have you may not absolutely need swap but having some is still recommended. I do not hibernate (boots fast enough for me) but if hibernating then you need swap equal to RAM in GiB not GB. And if dual booting with windows a shared NTFS partition is also recommended. But you usually cannot create that as part of the install, just leave some space. Or partition in advance (recommended).
One advantage of partitioning in advance is that the installer will use the swap space to speed up the install. Thanks Herman for the tip.

Then if it does not boot, run the boot script recommended above.
and/or:
Grub Rescue Prompt Megathread - drs305
[http://ubuntuforums.org/showthread.php?t=1594052](http://ubuntuforums.org/showthread.php?t=1594052)
Reinstall grub2 - Short version & full chroot version
[https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB%202](https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB%202)

Oldfred, 1-After installing, at start up I get "Error: unknown filesystem grub rescue?"
No indication of whether Grub or Grub2.  Still newbie here, (and this is Absolute Beginners section). 2-Regarding your "standard recommendation" for install. How is this different from what I have done previously [chose "primary", est4, and "/" mount point.] that was unsuccessful?

---

### Post by Mr Stoozer on 2011-06-23
Make sure you're installing GRUB (done during installation) to your 1st disk (ie sda not sda/1), if you install GRUB to a partition (ie the 'unallocated partition'), it needs to be chain-loaded (which requires GRUB to be installed to the MBR of your disk).

---

### Post by bk60544 on 2011-06-23
> **Mr Stoozer said:**
> Make sure you're installing GRUB (done during installation) to your 1st disk (ie sda not sda/1), if you install GRUB to a partition (ie the 'unallocated partition'), it needs to be chain-loaded (which requires GRUB to be installed to the MBR of your disk).

MrS, Thanks for your reply/suggestion. Again, newbie here. NOTHING in the install process (10.4 or 10.10) mentions GRUB or gives options about it. Looked in my "Beginning Ubuntu Linux" book for an explanation of "chain-loaded" but nothing is in the index, so no clue what you are referring to <sorry>.  When you refer to installing to 1st disk, do you mean 1st partition? I have only ONE disk (hdd).

---

### Post by oldfred on 2011-06-23
BIOS based computers only boot from the MBR or the first sector of the hard drive which is before the first partition. 

Chainloading is using one boot loader from the MBR to boot to another boot loader. It is how grub boots windows and can be used with grub but is an advanced way and now maybe not the best way to use grub2.

---

### Post by Mr Stoozer on 2011-06-23
> **bk60544 said:**
> MrS, Thanks for your reply/suggestion. Again, newbie here. NOTHING in the install process (10.4 or 10.10) mentions GRUB or gives options about it. Looked in my "Beginning Ubuntu Linux" book for an explanation of "chain-loaded" but nothing is in the index, so no clue what you are referring to <sorry>.  When you refer to installing to 1st disk, do you mean 1st partition? I have only ONE disk (hdd).

If memory serves, just after where you specify "EXT4"/"format"/"/" as you've mentioned, you get an advanced button. Make sure that GRUB is being installed to the hard drive, not a partition.

If you open up the Gnome System Monitor and switch to the "File Systems" tab, you'll see your hard drive and its partitions; like mine.
[IMG]http://i52.tinypic.com/5kgfav.png[/IMG]

As you can by my shot i have 2 hard drives. sda & sdb
The number represent the partitions (sda3 sdb1)

When you click the advanced button i speak of, you'll see options to install to sda sda1 sda2 sda3 (or whatever setup you have) - sda1,2,3 would be partitions and not where you want to install GRUB. Install it to sda - the "hard drive".

EDIT: After a little googling, i found this image, 
[IMG]http://i56.tinypic.com/xmtkxj.png[/IMG]
it says its for 10.10 though  seem to remember the UI a little differently, anyway, see the Device for Boot Loader Installation: make sure that's not set to install to a partition (ie sdb1 sda3)

---

### Post by bk60544 on 2011-06-24
@MrStooser Thanks for reply and screenshots. very helpful. I'll check if info corresponds AFTER I resolve current problem.
>>Yesterday did 5th install, and when prompted for where to install, I chose "next contiguous" and a later step indicated that the process would create partition #5 with ext4 [Linux] and partition #6 for swap. [Too upset to ask why #3 and #4 were skipped.]  I clicked on the *Advanced* button which presented a screen where "Install boot loader" was already checked, and **Device for boot loader** had "/dev/sda" already entered in the box, so I left it unchanged.  The process when to completion, I rebooted and at startup- "Error: no such partition    grub rescue>".  Unsuccessful yet AGAIN!
>>Now I booted from Live CD 10.4 and from the terminal entered "sudo fdisk -l" [info listed below].
Then I ran "boot_info_script.sh" suggested by Mr Stoozer and Drs305. [info listed below]
-----------
ubuntu@ubuntu:~$ sudo fdisk -l


Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000b9966


   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        5151    41374741    7  HPFS/NTFS
/dev/sda2            9916       20114    81923467+   7  HPFS/NTFS
Partition 2 does not end on cylinder boundary.
/dev/sda3           20115       30402    82631681    5  Extended
/dev/sda5           20115       29977    79222784   83  Linux
/dev/sda6           29978       30402     3407872   82  Linux swap / Solaris


Disk /dev/sdb: 1010 MB, 1010826752 bytes
 m
255 heads, 63 sectors/track, 122 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x91f72d24


   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1         123      987104    6  FAT16
Partition 1 has different physical/logical endings:
     phys=(121, 254, 63) logical=(122, 227, 40)

ubuntu@ubuntu:~$ 
```

=================================
                  Boot Info Script 0.60    from 17 May 2011


============================= Boot Info Summary: ===============================

 => Grub2 (v1.97-1.98) is installed in the MBR of /dev/sda and looks at sector 
    1 of the same hard drive for core.img. core.img is at this location and 
    looks in partition 5 for /boot/grub.

sda1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files:        /boot.ini /bootmgr /Boot/BCD /ntldr /NTDETECT.COM

sda2: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files:        /Windows/System32/winload.exe

sda3: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.04.1 LTS
    Boot files:        /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda6: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1    *             63   159,284,474   159,284,412   7 NTFS / exFAT / HPFS
/dev/sda2         159,284,475   323,131,409   163,846,935   7 NTFS / exFAT / HPFS
/dev/sda3         323,133,438   488,396,799   165,263,362   5 Extended
/dev/sda5         323,133,440   481,579,007   158,445,568  83 Linux
/dev/sda6         481,581,056   488,396,799     6,815,744  82 Linux swap / Solaris


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/loop0                                              squashfs   
/dev/sda1        5767B913142B0BAC                       ntfs       XP
/dev/sda2        3E72CDAB245F5751                       ntfs       Win7
/dev/sda5        fdd562ac-40ac-4a28-9d82-0ed3609fa1a2   ext4       Ubuntu
/dev/sda6        2f00b74b-58fb-4d56-8561-40896cc51668   swap       

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)


================================ sda1/boot.ini: ================================

--------------------------------------------------------------------------------
;
;Warning: Boot.ini is used on Windows XP and earlier operating systems.
;Warning: Use BCDEDIT.exe to modify Windows Vista boot options.
;
[boot loader]
timeout=30
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS
[operating systems]
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /NOEXECUTE=OPTIN /FASTDETECT
--------------------------------------------------------------------------------

=========================== sda5/boot/grub/grub.cfg: ===========================

--------------------------------------------------------------------------------
#
# DO NOT EDIT THIS FILE
#
# It is automatically generated by /usr/sbin/grub-mkconfig using templates
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
  if [ -n ${have_grubenv} ]; then if [ -z ${boot_once} ]; then save_env recordfail; fi; fi
}
insmod ext2
set root='(hd0,5)'
search --no-floppy --fs-uuid --set fdd562ac-40ac-4a28-9d82-0ed3609fa1a2
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
insmod ext2
set root='(hd0,5)'
search --no-floppy --fs-uuid --set fdd562ac-40ac-4a28-9d82-0ed3609fa1a2
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
menuentry 'Ubuntu, with Linux 2.6.32-24-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set fdd562ac-40ac-4a28-9d82-0ed3609fa1a2
    linux    /boot/vmlinuz-2.6.32-24-generic root=UUID=fdd562ac-40ac-4a28-9d82-0ed3609fa1a2 ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-24-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-24-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set fdd562ac-40ac-4a28-9d82-0ed3609fa1a2
    echo    'Loading Linux 2.6.32-24-generic ...'
    linux    /boot/vmlinuz-2.6.32-24-generic root=UUID=fdd562ac-40ac-4a28-9d82-0ed3609fa1a2 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-24-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set fdd562ac-40ac-4a28-9d82-0ed3609fa1a2
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set fdd562ac-40ac-4a28-9d82-0ed3609fa1a2
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sda1)" {
    insmod ntfs
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 5767b913142b0bac
    chainloader +1
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###
--------------------------------------------------------------------------------

=============================== sda5/etc/fstab: ================================

--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda5 during installation
UUID=fdd562ac-40ac-4a28-9d82-0ed3609fa1a2 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda6 during installation
UUID=2f00b74b-58fb-4d56-8561-40896cc51668 none            swap    sw              0       0
--------------------------------------------------------------------------------

=================== sda5: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

 194.214641571 = 208.536383488  boot/grub/core.img                             1
 198.231185913 = 212.849115136  boot/grub/grub.cfg                             1
 194.222061157 = 208.544350208  boot/initrd.img-2.6.32-24-generic              1
 194.213241577 = 208.534880256  boot/vmlinuz-2.6.32-24-generic                 1
 194.222061157 = 208.544350208  initrd.img                                     1
 194.213241577 = 208.534880256  vmlinuz                                        1
===========================

```
>>It seems to me (still newbie) that Grub2 *was* installed on the DISK (/dev/sda) rather than partion as directed by MrStoozer and Drs305.  I previously installed dual-boot (win7 and Ub10.10) and it was easy-peasy.  THIS is a nightmare!!

---

### Post by oldfred on 2011-06-24
i cannot see any problem in the boot script. Grub is in MBR and correctly looking at sda5, UUIDs seem to match. 

Sometimes just a reinstall of grub fixes things.

Is this by any chance an older computer? I see Windows 7 so I assume not, but all you boot files are above the old 137GB limit that some computers used to have. Also some newer computers seem to have similar issues but it is just a BIOS setting that makes the computer act like the older ones.

Check these BIOS settings.

These are quotes from others who reported similar issues and changed BIOS settings. Not all BIOS use exactly the same terms for settings:

It was in the BIOS. Under Onboard Devices Settings, the SATA Mode was set to SATA. I changed it to AHCI. Then another line showed up in the BIOS that stated "Change the AHCI DID for Linux to Enabled. I booted to win7 and it loaded some new drivers. I booted to Gpart and glory be there were my hard drives.

The mode for the disc was set to AUTO. Changed it to LBA. Then it worked.
Change SATA controller mode from AHCI to Compatibility (AHCI should be ok for Vista/7 & Linux), XP may not have AHCI driver.
[http://ubuntuforums.org/showthread.php?t=1694750&page=8](http://ubuntuforums.org/showthread.php?t=1694750&page=8) post #79
Standard BIOS Settings -> [drive you want to change] -> IDE Access -> “Large”, did the trick. 

SATA mode should stay in AHCI unless you are getting nasty issues (which shouldn't happen with linux or vista/win7). The main reason why people change SATA mode to 'compatibility' is because winXP wont work with AHCI without loading the drivers..and you need a floppy drive to load the drivers, which most newer computers don't have (and lots of people are lazy anyway).

Oldfred was right on, it was the SATA Native IDE setting that hosed Grub. I had to set the OnChip SATA Type to AHCI in order to boot using Grub. As for the OnChip SATA Port 4/5 Type setting it doesn't have any affect on Grub, it can be set to IDE or as SATA Type. My MB BIOS doesn't have a Compatibility or LBA setting so I have to find the AHCI XP drivers if I want to Multi-Boot XP and Ubuntu.

---

### Post by oldfred on 2011-06-25
You mentioned computer is from 2004. I would try the alternative SATA mode and see if it boots. It may then not let you boot XP but 7 should work.

While it was about 2002 when the 137GB boot limit in BIOS was not an issue, many laptops were not the newest designs and had limited BIOS. It may still be an issue on your computer. I might try shrinking the first windows partition enough for a /boot partition (sda4) of about 300 or 400MB. That would then be totally inside the 137GB limit. Just during reinstall select the sda4 as /boot, your current / as root & it will find swap. I still like a separate /home but lets just see if a /boot works.

---

### Post by Mr Stoozer on 2011-06-25
> **oldfred said:**
> Just during reinstall select the sda4 as /boot, your current / as root & it will find swap. I still like a separate /home but lets just see if a /boot works.

Doesn't that still require GRUB being installed to the MBR? In order to chainload GRUB on sda4 i mean.

---

### Post by oldfred on 2011-06-26
Having a /boot just is the kernel, init file and grub boot files, but not boot loader. Yes boot loader has to be in the MBR and I am not suggesting also having grub2's boot loader in the PBR partition boot sector of the /boot partition.

We just want a /boot partition as some older computers have to have all the boot files inside the first 137GB. Data or /home or a shared NTFS partition can then be beyound teh 137GB limit.

---

