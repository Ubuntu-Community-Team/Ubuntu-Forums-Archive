---
title: "OS Selection"
date: 2011-03-13
forum: New to Ubuntu
---

### Post by SEECo on 2011-03-13
Hi Ubuntu Experts,

I need some help here. I was having Windows 7 on my laptop toshiba m45-s351, than i installed ubuntu in an other partition. After the installation of ubuntu I logged into ubuntu. Now I want to Log into my Windows 7. How any help would be strictly appreciated.And thanks in advance.

---

### Post by llamabr on 2011-03-13
Hi.  Does windows 7 still use ntfs?

[https://help.ubuntu.com/community/MountingWindowsPartitions](https://help.ubuntu.com/community/MountingWindowsPartitions)

---

### Post by SEECo on 2011-03-13
Yup............!

---

### Post by howefield on 2011-03-13
> **SEECo said:**
> After the installation of ubuntu I logged into ubuntu. Now I want to Log into my Windows 7.

What exactly do you want to do ?

Are you talking about booting into Windows 7, or mounting the windows partition so you can access the files on it, or maybe something else altogether ?

---

### Post by vnpifhf on 2011-03-13
Restart, you should see the Grub boot menu and you select your other operating system.
Good day!

---

### Post by SEECo on 2011-03-13
I want to boot into windows 7 but the grub screen do not appears

---

### Post by vnpifhf on 2011-03-13
are you sure you haven't put ubuntu on the whole hard drive?

---

### Post by sandyd on 2011-03-13
go to
applications -> accessories -> terminal

type in
```

sudo fdisk -l
```
post output.

when typing in the password, it will not show

---

### Post by lisati on 2011-03-13
OK. Assuming Windows is still there somewhere, you should be able to access it. Someone has already suggested taking a look at the output from **fdisk -l**, which will help us figure out if it's still there.

To access the grub menu, try holding down the shift key while you're booting. (Note: older versions of grub use the "esc" key)

---

### Post by Mark Phelps on 2011-03-13
When you install Ubuntu second on a PC that already has Windows, it does NOT automatically add entries to the GRUB menu.

Go into Ubuntu, open a terminal and enter "sudo update-grub".

When you reboot, you SHOULD get a GRUB menu.  If the Win7 selection still does not appear or does not work, then post back here.

---

### Post by SEECo on 2011-03-14
I tried every thing ran the command sudo fdisk -l, sudo update-grub, tried pressing. But nothing changed and I have ubuntu on a single partition.

---

