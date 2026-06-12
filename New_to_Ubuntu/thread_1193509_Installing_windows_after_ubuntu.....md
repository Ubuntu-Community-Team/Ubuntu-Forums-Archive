---
title: "Installing windows after ubuntu...."
date: 2009-06-21
forum: New to Ubuntu
---

### Post by ninja senses on 2009-06-21
I recently built a computer and installed jaunty as my only OS, I now  need to install windows somehow, and keep my jaunty partition. but from what I have foudn it does not look easy.  I cant find a good write-up anywhere on how this can be done.  I have searched the forums.  Any help?!

---

### Post by TeoBigusGeekus on 2009-06-21
You have to boot up with the live cd and use the partition manager to create a new partition in which you will install windows. Otherwise windows will delete Ubuntu.
After that, your only concern will be how to restore grub because windows will destroy it.
[http://www.howtogeek.com/howto/ubuntu/reinstall-ubuntu-grub-bootloader-after-windows-wipes-it-out/]("http://www.howtogeek.com/howto/ubuntu/reinstall-ubuntu-grub-bootloader-after-windows-wipes-it-out/")

---

### Post by arochester on 2009-06-21
Have a look at [http://apcmag.com/the_definitive_dualbooting_guide_linux_vista_and_xp_stepbystep.htm](http://apcmag.com/the_definitive_dualbooting_guide_linux_vista_and_xp_stepbystep.htm)

---

### Post by presence1960 on 2009-06-21
Use the Ubuntu Live CD or the gparted Live CD to make a partition for Windows. The Windows bootloader will replace GRUB, but you can restore it like this :
> 1. Boot your computer up with Ubuntu CD
2. Open a terminal window or switch to a tty.
3. Type sudo grub. Should get text of which last line is grub>
4. Type "find /boot/grub/stage1". You'll get a response like "(hd0,1)". 
   Use whatever your computer spits out for the following lines.
5. Type "root (hd0,1)", or whatever your hard disk + boot partition 
   numbers are for Ubuntu.
6. Type "setup (hd0)", to install GRUB to MBR, or "setup (hd0,1)" or 
   whatever your hard disk + partition # is, to install GRUB to a 
   partition.
7. Quit grub by typing "quit".
8. Reboot and remove the bootable CD.

At #6 I would install GRUB to MBR, if windows & Ubuntu are on your first hard disk use setup (hd0)

---

