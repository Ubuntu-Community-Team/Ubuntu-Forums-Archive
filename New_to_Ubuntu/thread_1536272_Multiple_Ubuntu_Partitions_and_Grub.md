---
title: "Multiple Ubuntu Partitions and Grub"
date: 2010-07-22
forum: New to Ubuntu
---

### Post by Stigmata13 on 2010-07-22
Hello. Recently, I have debated adding another partition with Ubuntu 8.04. I currently use Lucid, but my graphics card is better supported in this older version, and I intend to use it for some light gaming under wine (Diablo II Lord of Destruction, and Starcraft to be exact.)

Anyway, I was worried that when I created this second partition, it would wipe Grub 2 and install Grub. Is there anyway I can install 8.04 and keep Grub 2?

---

### Post by Rubi1200 on 2010-07-22
If you install 8.04 AFTER 10.04 it will install the older version GRUB-legacy. I am not 100% sure of this, but there may also be an option when you install 8.04 to not install the bootloader. This may or may not be the answer.

But, the solution, as far as I know, is to simply reinstall GRUB2.

[https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB%202](https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB%202)

In any event, I would wait and see what others suggest before you do this.

---

### Post by -kg- on 2010-07-22
There is a method of installing another distro without replacing GRUB in the Master Boot record (the GRUB that you boot from).

When you go through the installation (will you be using Manual partitioning or "Side By Side" installation?), at the very last screen in the installation process, where it shows you what changes are going to be made to your hard drive, there is a button (bottom right, I think) that says "Advanced."

Clicking on that button will take you to a screen where you can elect where to install GRUB.  You will need to know the partition in which you are going to install 8.04 (sda5, sda6, etc.) and cause it to install GRUB in the root partition of your Hardy installation.  That will leave GRUB2 in the MBR of your drive.

When you reboot, you will not see Hardy as an option.  You will need to log back in to Lucid, pull up the terminal, and type:

```
sudo update-grub
```

That will cause Lucid's GRUB to detect Hardy's GRUB in it's partition, and when you reboot you should have Hardy in the menu as well.

Be it known, though, that when you update Hardy's kernel, it will not be reflected in Lucid's menu options.  You will have to run the above command every time you update your kernel in Hardy in order to detect it.

---

