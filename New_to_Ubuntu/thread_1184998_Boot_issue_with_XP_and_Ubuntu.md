---
title: "Boot issue with XP and Ubuntu"
date: 2009-06-11
forum: New to Ubuntu
---

### Post by mdenney304 on 2009-06-11
Hi everybody :-)  I've been lurking around the forums for the past few days, looking for answers to some of my install issues.  I've been lucky and have found some great info.  I'm impressed with not only the level of expertise available but the manner in which help is provided.  Often it is possible to infer the level of panic in which a post for help has been written but help is still provided with  a smile, so to speak.  Perhaps obtaining the skill level required to troubleshoot issues leads one to be more understanding and patient with those newcomers who have issues.  Hopefully someone will take pity on me and offer some information to help resolve my issue.
 Last week I installed **Ubuntu (Gnome 2.26.1, Kernel 2.6.28-11-generic, GCC Version 4.3.3(x86_64-linux-gnu)) **on an **Emachines m6810 (AMD Athlon 64, 512mb memory, 55gb HD/17gb free) notebook running XP Pro**.  The notebook was purchased refurbed six years ago and did not come with any discs for XP or other software.  The DVD-rom has since died. 

Initially I had internet connectivity issues.  I used my PS3 to search for a workable solution and was able to get connected.  I updated and began looking around my new OS.  There are many things I like about Ubuntu (package manager, quick, quiet).  Next I wanted to boot into XP so I could uninstall Ubuntu and try another flavor.  Well, I was unable to boot into XP.  I searched for a solution in the forum and found many options (mostly grub related), tried many (mostly grub related) and no luck.  So, I walked away for a time to clear my head and see the issue through fresh eyes.  More solutions presented themselves (virtual floppy to build boot disk, using USB to boot) but still no luck.  (Now I should admit that the solutions may not have worked simply because of my inexperience or inability.)  So now I throw myself on the mercy of the forum experts...please help :-)
 This information may be helpful, if more is needed, please let me know:
 
[SIZE=3]
[/SIZE]  **[SIZE=3]sudo fdisk -l returns[/SIZE]:**
 

 Disk /dev/sda: 60.0 GB, 60011642880 bytes 
 255 heads, 63 sectors/track, 7296 cylinders 
 Units = cylinders of 16065 * 512 = 8225280 bytes 
 Disk identifier: 0xf4d64506 
  
    Device Boot      Start         End      Blocks   Id  System 
 /dev/sda1   *           1        7296    58605088+   7  HPFS/NTFS 
  
 Disk /dev/sdb: 2021 MB, 2021654528 bytes 
 63 heads, 62 sectors/track, 1010 cylinders 
 Units = cylinders of 3906 * 512 = 1999872 bytes 
 Disk identifier: 0x6f20736b 
  
 This doesn't look like a partition table 
 Probably you selected the wrong device. 
  
    Device Boot      Start         End      Blocks   Id  System 
 /dev/sdb1   ?      199216      491461   570754815+  72  Unknown 
 Partition 1 has different physical/logical beginnings (non-Linux?): 
      phys=(357, 116, 40) logical=(199215, 34, 11) 
 Partition 1 has different physical/logical endings: 
      phys=(357, 32, 45) logical=(491460, 44, 51) 
 Partition 1 does not end on cylinder boundary. 
 /dev/sdb2   ?       43188      538843   968014120   65  Novell Netware 386 
 Partition 2 has different physical/logical beginnings (non-Linux?): 
      phys=(288, 115, 43) logical=(43187, 17, 47) 
 Partition 2 has different physical/logical endings: 
      phys=(367, 114, 50) logical=(538842, 14, 42) 
 Partition 2 does not end on cylinder boundary. 
 /dev/sdb3   ?      478721      974376   968014096   79  Unknown 
 Partition 3 has different physical/logical beginnings (non-Linux?): 
      phys=(366, 32, 33) logical=(478720, 18, 30) 
 Partition 3 has different physical/logical endings: 
      phys=(357, 32, 43) logical=(974375, 14, 39) 
 Partition 3 does not end on cylinder boundary. 
 /dev/sdb4   ?           1      931190  1818613248    d  Unknown 
 Partition 4 has different physical/logical beginnings (non-Linux?): 
      phys=(372, 97, 50) logical=(0, 0, 1) 
 Partition 4 has different physical/logical endings: 
      phys=(0, 10, 0) logical=(931189, 36, 30) 
 Partition 4 does not end on cylinder boundary. 
  
 Partition table entries are not in disk order 
  
 Disk /dev/sdc: 2021 MB, 2021654528 bytes 
 63 heads, 62 sectors/track, 1010 cylinders 
 Units = cylinders of 3906 * 512 = 1999872 bytes 
 Disk identifier: 0x6b736964 
  
 This doesn't look like a partition table 
 Probably you selected the wrong device. 
  
    Device Boot      Start         End      Blocks   Id  System 
 /dev/sdc1   ?      435740      852923   814758329+  74  Unknown 
 Partition 1 has different physical/logical beginnings (non-Linux?): 
      phys=(288, 110, 36) logical=(435739, 33, 45) 
 Partition 1 has different physical/logical endings: 
      phys=(366, 104, 37) logical=(852922, 31, 29) 
 Partition 1 does not end on cylinder boundary. 
 /dev/sdc2   ?      340549      478536   269488144   65  Novell Netware 386 
 Partition 2 has different physical/logical beginnings (non-Linux?): 
      phys=(107, 121, 32) logical=(340548, 59, 47) 
 Partition 2 has different physical/logical endings: 
      phys=(10, 121, 13) logical=(478535, 44, 42) 
 Partition 2 does not end on cylinder boundary. 
 /dev/sdc3   ?      137991      495994   699181456   53  OnTrack DM6 Aux3 
 Partition 3 has different physical/logical beginnings (non-Linux?): 
      phys=(345, 32, 19) logical=(137990, 7, 18) 
 Partition 3 has different physical/logical endings: 
      phys=(324, 77, 19) logical=(495993, 58, 49) 
 Partition 3 does not end on cylinder boundary. 
 /dev/sdc4   ?     1001027     1001044       32672   bb  Boot Wizard hidden 
 Partition 4 has different physical/logical beginnings (non-Linux?): 
      phys=(65, 1, 0) logical=(1001026, 30, 55) 
 Partition 4 has different physical/logical endings: 
      phys=(128, 0, 7) logical=(1001043, 13, 50) 
 Partition 4 does not end on cylinder boundary. 
  
 Partition table entries are not in disk order
  

 
[SIZE=3]
**sudo gedit /boot/grub/menu.lst returns**[/SIZE]   (you can probably tell that I've manipulated the list a bit per instructions found on the forum):
 

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
 default        1
 ## timeout sec
 # Set a timeout, in SEC seconds, before automatically booting the default entry
 # (normally the first entry defined).
 timeout        10
 ## hiddenmenu
 # Hides the menu by default (press ESC to see the menu)
 hiddenmenu
 # Pretty colours
 #color cyan/blue white/blue
 ## password ['--md5'] passwd
 # If used in the first section of a menu file, disable all interactive editing
 # control (menu entry editor and command-line)  and entries protected by the
 # command 'lock'
 # e.g. password topsecret
 ## password --md5 $1$gLhU0/$aW78kHK1QfV3P2b2znUoe/
 # password topsecret
 #
 # examples
 #
 # title        Windows 95/98/NT/2000
 # root        (hd0,0)
 # makeactive
 # chainloader    +1
 #
 # title        Linux
 # root        (hd0,1)
 # kernel    /vmlinuz root=/dev/hda2 ro
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
 # kopt=root=UUID=E6C0F12D188B62C0 loop=/ubuntu/disks/root.disk ro
 ## default grub root device
 ## e.g. groot=(hd0,0)
 # groot=()/ubuntu/disks
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
 # defoptions=quiet vga=769 splash
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
 ## specify if running in Xen domU or have grub detect automatically
 ## update-grub will ignore non-xen kernels when running in domU and vice versa
 ## e.g. indomU=detect
 ##      indomU=true
 ##      indomU=false
 # indomU=detect
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
 
title        Windows NT/2000/XP
 rootnoverify    (hd0,0)
 makeactive
 chainloader    +1
 
title        Ubuntu 9.04, kernel 2.6.28-11-generic
 root        ()/ubuntu/disks
 kernel        /boot/vmlinuz-2.6.28-11-generic root=UUID=E6C0F12D188B62C0 loop=/ubuntu/disks/root.disk ro quiet splash  
 initrd        /boot/initrd.img-2.6.28-11-generic
 
title        Ubuntu 9.04, kernel 2.6.28-11-generic (recovery mode)
 root        ()/ubuntu/disks
 kernel        /boot/vmlinuz-2.6.28-11-generic root=UUID=E6C0F12D188B62C0 loop=/ubuntu/disks/root.disk ro  single
 initrd        /boot/initrd.img-2.6.28-11-generic
 
title        Ubuntu 9.04, memtest86+
 root        ()/ubuntu/disks
 kernel        /boot/memtest86+.bin
 
 ### END DEBIAN AUTOMAGIC KERNELS LIST
 # This is a divider, added to separate the menu items below from the Debian
 # ones.
 title        Other operating systems:
 root
 
# This entry automatically added by the Debian installer for a non-linux OS
 # on /dev/sda1
 
-----------------------------------------------

 I found an [SIZE=3]**XP boot.ini file**[/SIZE] while searching through XP files (using system monitor) which contains this information.  Not sure if it's helpful:
 
 [boot loader] 
 default=C:\wubildr.mbr 
 [operating systems] 
 C:\wubildr.mbr = "Ubuntu" 
 multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional Edition" /fastdetect /NoExecute=OptIn

---

### Post by ronparent on 2009-06-11
Simply add the following to menu.lst:

[B]title		Windows XP
rootnoverify	(hd0,0)
chainloader 	+1[/B]

From a terminal edit menu.lst as root: ie **sudo gedit /boot/grub/menu.lst**

Save and you should have windows access in grub menu at your next boot.

---

### Post by mdenney304 on 2009-06-11
Thanks for the tip, but I can see XP in the boot list however when I select it as the OS to use, I am returned to the boot list and must choose another OS (Ubuntu).  Sorry, I should have included that information before.  I've also used Startup Manager to try and get XP to boot but no luck.

---

### Post by abhiroopb on 2009-06-12
Add this to grub:

    title Windows XP
    root (hd0,0)
    makeactive
    chainloader +1

---

### Post by mdenney304 on 2009-06-12
Thank you for the tip...sadly, your recommendation did not help.  Whenever my system attempts to boot up XP it gets stuck in an endless cycle of attempting to boot.

---

### Post by ronparent on 2009-06-12
You were apparently using umbuntu thru wubi at some point in time. I suspect that editing it out of C:\boot.ini could fix your problem? Because I'm unfamiliar with wubi sematics in the boot.ini file, however, someone who is would have to advise you.

---

### Post by Miljet on 2009-06-12
One thing that is confusing everyone is that you say that you see the option for Win XP in your boot menu, but it clearly is NOT listed in the menu.lst file you posted. That is why you have had several recommendations to add it.

---

### Post by mdenney304 on 2009-06-12
RE:Miljet
Hmmm...when I review my boot list I see the previously recommended text listed at the end of 'default options' as the excerpt below shows.  Should it be listed elsewhere in the list to be effective?

start excerpt:

## should update-grub add savedefault to the default options
 ## can be true or false
 # savedefault=false
 ## ## End Default Options ##
 
[B]title        Windows NT/2000/XP
 rootnoverify    (hd0,0)
 makeactive
 chainloader    +1[/B]
 
title        Ubuntu 9.04, kernel 2.6.28-11-generic
 root        ()/ubuntu/disks
 kernel        /boot/vmlinuz-2.6.28-11-generic root=UUID=E6C0F12D188B62C0 loop=/ubuntu/disks/root.disk ro quiet splash  
 initrd        /boot/initrd.img-2.6.28-11-generic

-end excerpt-

RE: Ronparent
Yes, I did obtain Ubuntu through wubi.  It was supposed to install inside XP so that I could 'demo' the OS however that didn't happen.  Probably through my own mistake, but nonetheless, here I am :-)

---

### Post by ronparent on 2009-06-12
The location of the boot instruction in menu.lst is imaterial.

---

