---
title: "Test drive ubuntu"
date: 2009-10-27
forum: New to Ubuntu
---

### Post by callender on 2009-10-27
Hello

As a "newby" (to both Unix and ubuntu), I would like to try out ubuntu, but don't want to overwrite my Windows XP installation.

What is the best way of test-driving this software? Can it be done from a pen-drive? 

Whichever way, how?

Thanks
Tony

---

### Post by kellemes on 2009-10-27
> **callender said:**
> Hello

As a "newby" (to both Unix and ubuntu), I would like to try out ubuntu, but don't want to overwrite my Windows XP installation.

What is the best way of test-driving this software? Can it be done from a pen-drive? 

Whichever way, how?

Thanks
Tony

Just boot the livesystem from the installdisk.

---

### Post by mcduck on 2009-10-27
You can simply burn the Ubuntu Desktop CD-image to a disk and start your computer with that CD, or use a program like [Unetbootin]("http://unetbootin.sourceforge.net/") to create a bootable flash drive with the image.

Which ever way you choose, booting from the CD/flash drive will bring you to working Ubuntu desktop that you can freely try to see if you ike it and if all your hardware works correctly. There's also icon on the desktop that allows you to start the installer, if you decide to install Ubuntu permanently on your computer.

It's also possible to just insert the Desktop CD while you are in Windows, and use Wubi to install Ubuntu into a file inside your Windows install. This will give you almost the same results as a separate Ubuntu install (all disk access will be a bit slower than on a separate install because Ubuntu will have to work through both it's own and the  Windows filesystem), but you won't have to mess with your drive partitions and Ubuntu can be uninstalled like any other Windows program.

Edit: I'd say using a flash drive is the best way to test Ubuntu, the CD comes next and installing inside Windows would be a good choice only if even after testing it from a live setup you are not sure if you want to install it or not.

---

### Post by martrn on 2009-10-27
> **callender said:**
> As a "newby" (to both Unix and ubuntu), I would like to try out ubuntu, but don't want to overwrite my Windows XP installation.What is the best way of test-driving this software? Can it be done from a pen-drive? Whichever way, how?

Yes installing ubuntu to a pen drive is the best way of "test-driving" ubuntu.  It is best if you install to a pen drive of 2GB or over and use USB1.1 or 2.0(better) while "test-driving" ubuntu.  See [http://unetbootin.sourceforge.net/]("http://unetbootin.sourceforge.net/") for installation instructions on how to install ubuntu to a pen drive. Format the drive for reiserfs (only for pen drive) for best usb performance.

---

### Post by raprap30 on 2009-10-27
Or, you could try using Wubi. :) Which is a fully fletched Ubuntu distro, except for insignificantly lower disk read speeds.

---

### Post by martrn on 2009-10-27
> **raprap30 said:**
> Or, you could try using Wubi.

raprap30 just took a leave of his senses  :frown: .

---

### Post by raprap30 on 2009-10-27
> **raprap30 said:**
>  :) Which is a fully fletched Ubuntu distro, except for insignificantly lower disk read speeds.

I edited it... :popcorn:

---

### Post by martrn on 2009-10-27
> **raprap30 said:**
> I edited it... 

raprap30 just regained his senses..  [though should read significantly]

---

### Post by raprap30 on 2009-10-27
Haha, I have woken up from my deep slumber. I was *Sleep-typing*...

---

### Post by raprap30 on 2009-10-27
> **martrn said:**
> [though should read significantly]

I was serious, I experience not much difference in speed. But yes, I know, in *theory* the difference in speed is supposed to be **epic slow**.

---

### Post by LewRockwell on 2009-10-27
wubi has received mixed reviews

some have reported catastrophic failures

back-up, Back-up, BACK-UP

as always, your mileage may vary

.

---

