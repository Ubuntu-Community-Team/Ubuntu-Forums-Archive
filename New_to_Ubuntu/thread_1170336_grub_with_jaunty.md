---
title: "grub with jaunty"
date: 2009-05-26
forum: New to Ubuntu
---

### Post by Arthur Millar on 2009-05-26
i have a problem after upgrading 
my dual boot went sour 
this is my list 

```

# sample /boot/grub/menu.lst entry for memtest86
#
# This example assumes the contents of /boot is on the root partition.
# If your /boot is on its own partition, remove /boot from the 'kernel' line.

title  memtest86+
root   (hd0,0)
kernel /boot/memtest86+.bin

title  memtest86+ (serial console 115200)
root   (hd0,0)
kernel /boot/memtest86+.bin console=ttyS0,115200n8

```

i have tried adding this frommy old menu.list
```

# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sdb1
title Windows Vista (loader)
root (hd1,0)
savedefault
makeactive
map (hd0) (hd1)
map (hd1) (hd0)
chainloader +1 
```
has somthing ghanged with grub?

---

### Post by alphacrucis2 on 2009-05-26
> **Arthur Millar said:**
> i have a problem after upgrading 
my dual boot went sour 
this is my list 

```

# sample /boot/grub/menu.lst entry for memtest86
#
# This example assumes the contents of /boot is on the root partition.
# If your /boot is on its own partition, remove /boot from the 'kernel' line.

title  memtest86+
root   (hd0,0)
kernel /boot/memtest86+.bin

title  memtest86+ (serial console 115200)
root   (hd0,0)
kernel /boot/memtest86+.bin console=ttyS0,115200n8

```

i have tried adding this frommy old menu.list
```

# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sdb1
title Windows Vista (loader)
root (hd1,0)
savedefault
makeactive
map (hd0) (hd1)
map (hd1) (hd0)
chainloader +1 
```
has somthing ghanged with grub?


Mine just has:

```
title		Windows Vista/Longhorn (loader)
rootnoverify	(hd0,0)
savedefault
makeactive
chainloader	+1
```

i.e Windows is located on the first partition of hd0. Yours seems to be looking for Windows on hd1 but maybe those map statements are swapping it around. What happens if you drop those out?

---

### Post by Arthur Millar on 2009-05-26
> **alphacrucis2 said:**
> Mine just has:

```
title		Windows Vista/Longhorn (loader)
rootnoverify	(hd0,0)
savedefault
makeactive
chainloader	+1
```

i.e Windows is located on the first partition of hd0. Yours seems to be looking for Windows on hd1 but maybe those map statements are swapping it around. What happens if you drop those out?

i tried that setting 
```
title		Windows Vista/Longhorn (loader)
rootnoverify	(hd1,0)
savedefault
makeactive
chainloader	+1
```

no change

---

### Post by presence1960 on 2009-05-26
I am assuming you can't boot to windows correct? your original post didn't exactly spell out your problem. If this is the case run in terminal ```
sudo fdisk -l
``` & ```
gksu gedit /boot/grub/menu.lst
``` Post the output of both commands here.

---

### Post by ibuclaw on 2009-05-26
Are you booted into Ubuntu now?

If so, backing up your menu.lst file and starting a fresh one could be the way to go in resolving this.

```
sudo mv /boot/grub/menu.lst /boot/grub/menu.lst.old
sudo update-grub

```

Also, could you post the output of the following:
```
sudo fdisk -l
```

Regards
Iain

---

### Post by Arthur Millar on 2009-05-26
wow dont i feel dumb lol i was editing the wrong file to begin with 
thanks 

SOLVED

---

### Post by presence1960 on 2009-05-26
great!!

---

