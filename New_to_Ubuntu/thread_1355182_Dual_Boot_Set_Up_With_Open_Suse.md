---
title: "Dual Boot Set Up With Open Suse"
date: 2009-12-14
forum: New to Ubuntu
---

### Post by guv999 on 2009-12-14
Hi 
I am keen to try dual booting Ubuntu and Open Suse.   There are plenty of threads around this and the process seems straight forward.  I do have a couple of questions though........
[LIST]
[*]Is it possible to select a default OS that will automatically run when the system boots without having to make a manual selection?
[*]Is it possible to share the contents of my Ubuntu Home folder in Open Suse?
[/LIST]
Appreciate any guidance

---

### Post by oldfred on 2009-12-14
Are you using grub, grub2 or whatever openSuse is using which I am not familiar with.

In grub legacy you can select which number from the list to boot. In grub2 you can use an exact title like this that I copied from someone else (meierfra I think) for windows but it can be any title.

If you refer to Windows by its number, you will have to edit on every update. But Grub 2 also lets you use the title. Suppose your Windows title is "Windows Vista (on /dev/sda1)". Then you can use in /etc/grub/default, and you won't have to edit Grub after kernel updates.

GRUB_DEFAULT="Windows Vista (on /dev/sda1)"

There can be major issues with sharing /home across distributions and gid's may be different. The best way is to create a /data partition with all your data and mount that with symlinks.

ln -s /media/8.04/Pictures .

That would make your Pictures folder from the data partition show up
in your normal home folder. Before you make a symlink though, you
want to make sure you won't link over an existing folder. If you try
to, you will get a "File exists" error. In that case, replace the .
in the above command with a new name for that folder.

If you want to remove a link, you can use the unlink command.

---

### Post by Geoff918 on 2009-12-14
I've run dual boot w/OpenSUSE before. You have to be a bit careful here. OpenSUSE doesn't play too nice as anything less than the most dominant OS on the system. (I even ran OpenSUSE, Vista, and Ubuntu on one machine because, well, no reason really).

Which is the last OS you installed, Ubuntu or OpenSUSE? The configuration should be set from there because it will have dominant control over the boot menu in all likelihood.

---

### Post by guv999 on 2009-12-15
Thanks for your help.  :)  I think I will play it safe and hold off until I do a fresh install when Lucid comes out before proceeding with this.  I just want to take a look at KDE outside of a virtual box environment so can easily wait a bit.

---

