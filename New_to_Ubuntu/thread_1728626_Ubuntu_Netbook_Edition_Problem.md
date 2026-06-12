---
title: "Ubuntu Netbook Edition Problem"
date: 2011-04-14
forum: New to Ubuntu
---

### Post by ossBASHA on 2011-04-14
Hello everyone,

I'm looking at installing Ubuntu NBE, however I went through the setup process numerous times and got stuck where I have to fill in my Name, User name, password etc. It reads "ready when you are" at the bottom of the screen and all my information is properly inputted, however it will not allow me to click "forward". I am 100% positive that I am entering my info properly. 

Help!

---

### Post by miradus on 2011-04-14
> **ossBASHA said:**
> Hello everyone,

I'm looking at installing Ubuntu NBE, however I went through the setup process numerous times and got stuck where I have to fill in my Name, User name, password etc. It reads "ready when you are" at the bottom of the screen and all my information is properly inputted, however it will not allow me to click "forward". I am 100% positive that I am entering my info properly. 

Help!

Hey there! Are you booting from a CD or Flash Drive? What steps did it allow you to complete in the installation process?

---

### Post by K_45 on 2011-04-14
Can you post a screenshot?

---

### Post by ossBASHA on 2011-04-14
> **miradus said:**
> Hey there! Are you booting from a CD or Flash Drive? What steps did it allow you to complete in the installation process?

I'm booting from a flash drive. Here's a screenshot:

[IMG][[img]http://www.freeimagehosting.net/uploads/th.5e480bcf28.png[/img]](http://www.freeimagehosting.net/image.php?5e480bcf28.png)[/IMG]

---

### Post by K_45 on 2011-04-14
Choose Require My Password to Log in. You can change it later. That should allow you to move forward.

---

### Post by ossBASHA on 2011-04-14
> **K_45 said:**
> Choose Require My Password to Log in. You can change it later. That should allow you to move forward.

I tried that before and it didn't work. What am I supposed to select for "mount point" when creating a partition? I think I selected /boot.

---

### Post by K_45 on 2011-04-15
As a basic manual partitioning scheme you should select:

/ as root, ext4 15GB or so (format/primary)

swap, double your RAM (primary)

/home, ext4 rest of the disk (format/primary)

You may need to specify a /boot partition if required (such as a server), but this isn't required right now.

---

### Post by 3rdalbum on 2011-04-15
No capital letters or spaces for your username. And the mount point for your main Ubuntu partition must be /; /boot only holds the bootloader, but / holds everything.

---

### Post by ossBASHA on 2011-04-16
Problem solved. I created the two separate partitions "/" and "/boot" and used a lower case username.

Thanks guys!

---

