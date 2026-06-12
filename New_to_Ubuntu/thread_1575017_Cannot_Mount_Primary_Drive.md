---
title: "Cannot Mount Primary Drive"
date: 2010-09-15
forum: New to Ubuntu
---

### Post by Swan_Htet_Aung on 2010-09-15
Hello everyone,

I have faced with two problems in "Lucide"

1- Cannot mount my C: Drive [---Displayed Error is in the Attachment---]
2- I can't see my boot manager at the start up of the windows. So that, I can't Access to my Windows XP. It automatically loaded the Ubuntu.

---

### Post by amjjawad on 2010-09-15
> **Swan_Htet_Aung said:**
> Hello everyone,

I have faced with two problems in "Lucide"

1- Cannot mount my C: Drive
2- I can't see my boot manager at the start up of the windows. So that, I can't Access to my Windows XP. It automatically loaded the Ubuntu.

1- Where exactly did you install Ubuntu? which drive?
2- What do you mean it automatically loaded to Ubuntu? don't you have a list of booting options to load from at the startup?

---

### Post by garvinrick4 on 2010-09-15
Run this in a terminal in Ubuntu and copy and paste to this thread:
```
sudo fdisk -l
``` (small -L)
```
sudo blkid
``` (second letter small L)

---

### Post by Swan_Htet_Aung on 2010-09-16
Thanks for the reply amjjawad and garvinrick4


> **amjjawad said:**
> 1- Where exactly did you install Ubuntu? which drive?
2- What do you mean it automatically loaded to Ubuntu? don't you have a list of booting options to load from at the startup?

1- I have installed Ubuntu on my D:/ (and my Windows is on C:/)

2- Yes, there is no booting options at the startup. (I have found some solutions to use grub(2) but I can't fixed it)

&

@garvinrick4
Nothing happen!

---

### Post by Swan_Htet_Aung on 2010-09-17
Bump!

anyone?

---

