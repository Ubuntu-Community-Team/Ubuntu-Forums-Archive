---
title: "Broke my linux again! usplash sucks! plz help!"
date: 2010-04-19
forum: New to Ubuntu
---

### Post by Crazedpsyc on 2010-04-19
I have been a loving user of Ubuntu since the release of Jaunty, but recently have switched to Mint 8 (like Karmic) because my ubuntu crashed yet again and my disk happens to be part of a large collection on my ceiling :P! Now Mint crashed for the first time, and although many people seem to have experinced this same error, none know how to fix it. When I try to boot, it shows the grub menu like normal, I press enter on Mint, then it goes to a black screen like normal with a little flashing grey underscore at the top left. Usually I just wait and it gets past that, but not now. When I press Alt+F1 it shows me this error message:
> 
usplash: no usable theme found for [XxY]
screen init failed
Others just waited and then it booted normally but I waited for several minutes (longer than it ever takes) and nothing happened. This was after I hibernated but hibernate has worked just fine before. Just hours before this I woke up from hibernation just fine and used it normally, although that was with "hibernate" from the synaptic instead of the regular hibernate from the shutdown menu. I am fine with starting with a fresh Mint if necessary, but I still want my files off of that one. The problem with that is, although I can access most of my filesystem, I encrypted my home directory, so I can't access it. Also, to make it even worse I don't know how I encrypted it lol. I either used the "Passwords and Encryption Keys" program with the default password encryption key, or some command I found while searching one of the bins or sbins. When I go to my home directory on that partition it shows two things: "Access Your Private Data" and "README.txt". the Access... thing opens a terminal for a split second, but otherwise does nothing. the readme says:
> 
THIS DIRECTORY HAS BEEN UNMOUNTED TO PROTECT YOUR DATA.

From the graphical desktop, click on:
 "Access Your Private Data"

or

From the command line, run:
 ecryptfs-mount-private
I ran the command and it says "ERROR: Encrypted private directory is not setup properly"
I also tried cding to my home directory there and running it, but still got the same error.
When I run that system in recovery mode it gives me a full screen terminal as usual, but never actually gets to the place I can run commands, it just scrolls through all the startup stuff and then stops.
I would really hate to lose everything because I just finished making a new theme and hadnt backed it up yet. Also if possible could anyone tell me how to copy complete programs from that partition?
Thanks in advance!
(the most important thing is to get the old hd decrypted, because I already have an extra OS. I just NEEEEd those files!)

---

### Post by e4uforums on 2010-04-19
Two possible answers here:
[http://www.linuxquestions.org/questions/linux-desktop-74/using-usplash-551478/](http://www.linuxquestions.org/questions/linux-desktop-74/using-usplash-551478/)

---

### Post by Crazedpsyc on 2010-04-19
Well the first option doesn't work because I don't have a "menu.lst" or menu.anything in my /boot/grub folder. the second might work but how do I run it from the broken system? I can run it from this one that works fine, but that's not useful.
here are all the contents of my /boot/grub:
915resolution.mod  efiemu64.o      ls.mod      reboot.mod
acpi.mod       efiemu.mod      lspci.mod      reiserfs.mod
affs.mod       elf.mod      lvm.mod      scsi.mod
afs_be.mod       ext2.mod      mdraid.mod      search.mod
afs.mod           extcmd.mod      memdisk.mod      serial.mod
aout.mod       fat.mod      memrw.mod      setjmp.mod
ata.mod           font.mod      minicmd.mod      sfs.mod
ata_pthru.mod       fs_file.mod      minix.mod      sh.mod
at_keyboard.mod    fshelp.mod      mmap.mod      sleep.mod
befs_be.mod       fs.lst      moddep.lst      tar.mod
befs.mod       fs_uuid.mod      msdospart.mod   terminfo.mod
biosdisk.mod       gfxterm.mod      multiboot.mod   test.mod
bitmap.mod       gptsync.mod      normal.mod      tga.mod
blocklist.mod       grub.cfg      ntfscomp.mod      true.mod
boot.img       grubenv      ntfs.mod      udf.mod
boot.mod       gzio.mod      ohci.mod      ufs1.mod
bsd.mod           halt.mod      part_acorn.mod  ufs2.mod
bufio.mod       handler.lst      part_amiga.mod  uhci.mod
cat.mod           handler.mod      part_apple.mod  usb_keyboard.mod
cdboot.img       hdparm.mod      part_gpt.mod      usb.mod
chain.mod       hello.mod      partmap.lst      usbms.mod
cmp.mod           help.mod      part_msdos.mod  usbtest.mod
command.lst       hexdump.mod      part_sun.mod      vbeinfo.mod
configfile.mod       hfs.mod      parttool.lst      vbe.mod
core.img       hfsplus.mod      parttool.mod      vbetest.mod
cpio.mod       iso9660.mod      password.mod      vga.mod
cpuid.mod       jfs.mod      pci.mod      vga_text.mod
crc.mod           jpeg.mod      play.mod      video_fb.mod
datehook.mod       kernel.img      png.mod      video.mod
date.mod       keystatus.mod  probe.mod      videotest.mod
datetime.mod       linux16.mod      pxeboot.img      xfs.mod
device.map       linuxmint.png  pxecmd.mod      xnu.mod
diskboot.img       linux.mod      pxe.mod      xnu_uuid.mod
dm_nv.mod       lnxboot.img      raid5rec.mod      zfsinfo.mod
drivemap.mod       loadenv.mod      raid6rec.mod      zfs.mod
echo.mod       loopback.mod   raid.mod
efiemu32.o       lsmmap.mod      read.mod

---

### Post by e4uforums on 2010-04-19
I'm sorry, I thought you were getting to a working terminal, my mistake.  Boot from a live cd and follow the link below to mount your existing installation.  This will give you a working environment that you can use to troubleshoot.

[http://ubuntuforums.org/showthread.php?t=316580](http://ubuntuforums.org/showthread.php?t=316580)

---

### Post by coffeecat on 2010-04-19
> **Crazedpsyc said:**
> > usplash: no usable theme found for [XxY]
screen init failed                      

Let's try to reconfigure usplash to see if that helps.

At the grub menu, choose recovery mode. Don't worry about the scrolling text. When you get to a menu of choices, select 'drop to root console without networking' (or words to that effect). You'll now be in a text-only root console with a # prompt. TAKE CARE. You have full root powers.

Now type:

```
update-alternatives --config usplash-artwork.so 
```There may be several usplash themes to choose from or there may be one. I don't know how many come with Mint. Choose whichever seems right. Now...

```
update-initramfs -u
```And when that's finished...

```
reboot
```... and see if you can boot up normally.

Caution - you had a crash and an unclean shutdown. The usplash problem may be only one problem. Let's hope for the best.

---

### Post by Crazedpsyc on 2010-04-19
Thanks everyone! Good news! after leaving it on the black screen for about 30 minutes I went to the Alt+F1 thing again and got additional nonsense! It asked me to put in the path to the usplash theme.so or press enter to boot, so I pressed enter, and it booted! Now everything works fine! the problem was that I deleted my usplash theme because it didn't work, so now I will install a new one or go to the default. So it looks like your idea was right coffeecat, thx! I just love this forum!

---

### Post by coffeecat on 2010-04-19
> **Crazedpsyc said:**
>  so now I will install a new one or go to the default.

If you need to reconfigure usplash and you can do this from a terminal in the GUI, remember to  prefix those commands I posted with "sudo". You don't need sudo in a root recovery console, but you will if you've logged into a GUI.

Good luck!

---

### Post by Crazedpsyc on 2010-04-21
Speaking of which, how do I make the recovery mode terminal require a password? is there a way to start vlock or some similar thing as soon as it is activated?

---

### Post by theozzlives on 2010-04-21
Karmic uses xsplash insted of usplash.

---

### Post by Crazedpsyc on 2010-04-21
huh? xsplash is just for that thing right before and after the login thing, usplash is long before login. in mint 8 it showed an ugly pulsing mint thing, so I changed that lol. at least I don't think I installed usplash... (mint 8 is the same as karmic)

---

