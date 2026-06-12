---
title: "problems booting after a month"
date: 2010-12-29
forum: New to Ubuntu
---

### Post by kingle502 on 2010-12-29
The first time I downloaded Ubuntu I would boot off a disc. after a month or so when the computer started the menu showing  my options of Vista or Ubuntu (10.10 I think) When I choose Ubuntu it cycle through showing "Toshiba" then comes back to the same menu. It will boot to the Vista and run.

  I ended up having to reload Ubuntu but bypassed the CD and booted up through the hard drive. Things have worked fine for a month then again the same problem happened again.

  I would just reload it again but I have so much saved info that it is a pain. I am a real newbie to Ubuntu and being older I am not savvy at all with computers. So the help needs to be easy to understand.

                                   Thanks, mark

---

### Post by cariboo on 2010-12-29
I looks like you have a problem with grub. I would suggest you use the Live CD to repair it. Boot from the Live CD and once at the desktop, open an Applications-Accessories->Terminal and type the following commands:

```
sudo fdisk -l
```

Take note of which partiton Ubuntu is on. Next in the same terminal type the following commands and press enter after each one:

[list=1]
[*]sudo mount /dev/sdXx /mnt
[*]sudo mount -o bind /dev /mnt/dev
[*]sudo mount -o bind /sys /mnt/sys
[*]sudo mount -o bind /proc /mnt/proc
[*]sudo chroot /mnt
[/list]

Where /dev/sdXx = your Ubuntu partititon. Next at the prompt type:

```
grub-install /dev/sda
```

Once the above command has finished running type:

```
update-grub
```

You should see a listing of your operating systems are the above command has run. Once things are finished, press Ctrl-D twice then reboot your system.

---

