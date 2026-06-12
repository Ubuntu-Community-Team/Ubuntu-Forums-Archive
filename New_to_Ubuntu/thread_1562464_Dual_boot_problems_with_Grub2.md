---
title: "Dual boot problems with Grub2"
date: 2010-08-27
forum: New to Ubuntu
---

### Post by nuddernuby on 2010-08-27
I'm battling with the same problem (10.04 and XP) Just a blank screen with flashing cursor.

I find this in Results.txt:
> 
=> Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #5 for /boot/grub.

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Grub 2
    Boot sector info:  Grub 2 is installed in the boot sector of sda1 and 
                       looks at sector 150929688 of the same hard drive for 
                       core.img, but core.img can not be found at this 
                       location. No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM



(I can show the rest of the file , if necessary)

How could core.img problem be fixed?

Alternatively, is it possible to revert back to GRUB in stead of GRUB2?
TIA

---

### Post by oldfred on 2010-08-27
It sounds like you have multiple problems. 

Grub2 should not be installed to a partition normally and you have it installed to the windows partition which overwrote essential windows boot code.

Fix for most, a few have other issues, better than windows fix in many cases as it also fixes other parameters:
This has instructions on using testdisk to repair the install of grub to the boot sector for windows from Ubuntu or Linux LiveCD.
[http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Boot_Sector](http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Boot_Sector)

Did you use an older CD as they now have that problem fixed in the latest versions - 10.04.1 LTS

But the flashing cursor is a grub boot error. I would first try reinstalling grub2 to the MBR (sda) not the partitions sda1, sda2 etc.

Install MBR from LiveCD, Ubuntu install on sda5 and want grub2 in drive sda's MBR:
Find linux partition, change sda5 if not correct, and/or even sda if sdb wanted:
sudo fdisk -l
sudo mount /dev/sda5 /mnt
sudo grub-install --root-directory=/mnt /dev/sda
If that returns any errors run:
sudo grub-install --recheck --root-directory=/mnt /dev/sda

---

### Post by nuddernuby on 2010-08-27
Thank you for your response, oldfred.
One or two quick points:
This is 10.04.1 LTS
I can boot both XP and Ubuntu from a Supergrub2 Disk - no problem.
I have reinstalled Grub2 several times, from command line as well as from Synaptic. If it writes it to the wrong sector, then it appears to be doing that of its own accord.
As an interim solution, I have repaired XP boot via FIXBOOT. I keep the Grub2 disc in the DVD Drive in order to have a menu.
I have also attempted writing a boot disc to USD Flash drive - but no success.
Now I have re-installed again, specifying /dev/sda.  XP is the default.
When I reboot, I end up with XP - but I still have a black screen - and if I change the default to Ubuntu, I still end up booting to XP... 
So, then I followed the instructions you gave. When rebooting I got:
> 
error: file not found
grub rescue>

Then I ran the re-check command. On rebooting I got:
> 

GNU GRUB version 1.98-1Ubuntu7
Minimal BASH-like line editing is supported. For the first word, TAB lists possible command completion. Anywhere else TAB lists possible device.... etc  etc  



So, now I don't know anymore...

---

### Post by oldfred on 2010-08-27
Since this is a solved thread, you will not get many looking at it except for answers. It would be better to start your own thread and post a new run of the boot_info script so we can see exactly where you are at.

Can you manually boot?
Manual boot:
Adjust drive, partition to your install sda1 = hd0,1 etc:
ls #lists partitions
ls (hd0,1)/
set root (hd0,1)
kernel /vmlinuz root=/dev/sda1 ro
initrd /initrd.img
boot

---

### Post by cariboo on 2010-08-27
Moved to a thread of it's own, seeing as this was tacked to the end of a solved thread.

There are a few more steps that oldfred missed. Boot from the Live CD, and once at the desktop, open a terminal and type:

[list=1]
[*] sudo mount /dev/sda5 /mnt
[*] sudo mount -o bind /sys /mnt/sys
[*] sudo mount -o bind /proc /mnt/proc
[*] sudo mount -o bind /dev /mnt/dev
[*] sudo chroot /mnt
[*] grub-install /dev/sda
[*] update-grub
[/list]

After running update-grub you should see a list of the OSs on your system. 

I'm continually adding operating systems to my computer. The one I'm using at the moment has XP, Kubuntu 10.10, Ubuntu 10.10, PCLinuxOS 2010 and Ubuntu+Xbmc 10.10. Everytime I install a new OS Grub gets over written, so I use the above commands to install grub the way I want.

---

### Post by nuddernuby on 2010-08-27
Thanks for creating the thread.
Yes, I can boot manually to either OS by using the super grub2 disk
Will try the steps and report back.

---

### Post by nuddernuby on 2010-08-27
BTW, here is boot_info_script result of current state before the next commands.

---

### Post by oldfred on 2010-08-27
Because you have grub2 you can do this to reinstall grub2.

Install MBR from LiveCD, Ubuntu install on sda5 and want grub2 in drive sda's MBR:

```
sudo mount /dev/sda5 /mnt
sudo grub-install --root-directory=/mnt /dev/sda

```
If that returns any errors run:
```
sudo grub-install --recheck --root-directory=/mnt /dev/sda

```

cariboo907 version is the full chroot when the above one does not work, so you still can run his.

You also have menu.lst in your grub folder. Sometimes that confuses grub2. I would also delete that. If then you still have issues we may want to uninstall both grub & grub2 and reinstall just grub2.

---

### Post by nuddernuby on 2010-08-27
...and after the new set of commands.

---

### Post by nuddernuby on 2010-08-27
I guess everything is now working correctly, except that I can't see anything.
Default OS is XP. If I reboot, XP appears after some time, presumably after timeout. If I reboot and use arrows to (blindly) move 4 lines up, I get Ubuntu.  So, what still remains is how to get rid of the black screen..

---

### Post by oldfred on 2010-08-27
You are supposed to see the menu with two operating systems. Did you turn off the menu in grub?

Also try holding down shift from BIOS boot until menu appears. If you get the menu then press e to edit the grub commands and on the kernel line replace quiet splash with nomodeset.

---

### Post by nuddernuby on 2010-08-27
No luck, I'm afraid.
Holding down Shift produces no menu - only 'Grub loading' and flashing cursor for about 4 seconds, then black screen again.
Tried changing 'quiet splash' to 'nomodeset' in /etc/default/grub, but also no luck. 
How do I check if menu is turned off?

---

### Post by nuddernuby on 2010-08-27
Thank you for your inputs so far. This is now taking too much time. I'm going to get some sleep...

---

### Post by skatinjj on 2010-08-27
> **nuddernuby said:**
> No luck, I'm afraid.
Holding down Shift produces no menu - only 'Grub loading' and flashing cursor for about 4 seconds, then black screen again.
Tried changing 'quiet splash' to 'nomodeset' in /etc/default/grub, but also no luck. 
How do I check if menu is turned off?

Can check [this]("http://ubuntuforums.org/showthread.php?t=1195275") when you get the chance.

---

### Post by oldfred on 2010-08-28
Changes to  /etc/default/grub will not take place until you run sudo update-grub. Timeouts in grub and some of the other settings change how the menu is shown. skatinjj's link to grub2 info explains some of the settings in section #5.

If you can blind up arrow to get Ubuntu to boot does it fully boot? If so then the timeouts or other setting in  /etc/default/grub may be the issue.

---

### Post by nuddernuby on 2010-08-30
Now here is something interesting.
I have more or less given up on this, accepting that my boot up will from now on include a blind punch of arrow keys to change the OS booted.

Have just flown over to Australia. Opened laptop, powered up and got ready to work the arrows, when....
Voilá, the menu presented itself flawlessly.
I rebooted a number of times - perfect every time.
Spooky, or what?

Shall we mark this thread as UNSOLVED SOLVED?  Or SOLVED UNSOLVED?

---

