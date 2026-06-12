---
title: "Just recovered from &quot;error: unknown filesystem&quot;, not sure how to proceed"
date: 2010-10-23
forum: New to Ubuntu
---

### Post by realdeal_55 on 2010-10-23
Hey, everybody!

My time with Ubuntu has been short, but the story behind my issue is long. I'll try to keep it succinct:

My buddy recommended that I try out Linux, and suggested I check out Ubuntu as a place to start. I ran the "Try Ubuntu" option off of a LiveCD I burned and really liked it, so I decided to install it alongside Windows Vista on my machine. I did, and everything worked fine. Then my buddy suggested I check out Kubuntu, for the eye candy factor. Following his instructions, I installed it to check it out. I wasn't a fan, so I decided to try uninstalling it, which didn't work too well; it was basically gone, but I was getting some weird errors. Since I wasn't too far along, my buddy said I should try reinstalling Ubuntu on the partition using the LiveCD. I did, and it seemed to be working fine for a little bit, but then programs started seizing up, my Wi-Fi connectivity started failing sporadically, and the OS just became inoperable.

That was on Sunday night; since then, I've been busy with school and running Vista. Tonight, I decided to try to fix the problem. Using the Windows Disk Management tool, I formatted the partition Ubuntu was installed on, booted Ubuntu from the LiveCD, and tried to install to a new partition. After the installation was complete, I restarted my machine as instructed. GRUB failed to load the OS boot options on startup, and I was left with a command prompt which said:

error: unknown filesystem
grub rescue>

After I tried several generic commands that did nothing (help, rescue, restore, boot, restart, exit, quit, etc.) I panicked for a bit, then booted Ubuntu from the LiveCD and followed the instructions in the second post of _[COLOR=RoyalBlue][this thread]("http://ubuntu-ky.ubuntuforums.org/showthread.php?t=1573372")[/COLOR]_ to boot up Vista again. That's where I am, now. 

I really liked Ubuntu for the few days it ran on my system; I know it works, and I'm determined to get it up and running as well as it had been, again. My problem is that I am still a newbie and have absolutely no idea where to go from here. I have come here seeking some guidance; any ideas anybody has would be highly appreciated! :-D

Please and thanks!

---

### Post by Quackers on 2010-10-23
Welcome to Ubuntu Forums :-)
Have a look through this thread for info on your problem

[http://ubuntuforums.org/showthread.php?t=1594052&highlight=grub+rescue+megathread](http://ubuntuforums.org/showthread.php?t=1594052&highlight=grub+rescue+megathread)

---

### Post by realdeal_55 on 2010-10-23
OK, so it looks like purging and reinstalling GRUB 2 is my next step:
[http://ubuntuforums.org/showthread.php?t=1581099](http://ubuntuforums.org/showthread.php?t=1581099)
The instructions for that want me to run a Boot Info Script; can I post my results file here to check for "obvious discrepancies"?

---

### Post by Quackers on 2010-10-23
Yes. Once the script is run it will produce a Results.txt file. Copy the contents of that file and paste it between CODE tags. For CODE tags click on New Reply then click on the # symbol in the toolbar. Paste the contents of the file between the generated code tags.

---

### Post by realdeal_55 on 2010-10-23
Here is my Results.txt file:
```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Lilo is installed in the MBR of /dev/sda
 => Windows is installed in the MBR of /dev/sdb

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows Vista
    Boot files/dirs:   /bootmgr /Boot/BCD /Windows/System32/winload.exe

sda2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda6: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sdb1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 640.1 GB, 640135028736 bytes
255 heads, 63 sectors/track, 77825 cylinders, total 1250263728 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *          2,048   770,344,469   770,342,422   7 HPFS/NTFS
/dev/sda2         770,344,958 1,246,733,311   476,388,354   5 Extended
/dev/sda5       1,230,733,312 1,246,733,311    16,000,000  82 Linux swap / Solaris
/dev/sda6         770,344,960 1,230,733,311   460,388,352  83 Linux


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 640.1 GB, 640135028736 bytes
255 heads, 63 sectors/track, 77825 cylinders, total 1250263728 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1               2,048 1,250,260,991 1,250,258,944   7 HPFS/NTFS


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda1        1AFE6758FE672B69                       ntfs                                     
/dev/sda2: PTTYPE="dos" 
/dev/sda5        684a1c36-885f-4080-aecd-c204096d45c4   swap                                     
/dev/sda6        1948fd36-705c-49f5-add4-8073a1bf872c   ext4                                     
/dev/sda: PTTYPE="dos" 
/dev/sdb1        BE2215592215184B                       ntfs       Documents Drive               
/dev/sdb: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)
/dev/loop0       /rofs                    squashfs   (ro,noatime)


=========================== sda6/boot/grub/grub.cfg: ===========================

#
# DO NOT EDIT THIS FILE
#
# It is automatically generated by grub-mkconfig using templates
# from /etc/grub.d and settings from /etc/default/grub
#

### BEGIN /etc/grub.d/00_header ###
if [ -s $prefix/grubenv ]; then
  set have_grubenv=true
  load_env
fi
set default="0"
if [ "${prev_saved_entry}" ]; then
  set saved_entry="${prev_saved_entry}"
  save_env saved_entry
  set prev_saved_entry=
  save_env prev_saved_entry
  set boot_once=true
fi

function savedefault {
  if [ -z "${boot_once}" ]; then
    saved_entry="${chosen}"
    save_env saved_entry
  fi
}

function recordfail {
  set recordfail=1
  if [ -n "${have_grubenv}" ]; then if [ -z "${boot_once}" ]; then save_env recordfail; fi; fi
}

function load_video {
  insmod vbe
  insmod vga
}

insmod part_msdos
insmod ext2
set root='(hd0,msdos6)'
search --no-floppy --fs-uuid --set 1948fd36-705c-49f5-add4-8073a1bf872c
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(hd0,msdos6)'
search --no-floppy --fs-uuid --set 1948fd36-705c-49f5-add4-8073a1bf872c
set locale_dir=($root)/boot/grub/locale
set lang=en
insmod gettext
if [ "${recordfail}" = 1 ]; then
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
menuentry 'Ubuntu, with Linux 2.6.35-22-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos6)'
    search --no-floppy --fs-uuid --set 1948fd36-705c-49f5-add4-8073a1bf872c
    linux    /boot/vmlinuz-2.6.35-22-generic root=UUID=1948fd36-705c-49f5-add4-8073a1bf872c ro   quiet splash
    initrd    /boot/initrd.img-2.6.35-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos6)'
    search --no-floppy --fs-uuid --set 1948fd36-705c-49f5-add4-8073a1bf872c
    echo    'Loading Linux 2.6.35-22-generic ...'
    linux    /boot/vmlinuz-2.6.35-22-generic root=UUID=1948fd36-705c-49f5-add4-8073a1bf872c ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.35-22-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos6)'
    search --no-floppy --fs-uuid --set 1948fd36-705c-49f5-add4-8073a1bf872c
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos6)'
    search --no-floppy --fs-uuid --set 1948fd36-705c-49f5-add4-8073a1bf872c
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows Vista (loader) (on /dev/sda1)" {
    insmod part_msdos
    insmod ntfs
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set 1afe6758fe672b69
    chainloader +1
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

### BEGIN /etc/grub.d/41_custom ###
if [ -f  $prefix/custom.cfg ]; then
  source $prefix/custom.cfg;
fi
### END /etc/grub.d/41_custom ###

=============================== sda6/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda6 during installation
UUID=1948fd36-705c-49f5-add4-8073a1bf872c /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=684a1c36-885f-4080-aecd-c204096d45c4 none            swap    sw              0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

=================== sda6: Location of files loaded by Grub: ===================


 609.3GB: boot/grub/core.img
 575.0GB: boot/grub/grub.cfg
 395.3GB: boot/initrd.img-2.6.35-22-generic
 609.3GB: boot/vmlinuz-2.6.35-22-generic
 395.3GB: initrd.img
 609.3GB: vmlinuz
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sda2

00000000  56 ed 08 00 00 00 01 00  4f 79 08 00 00 00 02 00  |V.......Oy......|
00000010  56 ed 08 00 00 00 03 00  98 57 08 00 00 00 04 00  |V........W......|
00000020  43 5d 08 00 00 00 01 00  16 59 08 00 00 00 01 00  |C].......Y......|
00000030  43 5d 08 00 00 00 02 00  4a 5d 08 00 00 00 01 00  |C]......J]......|
00000040  98 57 08 00 00 00 02 00  43 5d 08 00 00 00 01 00  |.W......C]......|
00000050  16 59 08 00 00 00 01 00  88 5d 08 00 00 00 01 00  |.Y.......]......|
00000060  f4 f5 08 00 00 00 01 00  48 8b 02 00 00 00 01 00  |........H.......|
00000070  ff 68 06 00 00 00 01 00  39 c4 05 00 00 00 01 00  |.h......9.......|
00000080  39 c4 05 00 00 00 01 00  a4 f6 08 00 00 00 01 00  |9...............|
00000090  a4 f6 08 00 00 00 02 00  ad f6 08 00 00 00 01 00  |................|
000000a0  39 c4 05 00 00 00 01 00  39 c4 05 00 00 00 01 00  |9.......9.......|
*
000000d0  39 c4 05 00 00 00 01 00  bb f6 08 00 00 00 01 00  |9...............|
000000e0  39 c4 05 00 00 00 01 00  39 c4 05 00 00 00 01 00  |9.......9.......|
*
00000150  39 c4 05 00 00 00 01 00  b8 91 08 00 00 00 01 00  |9...............|
00000160  b8 91 08 00 00 00 01 00  12 5b 08 00 00 00 01 00  |.........[......|
00000170  c4 f6 08 00 00 00 01 00  88 5d 08 00 00 00 01 00  |.........]......|
00000180  d7 f6 08 00 00 00 01 00  12 5b 08 00 00 00 01 00  |.........[......|
00000190  d7 f6 08 00 00 00 01 00  e7 f6 08 00 00 00 01 00  |................|
000001a0  f5 f6 08 00 00 00 01 00  f5 f6 08 00 00 00 01 00  |................|
000001b0  f5 f6 08 00 00 00 01 00  15 f7 08 00 00 00 00 fe  |................|
000001c0  ff ff 82 fe ff ff 02 f8  70 1b 00 24 f4 00 00 fe  |........p..$....|
000001d0  ff ff 05 fe ff ff 01 00  00 00 01 f8 70 1b 00 00  |............p...|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200


```Anything in there seem odd to you? Or should I proceed with the instructions for purging and reinstalling Grub 2?

---

### Post by Quackers on 2010-10-23
Unfortunately as I haven't used lilo, I'm not familiar with its workings. The only thing missing as far as I can see is that grub is not loaded in the mbr of sda. I might try just re-installing grub to sda by running the Ubuntu cd and using drs305's guide.

---

### Post by realdeal_55 on 2010-10-23
Following the "What Can I Try First?" instructions successfully loaded Grub on my next boot. I loaded Ubuntu, but then I started having the same problems I was having after I tried reinstalling last weekend (see first post); intermittent Wi-Fi and system seizures, etc.. I just hard booted my system and am in Vista, again. How can we go about troubleshooting this?

Please and thanks! :-D

---

### Post by coffeecat on 2010-10-23
That trick with lilo for getting booting into Windows again (which you linked to) is often recommended for those quitting Ubuntu and who haven't got a Windows CD to repair the MBR. I'd always assumed that the 'sudo lilo -M /dev/sda mbr' simply wrote the mbr with code equivalent to the Windows mbr. Interesting that the bootscript should reveal that it's actually lilo sitting there.

Anyway....

> **realdeal_55 said:**
>  intermittent Wi-Fi and system seizures, etc..

You are being unlucky. Intermittent WiFi might be solvable. System seizures might be the proverbial needle in a haystack. But let's be optimistic! :) 

WiFi: Boot into Ubuntu, allow the wi-fi to connect as much as it is able and then post the terminal output of:

```
sudo lshw -C network
```Useful tip: if you find your wireless is so flaky that you can't post the output, save it as a text file with gedit (not forgetting to include a .txt filename extension otherwise Windows will have a fit of the vapours). Transfer it to Vista and open it with Wordpad, not Notepad. If you open it in Notepad, it will appear all on one line. (I think I've got that the right way round. :?)

System seizures. Could be anything from faulty RAM to some obscure hardware incompatibility with Linux. Yes, it could be faulty RAM even if Windows is OK. Linux utilises RAM differently from Windows and is more likely to encounter faults in the upper registers.

For starters, post details of your hardware. Make and model if it is an OEM machine. Details of motherboard and graphics card if you built it yourself. And for good measure, post the terminal output of:

```
lspci
```And I am sure Quackers will be able to think of something I've forgotten! :p

---

### Post by realdeal_55 on 2010-10-24
Output from ```
sudo lshw -C network
``````
  *-network               
       description: Ethernet interface
       product: RTL8111/8168B PCI Express Gigabit Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: eth0
       version: 02
       serial: 00:24:1d:72:31:97
       size: 10MB/s
       capacity: 1GB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=half latency=0 link=no multicast=yes port=MII speed=10MB/s
       resources: irq:43 ioport:ce00(size=256) memory:fdfff000-fdffffff memory:fdfe0000-fdfeffff memory:fdf00000-fdf0ffff
  *-network
       description: Wireless interface
       physical id: 1
       logical name: wlan0
       serial: 00:26:5a:72:8f:13
       capabilities: ethernet physical wireless
       configuration: broadcast=yes ip=192.168.10.105 multicast=yes wireless=Ralink STA

```Output from ```
lspci
``````
00:00.0 Host bridge: ATI Technologies Inc RD780 Northbridge only dual slot PCI-e_GFX and HT1 K8 part
00:02.0 PCI bridge: ATI Technologies Inc RD790 PCI to PCI bridge (external gfx0 port A)
00:04.0 PCI bridge: ATI Technologies Inc RD790 PCI to PCI bridge (PCI express gpp port A)
00:0a.0 PCI bridge: ATI Technologies Inc RD790 PCI to PCI bridge (PCI express gpp port F)
00:11.0 SATA controller: ATI Technologies Inc SB700/SB800 SATA Controller [IDE mode]
00:12.0 USB Controller: ATI Technologies Inc SB700/SB800 USB OHCI0 Controller
00:12.1 USB Controller: ATI Technologies Inc SB700 USB OHCI1 Controller
00:12.2 USB Controller: ATI Technologies Inc SB700/SB800 USB EHCI Controller
00:13.0 USB Controller: ATI Technologies Inc SB700/SB800 USB OHCI0 Controller
00:13.1 USB Controller: ATI Technologies Inc SB700 USB OHCI1 Controller
00:13.2 USB Controller: ATI Technologies Inc SB700/SB800 USB EHCI Controller
00:14.0 SMBus: ATI Technologies Inc SBx00 SMBus Controller (rev 3a)
00:14.1 IDE interface: ATI Technologies Inc SB700/SB800 IDE Controller
00:14.2 Audio device: ATI Technologies Inc SBx00 Azalia (Intel HDA)
00:14.3 ISA bridge: ATI Technologies Inc SB700/SB800 LPC host controller
00:14.4 PCI bridge: ATI Technologies Inc SBx00 PCI to PCI Bridge
00:14.5 USB Controller: ATI Technologies Inc SB700/SB800 USB OHCI2 Controller
00:18.0 Host bridge: Advanced Micro Devices [AMD] Family 10h Processor HyperTransport Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] Family 10h Processor Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] Family 10h Processor DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] Family 10h Processor Miscellaneous Control
00:18.4 Host bridge: Advanced Micro Devices [AMD] Family 10h Processor Link Control
01:00.0 VGA compatible controller: ATI Technologies Inc RV770 LE [Radeon HD 4800 Series]
01:00.1 Audio device: ATI Technologies Inc HD48x0 audio
02:00.0 SATA controller: JMicron Technology Corp. JMB362/JMB363 Serial ATA Controller (rev 02)
02:00.1 IDE interface: JMicron Technology Corp. JMB362/JMB363 Serial ATA Controller (rev 02)
03:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 02)
04:0e.0 FireWire (IEEE 1394): Texas Instruments TSB43AB23 IEEE-1394a-2000 Controller (PHY/Link)

```System specs:
[IMG]http://i55.tinypic.com/2mzcf34.jpg[/IMG]
Built the system in August 2009.

---

### Post by coffeecat on 2010-10-24
OK

Number 1 - wireless. I see that lshw is having a fit of the taciturns today and telling us less about wireless than ethernet. It seems to do this occasionally. But at least it tells us that you have a Ralink wireless chipset, but not the actual chipset. For some Ralink chipsets, so I read, you can solve some problems by blacklisting a driver, but we need more details. Your wireless device doesn't appear in lspci, so can I assume it's a usb dongle? If so, make sure it's plugged in and post the output of:

```
lsusb
```Also, post the make and model, although this is often less useful than the output of lsusb. The lsusb output may appear unpromising, but it will give us the ID number, which can be googled.

1 - The Haystack. I told you that this might be fruitless, but I see the possibility of a little glint. You are using an ATI card. In Ubuntu, are you using the in-the-box open-source driver or the proprietary fglrx one? If the proprietary one, that might just be the problem. I have a slightly earlier card than yours:

```
02:00.0 VGA compatible controller: ATI Technologies Inc RV710 [Radeon HD 4350]
```... and I get all the gee-whiz flashy 3d compiz effects I need from the open-source driver. All the proprietary driver did for me was to mess up the pretty Plymouth boot splash. :rolleyes: So, unless you have need of the proprietary driver for gaming, it might be worth uninstalling it to see if that helps. Don't do anything just yet. The ATI proprietary driver tends to leave bits of itself lurking in the system and the 'Hardware Drivers' utility isn't always reliable in getting rid of it (at least last time I tried in an earlier version of Ubuntu). If you need it, I can post a link to how to get rid of it reliably.

---

### Post by realdeal_55 on 2010-10-24
Yeah, sorry, I should have noted before that my Wi-Fi adapter is a USB dongle. It's a D-Link CWA125NA.
Output of: ```
lsusb
``````
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 002: ID 046d:c517 Logitech, Inc. LX710 Cordless Desktop Laser
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 003: ID 07d1:3c0d D-Link System DWA-125 Wireless 150 USB Adapter
Bus 002 Device 002: ID 046d:080f Logitech, Inc. Webcam C120
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
```I'm not too sure how to tell which ATI driver I'm using. The "Additional Drivers" option under System > Administration said that "No proprietary drivers are in use on this system." So I guess there's the giveaway. The same window also explicitly said that I could install the fglrx driver, if I wanted to.

---

### Post by coffeecat on 2010-10-24
> **realdeal_55 said:**
> Yeah, sorry, I should have noted before that my Wi-Fi adapter is a USB dongle. It's a D-Link CWA125NA.```
Bus 002 Device 003: ID 07d1:3c0d D-Link System DWA-125 Wireless 150 USB Adapter
```

I've found some links for you. The bug report refers to Karmic and Lucid with that device non-functional whereas you're running Maverick with  intermittently working wireless, but I think it still might be relevant.

Bug report:

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/546653](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/546653)

Possibly useful thread:

[http://ubuntuforums.org/showthread.php?p=9700749](http://ubuntuforums.org/showthread.php?p=9700749)

... but keep that on the back-burner, and this seems to give the best lead:

[http://ubuntuforums.org/showpost.php?p=8966294&postcount=37](http://ubuntuforums.org/showpost.php?p=8966294&postcount=37)

It's from a 9-page thread if you have the energy to read the lot. I think it's worth trying what's described there. You don't have to bother with the ndiswrapper bit since you haven't installed ndiswrapper, nor the uninstalling of compiled drivers. Let us know how you get on.

> **realdeal_55 said:**
> I'm not too sure how to tell which ATI driver I'm using. The "Additional Drivers" option under System > Administration said that "No proprietary drivers are in use on this system." So I guess there's the giveaway. The same window also explicitly said that I could install the fglrx driver, if I wanted to.

OK, you're using the open-source driver. It just occurred to me that if you are experiencing wireless driver problems, they could be the cause of system freezes. Perhaps the fix described in that link will help.

---

### Post by realdeal_55 on 2010-10-24
> **coffeecat said:**
> ... but keep that on the back-burner, and this seems to give the best lead:

[http://ubuntuforums.org/showpost.php?p=8966294&postcount=37](http://ubuntuforums.org/showpost.php?p=8966294&postcount=37)

Following those instructions seems to have improved connectivity and stability. I'll monitor for a little while to see if it does anything funny. Otherwise, I'll come back in a few hours and change the thread to SOLVED.

Thanks for all your help! :-D

---

