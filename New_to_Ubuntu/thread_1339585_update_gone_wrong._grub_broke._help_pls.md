---
title: "update gone wrong. grub broke. help pls"
date: 2009-11-27
forum: New to Ubuntu
---

### Post by lazersgm on 2009-11-27
i had ubuntu working fine. i got a prompt for the normal system upgrades so i hit ok install them. when i reboted the comeputer it comes up to the grub prompt after it passes the windows boot prompt. not sure what the boot drive is or how to tell grub wich one to load. use to be a menu with 4 options here to load ubuntu or windows 7 or xp. thanks for any help you can give.

---

### Post by lazersgm on 2009-11-27
bump for help pls.

---

### Post by Exadrid on 2009-11-27
I recommend a reinstall. If you need help i can help you. Just PM me.

---

### Post by Buuntu on 2009-11-27
Only do the below portion if you are using grub < 2 (the default in anything but Karmic) 

[LIST=1]
[*]Boot your computer up with Ubuntu CD
[*]Open a terminal window or switch to a tty.
[*]Go [SuperUser]("https://help.ubuntu.com/community/SuperUser") (that is, type "sudo -s"). Enter root passwords as necessary.
[*]Type "grub"
[*]Type "find /boot/grub/stage1". You'll get a response like "(hd0,1)". Use whatever your computer spits out for the following lines.
[*]Type "root (hd0,1)", or whatever your hard disk + boot partition numbers are for Ubuntu.
[*]Type "setup (hd0)", to install GRUB to MBR, or "setup (hd0,1)" or whatever your hard disk + partition nr is, to install GRUB to a partition.
[*]Quit grub by typing "quit".
[*]Reboot and remove the bootable CD.
[/LIST]
This was taken straight from this site: [https://help.ubuntu.com/community/GrubHowto](https://help.ubuntu.com/community/GrubHowto), read through it if you have any questions

If you are running Karmic and are sure you have grub 2 ('grub-install -v', 1.97 = grub 2) then follow these instructions instead: [https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2)

---

### Post by lazersgm on 2009-11-29
found that there is a bug with the wubi installer and the newest updates. so reinstalled to a seprate drive with a real install instead of wubi. all works fine now. thanks for the help guys.

---

