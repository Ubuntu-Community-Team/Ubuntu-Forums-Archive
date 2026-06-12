---
title: "Problem installing GFX Grub"
date: 2009-01-03
forum: New to Ubuntu
---

### Post by looi76 on 2009-01-03
Hi, I'm having a problem getting GFX GRUB to work. I have installed it based on this Howto: [GfxBoot ( Grub like suse )]("http://ubuntuforums.org/showthread.php?t=208855"). 

Here is how I installed it:

First I downloaded the files required. I have used grub-gfxboot_0.97-36_amd64.deb since I'm using Ubuntu 8.10 64-bit.
[[IMG]http://img110.imageshack.us/img110/6505/upload01pz8.th.png[/IMG]](http://img110.imageshack.us/my.php?image=upload01pz8.png)

Then I have removed GRUB:
[[IMG]http://img528.imageshack.us/img528/3223/upload02so3.th.png[/IMG]](http://img528.imageshack.us/my.php?image=upload02so3.png)

The I have installed GFX GRUB:
[[IMG]http://img528.imageshack.us/img528/9369/upload2nn7.th.png[/IMG]](http://img528.imageshack.us/my.php?image=upload2nn7.png)

Then I have copied message.suse to /boot/grub:
[[IMG]http://img110.imageshack.us/img110/9762/screenshot3qs9.th.png[/IMG]](http://img110.imageshack.us/my.php?image=screenshot3qs9.png)

Then I have backup /boot/grub/menu.lst and edited it:
[[IMG]http://img528.imageshack.us/img528/3715/screenshot4pb6.th.png[/IMG]  ](http://img528.imageshack.us/my.php?image=screenshot4pb6.png)[[IMG]http://img528.imageshack.us/img528/7362/screenshot5iy4.th.png[/IMG]](http://img528.imageshack.us/my.php?image=screenshot5iy4.png)

Then I have configured grub:
[[IMG]http://img110.imageshack.us/img110/4172/screenshot6yj5.th.png[/IMG]](http://img110.imageshack.us/my.php?image=screenshot6yj5.png)

After I did the following steps, when I switch on my computer nothing has changed to GRUB! Can someone help?

---

### Post by F33n1k5 on 2009-08-01
I know how you feel, I recently updated to this new kernal and followed this tutorial for GFXGrub: [http://tuxenclave.wordpress.com/2008/01/18/how-to-install-gfx-grub-in-ubuntu/]("http://tuxenclave.wordpress.com/2008/01/18/how-to-install-gfx-grub-in-ubuntu/") and now I have to force boot into my linux with SGD. I have all my files in the right place, but when I type "sudo grub-install /dev/sda6" (6 is my linux partition) I get an "Unrecognized Command" error. Does anyone out there have a solution? I've added too many new progs and widgets to just re-install, plus I have XP and 7 rc1. (I'm using 3dsmax, so I can't make my system linux-only :( )

---

