---
title: "Dual Boot Ubuntu 10.10 and Win7"
date: 2011-02-11
forum: New to Ubuntu
---

### Post by Muhnamana on 2011-02-11
Ok, I've tried this a couple of times and can't load Ubuntu.

Here's the scenerio, I have 3 partitions.
      /dev/sda1 = ntfs (Win7)
      /dev/sda2 = ext4 with the / mount point
      /dev/sda3 = swap space

I've some tutorials where I need a /boot partition as well and others where I just need the root partition.

At the bottom, there is a drop down box for you to select the device for boot loader installation.
Those options include /dev/sda, /dev/sda1 (Win7) and /dev/sda2.

Can anyone assist in what else I need to do to get the dual boot working? My first thought is to install the boot loader onto /dev/sda but I'm unsure. It keeps booting Win7 and can't get the option to load Ubuntu.

[B]***EDIT***
Sorry, I placed this thread in the wrong area. New thread listed in the Installation/Upgrade area.[/B]

---

### Post by cariboo on 2011-02-12
You need to install grub on the mbr of the first hard drive in order for it to work. Boot from the live CD and once at the desktop, open a terminal and type the following commands:

[LIST=1]
[*]sudo mount /dev/sda2 /mnt
[*]sudo mount -o bind /dev /mnt/dev
[*]sudo mount -o bind /sys /mnt/sys
[*]sudo mount -o bind /proc /mnt/proc
[*]sudo chroot /mnt
[/LIST]

Once at the root prompt, type:

```
grub-install /dev/sda
```

once that command is finished type:

```
update-grub
```

you should see the boot options after running the above command. Press Ctrl-d twice, and reboot.

---

