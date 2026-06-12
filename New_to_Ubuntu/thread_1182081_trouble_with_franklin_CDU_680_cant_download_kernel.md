---
title: "trouble with franklin CDU 680/ cant download kernel update"
date: 2009-06-08
forum: New to Ubuntu
---

### Post by Graf Orlok on 2009-06-08
Hi. my Franklin CDU 680 is not recognized by UNR 9.04, someone else told me that i needed to download the kernel update from the jaunty proposed, but i cant do this because the option "complete generic linux kernel" is deselected and i cant select it. the other solution i got was to add the next line in the menu.lst       usbserial.vendor = 0x16d8 usbserial.product = 0x680 . the modified part is like this:

## additional options to use with the default boot option, but not with the 
## alternatives 
## e.g. defoptions=vga=791 resume=/dev/hda5 
# defoptions=quiet splash usbserial.vendor = 0x16d8 usbserial.product = 0x6803

also i noticed that after i do this the following part is also modified (i made a little research and understand that this is right  but im not sure)

## ## End Default Options ## 

title		Ubuntu 9.04, kernel 2.6.28-11-generic 
uuid		713a13bd-a737-4ad2-9f26-29e9f6bc831b 
kernel /boot/vmlinuz-2.6.28-11-generic root=UUID=713a13bd-a737-4ad2-9f26-29e9f6bc831b ro quiet splash usbserial.vendor = 0x16d8 usbserial.product = 0x6803 
initrd		/boot/initrd.img-2.6.28-11-generic

after that i put  sudo update-grub and the result is this

Searching for GRUB installation directory ... found: /boot/grub 
Searching for default file ... found: /boot/grub/default 
Testing for an existing GRUB menu.lst file ... found: /boot/grub/menu.lst 
Searching for splash image ... none found, skipping ... 
Found kernel: /boot/vmlinuz-2.6.28-11-generic 
Found kernel: /boot/memtest86+.bin 
Replacing config file /var/run/grub/menu.lst with new version 
Updating /boot/grub/menu.lst ... done

finally i put sudo grub-install /dev/sda (have a sata) and the result is

Searching for GRUB installation directory ... found: /boot/grub 
error: no such partition 
Installing GRUB to /dev/sda as (hd0)... 
Installation finished. No error reported. 
This is the contents of the device map /boot/grub/device.map. 
Check if this is correct or not. If any of the lines is incorrect, 
fix it and re-run the script `grub-install'. 

(hd0)	/dev/sda 
(hd1)	/dev/sdb

then, i was supposed to restart UNR and now the CDU 680 should be recognized and can do the procedure indicated by the manufacturer, but after i chose to start ubuntu, i got the next error

[0.000000] Booting Kernel: ' ' Invalid for parameter 'usbserial.vendor'

and then UNR loads as usual, but when i do modprobe usbserial vendor=0x4348 product=0x5523 i get the nex message FATAL: Module usbserial not found.

what im doing wrong? 

thanks for your time.

sorry about the post, first time posting and also im new to linux (sorry about the english but is not my mother tongue)

---

