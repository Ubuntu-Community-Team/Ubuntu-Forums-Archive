---
title: "Hidden Ubuntu Boot"
date: 2009-01-22
forum: New to Ubuntu
---

### Post by linuxguymarshall on 2009-01-22
Hey. I am looking to dual boot Ubuntu and Win XP on my netbook. Windows XP is currently installed and i am looking to install Ubuntu. I am really interesed in making Ubuntu "hidden". Like it would wait at a black screen for a second or two and if a certain key was not held down then Windows would boot normally. Anyone know a way to do something like this?

---

### Post by emarkd on 2009-01-22
edit your /boot/grub/menu.lst file and uncomment the 'hiddenmenu' option.  you may also want to set the timeout very short, like 2 seconds or so.

---

### Post by mcduck on 2009-01-23
Yes, you can just set Grub menu to hidden and Windows as default OS. The hidden menu always has a 3 sec timeout so changing the timeout would not make any difference.

It's not *completely* hidden, though, you'll see a black screen with text on top of the screen telling you to press Esc to show the menu.

---

### Post by caljohnsmith on 2009-01-23
Another option is to keep the Windows MBR (Master Boot Record) in your HDD so that if you don't do anything, you boot straight into Windows just like before you installed Ubuntu. And then to boot Ubuntu, you could install Grub to a USB stick, CD, or even floppy, so that when you wanted to boot Ubuntu, you would just stick in your USB stick/CD/floppy and voila, you boot into Ubuntu. Just an idea, but let me know if you want to pursue it.

---

### Post by linuxguymarshall on 2009-01-23
> **caljohnsmith said:**
> Another option is to keep the Windows MBR (Master Boot Record) in your HDD so that if you don't do anything, you boot straight into Windows just like before you installed Ubuntu. And then to boot Ubuntu, you could install Grub to a USB stick, CD, or even floppy, so that when you wanted to boot Ubuntu, you would just stick in your USB stick/CD/floppy and voila, you boot into Ubuntu. Just an idea, but let me know if you want to pursue it.

Very interesting

---

### Post by caljohnsmith on 2009-01-23
So which did you want? A Grub CD, floppy, or USB stick? How about posting the output of:
```
sudo fdisk -lu
```
And identify your partitions; also if a Grub USB stick is what you are after, have the USB stick connected when you run that command. In addition, you would need to check that your BIOS supports USB booting.

---

