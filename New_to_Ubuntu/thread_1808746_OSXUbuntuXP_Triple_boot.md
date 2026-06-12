---
title: "OSX/Ubuntu/XP Triple boot"
date: 2011-07-20
forum: New to Ubuntu
---

### Post by rchavez3 on 2011-07-20
Hi so i installed ubuntu on an intel based mac (10.6.1) and i was previously running windows xp and mac osx simultaneously and used refit as a bootloader. Deciding that i wanted a triple boot i burned a live ubuntu disk and used gparted to resize my mac partition to make space for an ubuntu installation. after resizing and making about 30GB available for ubuntu and using it as an ext4 type and reformatting it and also making a 1GB available partition for a swap and installing the bootloader on ext4 partition (where ubuntu is installed) i restarted my computer to see if it had installed successfully but when my refit menu came up and i selected to boot of the linux partition the grub menu pops up and shows me all three partitions and again i select ubuntu but this time when i select ubuntu and the system tries to boot all i get is a black screen with an underscore at the top left hand corner and it just sits there blinking forever......Can some guru help me please?????????????

---

### Post by skatinjj on 2011-07-20
I would imagine you do not need grub as you already have a boot loader.  The blinking underscore usually means it can not find OS files to boot from.

As for a solution, I am not 100 percent certain right now.

---

### Post by rchavez3 on 2011-07-21
Ok so i found that by changing the boot parameters from --quite splash to acpi=off it worked (I HAVE NO IDEA WHY). So now Ubuntu is running but do i have to keep doing this every time that i boot into ubuntu or can i make this a permanent change in some boot file in ubuntu so that it does this automatically?

---

### Post by skatinjj on 2011-07-21
[ubuntuforums.org/showthread.php?t=1671333]("ubuntuforums.org/showthread.php?t=1671333")

---

