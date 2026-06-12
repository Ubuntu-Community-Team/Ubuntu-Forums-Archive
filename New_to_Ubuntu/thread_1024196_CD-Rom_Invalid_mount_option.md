---
title: "CD-Rom Invalid mount option"
date: 2008-12-28
forum: New to Ubuntu
---

### Post by Dontechjuan on 2008-12-28
Hi, I was trying to get a game to install and and was having difficulty, so I posted a question on these forums. Someone replied that I needed to mount the drive with the  "unhide option". But I did not know what that is or how to do it, so I replied back for information on how to do it. After more than 24 hours without a reply I decided to try to figure it out on my own (I know I know big mistake). I found a menu on the cd-rom drive that had an item on the list called "mount options" and it had an empty white box next to it. So I decided to type "unhide" in the box. Then I umounted and tried to remount it. Now it will not mount the drive saying "Invalid mount option: Unable to mount". and now I can not find the mount options again. I tried unplugging both power and the data cable from the cd-rom and booting the computer several times trying to get the drive to reset back to default. That did not work and now I don not know what else to do. BTW it did occur to me first to try the file option of "show all hidden files and folders", but that was not what they meant by "unhide option".

---

### Post by taurus on 2008-12-28
Can you post your /etc/fstab?

Applications -> Accessories -> Terminal
```
cat /etc/fstab
```

---

### Post by Dontechjuan on 2008-12-28
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=a0abd2e7-0509-4dce-9a31-6f02d485a3a3 /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda5
UUID=088290cb-c3b5-4c60-95a2-bf7816cca0d1 none            swap    sw              0       0
/dev/hda        /media/cdrom0   udf,iso9660 user,noauto,exec 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec 0       0

---

### Post by mc4man on 2008-12-28
While I'm surprised it had effect on a cdrom drive try this (usually for fixing internal drives or volumes in same situation -entering invalid mount point or option

in terminal
```
gconf-editor
```

Expand the system tree, then the drive tree and or volume tree.
Look for an entry(s), if you find any highlight and see if there is one showing "mount_options [unhide]" (or whatever you entered

If so r. click on the entry (the option) and 'edit key', then click on the 'value' -> remove.

---

### Post by Dontechjuan on 2008-12-28
That did it. OMG thank you man I really appreciate it. Its no wonder you have been thanked 410 times lol.

---

### Post by Dontechjuan on 2008-12-28
maybe you can help me with my original problem as well. i was trying to get World of Warcraft wrath of the lich king (wotlk) installed through wine. i had already installed the original WoW and the first expansion Burning Crusade and had been playing it for a couple of weeks. Now i have wotlk and every time i clicked the installer.exe or used the terminal /media/"lich king"/installer.exe both methods show this message "Installer data not found" I was told be someone on the forums that i need to get the tome files unhide so he said i have to mount the drive using the "unhide option". unfortuatly i have not been using ubuntu long and am almost completely terminal illiterate lol. so i have no idea how to do that. somwbody said to type this in

 "sudo mount -o ro,unhide,uid=1000,gid=1000 /dev/cdrom /media/cdrom0/

Make sure you have unmounted the drive first with umount. then run this it should get ya going."
 
I tried entering it as its shown and i get this message "Mount: special device dev/cdrom does not exist" i checked the file and sure enough its not there, its in the media file with cdrom0 so i typed it in like this 

"sudo mount -o ro,unhide,uid=1000,gid=1000 /media/cdrom /media/cdrom0/"

and it says this "mount: /media/cdrom0 is not a block device" I wonder if it matters that in the media folder with cdrom file and cdrom0 file is the file with the name "lich king" so i placed the name in the terminal command like

"sudo mount -o ro,unhide,uid=1000,gid=1000 /media/cdrom /media/"lich king"/"

I got this message "mount: mount point /media/lich king does not exist" yet i open the media file and there is a file named "lich king" so i have no idea what I'm doing wrong. So plz help me and remember that im terminal illiterate so plz lead me through step by step with "copy paste" terminal commands. thank you.

---

### Post by Dontechjuan on 2008-12-28
I got the tome files shown using the unhide option and the installer finally runs. I click install and it goes to the select language screen. ok select english and click ok and it goes to the End User agreement and it loads the window boarder and the agrre disagree buttons but the text is gone and it freezes up and I have to force quit it. Does anyone know how to fix this?

---

