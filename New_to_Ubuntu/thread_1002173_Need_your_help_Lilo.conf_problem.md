---
title: "Need your help Lilo.conf problem"
date: 2008-12-04
forum: New to Ubuntu
---

### Post by Grim_Reper on 2008-12-04
Guys I need your help, and I think this is a rather difficult matter.

I have to partitions on my hdd one with vista and the other one with Backtrack 3 which uses Lilo boot-loader... I use the lilo boot-loader to select wich os i want to boot... 
Later I dicided to instal ubuntu but its a live usb with changes saving in the usb... i was messing arround in ubuntu and edited the lilo.conf that was in /media/disk/etc/ so i did gksudo gedit /media/disk/etc/lilo.conf
and made my changes, saved them and rebooted in backtrack and did lilo -v to commit changes to the MBR... When i tried booting back in backtrack there was a kernel panic... so i thought "damn screwd up" and dicided to boot again in my ubuntu live usb to edit lilo.conf again and revert all changes, but now my problem is lilo -v doesn't work in ubuntu... or at least i can't make it work... please guys i need your help this is really getting in my head...
Hope you guys can help me...

Grim Reaper

---

### Post by Grim_Reper on 2008-12-04
Guys Please its really important...

---

### Post by scorp123 on 2008-12-04
Google for "Super GRUB Disk" ... it's a small live distro which is specialised in bringing dead boot blocks back. The image doesn't do much else and therefore isn't too big. So you'd download "Super GRUB disk", burn it onto a CD and boot your dead PC with it. Once your back into Ubuntu or whatever other OS is installed you can use "lilo" from within there which should be easy once you get that far.

---

### Post by Grim_Reper on 2008-12-04
hey thanks for your help scorp123i i managed to find a solution booted in the live cd of backtrack 3 and tried to edit lilo and did lilo-v but it didn't work... so i remebered the chroot comand but i didn't know what it was for i just remebered that i used it once while installing backtrack to hdd... and then it come to me it probably is to instead of using the live cd get in the hdd install part...
so i did chroot /dev/sda6 /bin/bash and it worked i then tryed the lilo -v comand and it worked flawlessly

---

