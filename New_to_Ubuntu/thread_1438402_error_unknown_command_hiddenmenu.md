---
title: "error: unknown command hiddenmenu"
date: 2010-03-24
forum: New to Ubuntu
---

### Post by chenlin on 2010-03-24
can anybody help me???
 
I tried to wrire menu.lst, my menu.lst looks like this:
 
[COLOR=blue]default=0[/COLOR]
[COLOR=blue]timeout=20[/COLOR]
[COLOR=blue]hiddenmenu[/COLOR]
[COLOR=blue]title Ubuntu[/COLOR]
[COLOR=blue]     root (hd0,3)[/COLOR]
[COLOR=blue]     linux /boot/vmliux....... ro root=/dev/sda3[/COLOR]
[COLOR=blue]     initrd /boot/initrd.........[/COLOR]
[COLOR=blue]title WindowsXP[/COLOR]
[COLOR=blue]     rootnoverify (hd0,1)[/COLOR]
[COLOR=blue]     chainloader +1[/COLOR]
 
but when I reboot ubuntu,I got this error:
[COLOR=black]GRUB loading.[/COLOR]
[COLOR=red]error:unknown command 'hiddenmenu'[/COLOR]
[COLOR=red]error:unknown command 'title'[/COLOR]
(hd0,3):Filesystem is ext2.
 
Can anybody help me to get rid of this problem?? Many thanks!!!

---

### Post by andrewthomas on 2010-03-25
If you post the output of the boot info script in your next reply and I can probably help you.


Boot Info Script courtesy of forum member meierfra
Page with instructions and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Be sure to highlight and use code tags (#) to make it easier to read  when you post the results.txt.

---

