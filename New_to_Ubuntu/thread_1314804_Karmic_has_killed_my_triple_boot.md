---
title: "Karmic has killed my triple boot"
date: 2009-11-04
forum: New to Ubuntu
---

### Post by evolvedlight on 2009-11-04
Hey

I run Windows 7,XP, and ubuntu.

Just did a clean install of karmic, and I can't get into windows anymore. I need windows as karmic has a broken nvidea-settings for my dual moniters, flash is broken (although now fixed by installing flash from ubuntu partners repo)

I've done the standard install os-prober, setting up grub2 again, etc, but when I reboot I don't even get a grub choice, it goes straight to karmic.

Any ideas?

Steve

---

### Post by edin9 on 2009-11-04
ESC quickly at "Grub loading", and; ```
sudo update-grub
``` Or did you already try that?

---

### Post by LewRockwell on 2009-11-04
you might try Super Grub Disk to get booted into windows asap

.

---

### Post by fooman on 2009-11-04
try holding down the *shift* key as she boots to see the grub menu.

heres the wiki for grub2:

[https://wiki.ubuntu.com/Grub2](https://wiki.ubuntu.com/Grub2)

---

### Post by kansasnoob on 2009-11-04
Please post the output from terminal of:

```
sudo fdisk -l
```

and:

```
grub-install -v
```

---

### Post by kansasnoob on 2009-11-04
> **fooman said:**
> try holding down the *shift* key as she boots to see the grub menu.

heres the wiki for grub2:

[https://wiki.ubuntu.com/Grub2](https://wiki.ubuntu.com/Grub2)

+1! Pressing the ESC key no longer works with grub2! You must press the shift key!

---

### Post by evolvedlight on 2009-11-04
Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xcecaceca

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       25496   204796588+   7  HPFS/NTFS
/dev/sda2           25497       31871    51200000    7  HPFS/NTFS
/dev/sda3           56826      121601   520313220    7  HPFS/NTFS
/dev/sda4           31872       56825   200443005    5  Extended
/dev/sda5           31872       56339   196539178+  83  Linux
/dev/sda6           56340       56825     3903763+  82  Linux swap / Solaris


grub-install (GNU GRUB 1.97~beta4)

---

### Post by evolvedlight on 2009-11-04
> **fooman said:**
> try holding down the *shift* key as she boots to see the grub menu.

heres the wiki for grub2:

[https://wiki.ubuntu.com/Grub2](https://wiki.ubuntu.com/Grub2)

I can do that, and use the following commands to boot windows:
root (hd0, 1)
chainloader +1
boot

---

### Post by kansasnoob on 2009-11-05
> **evolvedlight said:**
> I can do that, and use the following commands to boot windows:
root (hd0, 1)
chainloader +1
boot

Is this solved then?

---

### Post by evolvedlight on 2009-11-06
> **kansasnoob said:**
> Is this solved then?

No, I want it to come up all the time, and I want it to have windows in there without me typing in the commands each time.

Grub 1, I just edited menu.lst. Its gone now

---

### Post by Mark Phelps on 2009-11-06
GRUB2 has "retired" menu.lst.  Nothing you do there will make a difference anymore.

You need to read the links to see the changes in GRUB2.  It's not just hand-editing a text file anymore to add other OSs.

---

### Post by oldfred on 2009-11-06
While the wiki entry gives some examples these two sites also have examples of windows boot entries added to a new file starting with 2 digits and an underscore which defines the order in grub.cfg in /etc/grub.d/ or in the /etc/grub.d/40_custom file that  is empty. Make the file executable and run grub update.

[http://members.iinet.net/~herman546/p20/GRUB2%20Configuration%20File%20Commands.html#chainloader_boot_entry](http://members.iinet.net/~herman546/p20/GRUB2%20Configuration%20File%20Commands.html#chainloader_boot_entry)

[http://ubuntuforums.org/showthread.php?t=1195275](http://ubuntuforums.org/showthread.php?t=1195275)

and from Herman's sie:
When you are finished putting all of your custom boot entries in your /etc/grub.d/06_custom file, it needs to be chmodded to make it executable,
[FONT=Bitstream Vera Sans Mono][/FONT][FONT=Bitstream Vera Sans Mono]sudo chmod 755 /etc/grub.d/40_custom
[/FONT]Use a command something like this to change the file permissions to make your file executable.

Finally, don't forget to run either the 'sudo update-grub' or 'sudo grub-mkconfig' command.
[FONT=Bitstream Vera Sans Mono]sudo grub-mkconfig -o /boot/grub/grub.cfg[/FONT]

---

### Post by markmaus on 2009-11-06
I have exactly the same problem.  My computer tri-boots WinXP, Win7 and Karmic.  WinXP is on sda1, Win7 is on sda2 and Karmic is on sda3.  There is an entry in the Grub2 list for Windows 7 but if I select it, it just reboots the computer.  Is this thread solved?  If so, none of the suggested fixes worked for me. The two links shown in the post above are way over my head.  I used to be able to edit the menu.lst file quite easily, but I don't understand the new Grub. Any suggestions?  Is there a way to regress to Grub1?  It seemed to work fine.

---

### Post by oldfred on 2009-11-06
Markmaus,

Your issue is a win7 issue and you should start your own thread so answers can be directed just to you and not get confused with the OP. Also then when others search for answers they will find just the similiar threads.

I do not see grub2 as all that more difficult than old grub, it is a lot different so we have a learning curve. Editing 40_custom is hardly more difficult than editing menu.lst, although the format is different. I usually just am copy and pasting entries anyway. If you have an error in menu.lst your entire system will not boot so I see grub2 as safer as you are just editing a subfile that is then incorporated into grub.cfg.

You may not be able to directly boot win7 as it combines its boot into the XP boot.

---

### Post by markmaus on 2009-11-06
> **evolvedlight said:**
> No, I want it to come up all the time, and I want it to have windows in there without me typing in the commands each time.

Grub 1, I just edited menu.lst. Its gone now

Evolvedlight, I've figured out how to restore my Windows boot loader so that I don't have to type in the commands every time I boot Windows.  I had the same problem as you.  This fix will enable you to boot either WinXP or Win7, but you will loose the ability to boot Karmic.  You will need to boot with your Windows 7 installation disk.  Hit Enter at the language selection prompt then hit "R" to get to the repair section.  You can then select the automatic boot repair tool, but it didn't do any good for me.  Then I selected the command prompt (console) and typed in the following commands:
BootRec.exe /fixmbr
BootRec.exe /FixBoot
BootRec.exe /ScanOs
BootRec.exe /RebuildBcd

There are some good instructions here:
[http://www.sevenforums.com/general-discussion/17521-how-fix-mbr-through-command-prompt.html](http://www.sevenforums.com/general-discussion/17521-how-fix-mbr-through-command-prompt.html)

Once you re-boot you will see the Win7 boot loader and be able to choose either WinXP or Win7.

I then had the bright idea to try installing Jaunty (because it uses Grub version .9) and then upgrading to Karmic (because an upgrade to Karmic will not install Grub2).  But when Jaunty installed Grub .9 it borked up the Windows bootloader and I couldn't find any combination of Grub entries that would fix it.  So I had to run the fixmbr commands from the Windows command prompt to fix it again. I hope this helps, when I figure out how to get Karmic to play nice with our tri-boot set up I'll post it.

---

### Post by kansasnoob on 2009-11-06
Just as general information to all you need not install an older version of Ubuntu to revert to legacy grub:

[http://ubuntuforums.org/showthread.php?t=1298932](http://ubuntuforums.org/showthread.php?t=1298932)

But right here, right now I'm going to focus on the OP's specific problem. Feel free to read along or even interject if you notice I've flubbed or even to ask non-specific questions, but I can only tackle one box per thread.

Otherwise it becomes too easy to assume that posted results of a specific command apply to the wrong box!

---

### Post by kansasnoob on 2009-11-06
> **markmaus said:**
> Evolvedlight, I've figured out how to restore my Windows boot loader so that I don't have to type in the commands every time I boot Windows.  I had the same problem as you.  This fix will enable you to boot either WinXP or Win7, but you will loose the ability to boot Karmic.  You will need to boot with your Windows 7 installation disk.  Hit Enter at the language selection prompt then hit "R" to get to the repair section.  You can then select the automatic boot repair tool, but it didn't do any good for me.  Then I selected the command prompt (console) and typed in the following commands:
BootRec.exe /fixmbr
BootRec.exe /FixBoot
BootRec.exe /ScanOs
BootRec.exe /RebuildBcd

There are some good instructions here:
[http://www.sevenforums.com/general-discussion/17521-how-fix-mbr-through-command-prompt.html](http://www.sevenforums.com/general-discussion/17521-how-fix-mbr-through-command-prompt.html)

Once you re-boot you will see the Win7 boot loader and be able to choose either WinXP or Win7.

I then had the bright idea to try installing Jaunty (because it uses Grub version .9) and then upgrading to Karmic (because an upgrade to Karmic will not install Grub2).  But when Jaunty installed Grub .9 it borked up the Windows bootloader and I couldn't find any combination of Grub entries that would fix it.  So I had to run the fixmbr commands from the Windows command prompt to fix it again. I hope this helps, when I figure out how to get Karmic to play nice with our tri-boot set up I'll post it.

This info is going in my "tool-box". Great to know.

---

### Post by kansasnoob on 2009-11-06
> **evolvedlight said:**
> Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xcecaceca

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       25496   204796588+   7  HPFS/NTFS
/dev/sda2           25497       31871    51200000    7  HPFS/NTFS
/dev/sda3           56826      121601   520313220    7  HPFS/NTFS
/dev/sda4           31872       56825   200443005    5  Extended
/dev/sda5           31872       56339   196539178+  83  Linux
/dev/sda6           56340       56825     3903763+  82  Linux swap / Solaris


grub-install (GNU GRUB 1.97~beta4)

**[COLOR="Red"]Please read this all![/COLOR]** I know it seems long winded, and believe me I'd rather be doing something else than typing this, but people have to learn what's going on with the new grub!

OK! Not solved, but then you said, "Grub 1, I just edited menu.lst. Its gone now".

So you did revert to legacy grub?

*Just BTW when I say legacy grub I mean old grub, when we say grub2 we're referring to the new grub which is the package grub-pc. If you run the command "grub-install -v" you'll see which version you have: 0.97 is the old grub whereas 1.97+ is the new grub (aka: grub2).*

Anyway I'm a bit confused when you say, "Grub 1, I just edited menu.lst. Its gone now". If you change from one to the other you must do more than just install and remove packages.

In my aforementioned thread I focus on changing from grub2 to legacy grub:

[http://ubuntuforums.org/showthread.php?t=1298932](http://ubuntuforums.org/showthread.php?t=1298932)

but in Appendix #2 of the same thread I briefly explain how to go back the other way.

If you run:

```
ls /boot/grub
```

Legacy grub should look like this:

> lance@lance-desktop:~$ ls /boot/grub
default        grubenv            menu.lst~          splashimages
device.map     installed-version  menu.lst.backup    stage1
e2fs_stage1_5  jfs_stage1_5       minix_stage1_5     stage2
fat_stage1_5   menu.lst           reiserfs_stage1_5  xfs_stage1_5


In grub2:

> lance@lance-desktop:~$ ls /boot/grub_backup
915resolution.mod  efiemu64.o     lspci.mod       reiserfs.mod
acpi.mod           efiemu.mod     lvm.mod         scsi.mod
affs.mod           elf.mod        mdraid.mod      search.mod
afs_be.mod         ext2.mod       memdisk.mod     serial.mod
afs.mod            extcmd.mod     memrw.mod       setjmp.mod
aout.mod           fat.mod        minicmd.mod     sfs.mod
ata.mod            font.mod       minix.mod       sh.mod
ata_pthru.mod      fs_file.mod    mmap.mod        sleep.mod
at_keyboard.mod    fshelp.mod     moddep.lst      tar.mod
befs_be.mod        fs.lst         msdospart.mod   terminfo.mod
befs.mod           fs_uuid.mod    multiboot.mod   test.mod
biosdisk.mod       gfxterm.mod    normal.mod      tga.mod
bitmap.mod         gptsync.mod    ntfscomp.mod    true.mod
blocklist.mod      grub.cfg       ntfs.mod        udf.mod
boot.img           grubenv        ohci.mod        ufs1.mod
boot.mod           gzio.mod       part_acorn.mod  ufs2.mod
bsd.mod            halt.mod       part_amiga.mod  uhci.mod
bufio.mod          handler.lst    part_apple.mod  usb_keyboard.mod
cat.mod            handler.mod    part_gpt.mod    usb.mod
cdboot.img         hdparm.mod     partmap.lst     usbms.mod
chain.mod          hello.mod      part_msdos.mod  usbtest.mod
cmp.mod            help.mod       part_sun.mod    vbeinfo.mod
command.lst        hexdump.mod    parttool.lst    vbe.mod
configfile.mod     hfs.mod        parttool.mod    vbetest.mod
core.img           hfsplus.mod    password.mod    vga.mod
cpio.mod           iso9660.mod    pci.mod         vga_text.mod
cpuid.mod          jfs.mod        play.mod        video_fb.mod
crc.mod            jpeg.mod       png.mod         video.mod
datehook.mod       kernel.img     probe.mod       videotest.mod
date.mod           keystatus.mod  pxeboot.img     xfs.mod
datetime.mod       linux16.mod    pxecmd.mod      xnu.mod
device.map         linux.mod      pxe.mod         xnu_uuid.mod
diskboot.img       lnxboot.img    raid5rec.mod    zfsinfo.mod
dm_nv.mod          loadenv.mod    raid6rec.mod    zfs.mod
drivemap.mod       loopback.mod   raid.mod
echo.mod           lsmmap.mod     read.mod
efiemu32.o         ls.mod         reboot.mod


OK, that seems like a lot to look at but focus on the size of the list (which obviously indicates grub2) and the presence of any of the legacy grub files (they're in alphabetical order)!

Having the two mixed does NOT work! At the best it will result in very slow boot times. Eventually you'll end up being able to boot nothing.

**So anyway the new grub 2 wasn't working for you!** We're all trying to still learn the ins and outs of grub2 but if I were you I'd revert to legacy grub for now per my HowTo.

**[COLOR="Red"]But that's not the only problem:[/COLOR]**

None of your Win will be automatically added to the menu.lst!

You have Win 7, Win XP, and Ubuntu. Your output from "fdisk -l" shows:

> /dev/sda1 * 1 25496 204796588+ 7 HPFS/NTFS
/dev/sda2 25497 31871 51200000 7 HPFS/NTFS
/dev/sda3 56826 121601 520313220 7 HPFS/NTFS
/dev/sda4 31872 56825 200443005 5 Extended
/dev/sda5 31872 56339 196539178+ 83 Linux
/dev/sda6 56340 56825 3903763+ 82 Linux swap / Solaris

So I assume that sda1 was the destination for your Win bootloader because it has a boot flag, **[COLOR="Red"]DO NOT try to edit boot flags[/COLOR]**, then sda2 and sda3 are Win XP and Win 7, and initially installing Ubuntu overwrote that boot-loader.

To know how to add those entries to the legacy grub menu.lst I'd almost need to have the computer in front of me, but I'd try this first:

> ### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root

##This entry added by me
title		Windows Bootloader
rootnoverify	(hd0,0)
savedefault
makeactive
chainloader	+1

Not so easy huh?

If that fails I'd have to see the output of the Boot Info Script as described here:

[http://ubuntuforums.org/showthread.php?t=1291280](http://ubuntuforums.org/showthread.php?t=1291280)

Only quote tags make it easier for me to read.

---

