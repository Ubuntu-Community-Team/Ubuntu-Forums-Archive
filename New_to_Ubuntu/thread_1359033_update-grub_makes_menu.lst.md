---
title: "update-grub makes menu.lst"
date: 2009-12-19
forum: New to Ubuntu
---

### Post by corti on 2009-12-19
[FONT=Arial]hello....
i[/FONT] just installed ubuntu 9.10 two days ago, as dual boot with xp...and i'm already in the middle of it...

actually all went well, but a small detail, which troubles my habits...ubuntu sets up the bootloader and the xp is lowest on the list....because i just begin with ubuntu i still will use xp as main platform for a while, and i want it to boot automatically.....

i looked in all the forums and found out that i would have to make a change in /etc/default/grub and set the default on the position where xp is....and then update-grub to make the* grub.cfg* file new.... only when i did the *update-grub*, it was looking for a menu.lst and asked if i want to let him make one...first i said no...nothing changed...then i said yes and it made a menu.lst....and now he does **this** after an update-grub:

Searching for GRUB installation directory ... found: /boot/grub
Searching for default file ... found: /boot/grub/default
Testing for an existing GRUB menu.lst file ... found: /boot/grub/menu.lst
Searching for splash image ... none found, skipping ...
Found kernel: /boot/vmlinuz-2.6.31-14-generic
Found GRUB 2: /boot/grub/core.img
Found kernel: /boot/memtest86+.bin
Updating /boot/grub/menu.lst ... done

it seems that the update-grub does not fit with grub2, instead of updating grub.cfg it makes a menu.lst, as it was usual in the old grub....but its definitly not possible, that there is an old ubuntu on my computer...Is there a possiblity to look at the script of update-grub or change it somehow?

---

### Post by Paqman on 2009-12-19
When you boot up, what actual version of Grub does it display? The version number will be at the top. The old Grub was 0.97 (I think), the new one should be 1.97.

It is possible that you've got Grub and Grub2 on the same system, although you should only end up with that if you upgraded. A fresh install should have got Grub2.

---

### Post by coffeecat on 2009-12-19
> **corti said:**
> it seems that the update-grub does not fit with grub2, instead of updating grub.cfg it makes a menu.lst, as it was usual in the old grub....but its definitly not possible, that there is an old ubuntu on my computer...Is there a possiblity to look at the script of update-grub or change it somehow?

On my Karmic system - a fresh install, not a dist-upgrade - /usr/bin/update-grub contains this short script:

```
#!/bin/sh -e
exec grub-mkconfig -o /boot/grub/grub.cfg "$@"
```... so 'update-grub' on a Karmic system *should* regenerate the grub2 grub.cfg file.

But the plots thickens. I discovered another update-grub at /usr/lib/grub-legacy/update-grub. I've looked inside. It's too long to post here, but that is indeed an old legacy grub update-grub that creates a menu.lst. However, it does not get invoked when I run 'sudo update-grub' and I have no idea what it is doing on my system.

Next thing. If I run:

```
whereis update-grub
```... I get as output ...

> update-grub: /usr/sbin/update-grub /usr/share/man/man8/update-grub.8.gzNo mention of /usr/lib/grub-legacy/update-grub. What do you get as the output of 'whereis update-grub' and what is the contents of your /usr/bin/update-grub? (If you have one.)

---

### Post by joes7 on 2009-12-19
StartUp Manager is your friend.

---

