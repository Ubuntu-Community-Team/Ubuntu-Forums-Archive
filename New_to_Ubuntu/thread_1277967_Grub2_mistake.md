---
title: "Grub2 mistake"
date: 2009-09-28
forum: New to Ubuntu
---

### Post by cheesypoof on 2009-09-28
I have a Vista/Ubuntu grub2 dual boot. I set the timeout to 0. After the reboot, I could not reach the menu to select Ubuntu. I tried hitting escape or holding shift to reach the menu with no success. Pressing those keys unfortunately only reboots the PC. It automatically boots Vista if I do nothing. I can't figure out how to reach the menu. I obviously was mistaken in my belief of what setting timeout 0 would do... I have a LiveCD by the way. What can I do to fix this?

---

### Post by Darkwing-Duck on 2009-09-29
Okay open the LiveCD. Once in there mount the main HD and navigate your way in the filesystem of the Local HD to  /boot/grub/

Once there edit the menu.lst file and change the timeout values.

This should fix your problem with the timeout!

Hope this helps.

---

### Post by oldfred on 2009-09-29
I see it is posted as solved but I do not know how?

Darkwing - you must have know the OP had old Grub not Grub2? 

If Grub 2, there is no menu.lst
and you should then edit  [SIZE=2][SIZE=1]**/etc/default/grub**[/SIZE]
[/SIZE]
[http://members.iinet.net/~herman546/p20/GRUB2%20Files.html#grub](http://members.iinet.net/~herman546/p20/GRUB2%20Files.html#grub)

---

### Post by Darkwing-Duck on 2009-09-29
DOH! You are right. I missed that one. Thank you for the correction. *notes Grub/Grub2* This is what happens when you post in the middle of the night LOL

---

### Post by cheesypoof on 2009-09-29
I loaded the LiveCD, did "gksudo nautilus", made the grub.cfg writable by root, and manually edited the timeout. I also reconfigured the /etc/default/grub to the correct timeout. I was skeptical about being able to modify its write status, that is why I did not do this before posting. Thanks though for the help. ;)

---

