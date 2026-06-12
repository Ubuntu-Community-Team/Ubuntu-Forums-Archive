---
title: "New kernel/kernel panic"
date: 2010-10-06
forum: New to Ubuntu
---

### Post by JamButty on 2010-10-06
After a routine update which included a new kernel (vmlinuz-2.6.32-25-generic) I get the 

Kernel panic - not syncing: VFS: Unable to mount root fs on unknown wn-block (0,0)

error when trying to boot from that kernel. The prior kernel (vmlinuz-2.6.32-24-generic) boots with no problems. Everything looks kosher in the /boot/grub/grub/cfg file. The coding for all three kernels offered in the boot menu is identical, with just the kernel and initrd file names varying. The root= values are correct. The kernel and initrd files are where they should be.
Other similar threads deal with new installations/partition errors and other esoterica that are not applicable here. I have updated grub and grub2. Problem persists after 2 weeks and many boots and other updates (not-kernel updates). One suggestion in a couple of threads is to reinstall grub2.  A few of issues with that:

issue 1 - I am confused about the roles of grub vs. grub2. Grub2 is my bootloader. updating grub always screws me up - just throws me to the grub prompt and I have to boot manually. Updating grub2 is what has solved bootloader problems before, yet in advice given here repeatedly and even in the grub2 documentation, the advice is always to update-grub, rather than update-grub2, even when it is clear the bootloader is grub2  ???

issue 2 - The grub2 documentation says
" GRUB 2 needs to be reinstalled when a user is presented with a blank  screen with only the word "GRUB", no prompt, and no ability to enter  commands." 
Since this is not the case, I am leery of this suggestion. Also, the fact that the other kernels boot fine from the bootloader menu makes me doubt grub2 is the problem.

issue 3. Trying to do it anyway I either don't understand how to, or can't, mount the linux partition. In the instructions for reinstalling grub2 after booting from the live-disk, I need to mount the linux partition first, which for me is sda5. So that should be 
```
sudo mount /dev/sda5/mnt
```that gives the error
```
can't find /dev/sda5/mnt in /etc/fstab or  /etc/mtab
```I can access the normal partition info from the live disk (on CD):
```
Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x6cea6cea

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       14068   112994814+   7  HPFS/NTFS
/dev/sda2           14068       19458    43294721    5  Extended
/dev/sda5           14068       19231    41475072   83  Linux
/dev/sda6           19231       19458     1818624   82  Linux swap / Solaris
```this looks the same in the live-disk environment and the normal one.  The fstab file on the partition reflects this partition info, but the live-disk seems to be looking at the fstab file on the live-disk itself, (judging from the output of
```
cat /etc/fstab
```while in the live-disk environment) which is a catch-22. Am I missing something from the mount command? 

Is there another likely reason why the old kernel boots and the new one does not? 
thanks.

---

### Post by drs305 on 2010-10-06
Ok, one at a time:

update-grub and update-grub2 do the same thing. They are both stubs for "grub-mkconfig -o /boot/grub/grub.cfg".

You are missing a space in your mount command:
```
sudo mount /dev/sda[COLOR="Red"]5/[/COLOR]mnt
sudo mount /dev/sda5 /mnt

```

The "cat /etc/fstab" would try to show the LiveCD file. If your real partition is mounted correctly per the command, you should "cat /mnt/etc/fstab" to view the 'real' file.

Your analysis is pretty good. If everything in the grub menu is the same except for the kernel number and the other entries work, it would seem the new kernel entry should at least pass the parameters to the system for continuing the boot. Whether the kernel works or not is not Grub2's concern.

If you post the contents of RESULTS.txt from the boot info script we can take a look for you:
[http://bootinfoscript.sourceforge.net/]("http://bootinfoscript.sourceforge.net/")

---

### Post by JamButty on 2010-10-06
About grub/grub2 - that makes sense. The first headers upgrade I had left me at the grub prompt for 3 days and many update-grub commands failed to resolve it. Eventually someone suggested update-grub2 which did resolve it, so I have been going on assumptions from that fluke since then.

The boot script output
```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #5 for /boot/grub.

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM

sda2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.04.1 LTS
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda6: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63   225,989,691   225,989,629   7 HPFS/NTFS
/dev/sda2         225,990,654   312,580,095    86,589,442   5 Extended
/dev/sda5         225,990,656   308,940,799    82,950,144  83 Linux
/dev/sda6         308,942,848   312,580,095     3,637,248  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        B438AAA038AA60DA                       ntfs       pls                           
/dev/sda2: PTTYPE="dos" 
/dev/sda5        ea5fdf48-c060-47a9-aff2-ad4e34147cc2   ext4                                     
/dev/sda6        90e62a41-5230-41a7-9a07-4cc26cf6eff5   swap                                     
/dev/sda: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sda5        /                        ext4       (rw,errors=remount-ro)


================================ sda1/boot.ini: ================================

[boot loader] 
timeout=30 
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS 
[operating systems] 
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Home Edition" /noexecute=optin /fastdetect 

=========================== sda5/boot/grub/grub.cfg: ===========================

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
search --no-floppy --fs-uuid --set ea5fdf48-c060-47a9-aff2-ad4e34147cc2
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
search --no-floppy --fs-uuid --set ea5fdf48-c060-47a9-aff2-ad4e34147cc2
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
menuentry 'Ubuntu, with Linux 2.6.32-25-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set ea5fdf48-c060-47a9-aff2-ad4e34147cc2
    linux    /boot/vmlinuz-2.6.32-25-generic root=UUID=ea5fdf48-c060-47a9-aff2-ad4e34147cc2 ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-25-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-25-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set ea5fdf48-c060-47a9-aff2-ad4e34147cc2
    echo    'Loading Linux 2.6.32-25-generic ...'
    linux    /boot/vmlinuz-2.6.32-25-generic root=UUID=ea5fdf48-c060-47a9-aff2-ad4e34147cc2 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-25-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-24-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set ea5fdf48-c060-47a9-aff2-ad4e34147cc2
    linux    /boot/vmlinuz-2.6.32-24-generic root=UUID=ea5fdf48-c060-47a9-aff2-ad4e34147cc2 ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-24-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-24-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set ea5fdf48-c060-47a9-aff2-ad4e34147cc2
    echo    'Loading Linux 2.6.32-24-generic ...'
    linux    /boot/vmlinuz-2.6.32-24-generic root=UUID=ea5fdf48-c060-47a9-aff2-ad4e34147cc2 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-24-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-21-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set ea5fdf48-c060-47a9-aff2-ad4e34147cc2
    linux    /boot/vmlinuz-2.6.32-21-generic root=UUID=ea5fdf48-c060-47a9-aff2-ad4e34147cc2 ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-21-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-21-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set ea5fdf48-c060-47a9-aff2-ad4e34147cc2
    echo    'Loading Linux 2.6.32-21-generic ...'
    linux    /boot/vmlinuz-2.6.32-21-generic root=UUID=ea5fdf48-c060-47a9-aff2-ad4e34147cc2 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-21-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set ea5fdf48-c060-47a9-aff2-ad4e34147cc2
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set ea5fdf48-c060-47a9-aff2-ad4e34147cc2
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Microsoft Windows XP Home Edition (on /dev/sda1)" {
    insmod ntfs
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set b438aaa038aa60da
    drivemap -s (hd0) ${root}
    chainloader +1
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

=============================== sda5/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda5 during installation
UUID=ea5fdf48-c060-47a9-aff2-ad4e34147cc2 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda6 during installation
UUID=90e62a41-5230-41a7-9a07-4cc26cf6eff5 none            swap    sw              0       0

=================== sda5: Location of files loaded by Grub: ===================


 118.0GB: boot/grub/core.img
 120.7GB: boot/grub/grub.cfg
 118.0GB: boot/initrd.img-2.6.32-21-generic
 130.5GB: boot/initrd.img-2.6.32-24-generic
 145.2GB: boot/initrd.img-2.6.32-25-generic
 117.9GB: boot/vmlinuz-2.6.32-21-generic
 126.5GB: boot/vmlinuz-2.6.32-24-generic
 125.5GB: boot/vmlinuz-2.6.32-25-generic
 145.2GB: initrd.img
 130.5GB: initrd.img.old
 125.5GB: vmlinuz
 126.5GB: vmlinuz.old
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sda2

00000000  c8 aa b7 f5 5d 46 6c ba  fc 1b 07 d5 5f f9 7d eb  |....]Fl....._.}.|
00000010  ff 98 2f 03 e3 fc e1 a0  80 10 47 6a a9 79 78 ee  |../.......Gj.yx.|
00000020  ff 7d 08 c8 da c8 ca ce  25 00 70 97 02 08 95 07  |.}......%.p.....|
00000030  ed 6f 5d b6 ad dc 92 bc  1a 03 42 ea ab de f5 ba  |.o].......B.....|
00000040  a2 63 db b5 ce 73 bb 2b  ef bd 1a 39 5e e2 86 a3  |.c...s.+...9^...|
00000050  21 1e f7 87 18 48 6e dd  28 66 e4 5c fb 7d 7a 29  |!....Hn.(f.\.}z)|
00000060  cf 1f be 3e 99 da 9f da  72 be 7f 90 ea 65 2c 8f  |...>....r....e,.|
00000070  7c 76 d3 c1 b0 b7 a6 55  ea e4 63 0d 4f af 5b 55  ||v.....U..c.O.[U|
00000080  ef 11 c8 29 17 30 87 d5  ce 77 87 bc a3 f0 47 c8  |...).0...w....G.|
00000090  43 26 38 8f 09 c3 d8 22  ee 77 23 db 72 32 1b c4  |C&8....".w#.r2..|
000000a0  1e 92 93 cb b5 b7 a2 74  77 29 26 47 a5 45 ce 53  |.......tw)&G.E.S|
000000b0  a5 f0 7e ae 4b 2d d1 61  f4 ea 3c 51 1b 95 ea 7f  |..~.K-.a..<Q....|
000000c0  77 7c 5d 21 08 ea 99 1a  11 c9 e6 f8 be eb 52 1f  |w|]!..........R.|
000000d0  2e c5 7b 79 08 e7 09 b9  e6 d4 1d 11 07 5b fb 69  |..{y.........[.i|
000000e0  24 9e 9a b8 c0 32 30 08  66 76 45 fa 5a e3 4e ae  |$....20.fvE.Z.N.|
000000f0  79 1e 56 a6 41 37 26 7a  a8 d2 6b cb 73 45 b7 33  |y.V.A7&z..k.sE.3|
00000100  da 7c 06 c9 33 f0 44 f7  77 4b 26 2d e6 91 a9 13  |.|..3.D.wK&-....|
00000110  0e 40 ba b2 dd ce f5 71  40 da a9 57 47 3b b7 e8  |.@.....q@..WG;..|
00000120  1a 52 14 91 54 c4 40 46  4e 39 93 01 60 74 55 1f  |.R..T.@FN9..`tU.|
00000130  71 e2 41 75 f9 98 7d 83  23 93 09 98 21 eb ea b5  |q.Au..}.#...!...|
00000140  6a 69 c1 2e be db 9d 3c  46 96 6a 5d 4e dc eb 4c  |ji.....<F.j]N..L|
00000150  30 fa 0a 35 33 f3 99 76  34 56 78 2b db 8e 4c da  |0..53..v4Vx+..L.|
00000160  25 df 8f e3 60 76 d5 30  8d ba df 1e 6f 7f 21 b0  |%...`v.0....o.!.|
00000170  29 be 94 5f 1a c3 7e ab  19 b9 ce 1c c4 c6 95 b9  |).._..~.........|
00000180  c0 5c 96 5b 76 d3 e7 88  8f 76 29 33 8d d3 05 f3  |.\.[v....v)3....|
00000190  30 f1 1c db fc 12 d5 cf  64 ad 14 98 90 7f 61 7a  |0.......d.....az|
000001a0  9b 31 5d f0 f3 60 31 31  77 e6 3d 57 0e 11 a4 c8  |.1]..`11w.=W....|
000001b0  bb 09 56 df cf 97 7e 9b  8d e3 cb 8d 97 7b 00 fe  |..V...~......{..|
000001c0  ff ff 83 fe ff ff 02 00  00 00 00 b8 f1 04 00 fe  |................|
000001d0  ff ff 05 fe ff ff 02 b8  f1 04 00 88 37 00 00 00  |............7...|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200


```

---

### Post by drs305 on 2010-10-06
I run both the -24 and -25 kernels without problem and see nothing wrong with your menuentries. Mine are identical except for the partition. 

Since you say -24 boots fine but -25 doesn't, I'd suggest booting to -24 and purging -25 (completely remove), including the headers and any modules. The easiest way is to install Ubuntu Tweak, but you can use Synaptic or the command line. The easiest method in Synaptic is to just type 2.6.32-25 in search window to see what's installed.

I'd probably wait until my next reboot and then try reinstalling the -25 kernel to see if it works. I really don't think it's a Grub issue.

You could try rebuilding the initrd image with mkinitramfs but it will be rebuilt when you reinstall the kernel anyway.

---

### Post by JamButty on 2010-10-06
That did it.
Deinstalled the 3 bits for kernel 2.6.32-25 (header files/kernel image/kernel headers) via Synaptic. Rebooted to grub prompt, booted manually to 2.6.32-24 kernel and reinstalled the same 2.6.32-25 bits, ran update-grub. Needed to boot back into 2.6.32-24 first (hung initially on 2.6.32-25), but then it worked.
Must have been something buggy in the initial update when I got the new kernel.
Thanks!

---

### Post by drs305 on 2010-10-06
> **JamButty said:**
> That did it.
Deinstalled the 3 bits for kernel 2.6.32-25 (header files/kernel image/kernel headers) via Synaptic. Rebooted to grub prompt, booted manually to 2.6.32-24 kernel and reinstalled the same 2.6.32-25 bits, ran update-grub. Needed to boot back into 2.6.32-24 first (hung initially on 2.6.32-25), but then it worked.
Must have been something buggy in the initial update when I got the new kernel.
Thanks!

Glad it's working now. 

Just curious what exactly happened when you first tried rebooting into -25?  Normally multiple reboots shouldn't be necessary (except to change the kernel in use) since the initrd image and grub.cfg are regenerated when a new kernel is installed.

---

### Post by JamButty on 2010-10-06
It hung at the initial Ubuntu splash screen with the alternating white and red dots. It has often hung at the second splash screen (immediately before presenting the login box), maybe every 5th or 6th boot, and requires powering off and on, but only once. This hung twice in a row at this earlier point. I assumed the red and white dots weren't just an MS-style meaningless gif, but actually reflected the progress of the boot and it was clearly hung twice, so I went into 24, then again into 25.

---

### Post by JamButty on 2010-10-13
Re-opening thread as the same issue recurred after the next update - same kernel panic etc.

I started to repeat what solved it before (deinstalling/reinstalling the three 2.6.32-25 bits) but I noted Synaptic states about these:

“You likely do not want to install this package directly. Instead, install the linux-generic meta-package, which will ensure that upgrades work correctly, and that supporting packages are also installed.”

I don't see anything offered in Synaptic (or Software Center) that matches this "linux-generic meta-package". After deinstalling that kernel, rebooting and running update manager hoping it would sort out the dependencies, but it just says "Your system is up-to-date"

So how do I install the "linux-generic meta-package" for kernel 2.6.32-25? Or is this "linux-generic meta-package" message in error?

I am currently running 2.6.32-24 with updated grub.

---

### Post by QLee on 2010-10-13
[QUOTE=JamButty]...
“You likely do not want to install this package directly. Instead, install the linux-generic meta-package, which will ensure that upgrades work correctly, and that supporting packages are also installed.”

I don't see anything offered in Synaptic (or Software Center) that matches this "linux-generic meta-package". After deinstalling that kernel, rebooting and running update manager hoping it would sort out the dependencies, but it just says "Your system is up-to-date"

So how do I install the "linux-generic meta-package" for kernel 2.6.32-25? Or is this "linux-generic meta-package" message in error?
...[/QUOTE]

Maybe they left off a punctuation mark, you want the meta package linux-generic which is a package that will always depend on the latest complete generic Linux kernel available.

Since you use Synaptic, look up above the linux-headers or search for linux-generic.

---

### Post by JamButty on 2010-10-13
The three bits I deinstalled were
linux-headers-2.6.32-25
linux-headers-2.6.32-25-generic
linux-image-2.6.32-25

These are the ones which advise against directly reinstalling. There is no "meta" in any package name or package description related to this kernel. There are two packages described as "Complete Generic Linux kernel" and their version is listed as "2.6.32.25.27" so that looks right. One is linux-generic-pae, the other just linux-generic. What is the difference between these?

---

### Post by drs305 on 2010-10-13
> **JamButty said:**
> The three bits I deinstalled were
linux-headers-2.6.32-25
linux-headers-2.6.32-25-generic
linux-image-2.6.32-25

These are the ones which advise against directly reinstalling. There is no "meta" in any package name or package description related to this kernel. There are two packages described as "Complete Generic Linux kernel" and their version is listed as "2.6.32.25.27" so that looks right. One is linux-generic-pae, the other just linux-generic. What is the difference between these?

The pae kernel allows 32-bit systems to access more RAM than the standard 32-bit kernel (4GB). The current CD appears to install the PAE kernel if it recognizes the need - at least on my last install. If you have a large amount of RAM, use the PAE kernel, otherwise the generic one will do.

Note: If you highlight "linux-image" in Synaptic and select Properties from the main menubar you will see it is contained in the "Meta Packages" section.  You can also click on "Sections" in the left pane, select "Meta Packages" and it will show all packages contained in that group.

---

### Post by JamButty on 2010-10-13
Ok, will try it. Thanks!

---

### Post by JamButty on 2010-10-13
After boot, grub prompt. Manual boot into 25 kernel gave “can not read file” at initrd command.
 Manually booted into 24, updated grub, rebooted, got grub prompt again. Manually booted into 24 kernel, updated and rebooted, getting menu this time, but 25 kernel still gave “kernel panic” error. Repeated – same result. Looking in Synaptic, I find the three bits for 2.6.32-25 are not installed as previously, only one – linux-image-2.6.32-25-generic, plus the linux-generic (complete kernel)
 deinstalled both of those. Did NOT update grub. Rebooted normally via bootmenu into 24. reinstalled those same 3 bits (to hell with the “complete” one). Rebooted. As before, it hung twice at the initial splash screen while trying to boot into 25 kernel, so I booted into 24, then into 25. Seems ok now.


I am really impressed with Ubuntu in general, but I have had this or similar dance  every time but one after kernel updates. It is getting really tedious. Ok, done griping. Thanks.

---

### Post by gordintoronto on 2010-10-14
There is something, um, "odd" in your hardware. Could you give a full description, please?

---

### Post by JamButty on 2010-10-14
Not sure if this is what you were asking for, but here is lshw output

   
    ```
description: Portable Computer
    product: Inspiron 9300
    vendor: Dell Inc.
    serial: xxxxxxxxxx
    width: 32 bits
    capabilities: smbios-2.3 dmi-2.3
    configuration: boot=normal chassis=portable uuid=44454C4C-4A00-104A-804D-C7C04F5A3631
  *-core
       description: Motherboard
       vendor: Dell Inc.
       physical id: 0
       serial: xxxxxxxxxx              .
     *-firmware
          description: BIOS
          vendor: Dell Inc.
          physical id: 0
          version: A05 (09/19/2005)
          size: 64KiB
          capacity: 512KiB
          capabilities: isa pci pcmcia pnp upgrade shadowing cdboot bootselect int13floppy720 int5printscreen int9keyboard int14serial int17printer int10video acpi usb agp smartbattery biosbootspecification netboot
     *-cpu
          description: CPU
          product: Intel(R) Pentium(R) M processor 1.73GHz
          vendor: Intel Corp.
          physical id: 400
          bus info: cpu@0
          version: 6.13.8
          slot: Microprocessor
          size: 1733MHz
          capacity: 1800MHz
          width: 32 bits
          clock: 133MHz
          capabilities: fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic mtrr pge mca cmov clflush dts acpi mmx fxsr sse sse2 ss tm pbe nx up bts est tm2 cpufreq
        *-cache:0
             description: L1 cache
             physical id: 700
             size: 8KiB
             capacity: 8KiB
             capabilities: internal write-back data
        *-cache:1
             description: L2 cache
             physical id: 701
             size: 2MiB
             capacity: 2MiB
             clock: 66MHz (15.0ns)
             capabilities: pipeline-burst internal varies unified
     *-memory
          description: System Memory
          physical id: 1000
          slot: System board or motherboard
          size: 2GiB
        *-bank:0
             description: DIMM DDR Synchronous 533 MHz (1.9 ns)
             vendor: 2C00000000000000
             physical id: 0
             serial: xxxxxxx
             slot: DIMM_A
             size: 1GiB
             width: 64 bits
             clock: 533MHz (1.9ns)
        *-bank:1
             description: DIMM DDR Synchronous 533 MHz (1.9 ns)
             vendor: 2C00000000000000
             physical id: 1
             serial: xxxxxxx
             slot: DIMM_B
             size: 1GiB
             width: 64 bits
             clock: 533MHz (1.9ns)
     *-pci
          description: Host bridge
          product: Mobile 915GM/PM/GMS/910GML Express Processor to DRAM Controller
          vendor: Intel Corporation
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 03
          width: 32 bits
          clock: 33MHz
        *-pci:0
             description: PCI bridge
             product: Mobile 915GM/PM Express PCI Express Root Port
             vendor: Intel Corporation
             physical id: 1
             bus info: pci@0000:00:01.0
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: pci pm msi pciexpress bus_master cap_list
             configuration: driver=pcieport
             resources: irq:24 memory:dd000000-dfefffff memory:c0000000-cfffffff(prefetchable)
           *-display
                description: VGA compatible controller
                product: NV41.8 [GeForce Go 6800]
                vendor: nVidia Corporation
                physical id: 0
                bus info: pci@0000:01:00.0
                version: a2
                width: 64 bits
                clock: 33MHz
                capabilities: pm msi pciexpress bus_master cap_list rom
                configuration: driver=nvidia latency=0
                resources: irq:16 memory:dd000000-ddffffff memory:c0000000-cfffffff(prefetchable) memory:de000000-deffffff memory:dfe00000-dfe1ffff(prefetchable)
        *-usb:0
             description: USB Controller
             product: 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #1
             vendor: Intel Corporation
             physical id: 1d
             bus info: pci@0000:00:1d.0
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master
             configuration: driver=uhci_hcd latency=0
             resources: irq:16 ioport:bf80(size=32)
        *-usb:1
             description: USB Controller
             product: 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #2
             vendor: Intel Corporation
             physical id: 1d.1
             bus info: pci@0000:00:1d.1
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master
             configuration: driver=uhci_hcd latency=0
             resources: irq:17 ioport:bf60(size=32)
        *-usb:2
             description: USB Controller
             product: 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #3
             vendor: Intel Corporation
             physical id: 1d.2
             bus info: pci@0000:00:1d.2
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master
             configuration: driver=uhci_hcd latency=0
             resources: irq:18 ioport:bf40(size=32)
        *-usb:3
             description: USB Controller
             product: 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #4
             vendor: Intel Corporation
             physical id: 1d.3
             bus info: pci@0000:00:1d.3
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master
             configuration: driver=uhci_hcd latency=0
             resources: irq:19 ioport:bf20(size=32)
        *-usb:4
             description: USB Controller
             product: 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB2 EHCI Controller
             vendor: Intel Corporation
             physical id: 1d.7
             bus info: pci@0000:00:1d.7
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: pm debug bus_master cap_list
             configuration: driver=ehci_hcd latency=0
             resources: irq:16 memory:ffa80800-ffa80bff
        *-pci:1
             description: PCI bridge
             product: 82801 Mobile PCI Bridge
             vendor: Intel Corporation
             physical id: 1e
             bus info: pci@0000:00:1e.0
             version: d3
             width: 32 bits
             clock: 33MHz
             capabilities: pci bus_master cap_list
             resources: ioport:2000(size=4096) memory:dcf00000-dcffffff memory:80000000-83ffffff(prefetchable)
           *-network:0
                description: Ethernet interface
                product: BCM4401-B0 100Base-TX
                vendor: Broadcom Corporation
                physical id: 0
                bus info: pci@0000:03:00.0
                logical name: eth0
                version: 02
                serial: xxxxxxxxxxxx
                size: 10MB/s
                capacity: 100MB/s
                width: 32 bits
                clock: 33MHz
                capabilities: pm bus_master cap_list ethernet physical mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
                configuration: autonegotiation=on broadcast=yes driver=b44 driverversion=2.0 duplex=half latency=64 link=no multicast=yes port=twisted pair speed=10MB/s
                resources: irq:18 memory:dcffe000-dcffffff
           *-pcmcia
                description: CardBus bridge
                product: RL5c476 II
                vendor: Ricoh Co Ltd
                physical id: 1
                bus info: pci@0000:03:01.0
                version: b3
                width: 64 bits
                clock: 33MHz
                capabilities: pcmcia bus_master cap_list
                configuration: driver=yenta_cardbus latency=176 maxlatency=5 mingnt=128
                resources: iomemory:b00704030-b0070402f irq:19 memory:dcf00000-dcf00fff ioport:2000(size=256) ioport:2400(size=256) memory:80000000-83ffffff(prefetchable) memory:84000000-87ffffff
           *-firewire
                description: FireWire (IEEE 1394)
                product: R5C552 IEEE 1394 Controller
                vendor: Ricoh Co Ltd
                physical id: 1.1
                bus info: pci@0000:03:01.1
                version: 08
                width: 32 bits
                clock: 33MHz
                capabilities: pm bus_master cap_list
                configuration: driver=ohci1394 latency=64 maxlatency=4 mingnt=2
                resources: irq:18 memory:dcffc800-dcffcfff
           *-generic
                description: SD Host controller
                product: R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter
                vendor: Ricoh Co Ltd
                physical id: 1.2
                bus info: pci@0000:03:01.2
                version: 17
                width: 32 bits
                clock: 33MHz
                capabilities: pm bus_master cap_list
                configuration: driver=sdhci-pci latency=64
                resources: irq:17 memory:dcffc700-dcffc7ff
           *-network:1
                description: Wireless interface
                product: PRO/Wireless 2200BG [Calexico2] Network Connection
                vendor: Intel Corporation
                physical id: 3
                bus info: pci@0000:03:03.0
                logical name: eth1
                version: 05
                serial: xxxxxxxxxx
                width: 32 bits
                clock: 33MHz
                capabilities: pm bus_master cap_list ethernet physical wireless
                configuration: broadcast=yes driver=ipw2200 driverversion=1.2.2kmprq firmware=ABG:9.0.5.27 (Dec 12 2007) ip=192.168.0.105 latency=64 link=yes maxlatency=24 mingnt=3 multicast=yes wireless=IEEE 802.11g
                resources: irq:17 memory:dcffd000-dcffdfff
        *-multimedia
             description: Multimedia audio controller
             product: 82801FB/FBM/FR/FW/FRW (ICH6 Family) AC'97 Audio Controller
             vendor: Intel Corporation
             physical id: 1e.2
             bus info: pci@0000:00:1e.2
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: pm bus_master cap_list
             configuration: driver=Intel ICH latency=0
             resources: irq:16 ioport:ed00(size=256) ioport:ec40(size=64) memory:dffffe00-dfffffff memory:dffffd00-dffffdff
        *-communication UNCLAIMED
             description: Modem
             product: 82801FB/FBM/FR/FW/FRW (ICH6 Family) AC'97 Modem Controller
             vendor: Intel Corporation
             physical id: 1e.3
             bus info: pci@0000:00:1e.3
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: pm cap_list
             configuration: latency=0
             resources: ioport:ee00(size=256) ioport:ec80(size=128)
        *-isa
             description: ISA bridge
             product: 82801FBM (ICH6M) LPC Interface Bridge
             vendor: Intel Corporation
             physical id: 1f
             bus info: pci@0000:00:1f.0
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: isa bus_master
             configuration: latency=0
        *-ide
             description: IDE interface
             product: 82801FBM (ICH6M) SATA Controller
             vendor: Intel Corporation
             physical id: 1f.2
             bus info: pci@0000:00:1f.2
             logical name: scsi0
             logical name: scsi1
             version: 03
             width: 32 bits
             clock: 66MHz
             capabilities: ide pm bus_master cap_list emulated
             configuration: driver=ata_piix latency=0
             resources: irq:17 ioport:1f0(size=8) ioport:3f6 ioport:170(size=8) ioport:376 ioport:bfa0(size=16)
           *-disk
                description: ATA Disk
                product: SAMSUNG HM160HC
                physical id: 0
                bus info: scsi@0:0.0.0
                logical name: /dev/sda
                version: LQ10
                serial: xxxxxxxx
                size: 149GiB (160GB)
                capabilities: partitioned partitioned:dos
                configuration: ansiversion=5 signature=6cea6cea
              *-volume:0
                   description: Windows NTFS volume
                   physical id: 1
                   bus info: scsi@0:0.0.0,1
                   logical name: /dev/sda1
                   logical name: /media/pls
                   version: 3.1
                   serial: xxxxxxxxx
                   size: 107GiB
                   capacity: 107GiB
                   capabilities: primary bootable ntfs initialized
                   configuration: clustersize=4096 created=2008-12-12 03:36:00 filesystem=ntfs label=pls mount.fstype=fuseblk mount.options=rw,nosuid,nodev,relatime,user_id=0,group_id=0,default_permissions,allow_other,blksize=4096 state=mounted
              *-volume:1
                   description: Extended partition
                   physical id: 2
                   bus info: scsi@0:0.0.0,2
                   logical name: /dev/sda2
                   size: 41GiB
                   capacity: 41GiB
                   capabilities: primary extended partitioned partitioned:extended
                 *-logicalvolume:0
                      description: Linux filesystem partition
                      physical id: 5
                      logical name: /dev/sda5
                      logical name: /
                      capacity: 39GiB
                      configuration: mount.fstype=ext4 mount.options=rw,relatime,errors=remount-ro,barrier=1,data=ordered state=mounted
                 *-logicalvolume:1
                      description: Linux swap / Solaris partition
                      physical id: 6
                      logical name: /dev/sda6
                      capacity: 1776MiB
                      capabilities: nofs
           *-cdrom
                description: DVD writer
                product: DVD+-RW ND-6500A
                vendor: _NEC
                physical id: 1
                bus info: scsi@1:0.0.0
                logical name: /dev/cdrom
                logical name: /dev/cdrw
                logical name: /dev/dvd
                logical name: /dev/dvdrw
                logical name: /dev/scd0
                logical name: /dev/sr0
                version: 202C
                serial: xxxxxxxxxxxxxxx
                capabilities: removable audio cd-r cd-rw dvd dvd-r
                configuration: ansiversion=5 status=nodisc
        *-serial UNCLAIMED
             description: SMBus
             product: 82801FB/FBM/FR/FW/FRW (ICH6 Family) SMBus Controller
             vendor: Intel Corporation
             physical id: 1f.3
             bus info: pci@0000:00:1f.3
             version: 03
             width: 32 bits
             clock: 33MHz
             configuration: latency=0
             resources: ioport:10c0(size=32)
  *-battery
       product: DELL C544759
       vendor: Sanyo
       physical id: 1
       slot: Sys. Battery Bay
       capacity: 72000mWh
       configuration: voltage=11.1V


```

---

### Post by gordintoronto on 2010-10-14
Thanks, good to see all the details.  I looked at a review from 2005 of the Inspiron 9300, which said the nVidia 6800 video controller was the high point. Now, the video controller is the low point. [smile]

Other than that, the whole thing is puzzling. I've never seen an actual kernel panic.

---

### Post by JamButty on 2010-10-15
yeh, everyone at the Club for Geriatric Computers think it's the bees' knees.  It gets harder to change environments quickly when you get old - guess it goes for CPUs too. Looking over other threads, it seems a kernel panic on initial installation is a common problem, but it usually gets chalked up to borked partitions or otherwise botched installations. Here, things are pretty straightforward. System worked flawlessly upon initial installation and only got cranky after the first linux headers update.

---

### Post by actionist on 2010-11-15
I get the same kernel panic too. The 25 kernel was working well for a while. I use Dell Vostro 1400. Currently using the 24 kernel.

---

