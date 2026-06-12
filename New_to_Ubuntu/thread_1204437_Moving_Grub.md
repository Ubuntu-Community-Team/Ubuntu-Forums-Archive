---
title: "Moving Grub"
date: 2009-07-04
forum: New to Ubuntu
---

### Post by skyjacker on 2009-07-04
I installed 9.04 on a usb hard drive, and put the boot loader on that drive also. I dual boot with XP, which I only use 1 or 2 days a month. If something happens to the usb drive, will I still be able to boot into XP? Should I move the Grub to my pc drive, if so how do I do that? Love Ubuntu, hate XP.... need some help.

---

### Post by theozzlives on 2009-07-04
> **skyjacker said:**
> I installed 9.04 on a usb hard drive, and put the boot loader on that drive also. I dual boot with XP, which I only use 1 or 2 days a month. If something happens to the usb drive, will I still be able to boot into XP? Should I move the Grub to my pc drive, if so how do I do that? Love Ubuntu, hate XP.... need some help.

I'd setup dual boot on your PC. It's a much more effective way of booting.

---

### Post by skyjacker on 2009-07-04
> **theozzlives said:**
> I'd setup dual boot on your PC. It's a much more effective way of booting.
Do you mean reinstalling ubuntu on the pc, and then assigning Grub to that partition?

---

### Post by cariboo on 2009-07-04
It all depends on how you have things setup. Can you boot into XP with out the usb drive connected? How is the boot order set in you BIOS?

---

### Post by skyjacker on 2009-07-04
> **cariboo907 said:**
> It all depends on how you have things setup. Can you boot into XP with out the usb drive connected? How is the boot order set in you BIOS? If I try power down the pc, unhook the usb drive, and then power up, it goes into the grub menu screen with an error message "grub error 21".
The boot order is pc hard drive, then usb hard drive. Guess I'll have to reinstall ubuntu on the pc hard drive, right? I set up a separate /home, can I copy it to a cd and copy it to the new installation?
Thanks for your help.

---

### Post by presence1960 on 2009-07-04
> **skyjacker said:**
> If I try power down the pc, unhook the usb drive, and then power up, it goes into the grub menu screen with an error message "grub error 21".
The boot order is pc hard drive, then usb hard drive. Guess I'll have to reinstall ubuntu on the pc hard drive, right? I set up a separate /home, can I copy it to a cd and copy it to the new installation?
Thanks for your help.

it sounds like you installed GRUB to your internal drive, that's why you get Error 21. here is error 21 described from the GRUB manual :
```
21 : Selected disk does not exist
    This error is returned if the device part of a device- or full file name refers to a disk or BIOS device that is not present or not recognized by the BIOS in the system. 

```

GRUB was installed to your internal HDD and points to menu.lst on your USB drive. Since USB drive is unplugged you get error 21.

What you can do is restore GRUB to the USB drive with the USB drive plugged in of course. Iam assuming you only have 1 internal HDD and the USB drive. If you have others you will have to alter the commands root (hd1,x) and setup (hd1) to match your setup:
```
1. Boot your computer up with Ubuntu CD
2. Open a terminal window or switch to a tty.
3. Type sudo grub. Should get text of which last line is grub>
4. Type "find /boot/grub/stage1". You'll get a response like "(hd0,1)". 
   Use whatever your computer spits out for the following lines.
5. Type "root (hd1,x)",where x is the partition on your USB drive for Ubuntu / (root). Numbering starts at 0, so first partition would be 0 -> (hd1,0)
6. Type "setup (hd1)", to install GRUB to MBR, assuming you only have 1 internal HDD and the USB drive.
7. Quit grub by typing "quit".
8. Reboot and remove the bootable CD. make sure Ubuntu boots
```

Next you want to unplug your USB drive and restore windows bootloader to MBR of internal drive so when USB is unplugged windows will boot. Here is a link : [http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)  after complete check booting without USB to see if windows boots ok. If so one more step. In BIOS set your boot order to CD/USB or Removable/Hard disk. This will allow you to boot from CD when one is in the drive, when your USB is plugged in it will boot off of that and give you GRUB, or if USB is unplugged will go to HDD and boot windows bootloader.

---

