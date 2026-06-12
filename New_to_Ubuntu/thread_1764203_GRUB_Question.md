---
title: "GRUB Question???"
date: 2011-05-21
forum: New to Ubuntu
---

### Post by TAspr on 2011-05-21
Hello, I installed Ubuntu alongside of Windows7 and I have a question.  It reboots, then gives me a choice of either Windows 7 or Ubuntu; with that said, is that a form of a GRUB menu since it was installed alongside of Windows, or something else?  Is GRUB a utility that only shows up when installing Ubuntu on a separate drive?

Is there a way to get rid of the countdown timer and manually choose Windows7 or Ubuntu?

---

### Post by scradock on 2011-05-21
> **TAspr said:**
> Hello, I installed Ubuntu alongside of Windows7 and I have a question.  It reboots, then gives me a choice of either Windows 7 or Ubuntu; with that said, is that a form of a GRUB menu since it was installed alongside of Windows, or something else?  Is GRUB a utility that only shows up when installing Ubuntu on a separate drive?

Is there a way to get rid of the countdown timer and manually choose Windows7 or Ubuntu?

Use the up/down arrow keys to select one or the other, then hit "enter".

---

### Post by TAspr on 2011-05-21
> **scradock said:**
> Use the up/down arrow keys to select one or the other, then hit "enter".

To get rid of the countdown?

---

### Post by Lateralis on 2011-05-21
Grub is the [**GR**and **U**nified **B**ootloader]("http://www.gnu.org/software/grub/"), which is one of a few bootloaders you can user to boot a Linux or dual boot system.  It consists of a small program which sits in the MBR and looks for configuration files in the /boot/grub directory of your Ubuntu installation.  Without these configuration files grub will not work. 

So in this sense, Grub is a utility which enables you to boot your system.  In every Linux distribution that I can think of, Grub is installed by default during the installation of the OS to the hard drive.  Without it, you could not boot your Linux system.  

As for getting rid of the timer, the default countdown time is 10 seconds.  If you hit a key such as a down arrow, that countdown is suspended, so you can look at the grub menu as long as you like.  You can change the default time and the default highlighted menu entry to suit your needs.  Check out the grub 2 wiki link in my signature for more info. =)

---

### Post by TAspr on 2011-05-21
> **Lateralis said:**
> Grub is the [**GR**and **U**nified **B**ootloader]("http://www.gnu.org/software/grub/"), which is one of a few bootloaders you can user to boot a Linux or dual boot system.  It consists of a small program which sits in the MBR and looks for configuration files in the /boot/grub directory of your Ubuntu installation.  Without these configuration files grub will not work. 

So in this sense, Grub is a utility which enables you to boot your system.  In every Linux distribution that I can think of, Grub is installed by default during the installation of the OS to the hard drive.  Without it, you could not boot your Linux system.  

As for getting rid of the timer, the default countdown time is 10 seconds.  If you hit a key such as a down arrow, that countdown is suspended, so you can look at the grub menu as long as you like.  You can change the default time and the default highlighted menu entry to suit your needs.  Check out the grub 2 wiki link in my signature for more info. =)


Ok, I will check it out.  My issue is not so much changing the selection, but if I turn on the PC, I did not want to go into either, but make a choice when I came back to it.  I know, small issue, but that is what I wanted.

---

### Post by Lateralis on 2011-05-21
As I say, Grub is installed by default during the installation of Ubuntu.  When you boot into your new dual boot system you will be presented with a menu that will list all of your possible boot options, in this case, Ubuntu and Windows 7. =)

By default, Ubuntu is listed first in the list and Windows somewhere near the bottom.  Just use the arrow keys to make your selection and off you go!

---

