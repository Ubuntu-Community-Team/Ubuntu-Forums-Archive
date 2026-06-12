---
title: "Laptop without HDD, ubuntu installed onto a SD card, how can I boot it using GRUB?"
date: 2009-01-11
forum: New to Ubuntu
---

### Post by zoo0828 on 2009-01-11
Hi, guys, need your help!

I've got a laptop without HDD (sent to repair) that runs ubuntu (CDROM or USB stick) like a charm, it is absolutely great since almost all the hardware are recognized and working fine including wireless card and even the bluetooth...

Then I happily installed the ubuntu onto a 8G SDHC card without any problem, however, it turned out that the laptop can not boot from the SD card, ok, then I made a bootable USB stick with the GRUB4DOS on it, now here comes my question:

How can I boot from the USB stick and subsequently boot the ubuntu on the SD card using the GRUB?

Looks like the 
"root=UUID=56e62b12-d926-4eb3-b73f-9cb0280114bc" is not pointing to the SD card...


Below is the menu.lst I managed to copy from the SD card
/boot/grub/menu.lst

## ## End Default Options ##

title		Ubuntu 8.10, kernel 2.6.27-7-generic
uuid		56e62b12-d926-4eb3-b73f-9cb0280114bc
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=56e62b12-d926-4eb3-b73f-9cb0280114bc ro quiet splash 
initrd		/boot/initrd.img-2.6.27-7-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-7-generic (recovery mode)
uuid		56e62b12-d926-4eb3-b73f-9cb0280114bc
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=56e62b12-d926-4eb3-b73f-9cb0280114bc ro  single
initrd		/boot/initrd.img-2.6.27-7-generic

title		Ubuntu 8.10, memtest86+
uuid		56e62b12-d926-4eb3-b73f-9cb0280114bc
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

---

### Post by taseedorf on 2009-01-12
Booting from the flash disk is impossible, unless your motherboard supports it.  Not all motherboards do.  For example, I can't on my desktop or my netbook.  I think you're sol.

---

### Post by Captain_tux on 2009-01-12
Depending on your system, you're gonna need to enter F2, F10, F12, ESC, etc., to enter your BIOS and change the boot sequence order.

If you're using a newer laptop (less than 3-4) years old, your motherboard should be able to support booting from USB.

---

### Post by boof1988 on 2009-01-12
One option is to make a [[COLOR="Blue"]Boot CD that boots to USB-Flash[/COLOR]](http://www.pendrivelinux.com/usb-boot-cd-for-ubuntu-810/).

Edit: Though I don't know if this helps or not.  There are probably different drivers for the sd card.  Maybe there is a way to find the drivers for the sd card and include them on the cd?

Maybe that would help...  I want to make one eventually for a Dell GX110 that seems like it can't boot to USB.

---

### Post by akimatsu123 on 2009-01-12
depends on your OS. I have a brand new computer, which supports booting from SD. My old one didnt. I know that there is a bootable CD that makes it possible for you to boot off a USB (confusing i know, you boot the CD, which reads off the USB) but I'm not sure if that supports SD cards. 

If your OS supports booting from SD cards, you need to interrupt startup, and pick ur SD card. You need to have GRUB installed on the SD card, which u can specify to do so when installing Ubuntu in the installer.

---

### Post by zoo0828 on 2009-01-15
Many thanks to all of you, I finally solved the case.

Myabe I didn't make myself very clear, my laptop supports booting from USB stick but not the SD card.

Why I wanted to use the SD card is that my USB stick is only 1G in size can not accommodate an Ubuntu installation.

Here is how I make it working:
1. boot from the CDROM
2. format the 1G USB stick as ext3 and mount as / (root)
3. mount part of the 8G SD, say 6G, as /usr (which will have about 1.8G of data)
4. (optional) use the rest of the SD as the swap space

The outcome is that the laptop boots from the USB stick and utilize the 8G SD as the storage, now it flies.......

Thanks again!

---

### Post by boof1988 on 2009-01-15
> **zoo0828 said:**
> Many thanks to all of you, I finally solved the case.

Myabe I didn't make myself very clear, my laptop supports booting from USB stick but not the SD card.

Why I wanted to use the SD card is that my USB stick is only 1G in size can not accommodate an Ubuntu installation.

Here is how I make it working:
1. boot from the CDROM
2. format the 1G USB stick as ext3 and mount as / (root)
3. mount part of the 8G SD, say 6G, as /usr (which will have about 1.8G of data)
4. (optional) use the rest of the SD as the swap space

The outcome is that the laptop boots from the USB stick and utilize the 8G SD as the storage, now it flies.......

Thanks again!

I like your solution...  I often forget that the directories can be mounted on different drives (they don't *have* to be on the same drive).

Cheers

---

### Post by ap2tm on 2010-06-25
You donot need two things to boot from external source. I saw solution on this forum is suggesting that you need a usb key and sdhc card to boot from external source. You donot need both. You can use either.
 
I had been using usb memory stick or sdhc card for booting and running from it. I donot use both together. Easy solution is use a sdhc card reader it will act as a memory stick. Install from CD on either usb memory stick or sdhc card (in card reader). Generally, sdhc cards are faster than usb keys. I am using Class 6 card. Now recently class 10 became available in the market. I will switch it to.
 
I use Ubuntu 8.x, 9.x and 10.x versions on sdhc cards. Minimum card size you can use is 4 gig.
 
If you want to use ubuntu occassionally, then you can only make a bootable usb device and use it. It will fit in 1 gig usb key. This will be only for run purpose.
 
There are tons of instruction available on Ubuntu forums. If someone need any help, please email me.

---

