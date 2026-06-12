---
title: "reinstalling grub"
date: 2009-10-27
forum: New to Ubuntu
---

### Post by sandyd on 2009-10-27
i used to do it a lot when i had my old computer, but now, im having a brain freeze.
 
i just recieved the win7 upgrade disk in the mail.
 
how do i reinstate grub into the mbr after the windows 7 upgrade completes?
 
p.s. does the upgrade even wipe the bootloader?

---

### Post by shadow120 on 2009-10-27
```
sudo update-grub
```

this will update the mbr but i dont think the windows 7 update will change the bootloader

---

### Post by philinux on 2009-10-27
> **carlee said:**
> i used to do it a lot when i had my old computer, but now, im having a brain freeze.
 
i just recieved the win7 upgrade disk in the mail.
 
how do i reinstate grub into the mbr after the windows 7 upgrade completes?
 
p.s. does the upgrade even wipe the bootloader?

Upgrade should not mess with mbr but who knows. If it does then...

If this is your Karmic install then you need to chroot from the live cd.

[http://www.ubuntu-inside.me/2009/06/howto-recover-grub2-after-windows.html](http://www.ubuntu-inside.me/2009/06/howto-recover-grub2-after-windows.html)

---

### Post by sandyd on 2009-10-27
> **philinux said:**
> Upgrade should not mess with mbr but who knows. If it does then...
 
If this is your Karmic install then you need to chroot from the live cd.
 
[http://www.ubuntu-inside.me/2009/06/howto-recover-grub2-after-windows.html](http://www.ubuntu-inside.me/2009/06/howto-recover-grub2-after-windows.html)
heres the confusion.
im not sure weather im using grub2 or the normal grub since i updated from jaunty to karmic.
 
and yes.... just as i thought... it destroyed grub....

---

### Post by philinux on 2009-10-27
Hi carlee,

Try this
```

grub-install -v
```

If it's grub2 you will get this.

```
root@philcb-desktop:/# grub-install -v
grub-install (GNU GRUB 1.97~beta4)
```

---

### Post by salingova on 2009-11-01
Hi guys,
I need help upgrading grub to the new version grub 2. I am trying to follow the instructions here [https://wiki.ubuntu.com/Grub2](https://wiki.ubuntu.com/Grub2), but when I get to the point I have to choose OK at the grub-pc configuration I don't know how to do that. Hitting enter doesn't do nor does a mouse click.
If you know how to do this pls give me some advice.
Thx

---

### Post by sandyd on 2009-11-01
> **salingova said:**
> Hi guys,
I need help upgrading grub to the new version grub 2. I am trying to follow the instructions here [https://wiki.ubuntu.com/Grub2](https://wiki.ubuntu.com/Grub2), but when I get to the point I have to choose OK at the grub-pc configuration I don't know how to do that. Hitting enter doesn't do nor does a mouse click.
If you know how to do this pls give me some advice.
Thx
the tab key should give you some help.

---

### Post by salingova on 2009-11-01
Thx a lot, I guess this knowledge is assumed to be known, but its really this small stuff that I always get stuck at when I'm trying to follow some tutorial :)

---

