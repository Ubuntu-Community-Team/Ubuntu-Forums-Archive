---
title: "Cannot get 8.04 to install on multi disk setup"
date: 2009-09-17
forum: New to Ubuntu
---

### Post by dgub on 2009-09-17
Hallo

I am having endless problems getting 8.04 to install  on a PATA/SATA disk setup where the PATA is not the boot disk although it is seen as the first disk in the BIOS.

This has to dual boot with XP.

I have lost count of the number of times I have tried to install it but it is well into double figures.

I have found through trial & error that it is better to manually select the partition for Ubuntu to stop it overwriting another partition.

I set it up on the last HD of 4 with the following partiions
/
swap
/usr
/home
These are from the front of the disk. No other data/OS is on this disk.

That works ok.

At the end of the install there is an advanced option to select the boot disk. By default it shows HD0, but I set it to use the boot disk which is sdd - the XP boot disk.

When it reboots all I get is GRUB at the top of the screen. Nothing further happens.

If I select the boot disk as sdd1, then the Grub menu comes up and it will boot ok into Ubuntu. However XP will not boot and comes up with NTLDR is missing. Have now discovered that choosing the sdd1 option erases the XP partition. 

I have images of the XP partition so that I can get Windows working again but that leaves Ubuntu installed but not accessible.

I have tried all sorts of variations but cannot get beyond this point.

None of "NTLDR is missing" searches here are relevant to my setup - obvious because the partition has been erased.

I found one link here

[http://www.techradar.com/news/computing/recover-data-with-linux-633042](http://www.techradar.com/news/computing/recover-data-with-linux-633042)

which I thought would solve it, but although it runs, it does not produce a result.

The details of my device.map is 
> (hd0)	/dev/sda
(hd1)	/dev/sdb
(hd2)	/dev/sdc
(hd3)	/dev/sdd

and menu.lst
> # menu.lst - See: grub(8), info grub, update-grub(8)
#            grub-install(8), grub-floppy(8),
#            grub-md5-crypt, /usr/share/doc/grub
#            and /usr/share/doc/grub-doc/.

## default num
# Set the default entry to the entry number NUM. Numbering starts from 0, and
# the entry number 0 is the default if the command is not used.
#
# You can specify 'saved' instead of a number. In this case, the default entry
# is the entry saved with the command 'savedefault'.
# WARNING: If you are using dmraid do not use 'savedefault' or your
# array will desync and will not let you boot your system.
default		0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout		10

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
#hiddenmenu

# Pretty colours
#color cyan/blue white/blue

## password ['--md5'] passwd
# If used in the first section of a menu file, disable all interactive editing
# control (menu entry editor and command-line)  and entries protected by the
# command 'lock'
# e.g. password topsecret
#      password --md5 $1$gLhU0/$aW78kHK1QfV3P2b2znUoe/
# password topsecret

#
# examples
#
# title		Windows 95/98/NT/2000
# root		(hd0,0)
# makeactive
# chainloader	+1
#
# title		Linux
# root		(hd0,1)
# kernel	/vmlinuz root=/dev/hda2 ro
#

#
# Put static boot stanzas before and/or after AUTOMAGIC KERNEL LIST

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
# kopt=root=UUID=73fcf5ff-e5b0-4084-8b01-f53bafb407cb ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd3,0)

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

title		Ubuntu 8.04.3 LTS, kernel 2.6.24-24-generic
root		(hd3,0)
kernel		/boot/vmlinuz-2.6.24-24-generic root=UUID=73fcf5ff-e5b0-4084-8b01-f53bafb407cb ro quiet splash
initrd		/boot/initrd.img-2.6.24-24-generic
quiet

title		Ubuntu 8.04.3 LTS, kernel 2.6.24-24-generic (recovery mode)
root		(hd3,0)
kernel		/boot/vmlinuz-2.6.24-24-generic root=UUID=73fcf5ff-e5b0-4084-8b01-f53bafb407cb ro single
initrd		/boot/initrd.img-2.6.24-24-generic

title		Ubuntu 8.04.3 LTS, memtest86+
root		(hd3,0)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Microsoft Windows XP Professional
root		(hd0,0)
savedefault
chainloader	+1


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sdb1
title		Microsoft Windows XP Professional
root		(hd1,0)
savedefault
map		(hd0) (hd1)
map		(hd1) (hd0)
chainloader	+1



The current position is that after again installing Ubuntu I have had to restore the MBR to get XP working. Ubuntu remains installed on the last SATA disk.

I would appreciate some help in moving forward from here please.

---

### Post by Hospadar on 2009-09-17
I would do your setup to the point where you get the missing ntldr message.
You can (from google somewhere, or an install cd) get the ntldr file manually, and if you put it on the root of the windows drive it should work ok.  I've done this method before with success.

---

### Post by dgub on 2009-09-17
> **Hospadar said:**
> I would do your setup to the point where you get the missing ntldr message.
You can (from google somewhere, or an install cd) get the ntldr file manually, and if you put it on the root of the windows drive it should work ok.  I've done this method before with success.

Thank you for your thoughts but ntldr is missing because setting sbb1 as the boot erases the XP partition. 

I have just tried installing again using sbb1 as the boot partition then restoring the XP image back to that partition. That gets XP back and gets rid of Grub - so no further forward unfortunately.

---

### Post by egalvan on 2009-09-17
Several questions come to mind...

so please post the output of the following terminal commands

```
sudo blkid

sudo fdisk -l
```

enclose them in "code" tags rather than "quote" tags, please..
makes them easer to read, and also shortens the post length.

I've always been a proponent of installing XP on the first primary partition of the first hard drive... it makes life easier.
It IS possible to change this, but it is more work.

I also want to clarify a few things...

GRUB does not delete or create partitions..
it works with master boot records (MBR).

GRUB exists as a seperate "mini-OS" from any other OS.
It can even be installed in it's own seperate partition or drive.

Changing from a Windows MBR to a GRUB MBR does not delete the Windows partition.

Windows and *nix see drives differently,  so using the drive order that XP sees in GRUB/Linux can lead to errors.
Also, Windows hard-codes the drive letters in the registry.
GRUB/Linux redo them every boot
 (which is why 'dev/' has changed to 'UUID' as the way to  identify drives/partitions... dev/ can change, UUID are "permanent".

---

### Post by egalvan on 2009-09-17
Further, here is a compilation of notes I have that can help re-install GRUB...
these come from several different sources, among them this forum, and hermanzone, and aysiu's "psycocats" web site.

If you get a stable XP install, then try these...

A live CD, such as the Ubuntu LiveCD, or PartedMagic LiveCD,
is needed if you have no working Linux.

also, read this about XP remembering assigned drive letters...

[http://www.goodells.net/multiboot/partsigs.htm](http://www.goodells.net/multiboot/partsigs.htm)

good luck

```
Quick Re-Install GRUB, if file locations are known
4-step short story

In terminal
  sudo grub
  root (hd0,x)    <-- this must point to location of 'stage1', else see nb:
  setup (hd0)     <-- installs grub IPL to MBR of first hard drive. Prefered method.
  quit

Reboot

nb: if location of 'stage1' is unknown,
  find grub/stage1
or
  find /boot/grub/stage1
is needed, after step #1
Or use next method instead.

----------------------

Re-Install GRUB, if file locations are un-known
long story

1. Boot your computer up with Live CD
2. Open a terminal window (or switch to a tty ).
3. Type 'sudo grub'.
   Should get text of which last line is "grub>"
4. Type "find /boot/grub/stage1".
   You'll get a response like "(hd0,1)".
   Use whatever your computer spits out for the following lines.
5. Type "root (hd0,1)" ( what you got in step #4 hard disk + boot partition )
6. Type
       "setup (hd0)", to install GRUB to MBR, prefered method
OR     "setup (hd0,1)" (whatever your hard disk + partition # is)
                       to install GRUB to a  partition.
7. Quit grub by typing "quit".
8. Reboot and remove the bootable CD.
```

---

### Post by dgub on 2009-09-17
> **egalvan said:**
> Several questions come to mind...

so please post the output of the following terminal commands

```
sudo blkid

sudo fdisk -l
```
<snip>


Thank you for your reply. The output from these commands is as follows:-

```
ubuntu@ubuntu:~$ sudo blkid
/dev/sda1: UUID="FCCC8E1BCC8DCFF6" LABEL="PATA drive" TYPE="ntfs" 
/dev/sdb1: UUID="1F31D09C37FECC09" LABEL="New Boot" TYPE="ntfs" 
/dev/sdb5: UUID="7B8C348A22312740" LABEL="Photos" TYPE="ntfs" 
/dev/sdb6: UUID="16F50C0F4BB5A37A" LABEL="Temp" TYPE="ntfs" 
/dev/sdb7: UUID="0454C837000FA6ED" LABEL="Programs" TYPE="ntfs" 
/dev/sdb8: UUID="32F14BE275A21C66" LABEL="Data" TYPE="ntfs" 
/dev/sdb9: UUID="2FDD267671BD39A5" LABEL="Download" TYPE="ntfs" 
/dev/sdb10: UUID="26581A250C2A9791" TYPE="ntfs" 
/dev/sdc1: UUID="6C6CA94B6CA910BE" LABEL="Large" TYPE="ntfs" 
/dev/sdd1: UUID="73fcf5ff-e5b0-4084-8b01-f53bafb407cb" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sdd2: UUID="21a240da-9208-4524-b118-53d2cdb5538d" TYPE="swap" 
/dev/sdd3: UUID="d4c7877e-72a4-4c72-a53d-c5dee97528a1" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sdd5: UUID="ea5d0268-5f22-49f7-8e0c-3a0c0c205c87" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sdd6: UUID="EC0C6CD50C6C9BF8" LABEL="Sata 3" TYPE="ntfs" 
/dev/loop0: TYPE="squashfs" 

~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x9bc11ff5

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        3191    25631676    7  HPFS/NTFS
/dev/sda2   *        3192       38913   286936965   83  Linux

Disk /dev/sdb: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000acfad

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1        2550    20482843+   7  HPFS/NTFS
/dev/sdb2            2551       38913   292085797+   5  Extended
/dev/sdb5            2551        6374    30716248+   7  HPFS/NTFS
/dev/sdb6            6375        9434    24579418+   7  HPFS/NTFS
/dev/sdb7            9435       11984    20482843+   7  HPFS/NTFS
/dev/sdb8           11985       17211    41985846    7  HPFS/NTFS
/dev/sdb9           17212       19970    22161636    7  HPFS/NTFS
/dev/sdb10          19971       38913   152159616    7  HPFS/NTFS

Disk /dev/sdc: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x9ee13071

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1       38913   312568641    7  HPFS/NTFS

Disk /dev/sdd: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000c9a17

   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1   *           1        2082    16723633+  83  Linux
/dev/sdd2            2083        3013     7478257+  82  Linux swap / Solaris
/dev/sdd3            3014       10710    61826152+  83  Linux
/dev/sdd4           10711       38913   226540597+   f  W95 Ext'd (LBA)
/dev/sdd5           10711       15694    40033948+  83  Linux
/dev/sdd6           15695       38913   186506586    7  HPFS/NTFS
ubuntu@ubuntu:~$ 



```

On your second post I tried that using (hd1) and on reboot that just shows GRUB at the top of the screen. I had to restore the MBR to get a working system again.

Unfortunately the first disk is an older IDE (PATA) drive which is no longer a booting drive.

If on the Ubuntu install, the boot disk is set as sbb1 rather than sbb then it does indeed remove the partition.

I am beginning to think this is not possible to install. Are there any particular bugs in 8.04 relating to this that are solved in a later version?

---

### Post by egalvan on 2009-09-17
> **dgub said:**
> 

On your second post I tried that using (hd1) and on reboot that just shows GRUB at the top of the screen. I had to restore the MBR to get a working system again.

Unfortunately the first disk is an older IDE (PATA) drive which is no longer a booting drive.

If on the Ubuntu install, the boot disk is set as sbb1 rather than sbb then it does indeed remove the partition.

I am beginning to think this is not possible to install. Are there any particular bugs in 8.04 relating to this that are solved in a later version?


A quick perusal shows no glaring errors. I'm a bit pressed for time right now, though.

But I will say this...

This IS POSSIBLE, because it's been done before.

The age of the drives is immaterial, except if it is not operating correctly.

The type of drive (PATA or SATA) is also immaterial.

The BOOT ORDER is critical. You MUST find what drive is the boot drive when using Linux.
THIS is the MBR to which GRUB should be loaded...
all else flows from here.

When the machine boots up, the BIOS will look to a specific drive.
It will read 446 bytes from the start of the drive,
and start executing the code it loaded.
This is the IPL (Initial Program Loader)

It can be Microsoft, or GRUB.

Microsoft IPL just jumps to a set location... which is why it is to limited, and most Linux users do NOT use MS IPL.

GRUB IPL is generated when installing GRUB. It points to wherever the stage1.5 file is located.
so it is much more general, and versatile... which is why it is used by Linux folks.

The boot order is a bit complicated...

here is a website with more detailed info.

[http://www.ibm.com/developerworks/library/l-bootload.html?ca=dgr-lnxw01LILOandGRUB](http://www.ibm.com/developerworks/library/l-bootload.html?ca=dgr-lnxw01LILOandGRUB)

here's another...

[http://en.wikipedia.org/wiki/Boot_sequence](http://en.wikipedia.org/wiki/Boot_sequence)

look further at the section titled *Boot sequence on standard PC (IBM-PC compatible)*


the reason I am giving you all this info is to try to help you help yourself...
you are trying to boot windows in a non-windows way, and windows does not like that.
Windows wants to be the only OS on your machine, installed on the first primary partition of the first hard drive.

Linux is much more forgiving... it really does not care where it is installed, as long as the boot loader can find it...
and GRUB is similar, not caring where it is installed as long as it's IPL can find it. (some restrictions apply to this scenario, but they ae irrelevant at this point, as I don't think your machine is so old that is is BIOS-limited on the hard drive size.)

I'm also very leary of GRUB "removing partitions". I have NEVER heard of that before.
it DOES replace the IPL, which can cause a Windows partition to be invisible to Windows.


I'm beginning to think you have bigger fish to fry here.

How many different Windows installations exist on this system?


And try to nail down which is the boot drive.
This is critical.


I really wish caljohnsmith or meifera were still around, they are extremely knowledgable about boot stuff...

---

### Post by egalvan on 2009-09-17
OK recalling caljohnsmith and meifera made me remember this script they wrote

[http://sourceforge.net/projects/bootinfoscript/](http://sourceforge.net/projects/bootinfoscript/)

download it to your desktop. double-click to execute it.

it will generate a file called RESULTS.txt

upload it here, maybe it will shed some light.

---

### Post by egalvan on 2009-09-17
This is the RESULTS.txt from my machine...
So you can see what kind of information the script generates.

---

### Post by dgub on 2009-09-17
> **egalvan said:**
> OK recalling caljohnsmith and meifera made me remember this script they wrote

[http://sourceforge.net/projects/bootinfoscript/](http://sourceforge.net/projects/bootinfoscript/)

download it to your desktop. double-click to execute it.

it will generate a file called RESULTS.txt

upload it here, maybe it will shed some light.

Thanks for taking the time to reply. 

It is getting a bit late here so will go through it tomorrow and post back the results.

---

### Post by oldfred on 2009-09-17
OK, I am very confused. The results.txt you posted only shows one HD and it looks correct. Windows is on the first partition and linux in partition 5. That should work. 

Your earlier posts show 4 hd's. As egalvan said the BIOS boot order is critical to how the system boots. It does not matter whether the first drive is Pata or Sata and the order when installed should not be changed and grub must be installed to the boot drive (hd0,0). 
If you install Grub anywhere else it assumes you are knowledgeable enough to chainboot, rewrite a current menu.lst to correctly find grub to boot, or permanently change the boot order and edit menu.lst. Booting you computer will only go the first HD as specified in BIOS.   If you change the HD  order in BIOS you have to change all the grub entries like (hd0,1) to match their new location. Ubuntu will keep working as it uses the UUID entries that do not change (unless you repartition your system).

---

### Post by egalvan on 2009-09-18
> **oldfred said:**
> OK, I am very confused. The results.txt you posted only shows one HD and it looks correct. Windows is on the first partition and linux in partition 5.

Your earlier posts show 4 hd's. .

Ummm, I think you are looking at the example I posted.
Not the OP's results.txt...

This was from my own machine, intended to give him a preview of what the script does, and what information it can supply....

Sorry.

---

### Post by dgub on 2009-09-18
> **egalvan said:**
> OK recalling caljohnsmith and meifera made me remember this script they wrote

[http://sourceforge.net/projects/bootinfoscript/](http://sourceforge.net/projects/bootinfoscript/)

download it to your desktop. double-click to execute it.

it will generate a file called RESULTS.txt

upload it here, maybe it will shed some light.

I tried that but it does not run either Live CD or a temp install of Ubuntu. Double clicking on it just brings up the text editor. The instructions to run it at the top do not work either, even changing the "script_028" to "script032"

In the meantime I have unplugged the PATA drive and that will produce a working menu in which both O/S's will boot. I can even plug the PATA drive back in at Grub and both will load and read the disk, but this is a crazy way to work. 

I don't know if this is relevant but the PATA drive is a slave to a CDROM drive. Because that is now faulty I have removed it leaving the PATA as a slave drive. Since everything worked in XP I did not bother to change anything.

Logically I would have thought that if I just change the disk references by 1 in the menu.lst it should work, but have tried that in the past and it did not. I am enclosing the current device.map and menu.lst

> 
(hd0)	/dev/sda
(hd1)	/dev/sdb
(hd2)	/dev/sdc


```
# menu.lst - See: grub(8), info grub, update-grub(8)
#            grub-install(8), grub-floppy(8),
#            grub-md5-crypt, /usr/share/doc/grub
#            and /usr/share/doc/grub-doc/.

## default num
# Set the default entry to the entry number NUM. Numbering starts from 0, and
# the entry number 0 is the default if the command is not used.
#
# You can specify 'saved' instead of a number. In this case, the default entry
# is the entry saved with the command 'savedefault'.
# WARNING: If you are using dmraid do not use 'savedefault' or your
# array will desync and will not let you boot your system.
default		0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout		10

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
#hiddenmenu

# Pretty colours
#color cyan/blue white/blue

## password ['--md5'] passwd
# If used in the first section of a menu file, disable all interactive editing
# control (menu entry editor and command-line)  and entries protected by the
# command 'lock'
# e.g. password topsecret
#      password --md5 $1$gLhU0/$aW78kHK1QfV3P2b2znUoe/
# password topsecret

#
# examples
#
# title		Windows 95/98/NT/2000
# root		(hd0,0)
# makeactive
# chainloader	+1
#
# title		Linux
# root		(hd0,1)
# kernel	/vmlinuz root=/dev/hda2 ro
#

#
# Put static boot stanzas before and/or after AUTOMAGIC KERNEL LIST

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
# kopt=root=UUID=73fcf5ff-e5b0-4084-8b01-f53bafb407cb ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd2,0)

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

title		Ubuntu 8.04.3 LTS, kernel 2.6.24-24-generic
root		(hd2,0)
kernel		/boot/vmlinuz-2.6.24-24-generic root=UUID=73fcf5ff-e5b0-4084-8b01-f53bafb407cb ro quiet splash
initrd		/boot/initrd.img-2.6.24-24-generic
quiet

title		Ubuntu 8.04.3 LTS, kernel 2.6.24-24-generic (recovery mode)
root		(hd2,0)
kernel		/boot/vmlinuz-2.6.24-24-generic root=UUID=73fcf5ff-e5b0-4084-8b01-f53bafb407cb ro single
initrd		/boot/initrd.img-2.6.24-24-generic

title		Ubuntu 8.04.3 LTS, memtest86+
root		(hd2,0)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Microsoft Windows XP Professional
root		(hd0,0)
savedefault
makeactive
chainloader	+1


```

---

### Post by oldfred on 2009-09-18
Sorry egalvan It was my fault for not noticing the posting of the results.txt was not dgub's version.

dgub,
To get the bootinfoscript.sh to work you may have to make it executable. I use Nautilus, right click to get properties, third tab for permissions and check execute box. When you double click it, it may seem nothing happens as it runs in the background and writes the results.txt to the same directory. If you want to see it run, open a terminal and change to the directory the script is in and use ./ to execute. 

Someone previous posted that the device.map file is not used for much.

I think your motherboard is bringing the pata drive up first but you do not have grub installed in it. When you disconnect the pata drive the system boots from the grub in the sata drive which is correctly installed.

---

### Post by dgub on 2009-09-18
> **oldfred said:**
> Sorry egalvan It was my fault for not noticing the posting of the results.txt was not dgub's version.

dgub,
To get the bootinfoscript.sh to work you may have to make it executable. I use Nautilus, right click to get properties, third tab for permissions and check execute box. When you double click it, it may seem nothing happens as it runs in the background and writes the results.txt to the same directory. If you want to see it run, open a terminal and change to the directory the script is in and use ./ to execute. 

Someone previous posted that the device.map file is not used for much.

I think your motherboard is bringing the pata drive up first but you do not have grub installed in it. When you disconnect the pata drive the system boots from the grub in the sata drive which is correctly installed.

Thanks Oldfred

I followed that through and made it an executable and it appeared to run but cannot find the "results.txt". Since I ran it from the Desktop it should have appeared there, but cannot find it even using a system search.

You are right in the the BIOS lists the PATA drive first. It is possible to re-order them in BIOS but Ubuntu ignores that. I don't really want to throw away a good drive just for this.

---

### Post by dgub on 2009-09-19
> **dgub said:**
> Thanks Oldfred

I followed that through and made it an executable and it appeared to run but cannot find the "results.txt". Since I ran it from the Desktop it should have appeared there, but cannot find it even using a system search.

You are right in the the BIOS lists the PATA drive first. It is possible to re-order them in BIOS but Ubuntu ignores that. I don't really want to throw away a good drive just for this.

I tried this again from the Live CD and still it does not seem to produce that file.

In the meantime I have tried some other ideas. I changed the PATA disk to Master status and installed Ubuntu again. At the end I allowed it to use the default hd0 for the boot disk, which is the PATA one. On reboot it again came up with Error 17 etc. Rebooted again and this time used the BIOS boot menu and selected the PATA disk to boot from. This time it worked with both O/S's being able to load. I then changed the order in the in which the disks are loaded in BIOS making the PATA one first. Now that seems to work ok.

Thanks for all the help over this. It has been a real pain and have really wondered if it was worth all the effort.

---

