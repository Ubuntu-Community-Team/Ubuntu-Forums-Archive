---
title: "Dual booting: change the booting order"
date: 2009-03-21
forum: New to Ubuntu
---

### Post by emmwee on 2009-03-21
I have dual booting windows / ubuntu (installation with wubi). After turning on my pc, I have to choose one of them. If I loose time the systems starts the first one.
Actually the first one is "Microsoft Windows Vista" (probably because it comes before "Ubuntu" in the alphabet). How can I change this (I mean: how can I get Ubuntu as the first one in the list so that the system starts Ubuntu when I loose time ...)?

---

### Post by blastus on 2009-03-21
sudo gedit /boot/grub/menu.lst

You should see a line in the file like this...

default		0

The entry number (in the above case it's 0) tells GRUB (the bootloader) which entry to boot to by default if you don't interact with the bootloader.

If you look closely further down in the menu.lst file you should be able to determine the entry that corresponds to Ubuntu. The entry number is simply the ordinal number of the entry, for example, the first entry is 0, the second is 1 etc...

On my system the first entry is this...

title		Ubuntu 8.10, kernel 2.6.27-11-generic
uuid		83e51c75-707e-4d91-ad85-2985cf83eba0
kernel		/vmlinuz-2.6.27-11-generic root=/dev/mapper/sda3_crypt ro quiet splash 
initrd		/initrd.img-2.6.27-11-generic
quiet

...so "default 0" on my system will boot to the entry "Ubuntu 8.10, kernel 2.6.27-11-generic" by default.

---

### Post by emmwee on 2009-03-21
I opened the file. I found "default 0", a lot of comments and towards the end of the file
> title		Ubuntu 8.10, kernel 2.6.27-11-generic
root		()/ubuntu/disks
kernel		/boot/vmlinuz-2.6.27-11-generic root=UUID=ECE6AC8FE6AC5B98 loop=/ubuntu/disks/root.disk ro ROOTFLAGS=syncio quiet splash 
initrd		/boot/initrd.img-2.6.27-11-generic
and so on.
Maybe the determinating lines are the last ones? Here they are:
> ### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Windows Vista/Longhorn (loader)
root		(hd0,0)
savedefault
chainloader	+1


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda2
title		Windows Vista/Longhorn (loader)
root		(hd0,1)
savedefault
chainloader	+1

I'm a bit afraid to change something ...

---

### Post by lisati on 2009-03-21
I'm not sure if modifying menu.lst will work in all circumstances: on my vista laptop I currently have Ubuntu installed "within Windows" (Wubi'ed?) - the boot order on this machine is controlled by the Windows bootloader, which presents Vista first and Ubuntu second. Grub is only invoked if I select Ubuntu.

---

### Post by hlo on 2009-03-21
look at what is before the DEBIAN line
this is how my menu.lst looks 

```
## ## End Default Options ##

title		Ubuntu 8.10, kernel 2.6.27-13-generic (on /dev/sda11)
root		(hd0,10)
kernel		/boot/vmlinuz-2.6.27-13-generic root=UUID=a525913e-9545-4d4d-87f0-374ad4164b6f ro splash vga=775
initrd		/boot/initrd.img-2.6.27-13-generic

title		Ubuntu 8.04, memtest86+
root		(hd0,10)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST
# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root

# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Windows NT/2000/XP (loader)
root		(hd0,0)
savedefault
makeactive
chainloader	+1

```

so default = 0 would boot Ubuntu (the first title entry), default = 1 the memory test and default = 2 would boot to windows

be careful though, a mistake can screw up system boot

---

