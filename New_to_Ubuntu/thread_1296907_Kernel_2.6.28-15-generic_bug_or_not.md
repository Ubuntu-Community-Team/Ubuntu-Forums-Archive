---
title: "Kernel 2.6.28-15-generic bug or not?"
date: 2009-10-21
forum: New to Ubuntu
---

### Post by igor1102828 on 2009-10-21
Hello, everybody. I wonder, if this is a kernels' bug or not?
I have puzzling on-any-screen self-generated "5" every 4-5 seconds after upgrading [COLOR="Red"]***from Ubuntu 8.10 to Ubuntu 9.04***[/COLOR].
***It is impossible even to pass the login stage!!***
This is absolutely [COLOR="Red"]the same[/COLOR] effect that I had when uppgraded [COLOR="Red"]from Ubuntu 6.06 LTS to Ubuntu 8.04[/COLOR]. 
it was not solved then because when I moved to the version Ubuntu 8.10, the effect has disappeared. 
What I tried to do:
1) Assuming that it comes from keyboard I changed the models of keyboards (and mouses), plugged out keyboards and mouse at all,
 the effect is present.
2) In order to pass over the login stage, i've booted from LiveCD Ubuntu 9.04 32bit and 64bit. Then "5555..." is generated in terminal window, in gedit, etc... Then I've burned CD for Ubuntu 9.10 and have booted from it - the "5"-Effect IS PRESENT.
Note: all the md5sums have been checked. 
2) Tried to boot with different options. Below I give the extract from my  /boot/grub/menu.lst with my comments (after ##---> ##):
********************************************************************```

## ## End Default Options (I've inserted "root (hd1,0)" in 2nd line ##  

title           Ubuntu 8.14, kernel 2.6.27-14-generic                       ##---> NO "5"-Effect, but  PC hangs ~3 times a day ##
root            (hd1,0)
uuid            c2970882-feee-4b3b-9ea5-80b3148f1356
kernel          /boot/vmlinuz-2.6.27-14-generic root=UUID=c2970882-feee-4b3b-9ea5-80b3148f1356 ro quiet splash noapic
initrd          /boot/initrd.img-2.6.27-14-generic
savedefault
quiet

title           Ubuntu 8.15, kernel 2.6.28-15-generic                          ##--->"5"-Effect IS PRESENT ##
root            (hd1,0)
uuid            c2970882-feee-4b3b-9ea5-80b3148f1356
kernel          /boot/vmlinuz-2.6.28-15-generic root=UUID=c2970882-feee-4b3b-9ea5-80b3148f1356 ro quiet splash noapic
initrd          /boot/initrd.img-2.6.28-15-generic
savedefault
quiet

title           Ubuntu 8.15, kernel 2.6.28-15-generic (recovery mode)         ##--->"5"-Effect IS PRESENT##
root            (hd1,0)
uuid            c2970882-feee-4b3b-9ea5-80b3148f1356
kernel          /boot/vmlinuz-2.6.28-15-generic root=UUID=c2970882-feee-4b3b-9ea5-80b3148f1356 ro quiet splash noapic
initrd          /boot/initrd.img-2.6.28-15-generic
savedefault
quiet

title           Ubuntu 8.14, kernel 2.6.27-14-generic (recovery mode)         ##--->NO "5"-Effect ##
root            (hd1,0)
uuid            c2970882-feee-4b3b-9ea5-80b3148f1356
kernel          /boot/vmlinuz-2.6.27-14-generic root=UUID=c2970882-feee-4b3b-9ea5-80b3148f1356 ro single
initrd          /boot/initrd.img-2.6.27-14-generic
savedefault
quiet

title           A mozhno Ubuntu 8.11, kernel 2.6.27-11-generic      ##--->NO "5"-Effect ##
root            (hd1,0)
uuid            c2970882-feee-4b3b-9ea5-80b3148f1356
kernel          /boot/vmlinuz-2.6.27-11-generic root=UUID=c2970882-feee-4b3b-9ea5-80b3148f1356 ro quiet splash noapic
initrd          /boot/initrd.img-2.6.27-11-generic
savedefault
quiet

title           Ubuntu 8.11, kernel 2.6.27-11-generic (recovery mode)
uuid            c2970882-feee-4b3b-9ea5-80b3148f1356
kernel          /boot/vmlinuz-2.6.27-11-generic root=UUID=c2970882-feee-4b3b-9ea5-80b3148f1356 ro  single noapic
initrd          /boot/initrd.img-2.6.27-11-generic

title           Ubuntu 8.11, memtest86+
uuid            c2970882-feee-4b3b-9ea5-80b3148f1356
kernel          /boot/memtest86+.bin
quiet

# This is a divider, added to separate the menu items below from the Debian
# ones.
title           Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title           Nostalgia                           ##--->This is second-boot Windows XP on other disk, NO "5"-Effect ##
root            (hd0,0)
savedefault
makeactive
chainloader     +1
```
********************************************************************
I've bought this PC with preinstalled Vista, which worked without problems. Then I've reformatted disks and installed first
three-boot system (Vista, XP Prof. and Ubuntu), the I've removed Vista. 
Any ideas or suggestions?

just in case, the spec of my PC: 

AMD Athlon(tm) Dual Core Processor 4200+ 2.20 Ghz
(ACPI x86-based PC)
Memory RAM 2047 Mb
System type 32-bit Operating system
Display adaptors - NVIDIA GeForce 7500 LE
IDE ATA/ATAPI controllers:
IDE channel
IDE channel
NVIDIA nForce serial ATA Controller
NVIDIA nForce serial ATA Controller
Standard Dual Channel PCIIDE Controller
IEEE 1394 Bus host controllers:
AGERE OHCI Compliant IEEE 1394 Host Controller
Keyboard: HID Kyboard device
Monitor: LG L1960TR(Analog)
Network adapters:
Fujitsu Siemens Computers WLAN 802.11b/g (SiS163u)
NVIDIA nForce Networking controller
Processors:
AMD Athlon(tm) 64 X2 Dual Core Processor 4200+
AMD Athlon(tm) 64 X2 Dual Core Processor 4200+
Sound, video and Game controllers
Pinnacle PCTV 310i Capture Device
RealTek High Definition Audio
Storage controllers
Adaptec AIC-7870 PCI SCSI Controller (Emulated)
Microsoft iSCSI Initiator

---

### Post by fooman on 2009-10-21
well i'm no grub expert,  but i see a few things in the ubuntu lines that should not be there.  namely,  the "8.15" in the title should be "9.04" if thats what your using (not sure if that makes any difference at all...but i would suggest you change it anyways).
the "root (hd1,0)" should not be there.
the "savedefault" should not be there.

try adding the lines i have edited below.  put them just below the **End Default Options...." line and just above first section:
```

title           Ubuntu 9.04, kernel 2.6.28-15-generic        
uuid            c2970882-feee-4b3b-9ea5-80b3148f1356
kernel          /boot/vmlinuz-2.6.28-15-generic root=UUID=c2970882-feee-4b3b-9ea5-80b3148f1356 ro quiet splash 
initrd          /boot/initrd.img-2.6.28-15-generic
quiet
```so that the end result looks like this:

```
## ## End Default Options (I've inserted "root (hd1,0)" in 2nd line ##  

title           Ubuntu 9.04, kernel 2.6.28-15-generic        
uuid            c2970882-feee-4b3b-9ea5-80b3148f1356
kernel          /boot/vmlinuz-2.6.28-15-generic root=UUID=c2970882-feee-4b3b-9ea5-80b3148f1356 ro quiet splash 
initrd          /boot/initrd.img-2.6.28-15-generic
quiet

title           Ubuntu 8.14, kernel 2.6.27-14-generic                       ##---> NO "5"-Effect, but  PC hangs ~3 times a day ##
root            (hd1,0)
uuid            c2970882-feee-4b3b-9ea5-80b3148f1356
kernel          /boot/vmlinuz-2.6.27-14-generic root=UUID=c2970882-feee-4b3b-9ea5-80b3148f1356 ro quiet splash noapic
initrd          /boot/initrd.img-2.6.27-14-generic
savedefault
quiet

title           Ubuntu 8.15, kernel 2.6.28-15-generic                          ##--->"5"-Effect IS PRESENT ##
root            (hd1,0)
uuid            c2970882-feee-4b3b-9ea5-80b3148f1356
kernel          /boot/vmlinuz-2.6.28-15-generic root=UUID=c2970882-feee-4b3b-9ea5-80b3148f1356 ro quiet splash noapic
initrd          /boot/initrd.img-2.6.28-15-generic
savedefault
quiet

title           Ubuntu 8.15, kernel 2.6.28-15-generic (recovery mode)         ##--->"5"-Effect IS PRESENT##
root            (hd1,0)
uuid            c2970882-feee-4b3b-9ea5-80b3148f1356
kernel          /boot/vmlinuz-2.6.28-15-generic root=UUID=c2970882-feee-4b3b-9ea5-80b3148f1356 ro quiet splash noapic
initrd          /boot/initrd.img-2.6.28-15-generic
savedefault
quiet

title           Ubuntu 8.14, kernel 2.6.27-14-generic (recovery mode)         ##--->NO "5"-Effect ##
root            (hd1,0)
uuid            c2970882-feee-4b3b-9ea5-80b3148f1356
kernel          /boot/vmlinuz-2.6.27-14-generic root=UUID=c2970882-feee-4b3b-9ea5-80b3148f1356 ro single
initrd          /boot/initrd.img-2.6.27-14-generic
savedefault
quiet

title           A mozhno Ubuntu 8.11, kernel 2.6.27-11-generic      ##--->NO "5"-Effect ##
root            (hd1,0)
uuid            c2970882-feee-4b3b-9ea5-80b3148f1356
kernel          /boot/vmlinuz-2.6.27-11-generic root=UUID=c2970882-feee-4b3b-9ea5-80b3148f1356 ro quiet splash noapic
initrd          /boot/initrd.img-2.6.27-11-generic
savedefault
quiet

title           Ubuntu 8.11, kernel 2.6.27-11-generic (recovery mode)
uuid            c2970882-feee-4b3b-9ea5-80b3148f1356
kernel          /boot/vmlinuz-2.6.27-11-generic root=UUID=c2970882-feee-4b3b-9ea5-80b3148f1356 ro  single noapic
initrd          /boot/initrd.img-2.6.27-11-generic

title           Ubuntu 8.11, memtest86+
uuid            c2970882-feee-4b3b-9ea5-80b3148f1356
kernel          /boot/memtest86+.bin
quiet

# This is a divider, added to separate the menu items below from the Debian
# ones.
title           Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title           Nostalgia                           ##--->This is second-boot Windows XP on other disk, NO "5"-Effect ##
root            (hd0,0)
savedefault
makeactive
chainloader     +1
```then try to boot again,  using the first (top) option in the grub menu....see if thats any better.

hope it helps.

---

### Post by bumanie on 2009-10-21
Unless you have two hard drives (hd1,0) is not needed as this refers to a second hard drive. It is likely that grub is looking for a non-existent second hard drive to boot from. If you post the output of > sudo fdisk -l from a live cd, it will give a better indication of how your hard drive and partitions are set up.

---

### Post by igor1102828 on 2009-10-21
> **bumanie said:**
> Unless you have two hard drives (hd1,0) is not needed as this refers to a second hard drive. It is likely that grub is looking for a non-existent second hard drive to boot from. If you post the output of  from a live cd, it will give a better indication of how your hard drive and partitions are set up.

I do have two disks, on (hd0,0) is sitting boot for Windows XP (look at the end of my menu.lst, I've coded by the word Nostalgia Windows XP.
The only thing which has been changed in the /boot/grub/menu.lst after the upgrade (from binaries via Sinaptic ) to Ubuntu 9.04 was the lines with 
Ubuntu 8.15, kernel 2.6.28-15-generic. All the rest was in previous menu.lst
and everything worked perfectly with 8.10 version.Now I am sitting with the boot from the line:  
```
$ uname -a
Linux its-desktop 2.6.27-14-generic #1 SMP Mon Aug 31 13:01:41 UTC 2009 i686 GNU/Linux
``` and if the PC did not hang from time to time I'd be satisfied. But the puzzle still exists: I had ***the same*** thing when went 6.06 ---> 8.04

```
$ sudo fdisk -l
[sudo] password for its: 

Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xfd955f28

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        3831    30772476    7  HPFS/NTFS
/dev/sda2            3832       16691   103297950    7  HPFS/NTFS
/dev/sda3           16692       30400   110117542+   5  Extended
/dev/sda5           16692       25630    71802486    b  W95 FAT32
/dev/sda6           25631       30400    38314993+   b  W95 FAT32

Disk /dev/sdb: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x3843054c

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           2        1276    10241437+  83  Linux
/dev/sdb2            1278        1568     2337457+  82  Linux swap / Solaris
/dev/sdb3            1572       17141   125066025   83  Linux
/dev/sdb4           17142       30400   106502917+   5  Extended
/dev/sdb5           17142       25441    66669718+  83  Linux
/dev/sdb6           25443       28743    26515251   83  Linux
/dev/sdb7           28744       30400    13309821    b  W95 FAT32
```

---

### Post by bumanie on 2009-10-21
In that case, (hd1,0) is correct. Why it won't boot??? Sorry, I don't know. You could try supergrub disk from [here]("http://www.supergrubdisk.org/index.php?pid=5") and see if it sorts things out for you. Keep in mind, that an upgrade via upgrade manager can sometimes damage a system, it is not a perfect package, although works in most cases. I prefer fresh installations rather than using update manager, but I think there is a warning telling would-be users that the operation may damage your system. Sorry can't help with other suggestions at this stage. My system is presently running on kernel 2.6.28-15-generic, so unless there is an idiosyncratic issue with your computer, it is not the kernel causing problems as I am writing from the ubuntu 9.04 running that kernel. May be it is best to boot a live cd, save important stuff and then do a fresh installation.

---

### Post by igor1102828 on 2009-10-21
It might be of interest to have a look at the discussion of the same issue when I upgraded from 6.06 to 8.04:

[http://ubuntuforums.org/showthread.php?t=983075]("http://ubuntuforums.org/showthread.php?t=983075")

Unfortumately, no solution has been found in previous time.

---

### Post by lavinog on 2009-10-21
Let me see if I understand correctly
you upgraded to 9.04 and now you get the number 5 repeated everywhere.
Does it repeat fast like if you were holding down the key, or is the timing random?

Does it happen with the keyboard and mouse disconnected?

---

### Post by fooman on 2009-10-21
just curious....did you try my suggestion above?

---

### Post by igor1102828 on 2009-10-21
I am sorry, guys, probably, I've described the problem not in the best way, which caused some misunderstanding.
It does boot, both, from the line of Ubuntu 9.04 from the hard disk, and from Live CD. Simply, when I open any editor, or terminal window (when booted from Live CD, the line "try Ubuntu...", where the password is not required), or, if I go to the command-mode black window, everywhere I watch on-screen generated
"5...5...5...5...", where the dots stand for the time delay ~ 5 seconds.
The puzzle is why it does not happen if I boot with other kernels and does with 2.6.28.15th! 
This is why I assume that there is something in the kernels of Ubuntu 9.04 and Ubuntu 8.04 which gives to the hardware of *my PC* command to generate on screen these damned "5"-s. So, the question is **[COLOR="Red"]what is the difference between working and failing kernels?[/COLOR]**

---

### Post by igor1102828 on 2009-10-21
> **fooman said:**
> just curious....did you try my suggestion above?
Not yet: I simply don't understand 1) how the grub will find the place where from to boot: by default it always seeks the boot part on the (hd0,0), but there I have Windows XP, while Linux part I have on (hd1,0)
and 2) how it may be connected with generating of printing "5"-s on screen?
It does not happen with booting from other lines of menu.lst and never happened with Ubuntu 6.06 and Ubuntu 8.10.. It seems to me that the roots are growing from some other place. I'd appreciate if you clarified me your way of thinking.

---

### Post by igor1102828 on 2009-10-21
It seems that this is indeed important to understand just because I had the same problem after booting the last version, Ubuntu 9.10, too.  
Howeevr, its quite possible that this conflict of soft- and hardware is specific for my hardware (the spec. is given above). Then, "who"  is suspisious?

---

### Post by fooman on 2009-10-21
> **igor1102828 said:**
> Not yet: I simply don't understand 1) how the grub will find the place where from to boot: by default it always seeks the boot part on the (hd0,0), but there I have Windows XP, while Linux part I have on (hd1,0)
and 2) how it may be connected with generating of printing "5"-s on screen?
It does not happen with booting from other lines of menu.lst and never happened with Ubuntu 6.06 and Ubuntu 8.10.. It seems to me that the roots are growing from some other place. I'd appreciate if you clarified me your way of thinking.

well, i never said it would help with the "5" issue...  in your opening post,  you stated that " [B][I]It is impossible even to pass the login stage!!"

[/I][/B]so i assumed that you were not able to even boot into the kernel.  that was why i made the suggestion. 

as far as "1) how the grub will find the place where from to boot"

unless you told it otherwise...i believe that grub gets installed on the mbr of the ubuntu drive by default.  therefore i don't think it needs to be told where to look.   the only drives that may need the "root (hd*.*)" and "savedefault" are other bootable drives you have os's installed on (windows or other linux distros).  those lines may have been necessary on older versions of grub...nowadays i do not think it is needed   but, i could of course be wrong (they are not there in my grub,  except for in my suse and vista entries).

sorry but i have no clue as to your repeating "5" problem,  other then to suggest a new keyboard.  which i think you have already tried.

---

### Post by igor1102828 on 2009-10-22
> **lavinog said:**
> Let me see if I understand correctly
you upgraded to 9.04 and now you get the number 5 repeated everywhere. - [COLOR="Navy"]YES[/COLOR]

> **lavinog said:**
> Does it repeat fast like if you were holding down the key, or is the timing random?- [COLOR="Navy"]No! It appears approximately every 4-:-5 seconds: I am able to write my suer name in the login window, but not able to pass the password stage. It reminds slowly charging and discharging condensator... [/COLOR]

> **lavinog said:**
> Does it happen with the keyboard and mouse disconnected? [COLOR="Navy"]Yes[/COLOR]

[COLOR="Navy"]I decided to come back to 8.10 - I need this computer. But this is really a pity, because the same stuff happens when I test the newcoming Ubuntu 9.10. At the moment it remains  only to hope that this puzzle will be solved and me, as well as other owners of Fujitsu-Siemens PCs will be able to follow the progress...[/COLOR]

---

### Post by LewRockwell on 2009-10-22
[https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/84280](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/84280)

.

---

### Post by fooman on 2009-10-22
> **LewRockwell said:**
> [https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/84280](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/84280)

.

wow,  nice find lew!  =D>

---

### Post by lavinog on 2009-10-22
igor does your system have a tv card?

can you post the dmesg file?

---

