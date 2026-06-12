---
title: "multi install pendrive"
date: 2010-06-23
forum: New to Ubuntu
---

### Post by manowar689 on 2010-06-23
ok heres the thing i work alot with the repair of windows computers so i successfully created a multi os install pendrive with grub4dos a fat 32 formatted pendrive it has the following 

1: windows 7 installer 
2: windows xp installer 
3: windows xp live 
4: ubuntu linux 

the problem is i cant get the ubuntu option to work i have the contents of the cd saved in a folder called ubuntulive so its location is x:/ubuntulive if it were a windows comp im more then willing to answer questions to and this is the menu.lst 
```

color black/red red/black
timeout 10
default /default

title Windows XP
map --unmap=0:0xff
map --unhook
savedefault
find --set-root --ignore-cd /usbdrive.tag
configfile /winsetup.lst

title Windows XP LIVE
map --unmap=0:0xff
map --unhook
root (hd0,0)
chainloader /minint/setupldr.bin

# ubuntu linux live/installer
title ubuntu Linux 
root=(hd0,0)
linux  ubuntulive/casper/vmlinuz 
initrd ubuntulive/casper/initrd

title Windows 7
map --unmap=0:0xff
map --unhook
root (hd0,0)
chainloader /BOOTMGR

```

THX if you help its bugging me to death :lolflag:

---

