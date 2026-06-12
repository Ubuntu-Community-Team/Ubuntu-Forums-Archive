---
title: "XP, Vista, Ubuntu 8.04 Triple Boot - Ubuntu wont boot"
date: 2009-02-13
forum: New to Ubuntu
---

### Post by speedjunkie on 2009-02-13
Ok I have a desktop with a 200gb hard drive 100gigs is for Vista (came from the factory - oem install) 50 gigs for 8.04 Ubuntu, and 50 gigs for Windows XP Home Edition.  I am trying to use EasyBCD to configure my booting needs.  I have it set-up and can boot into Vista and XP but when I try to boot into Ubuntu I get Grub Error 27 Partition Not Found (or something like that).  I am using the NeoGrub option in EasyBCD and my menu.lst for NeoGrub looks like this:

```
# NeoSmart NeoGrub Bootloader Configuration File
#
# This is the NeoGrub configuration file, and should be located at C:\NST\menu.lst
# Please see the EasyBCD Documentation for information on how to create/modify entries:
# http://neosmart.net/wiki/display/EBCD

find --set-root --ignore-floppies /boot/grub/menu.lst
configfile /boot/grub/menu.lst

# All your boot are belong to NeoSmart!

title        Ubuntu 8.04.2, kernel 2.6.24-23-generic
root        (hd1,1)
kernel        /boot/vmlinuz-2.6.24-23-generic root=UUID=d0f1a197-9517-409d-9924-aafb7923ab52 ro quiet splash
initrd        /boot/initrd.img-2.6.24-23-generic
quiet

title        Ubuntu 8.04.2, kernel 2.6.24-23-generic (recovery mode)
root        (hd1,1)
kernel        /boot/vmlinuz-2.6.24-23-generic root=UUID=d0f1a197-9517-409d-9924-aafb7923ab52 ro single
initrd        /boot/initrd.img-2.6.24-23-generic

title        Ubuntu 8.04.2, memtest86+
root        (hd1,1)
kernel        /boot/memtest86+.bin
quiet 
```
Does anyone have any clue?

---

### Post by taseedorf on 2009-02-13
you have to install grub....

however, make sure you do not install it to the mbr

go into ubuntu...
and install grub 
sudo grub
setup 
etc..


also, the hard drive is probably at (hd0,1) so try changing that
or even try changing it to (hd0,0) if it doesnt work

---

### Post by caljohnsmith on 2009-02-13
So is Ubuntu on sda2? If so, in your NeoGrub's menu.lst try using (hd0,1) instead of (hd1,1). If that doesn't work, how about booting your Ubuntu Live CD (the Ubuntu install CD), download the [Boot Info Script]("https://sourceforge.net/projects/bootinfoscript/") to the Live CD desktop, open a terminal (Applications > Accessories > Terminal) and do:
```
sudo bash ~/Desktop/boot_info_script*.sh
```
That will create a "RESULTS.txt" file in the same directory from where the script is run, namely your desktop; please copy/paste the contents of the RESULTS.txt file to your next post, highlight the copied text, and click the pound/hash sign # graphic in the Ubuntu forum message box so that the text will get "code" tags put around it. The results of that script will help clarify your setup and hopefully what the solution to your booting problem might be.

---

### Post by speedjunkie on 2009-02-13
[QUOTE=taseedorf]you have to install grub....

however, make sure you do not install it to the mbr

go into ubuntu...
and install grub 
sudo grub
setup 
etc..


also, the hard drive is probably at (hd0,1) so try changing that
or even try changing it to (hd0,0) if it doesn't work[/QUOTE]

The neogrub is setup correctly as I copied those three entries from the grub menu.lst file.  If I boot Ubuntu using the live cd and take the boot flag off of the first partition (Vista) then grub boots (not easybcd) correctly and I can boot into Ubuntu (which I am currently using to browse the web).  Also before I had installed XP I was dual booting vista and Ubuntu just fine using Grub, when I installed XP (making no changes to grubs menu.lst file) XP would boot when I clicked on the Vista Option in grub.  I would better like it if I could tripple boot these and use grub if someone could help me with that.

[QUOTE=caljohnsmith]So is Ubuntu on sda2? If so, in your NeoGrub's menu.lst try using (hd0,1) instead of (hd1,1). If that doesn't work, how about booting your Ubuntu Live CD (the Ubuntu install CD), download the Boot Info Script to the Live CD desktop, open a terminal (Applications > Accessories > Terminal) and do:
Code:
```

sudo bash ~/Desktop/boot_info_script*.sh
```

That will create a "RESULTS.txt" file in the same directory from where the script is run, namely your desktop; please copy/paste the contents of the RESULTS.txt file to your next post, highlight the copied text, and click the pound/hash sign # graphic in the Ubuntu forum message box so that the text will get "code" tags put around it. The results of that script will help clarify your setup and hopefully what the solution to your booting problem might be.[/QUOTE]

I tried doing
```

sudo bash ~/Desktop/boot_info_script*.sh
```
and it didnt work, it gave me this as an error
```
bash: /home/richard/Desktop/boot_info_script*.sh: No such file or director
```

Like I said earlier I would LOVE it if I could use Grub for my booting needs but I just need help setting it up because when I installed XP I am guessing it overwrote the Vista MBR Because when I boot using Grub and choose my Vista Option (worked before XP was Installed) it boots XP.  I knew that was going to happen so I am going to have to fix the vista mbr and then set-up grub correctly so it will boot vista and xp but I dont know how to set it up to boot xp.  

here is my menu.lst file as it stands now
```
## ## End Default Options ##

title		Ubuntu 8.04.2, kernel 2.6.24-23-generic
root		(hd1,1)
kernel		/boot/vmlinuz-2.6.24-23-generic root=UUID=d0f1a197-9517-409d-9924-aafb7923ab52 ro quiet splash
initrd		/boot/initrd.img-2.6.24-23-generic
quiet

title		Ubuntu 8.04.2, kernel 2.6.24-23-generic (recovery mode)
root		(hd1,1)
kernel		/boot/vmlinuz-2.6.24-23-generic root=UUID=d0f1a197-9517-409d-9924-aafb7923ab52 ro single
initrd		/boot/initrd.img-2.6.24-23-generic

title		Ubuntu 8.04.2, memtest86+
root		(hd1,1)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Windows Vista/Longhorn (loader)
root		(hd1,0)
savedefault
makeactive
map		(hd0) (hd1)
map		(hd1) (hd0)
chainloader	+1

title		Windows XP
root 		(hd1,3)
makeactive
chainloader	+1
```

This works fine to boot all the ubuntu kernels but the "Windows Vista/Longhorn (loader) boots XP and the "Windows XP" bring back some error (I think the ntldr is missing error).

Here is how my partitions are set-up:
/dev/sda1    ntfs    /media/sda1    93.16GiB(Vista)
/dev/sda2    ext3    /              45.31GiB(Ubuntu)
/dev/sda3    ntfs    no mount point 45.31GiB(XP)
/dev/sda4    extended               2.53GiB
/dev/sda5    linux-swap             2.53GiB

---

### Post by caljohnsmith on 2009-02-13
You have to first download the Boot Info Script to your desktop before you can run that command. Please see the link in my previous post.

---

### Post by stchman on 2009-02-13
What order did you install the OSes?  I have found that GRUB can handle all of them.  You need to install the OSes in the following order:

XP
Vista
Ubuntu

GRUB will find them.

---

### Post by speedjunkie on 2009-02-13
go it fixed...the windows vista option in grub boots the windows boot manager which I can choose wither xp or vista which is fine with me because I can now boot into all my oses

---

