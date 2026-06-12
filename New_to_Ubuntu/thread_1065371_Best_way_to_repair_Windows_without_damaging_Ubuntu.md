---
title: "Best way to repair Windows without damaging Ubuntu"
date: 2009-02-09
forum: New to Ubuntu
---

### Post by webmiester on 2009-02-09
Hi guys,

guess what?  My Windows XP patition crashed AGAIN.  It's no surprise really...

But what I hate is that eveytime I reinstall it using its CD, it would overwrite GRUB and the last time I did it, my Ubuntu wouldnt start anymore even after restoring GRUB.

What is the best way for me to restore/repair windows without damaging my UBUNTU partition or boot loader?  I know everyone with a dual boot experiences this knowing how unstable Windows is.

It's sad that I still have to be dependent on Windows because of certain hardware driver issues with linux...

Thanks so much.

---

### Post by jrusso2 on 2009-02-09
Make a copy of grub and place it on the Linux side.  Or just reinstall grub after Windows repair.

---

### Post by webmiester on 2009-02-09
> **jrusso2 said:**
> Make a copy of grub and place it on the Linux side.  Or just reinstall grub after Windows repair.

I used supergrub to reinstall GRUB before and it didnt work,  Is there a way for me to reinstll just GRUB using the Ubuntu installer CD?

---

### Post by webmiester on 2009-02-09
> **jrusso2 said:**
> Make a copy of grub and place it on the Linux side.  Or just reinstall grub after Windows repair.

BTW, how do I make a copy of grub and put it on the linux side?

---

### Post by 2hot6ft2 on 2009-02-09
You haven't given any info about the system like how many drives there are or anything. So if there is just 1 drive such as in a laptop it would be like this to restore Grub to your MBR, so if you boot your Live CD, open a terminal (Applications > Accessories > Terminal) and do:

```
sudo grub
grub> root (hd0,0)
grub> setup (hd0)
grub> quit

```
And that's all it should take.

If there is more than 1 drive then post the output of
```
fdisk -l
```
and
```
sudo grub
find /boot/grub/stage1
```
then you can use
```
grub> quit
```
to exit

---

