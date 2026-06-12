---
title: "US will not load on my computer"
date: 2009-05-17
forum: New to Ubuntu
---

### Post by PatrickMoore on 2009-05-17
i decided to retry Ubuntu studio. i installed and now im getting an error on bootup

clocksource tsp unstable.

im a little confused. is this a bug with U.S.?

---

### Post by Aaardwark on 2009-05-17
As far as I understand that means the kernel is detecting that it cannot rely on the computers clock to be constant.

I don't know if [this]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/190414") is your specific problem. But you can try their solution:
> You can tell it to use the HPET clocksource from the start by adding "clocksource=hpet" to your kernel command line. The kernel command line is specified in /boot/grub/menu.lst at the line starting with "# kopt=...".

---

### Post by PatrickMoore on 2009-05-17
Im not able to edit it seems. i tried editing while in grub as i cannot access my os and nothing is changing. is anyone else having this issue

---

### Post by Aaardwark on 2009-05-17
I found [this]("http://ubuntuforums.org/showthread.php?t=698211&page=2") other thread, where they explain all the way from grub:
> hi

I have this clocksource tsc unstable problem ...
i recently solved it ..

I have 1 ide and sata disk .. with HDMI enabled motherboard ASUS

in the grub screen I put

clocksource=hpet acpi=off noacpi

you can do it by ...pressing e ....

when u are done editing ..enter ... press b


then make this changes permanent ... got to /boot/grub/menu.list ...
you can edit the lines like mine ..


title Ubuntu 8.04.1, kernel 2.6.24-19-generic My Edition
root (hd0,0)
kernel /boot/vmlinuz-2.6.24-19-generic root=UUID=a4646 ro quiet splash xforcevesa clocksource=hpet acpi=off noacpi
initrd /boot/initrd.img-2.6.24-19-generic
quiet


title Ubuntu 8.04.1, kernel 2.6.24-19-generic
root (hd0,0)
kernel /boot/vmlinuz-2.6.24-19-generic root=UUID=a4647b17-16c6 ro quiet splash xforcevesa
initrd /boot/initrd.img-2.6.24-19-generic
quiet

title Ubuntu 8.04.1, kernel 2.6.24-19-generic (recovery mode)
root (hd0,0)
kernel /boot/vmlinuz-2.6.24-19-generic root=UUID=a4647b8-9846-b7f3a8dd16c6 ro single
initrd /boot/initrd.img-2.6.24-19-generic

title Ubuntu 8.04.1, memtest86+
root (hd0,0)
kernel /boot/memtest86+.bin
quiet

Hope it works! :)

---

