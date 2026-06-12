---
title: "Error 15 help"
date: 2010-04-29
forum: New to Ubuntu
---

### Post by Vikapower on 2010-04-29
Hi everyone.
I'm quite unexperienced in Ubuntu and my sisters Dell inspiron 10 displays the famous error 15. I have read lots of lots of things on the net during theses 4-5 past days but didn't get any solution.

Ok so as said Dell Inspiron mini 10 with Ubuntu 8.04 LTS system shows the error 15 and to make a real picture of what's happening the computer starts normally then displays this error then I press 'enter' and appears :

```
Ubuntu 8.04.2, kernel 2.6.24-24-lpia
Ubuntu 8.04.2, kernel 2.6.24-24-lpia (recovery mode)
Ubuntu 8.04.2, kernel 2.6.24-24-lpia
Ubuntu 8.04.2, kernel 2.6.24-24-lpia (recovery mode)
System Restore
```

Whichever system I choose : 'file not found' anyway last night I successfully made a Live USB Ubuntu 9.10 with Unetbootin to access the computer since the Inspiron mini has no CDR/W player to find the problem **fdisk -l** gives me :
```
Disk  /dev/sda: 160.0 GB,  160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x2e3e8e76

Device boot   Start   End   Blocks   Id   Sytem
/dev/sda1    1    3    24066    de    Dell Utility
/dev/sda2    *    4    19213    15404325    83   Linux
/dev/sda3    19214    19457    1959930    lc    Hidden W95 FAT32  (LBA)

Disk /dev/sdb: 4022 MB, 4022337024 bytes
255 Heads, 63 sectors, 489 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00000000
```

I watched the **'menu.lst'** and informations related to its problems [...] Here it is (short) :
```
title  Ubuntu 8.04.2, Kernel 2.6.24-24-lpia
root  (hd0,1)
kernel  /boot/vmlinuz-2.6.24-24-lpia  ro  root=UUID=77eb26dc-768b-4e59-bf5a-bb0e8f20f746 acpi_osi=Linux  hpet=disabled quiet splash
initrd  /boot/initrd.img-2.6.24-24-lpia 
quiet

title  Ubuntu 8.04.2, Kernel 2.6.24-24-lpia (recovery mode)
root  (hd0,1)
kernel  /boot/vmlinuz-2.6.24-24-lpia  ro  root=UUID=77eb26dc-768b-4e59-bf5a-bb0e8f20f746 acpi_osi=Linux  hpet=disabled single
initrd  /boot/initrd.img-2.6.24-24-lpia

title  Ubuntu 8.04.2, Kernel 2.6.24-24-lpia
root  (hd0,1)
kernel  /boot/vmlinuz-2.6.24-24-lpia  ro  root=UUID=77eb26dc-768b-4e59-bf5a-bb0e8f20f746 acpi_osi=Linux  hpet=disabled quiet splash
initrd  /boot/initrd.img-2.6.24-24-lpia 
quiet

title  Ubuntu 8.04.2, Kernel 2.6.24-24-lpia (recovery mode)
root  (hd0,1)
kernel  /boot/vmlinuz-2.6.24-24-lpia  ro  root=UUID=77eb26dc-768b-4e59-bf5a-bb0e8f20f746 acpi_osi=Linux  hpet=disabled single
initrd  /boot/initrd.img-2.6.24-24-lpia

### END DEBIAN AUTOMAGIC KERNELS LIST

title System Restore
root  (hd0,2)
Chailoader  +1
boot
sudo cp  /boot/grub/menu.lst  /boot/grub.menu.lst.copy
sudo gedit  /boot/grub/menu.lst  /boot/grub.menu.lst.copy
```

Well I need someone with way much more experience than me to see what's going bad because I really don't get the solution.

I tried that solution already ([http://stringofthoughts.wordpress.com/2009/05/25/grub-error-15-debianubuntu/](http://stringofthoughts.wordpress.com/2009/05/25/grub-error-15-debianubuntu/)) but doesn't seem to work, I also read articles on the MBR defection and tried applying the solution to that nothing anyway [...] Is there something wrong ? :D

---

### Post by Vikapower on 2010-04-29
Hi everyone.
I'm quite unexperienced in Ubuntu and my sisters Dell inspiron 10 displays the famous error 15. I have read lots of lots of things on the net during theses 4-5 past days but didn't get any solution.

Ok so as said Dell Inspiron mini 10 with Ubuntu 8.04 LTS system shows the error 15 and to make a real picture of what's happening the computer starts normally then displays this error then I press 'enter' and appears :

```
Ubuntu 8.04.2, kernel 2.6.24-24-lpia
Ubuntu 8.04.2, kernel 2.6.24-24-lpia (recovery mode)
Ubuntu 8.04.2, kernel 2.6.24-24-lpia
Ubuntu 8.04.2, kernel 2.6.24-24-lpia (recovery mode)
System Restore
```

Whichever system I choose : 'file not found' anyway last night I successfully made a Live USB Ubuntu 9.10 with Unetbootin to access the computer since the Inspiron mini has no CDR/W player to find the problem **fdisk -l** gives me :
```
Disk  /dev/sda: 160.0 GB,  160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x2e3e8e76

Device boot   Start   End   Blocks   Id   Sytem
/dev/sda1    1    3    24066    de    Dell Utility
/dev/sda2    *    4    19213    15404325    83   Linux
/dev/sda3    19214    19457    1959930    lc    Hidden W95 FAT32  (LBA)

Disk /dev/sdb: 4022 MB, 4022337024 bytes
255 Heads, 63 sectors, 489 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00000000
```

I watched the **'menu.lst'** and informations related to its problems [...] Here it is (short) :
```
title  Ubuntu 8.04.2, Kernel 2.6.24-24-lpia
root  (hd0,1)
kernel  /boot/vmlinuz-2.6.24-24-lpia  ro  root=UUID=77eb26dc-768b-4e59-bf5a-bb0e8f20f746 acpi_osi=Linux  hpet=disabled quiet splash
initrd  /boot/initrd.img-2.6.24-24-lpia 
quiet

title  Ubuntu 8.04.2, Kernel 2.6.24-24-lpia (recovery mode)
root  (hd0,1)
kernel  /boot/vmlinuz-2.6.24-24-lpia  ro  root=UUID=77eb26dc-768b-4e59-bf5a-bb0e8f20f746 acpi_osi=Linux  hpet=disabled single
initrd  /boot/initrd.img-2.6.24-24-lpia

title  Ubuntu 8.04.2, Kernel 2.6.24-24-lpia
root  (hd0,1)
kernel  /boot/vmlinuz-2.6.24-24-lpia  ro  root=UUID=77eb26dc-768b-4e59-bf5a-bb0e8f20f746 acpi_osi=Linux  hpet=disabled quiet splash
initrd  /boot/initrd.img-2.6.24-24-lpia 
quiet

title  Ubuntu 8.04.2, Kernel 2.6.24-24-lpia (recovery mode)
root  (hd0,1)
kernel  /boot/vmlinuz-2.6.24-24-lpia  ro  root=UUID=77eb26dc-768b-4e59-bf5a-bb0e8f20f746 acpi_osi=Linux  hpet=disabled single
initrd  /boot/initrd.img-2.6.24-24-lpia

### END DEBIAN AUTOMAGIC KERNELS LIST

title System Restore
root  (hd0,2)
Chailoader  +1
boot
sudo cp  /boot/grub/menu.lst  /boot/grub.menu.lst.copy
sudo gedit  /boot/grub/menu.lst  /boot/grub.menu.lst.copy
```

Well I need someone with way much more experience than me to see what's going bad because I really don't get the solution.

I tried that solution already ([http://stringofthoughts.wordpress.com/2009/05/25/grub-error-15-debianubuntu/](http://stringofthoughts.wordpress.com/2009/05/25/grub-error-15-debianubuntu/)) but doesn't seem to work, I also read articles on the MBR defection and tried applying the solution to that nothing anyway [...] Is there something wrong ? :D

---

### Post by K.Mandla on 2010-04-29
Moved to Absolute Beginner Talk. Similar threads merged. ;)

---

### Post by Vikapower on 2010-04-29
> **K.Mandla said:**
> Moved to Absolute Beginner Talk. Similar threads merged. ;)
Thanks but why are there 2 same posts of mines...:smile: Still no answers ? :)

---

