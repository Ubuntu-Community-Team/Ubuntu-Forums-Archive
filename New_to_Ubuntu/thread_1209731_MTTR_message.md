---
title: "MTTR message"
date: 2009-07-10
forum: New to Ubuntu
---

### Post by C. M .Hughes on 2009-07-10
I get the attached messages on every boot (see picture). 

I have tried editing /boot/grub/menu.lst so that it reads

title Ubuntu 9.04, kernel 2.6.28-11-generic
uuid 9a3ea422-4178-4359-9195-a69120ea5f87
kernel /boot/vmlinuz-2.6.28-11-generic root=UUID=9a3ea422-4178-4359-9195-a69120ea5f87 ro quiet splash nomtrr
initrd /boot/initrd.img-2.6.28-11-generic
quiet

but it has not helped. Does anyone have any ideas? Many thanks.

---

### Post by LewRockwell on 2009-07-10
> **C. M .Hughes said:**
> I get the attached messages on every boot (see picture). 

I have tried editing /boot/grub/menu.lst so that it reads

title Ubuntu 9.04, kernel 2.6.28-11-generic
uuid 9a3ea422-4178-4359-9195-a69120ea5f87
kernel /boot/vmlinuz-2.6.28-11-generic root=UUID=9a3ea422-4178-4359-9195-a69120ea5f87 ro quiet splash nomtrr
initrd /boot/initrd.img-2.6.28-11-generic
quiet

but it has not helped. Does anyone have any ideas? Many thanks.

looks like "nomtrr" gets called as a part of "video=vesafb:nomtrr" as opposed to just getting "thrown-in"

my first thought would be making sure your BIOS is up to date

.

---

### Post by C. M .Hughes on 2009-07-10
Thanks for the response. I tried putting it in like this:

kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=9a3ea422-4178-4359-9195-a69120ea5f87 ro quiet splash video=vesafb:nomtrr

Still the same screen. 

I'll look into my BIOS- thanks for the suggestions.

---

