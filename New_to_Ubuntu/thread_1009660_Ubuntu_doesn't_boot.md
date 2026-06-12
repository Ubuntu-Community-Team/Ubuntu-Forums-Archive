---
title: "Ubuntu doesn't boot"
date: 2008-12-12
forum: New to Ubuntu
---

### Post by ECas123 on 2008-12-12
okay so I tried installing XP then after I did, ubuntu didn't boot (something might have happend with GRUB, don't know) so I deleted the partition then tried booting back into Ubuntu but it didn't. Here's a screenshot of the partion editor. Am I doing anything wrong???
[IMG]http://i34.tinypic.com/esnia1.png[/IMG]

---

### Post by caljohnsmith on 2008-12-12
Sounds like you just need to restore Grub to your MBR, so if you boot your Live CD, open a terminal (Applications > Accessories > Terminal) and do:
```
sudo grub
grub> root (hd0,0)
grub> setup (hd0)
grub> quit
```
And that's all it should take. If not, let me know.

---

### Post by ECas123 on 2008-12-12
So I tried installing XP then deleteing the partion (keeping the unallocated space for later) but now Ubuntu doesn't boot. I messed with the flags and now don't know what to do. Here's a screenshot of the partition editor 
[IMG]http://i34.tinypic.com/esnia1.png[/IMG]

---

### Post by Jermcb on 2008-12-12
When you turn on the computer, do you get into the GRUB menu?

How did you get into ubuntu to take a screenshot of the partitions?

---

### Post by ECas123 on 2008-12-12
> **caljohnsmith said:**
> Sounds like you just need to restore Grub to your MBR, so if you boot your Live CD, open a terminal (Applications > Accessories > Terminal) and do:
```
sudo grub
grub> root (hd0,0)
grub> setup (hd0)
grub> quit
```
And that's all it should take. If not, let me know.

Yay! Thanks. Now I just need a tutorial on installing XP safely from Ubuntu

---

### Post by TJCIB on 2008-12-12
Installing Windows wipes away Grub.

I htink just the first part is good for you.
[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)

---

### Post by caljohnsmith on 2008-12-12
Did you try creating a primary NTFS partition with that empty space first using Ubuntu's gparted partition editor, and then installing XP? Or did you try installing XP to the empty space on the HDD? If you haven't tried making a partition first, I would give that a shot.

---

### Post by overdrank on 2008-12-12
Please do not create multiple threads on the same issue. Threads merged :)

---

