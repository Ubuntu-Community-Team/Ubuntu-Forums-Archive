---
title: "Which grub installed on fresh 9.10 install ?"
date: 2009-11-04
forum: New to Ubuntu
---

### Post by laffinet on 2009-11-04
Which grub installed on fresh 9.10 install ?	

I'm confused. 

I've been running 9.04 and just upgraded to 9.10 doing the following:

- Manual partitioning
- format / and change to ext4
- keep my /home partition
- install bootloader (advanced options)

From what I understand Karmic installs grub2 as default and the file structure (/boot/grub/ etc. looks like it did.
However
```
grub-install -v
``` 
returns 0.97

I tried changing some settings (namely getting rid of "quiet splash") and then did

```
update-grub
```

Which tells me that menu.lst doesn't exist and ask if it should create one ?

Huh ? I thought I'm using grub2, so no menu.lst ?

When I try to install grub-pc I get an error about broken dependencies. What's going on ?

Any help will be much appreciated !

---

### Post by wilee-nilee on 2009-11-04
It is Grub2. The broken dependencies is strange as grub-pc should of been the default. Have you done any done changes to your system that might help all of us figure this out with you. The update grub should be run with sudo starting it and this will rewrite the grub recognizing other OS theoretically in grub2, it worked fine for me in recognizing the XP partition and recovery partition for XP. When you tried to install grub-pc did you get the dependencies information and did you do this in a terminal or synaptic. In synaptic there is a way of showing what else you need.

---

### Post by philinux on 2009-11-04
I did a clean install yesterday. 

This is what you should get.

```
grub-install -v
grub-install (GNU GRUB 1.97~beta4
```

---

### Post by ranch hand on 2009-11-04
Read the link in my sig for grub2 info, the links are real good.

Go to synaptic and click on Status and see if it is reporting  broken packages.

Have synaptic fix them and try your install again.

Let  us know what happens.

---

### Post by SunnyRabbiera on 2009-11-04
Its grub2, any issues are to be expected though as grub2 is still new.

---

### Post by Ant59 on 2009-11-04
The version number is 1.97. It is called GRUB2, however the version is not yet 2.0.

---

### Post by kansasnoob on 2009-11-04
> **laffinet said:**
> Which grub installed on fresh 9.10 install ?	

I'm confused. 

I've been running 9.04 and just upgraded to 9.10 doing the following:

- Manual partitioning
- format / and change to ext4
- keep my /home partition
- install bootloader (advanced options)

From what I understand Karmic installs grub2 as default and the file structure (/boot/grub/ etc. looks like it did.
However
```
grub-install -v
``` 
returns 0.97

I tried changing some settings (namely getting rid of "quiet splash") and then did

```
update-grub
```

Which tells me that menu.lst doesn't exist and ask if it should create one ?

Huh ? I thought I'm using grub2, so no menu.lst ?

When I try to install grub-pc I get an error about broken dependencies. What's going on ?

Any help will be much appreciated !

If "grub-install -v" shows 0.97 you have legacy grub!

You could also run a simple command:

> ls /boot/grub

Typical legacy grub:

> lance@lance-desktop:~$ ls /boot/grub
default        installed-version  menu.lst.backup    stage1
device.map     jfs_stage1_5       minix_stage1_5     stage2
e2fs_stage1_5  menu.lst           reiserfs_stage1_5  xfs_stage1_5
fat_stage1_5   menu.lst~          splashimages


Typical grub2:

> root@lance-desktop:/# ls /boot/grub_backup
915resolution.mod  efiemu64.o	  lspci.mod	  reiserfs.mod
acpi.mod	   efiemu.mod	  lvm.mod	  scsi.mod
affs.mod	   elf.mod	  mdraid.mod	  search.mod
afs_be.mod	   ext2.mod	  memdisk.mod	  serial.mod
afs.mod		   extcmd.mod	  memrw.mod	  setjmp.mod
aout.mod	   fat.mod	  minicmd.mod	  sfs.mod
ata.mod		   font.mod	  minix.mod	  sh.mod
ata_pthru.mod	   fs_file.mod	  mmap.mod	  sleep.mod
at_keyboard.mod    fshelp.mod	  moddep.lst	  tar.mod
befs_be.mod	   fs.lst	  msdospart.mod   terminfo.mod
befs.mod	   fs_uuid.mod	  multiboot.mod   test.mod
biosdisk.mod	   gfxterm.mod	  normal.mod	  tga.mod
bitmap.mod	   gptsync.mod	  ntfscomp.mod	  true.mod
blocklist.mod	   grub.cfg	  ntfs.mod	  udf.mod
boot.img	   grubenv	  ohci.mod	  ufs1.mod
boot.mod	   gzio.mod	  part_acorn.mod  ufs2.mod
bsd.mod		   halt.mod	  part_amiga.mod  uhci.mod
bufio.mod	   handler.lst	  part_apple.mod  usb_keyboard.mod
cat.mod		   handler.mod	  part_gpt.mod	  usb.mod
cdboot.img	   hdparm.mod	  partmap.lst	  usbms.mod
chain.mod	   hello.mod	  part_msdos.mod  usbtest.mod
cmp.mod		   help.mod	  part_sun.mod	  vbeinfo.mod
command.lst	   hexdump.mod	  parttool.lst	  vbe.mod
configfile.mod	   hfs.mod	  parttool.mod	  vbetest.mod
core.img	   hfsplus.mod	  password.mod	  vga.mod
cpio.mod	   iso9660.mod	  pci.mod	  vga_text.mod
cpuid.mod	   jfs.mod	  play.mod	  video_fb.mod
crc.mod		   jpeg.mod	  png.mod	  video.mod
datehook.mod	   kernel.img	  probe.mod	  videotest.mod
date.mod	   keystatus.mod  pxeboot.img	  xfs.mod
datetime.mod	   linux16.mod	  pxecmd.mod	  xnu.mod
device.map	   linux.mod	  pxe.mod	  xnu_uuid.mod
diskboot.img	   lnxboot.img	  raid5rec.mod	  zfsinfo.mod
dm_nv.mod	   loadenv.mod	  raid6rec.mod	  zfs.mod
drivemap.mod	   loopback.mod   raid.mod
echo.mod	   lsmmap.mod	  read.mod
efiemu32.o	   ls.mod	  reboot.mod


---

### Post by SunnyRabbiera on 2009-11-04
> **Ant59 said:**
> The version number is 1.97. It is called GRUB2, however the version is not yet 2.0.

Yes but that versioning number is around RC-ish so its nearly version 2, but we wont see the real GRUB2 till 10.04 Lucid Lynx, hopefully all bugs will be gone by then.

---

### Post by ranch hand on 2009-11-04
Grub-legacy is 0.97.  It never made it to 1.

---

### Post by iruel on 2009-11-04
it's are 1.97 and if you want to configure it placed on **/boot/grub/grub.cfg**

---

### Post by laffinet on 2009-11-04
> **kansasnoob said:**
> You could also run a simple command:

```
ls /boot/grub
```  


That is the interesting bit. My /boot/grub/ contains all the grub 2 files (as in your typical grub2), however grub-install -v says 0.97.

Plus when I run update-grub it tells me there is no menu.lst and asks if it should create one, which I thought is a grub legacy thing. :confused:

---

### Post by iruel on 2009-11-04
> **laffinet said:**
> That is the interesting bit. My /boot/grub/ contains all the grub 2 files (as in your typical grub2), however grub-install -v says 0.97.

Plus when I run update-grub it tells me there is no menu.lst and asks if it should create one, which I thought is a grub legacy thing. :confused:

would you try this command please
**sudo apt-cache policy grub**

this is the result if you still on jaunty,
[I]grub:
  Installed: 0.97-29ubuntu53
  Candidate: 0.97-29ubuntu53[/I]

if on 9.10_** by default or fresh install**_ you will not found any _**menu.lst**_ but it's became _**grub.cfg**_
:D

---

### Post by LewRockwell on 2009-11-04
Grub 2 Stuff:

[https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2)

[http://ubuntuforums.org/showthread.php?t=1195275](http://ubuntuforums.org/showthread.php?t=1195275)

[http://ubuntuforums.org/showthread.php?t=1302743](http://ubuntuforums.org/showthread.php?t=1302743)

[http://ubuntuforums.org/showthread.php?t=1287602](http://ubuntuforums.org/showthread.php?t=1287602)

.

---

### Post by laffinet on 2009-11-04
> **iruel said:**
> would you try this command please
**sudo apt-cache policy grub**


Will do when I get home

> **iruel said:**
>  if on 9.10 by default or fresh install

What do you mean "if on 9.10 by default" ?

That's the confusing bit, I have all the files for grub2, no menu.lst (as it should be), yet grub-install -v tells me 0.97 ???

---

### Post by iruel on 2009-11-04
> **laffinet said:**
> Will do when I get home
What do you mean "if on 9.10 by default" ?

it's if you has install 9.10 by fresh install not upgraded from 9.04

> **laffinet said:**
> 
That's the confusing bit, I have all the files for grub2, no menu.lst (as it should be), yet grub-install -v tells me 0.97 ???

maybe it's wrong version on 9.10,because now i had back to 9.04 because to many diffrent feature on 9.10, and also 9.10 to many removed library and some bugs on environment

---

### Post by kansasnoob on 2009-11-04
> **laffinet said:**
> That is the interesting bit. My /boot/grub/ contains all the grub 2 files (as in your typical grub2), however grub-install -v says 0.97.

Plus when I run update-grub it tells me there is no menu.lst and asks if it should create one, which I thought is a grub legacy thing. :confused:

OK. I saw that happen during the development cycle and what I had to do was **[COLOR="Red"](do not proceed until you've read this all and understand WHERE to install grub)[/COLOR]**:

```
sudo mv /boot/grub /boot/grub_old
```

```
sudo mkdir /boot/grub
```

```
sudo apt-get --purge remove grub grub-common
```

```
sudo apt-get install grub-pc
```

```
sudo update-grub
```

```
sudo grub-install /dev/sd**[COLOR="Red"]X[/COLOR]**
``` (replace /dev/sd**[COLOR="Red"]X[/COLOR]** with your proper destination)

If you're unsure what the [COLOR="Red"]**X**[/COLOR] should be post the output of:

```
sudo fdisk-l
```

and we'll go from there.

---

### Post by ranch hand on 2009-11-04
This is why I do not do upgrades.  It is also why folks should consider a clean install htis time eve n if they upgraded before and continue to do so later.  There are too many, very basic, changes in here to be screwing around this way.

What you have is either grub2 corrupted by grub-legacy, or grub-legacy corrupted by grub2.  I happen to love them both but they do not mix.

I would chroot in from a LiveCD and tell apt to remove grub, grub-pc and grub-common (whatever it can find) and then tell apt to install grub-pc and grub-common.  I would not use the purge command as I think you would be shocked by what was removed.

---

### Post by ranch hand on 2009-11-04
Ignore my advice on "purge".  Listen to kansasnoob.

---

### Post by kansasnoob on 2009-11-04
> **ranch hand said:**
> Ignore my advice on "purge".  Listen to kansasnoob.

Thanks for the vote of confidence ;)

The one thing that always scares me is the possibility of misunderstanding. Thus all the red electronic ink.

---

### Post by kansasnoob on 2009-11-04
BTW I've seen this happen once on a fresh install of / where an ext4 /home was kept unformatted.

Still some bugs in the works:p

---

### Post by ranch hand on 2009-11-04
> **kansasnoob said:**
> Thanks for the vote of confidence ;)

The one thing that always scares me is the possibility of misunderstanding. Thus all the red electronic ink.
Hey, I'm noober than you are, too many cooks ruin the stew, you are using a smaller hammer.

Sounds good to me.

---

### Post by laffinet on 2009-11-04
> **ranch hand said:**
> This is why I do not do upgrades. 

Have a look at my first post. I did not do an upgrade, I did a fresh install (albeit keeping my /home partition).

---

### Post by kansasnoob on 2009-11-04
Then again sometimes another cook adds just the right ingredient!

IMHO it's always good to hear other opinions.

I've been wrong more than once!

---

### Post by kansasnoob on 2009-11-04
> **laffinet said:**
> Have a look at my first post. I did not do an upgrade, I did a fresh install (albeit keeping my /home partition).

I saw that. Would you mind posting the output of:

```
sudo fdisk -l
```

---

### Post by laffinet on 2009-11-04
This upgrade/fresh install talk got me thinking and there might be something else worth mentioning:

Before I did the fresh install I created a list of all installed applications using "sudo dpkg --get-selections > /home/user/package.selections" (see [here]("http://linuxologist.com/linuxhowto/howto-fresh-ubuntu-install-without-losing-your-current-settings/")). Once I did the fresh 9.10 install I used that list to re-install all the applications ("sudo dpkg --set-selections /home/package.selections && apt-get dselect-upgrade". I'm beginning to think that might have created the issues with grub.

---

### Post by ranch hand on 2009-11-04
> **laffinet said:**
> Have a look at my first post. I did not do an upgrade, I did a fresh install (albeit keeping my /home partition).
Ah, I really need to learn to read someday.

---

### Post by kansasnoob on 2009-11-04
> **laffinet said:**
> This upgrade/fresh install talk got me thinking and there might be something else worth mentioning:

Before I did the fresh install I created a list of all installed applications using "sudo dpkg --get-selections > /home/user/package.selections" (see [here]("http://linuxologist.com/linuxhowto/howto-fresh-ubuntu-install-without-losing-your-current-settings/")). Once I did the fresh 9.10 install I used that list to re-install all the applications ("sudo dpkg --set-selections /home/package.selections && apt-get dselect-upgrade". I'm beginning to think that might have created the issues with grub.

Regardless you must figure out what you want to do.

I've still seen no "fdisk -l".

And I'm getting too tired to be of use now anyway, so I'll see you tomorrow.

---

### Post by laffinet on 2009-11-04
> **kansasnoob said:**
> 
I've still seen no "fdisk -l".

And I'm getting too tired to be of use now anyway, so I'll see you tomorrow.

That's because I'm not at home at the moment so can't access my computer ;)

Thanks for your help so far. 
I'll do the "fdisk -l" when I get home. From there I'll see if I can figure out which /dev/sdX to use for grub install and then go ahead with what you described earlier (purging and reinstalling grub). If I can't figure it out I'll just post here and let you decide :p:p

---

### Post by laffinet on 2009-11-05
Okay kansasnoob, I did what you said. Everything went ok, only thing I am slightly concerned about is that it warned me that installing to a partition instead of MBR is a bad idea. Everything's fine now, though.

Here's my fdisk -l:

```
Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x76c48f32

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        2550    20482843+  83  Linux
/dev/sda2            2551        2793     1951897+  82  Linux swap / Solaris
/dev/sda3            3061       19457   131708902+  83  Linux

```

So I installed to /dev/sda1

---

