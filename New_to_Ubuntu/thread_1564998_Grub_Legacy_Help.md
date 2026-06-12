---
title: "Grub Legacy Help"
date: 2010-08-31
forum: New to Ubuntu
---

### Post by UnknownFear on 2010-08-31
Yes, I know Grub2 is the new age, but I chose to revert back to Grub Legacy. I have Mac OS X and Windows 7 running along side Ubuntu 10.04. When I reverted to Legacy, both my Windows and Mac OS X entries are gone, but I know they are still on the system as I checked in Disk Utility. Can someone please help me get these entries back in Legacy Grub?

---

### Post by andrewthomas on 2010-08-31
Do you still have a /boot/grub/grub.cfg file?

---

### Post by UnknownFear on 2010-08-31
> **andrewthomas said:**
> Do you still have a /boot/grub/grub.cfg file?

Yes! :D thank God! :D

Here is the output. I only need Windows 7 and Mac OS X. I can configure Ubuntu with menu.list.

**/boot/grub/grub.cfg**
### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Mac OS X (32-bit) (on /dev/sda2)" {
	insmod hfsplus
	set root='(hd0,2)'
	search --no-floppy --fs-uuid --set d709e556d350e119
        insmod vbe
        set do_resume=0
        if [ /var/vm/sleepimage -nt10 / ]; then
           if xnu_resume /var/vm/sleepimage; then
             set do_resume=1
           fi
        fi
        if [ $do_resume == 0 ]; then
           xnu_uuid d709e556d350e119 uuid
           if [ -f /Extra/DSDT.aml ]; then
              acpi -e /Extra/DSDT.aml
           fi
           xnu_kernel /mach_kernel boot-uuid=${uuid} rd=*uuid
           if [ /System/Library/Extensions.mkext -nt /System/Library/Extensions ]; then
              xnu_mkext /System/Library/Extensions.mkext
           else
              xnu_kextdir /System/Library/Extensions
           fi
           if [ -f /Extra/Extensions.mkext ]; then
              xnu_mkext /Extra/Extensions.mkext
           fi
           if [ -d /Extra/Extensions ]; then
              xnu_kextdir /Extra/Extensions
           fi
           if [ -f /Extra/devprop.bin ]; then
              xnu_devprop_load /Extra/devprop.bin
           fi
           if [ -f /Extra/splash.jpg ]; then
              insmod jpeg
              xnu_splash /Extra/splash.jpg
           fi
           if [ -f /Extra/splash.png ]; then
              insmod png
              xnu_splash /Extra/splash.png
           fi
           if [ -f /Extra/splash.tga ]; then
              insmod tga
              xnu_splash /Extra/splash.tga
           fi
        fi
}
menuentry "Windows 7 (loader) (on /dev/sda3)" {
	insmod ntfs
	set root='(hd0,3)'
	search --no-floppy --fs-uuid --set 00ae787bae786b54
	chainloader +1
}
### END /etc/grub.d/30_os-prober ###[/CODE]

Any ideas? I know I can just copy the whole Windows 7 entry over, but I don't know what all to copy over for the Mac OS X entry.

---

### Post by UnknownFear on 2010-08-31
I currently updated my menu.lst to show my 3 entries. Ubuntu works fine, but Mac OS X doesn't work at all, and Windows gives me an error. Any help with this? I know for sure they are still on the computer, I just need to correctly point grub to the right spot.

Here is my menu.lst:

```

title		Ubuntu 10.04 LTS
uuid		61b51b95-c9e6-4f46-be75-bef0be759104
kernel		/boot/vmlinuz-2.6.32-24-generic root=UUID=61b51b95-c9e6-4f46-be75-bef0be759104 ro quiet splash 
initrd		/boot/initrd.img-2.6.32-24-generic
quiet

title		Mac OS X Snow Leopard
root		(hd0,2)		
		insmod hfsplus
search --no-floppy --fs-uuid --set d709e556d350e119

title 		Windows 7
root		(hd0,3)
makeactive
search --no-floppy --fs-uuid --set 00ae787bae786b54
chainloader 	+1

```

---

### Post by andrewthomas on 2010-08-31
> **UnknownFear said:**
> 
Any ideas? I know I can just copy the whole Windows 7 entry over, but I don't know what all to copy over for the Mac OS X entry.
Just make sure that you 
```
title windows 7 (chainload)
root (hd0,2)
chainloader +1
```subtract 1 from the partition #. Do you have a bootloader on the mac OS partition that you can chainload off of?

---

### Post by UnknownFear on 2010-08-31
I honestly have no idea. I change each roots and subtracted 1. I'll see if that worked. This is not my update menu.lst

```

title		Ubuntu 10.04 LTS
uuid		61b51b95-c9e6-4f46-be75-bef0be759104
kernel		/boot/vmlinuz-2.6.32-24-generic root=UUID=61b51b95-c9e6-4f46-be75-bef0be759104 ro quiet splash 
initrd		/boot/initrd.img-2.6.32-24-generic
quiet

title		Mac OS X Snow Leopard
root		(hd0,1)		
makeactive
chainloader +1

title 		Windows 7
root		(hd0,2)
makeactive
chainloader +1

```

---

### Post by UnknownFear on 2010-08-31
IT WORKS!!! ^_^ Both Windows and Mac OS X are working perfectly. Thank you SOO MUCH for your help andrewthomas!!

---

### Post by andrewthomas on 2010-08-31
No problem. If you don't mind me asking, why did you want to revert from grub2 to grub?

BTW, you should mark the thread as [SOLVED] from the thread tools menu

---

### Post by Windows Nerd on 2010-08-31
> **andrewthomas said:**
> No problem. If you don't mind me asking, why did you want to revert from grub2 to grub?

BTW, you should mark the thread as [SOLVED] from the thread tools menu

Grub 2 is buggy. Also configuring it is much simpler.

---

### Post by UnknownFear on 2010-08-31
> **Windows Nerd said:**
> Grub 2 is buggy. Also configuring it is much simpler.

Basically sums up why I reverted to legacy grub over grub2.

---

