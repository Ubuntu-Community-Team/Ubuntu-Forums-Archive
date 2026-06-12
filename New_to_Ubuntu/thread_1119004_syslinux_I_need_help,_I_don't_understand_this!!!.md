---
title: "syslinux I need help, I don't understand this!!!"
date: 2009-04-07
forum: New to Ubuntu
---

### Post by ericeclifford on 2009-04-07
Ok well here is the scoop.

First I took a iso image and I put it in my solid state disk.

The drive is FAT 16 and it boots fine.

Now i try to take another Iso Image, by either putting it on another partition?

Or I put it on the same partition as the first iso.

What I am trying to do is have 2 LIVE iso images bootable on my solid state disk. it is possible with 1 as far as I know because it. But how do I Change the syslinux.cfg to boot from it and where do I put the other image and boot files, here is my syslinux.cfg as of now.

now I added the second label live 1, because that is where I want to boot the second iso image from, and I put the second filesystem.manifest in the casper1 folder that I made. the first iso manifest is in the casper folder along with vmlinuz kernal thingy. I NEED HELp here is my syslinux.cfg

DEFAULT /casper/vmlinuz
GFXBOOT bootlogo
APPEND  file=/cdrom/preseed/ubuntu.seed boot=casper initrd=/casper/initrd.gz quiet splash --
LABEL live
  menu label ^Try Ubuntu without any change to your computer
  kernel /casper/vmlinuz
  append  file=/cdrom/preseed/ubuntu.seed boot=casper initrd=/casper/initrd.gz quiet splash --
LABEL live1
  menu label ^Live1
  kernal /casper1/casper/vmlinuz
  append  file=/cdrom/preseed/ubuntu.seed boot=casper initrd=/casper1/casper/initrd.gz quiet splash --
LABEL live-install
  menu label ^Install Ubuntu
  kernel /casper/vmlinuz
  append  file=/cdrom/preseed/ubuntu.seed boot=casper only-ubiquity initrd=/casper/initrd.gz quiet splash --
LABEL check
  menu label ^Check CD for defects
  kernel /casper/vmlinuz
  append  boot=casper integrity-check initrd=/casper/initrd.gz quiet splash --
LABEL memtest
  menu label Test ^memory
  kernel /install/mt86plus
  append -
LABEL hd
  menu label ^Boot from first hard disk
  localboot 0x80
  append -
DISPLAY isolinux.txt
TIMEOUT 300
PROMPT 1
F1 f1.txt
F2 f2.txt
F3 f3.txt
F4 f4.txt
F5 f5.txt
F6 f6.txt
F7 f7.txt
F8 f8.txt
F9 f9.txt
F0 f10.txt





Any Ideas would much appreciated :popcorn:

---

### Post by ericeclifford on 2009-04-07
Should I erase the default line at the first line and add in something else or just delete it?

---

### Post by ericeclifford on 2009-04-08
can anyone help?

---

### Post by ericeclifford on 2009-04-08
My Usbcreator  does not work to help me, i guess because its /dev/sda1 and its not a usb, its a IDE solid state disk.

---

### Post by ericeclifford on 2009-04-08
anyone know how to do this?

---

### Post by Jakey_TheSnake on 2009-04-08
If you formatted it to FAT32 it would probably recognise it as a USB. 

Uhhh, you could install GRUB bootloader on it?

---

### Post by ericeclifford on 2009-04-08
I guess I could try grub but I really do not even see how the hell people use grub on a live USB or Live cd, Ive been searching and couldnt find sht.

---

### Post by LowSky on 2009-04-08
I was googleing to try to answer this for you and found this and while hilarious is quite helpful

[http://lmgtfy.com/?q=boot+multiple+iso+from+usb](http://lmgtfy.com/?q=boot+multiple+iso+from+usb)

---

### Post by Jakey_TheSnake on 2009-04-08
I'm not an expert at this sort of thing, but I know the way you *should* do it is by installing a bootloader (not necessarily GRUB, mind). 

How about creating a Ubuntu Live-USB, then save the /boot/grub/menu.lst and save + upload it here. 

Then create the Live-USB of your other OS, and check out its equivalent to menu.lst and see where it boots the kernel and initrd from. Then wipe it clean, put Ubuntu Live-USB back on there with however much storage space, then partition it to take up half of the drive. Put the other OS on the other half, and then edit the /boot/grub/menu.lst (Ubuntu's) with the info you gained from the other OS (remember you'll need to change the root to (hd0,1) for it), and give the Ubuntu partition the "boot" flag with partition editor. Then you should be able to get a working GRUB up...

---

### Post by ericeclifford on 2009-04-08
> **LowSky said:**
> I was googleing to try to answer this for you and found this and while hilarious is quite helpful

[http://lmgtfy.com/?q=boot+multiple+iso+from+usb](http://lmgtfy.com/?q=boot+multiple+iso+from+usb)


Ya well ty for the help,  but still Wasnt good enough at most of these pages and they all talk about grub, not syslinux,  And the USB creator does not work for me or shows my Solid state disk on there menu, I am on hardy 8.04.2 and the 2 iso images that i want to boot on my live usb are hardy 8.04.2 with minor changes done to both of them. And I want the live usb so it doesnt save anything. I also am trying to do it on 1 partition, not have multiple partitions.

---

