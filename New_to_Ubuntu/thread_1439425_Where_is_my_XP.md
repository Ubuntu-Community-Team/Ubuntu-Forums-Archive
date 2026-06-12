---
title: "Where is my XP?"
date: 2010-03-26
forum: New to Ubuntu
---

### Post by Snoeck on 2010-03-26
Hi!

I have a major problem with booting my laptop. 
my computer has 2 major partitions: 50 GB for Windows XP and 200 GB for Ubuntu.

When I start my computer, it says "grub loading" but then immediately proceeds with starting up ubuntu, without giving me the choice in XP or Ubuntu.

Can someone help me?

Greetz!

---

### Post by halitech on 2010-03-26
once you load Ubuntu, open a terminal and run

```
sudo fdisk -l
```
and post the info here

---

### Post by Cork87 on 2010-03-26
In the file /boot/grub/menu.lst you can adjust the time out of grub so you have longer to view the menu.

---

### Post by philinux on 2010-03-26
> **Cork87 said:**
> In the file /boot/grub/menu.lst you can adjust the time out of grub so you have longer to view the menu.

Ok if he's got grub legacy, if he's got grub2 then the file to edit is /etc/default/grub. 

@snoeck when you boot press the esc key or the shift key to display grubs menu.

Open a terminal and use this. Tell us what come back.
```
apt-cache policy grub-pc
```

---

