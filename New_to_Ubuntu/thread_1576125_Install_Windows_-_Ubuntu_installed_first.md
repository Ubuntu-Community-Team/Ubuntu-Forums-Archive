---
title: "Install Windows - Ubuntu installed first"
date: 2010-09-16
forum: New to Ubuntu
---

### Post by jkurtisr32 on 2010-09-16
So...

I've come across many guides regarding the installation of Windows on a computer with Ubuntu already installed. It looks like you need to go through all of these steps to recover the Grub because it gets destroyed during the new installation.

I am trying to install Windows on a completely separate HDD. Do I need to follow the same steps to preserve/recover the Grub even though I will be installing Windows on a separate HDD?

---

### Post by ubunterooster on 2010-09-16
If you take out the Ubuntu drive, install Windows, and stick the Ubuntu drive back in. Then no.

---

### Post by jkurtisr32 on 2010-09-16
> **ubunterooster said:**
> If you take out the Ubuntu drive, install Windows, and stick the Ubuntu drive back in. Then no.

Thanks, dude. I'm going to get on that now.

Anyone happen to know how to configure the Grub to automatically give me the option of which op sys to boot into at startup?

---

### Post by ubunterooster on 2010-09-16
I'm current;y posting via windows so I don't know the exact name but you want the utility named something similar to "startup-manager"

---

### Post by jtarin on 2010-09-16
> **jkurtisr32 said:**
> Thanks, dude. I'm going to get on that now.

Anyone happen to know how to configure the Grub to automatically give me the option of which op sys to boot into at startup?Once you have installed Windows and returned your Ubuntu drive to your machine boot into Ubuntu and run ```
sudo update-grub

```You should see if your Windows install is detected at that point and if it is then Ubuntu and Windows will be available from the Grub2 boot menu at the start.Make sure your Ubuntu drive is set to first bootin the bios.

---

### Post by jkurtisr32 on 2010-09-17
> **jtarin said:**
> Once you have installed Windows and returned your Ubuntu drive to your machine boot into Ubuntu and run ```
sudo update-grub

```You should see if your Windows install is detected at that point and if it is then Ubuntu and Windows will be available from the Grub2 boot menu at the start.Make sure your Ubuntu drive is set to first bootin the bios.

Thanks for the help.

-Kurt

---

### Post by jtarin on 2010-09-17
Did it work OK?

---

### Post by jkurtisr32 on 2010-09-17
> **jtarin said:**
> Did it work OK?

I think I ****ed something up. I set my Ubuntu drive as the first boot device, but the computer would always boot Windows first. This would happen even if I selected my Ubuntu drive manually at startup.

Luckily, my Ubuntu installation was brand new, so I just took the bitch route and installed it again after Windows. Yeah... I know.

EDIT: The grub2 did start properly when I booted into Ubuntu, and the update of the grub had identified the windows install. However, the only way to get the computer to boot Ubuntu was to remove the Windows drive

---

### Post by macem29 on 2010-09-17
> **jkurtisr32 said:**
>  so I just took the bitch route and installed it again after Windows. Yeah... I know. :D

the beauty of an OS that you can stick in, in a half hour

---

