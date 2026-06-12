---
title: "grub-install /dev/sda"
date: 2009-04-26
forum: New to Ubuntu
---

### Post by wstay on 2009-04-26
I lost my grub bootloader when I re-installed Wxp.
I tried to get back the grub bootloader by using the Ubuntu8.10 installation disc by going to the Desktop and using the terminal, I enter the following command:

ubuntu@ubuntu:~$ su
Password: 
root@ubuntu:/home/ubuntu# grub-install /dev/sda
Probing devices to guess BIOS drives. This may take a long time.
Could not find device for /boot: Not found or not a block device.

Can someone please help me with this error message?

---

### Post by talsemgeest on 2009-04-26
Take a look at my bootloader tutorial [here.](http://ubuntuforums.org/showthread.php?t=1014708)

---

### Post by presence1960 on 2009-04-26
> **wstay said:**
> I lost my grub bootloader when I re-installed Wxp.
I tried to get back the grub bootloader by using the Ubuntu8.10 installation disc by going to the Desktop and using the terminal, I enter the following command:

ubuntu@ubuntu:~$ su
Password: 
root@ubuntu:/home/ubuntu# grub-install /dev/sda
Probing devices to guess BIOS drives. This may take a long time.
Could not find device for /boot: Not found or not a block device.

Can someone please help me with this error message?

To restore GRUB try this:

1. Boot your computer up with Ubuntu CD
2. Open a terminal window or switch to a tty.
3. Go SuperUser (that is, type "sudo -s"). Enter root passwords as 
   necessary.
4. Type "grub"
5. Type "find /boot/grub/stage1". You'll get a response like "(hd0,1)". 
   Use whatever your computer spits out for the following lines.
6. Type "root (hd0,1)", or whatever your hard disk + boot partition 
   numbers are for Ubuntu.
7. Type "setup (hd0)", to install GRUB to MBR, or "setup (hd0,1)" or 
   whatever your hard disk + partition # is, to install GRUB to a 
   partition.
8. Quit grub by typing "quit".
9. Reboot and remove the bootable CD.

---

### Post by talsemgeest on 2009-04-26
> **presence1960 said:**
> To restore GRUB try this:

```
1. Boot your computer up with Ubuntu CD
2. Open a terminal window or switch to a tty.
3. Go SuperUser (that is, type "sudo -s"). Enter root passwords as 
   necessary.
4. Type "grub"
5. Type "find /boot/grub/stage1". You'll get a response like "(hd0,1)". 
   Use whatever your computer spits out for the following lines.
6. Type "root (hd0,1)", or whatever your hard disk + boot partition 
   numbers are for Ubuntu.
7. Type "setup (hd0)", to install GRUB to MBR, or "setup (hd0,1)" or 
   whatever your hard disk + partition # is, to install GRUB to a 
   partition.
8. Quit grub by typing "quit".
```
9. Reboot and remove the bootable CD.
Yep, thats what is outlined in my tutorial. Give it a try, it should work. :)

---

### Post by presence1960 on 2009-04-26
> **talsemgeest said:**
> Yep, thats what is outlined in my tutorial. Give it a try, it should work. :)

I hear you, I should have read your tutorial before posting instead of after.

---

