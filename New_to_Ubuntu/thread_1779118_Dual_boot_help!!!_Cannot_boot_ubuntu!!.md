---
title: "Dual boot help!!! Cannot boot ubuntu!!"
date: 2011-06-10
forum: New to Ubuntu
---

### Post by winslowevan on 2011-06-10
Heres the story, I needed windows so I downloaded a moded windows xp called black edition. Anyways I installed it on a tiny partition already on my hd. What happened next is that It wouldn't fully install, now every time I boot it boots in xp and asks for a boot disc but won't install. I tried to delete the partition with UBdisc but don't want to mess up. The boot screen commands are of no help either as none of them change the booting system. Reinstalling is not possible as I have files I need. What I would like most is to know:[COLOR="SandyBrown"]how to remove xp and how to boot in ubuntu again. I  know its still there.[/COLOR] thanks

---

### Post by CryptSphinx on 2011-06-10
you need to fix grub first 

you will need :

1. A live disc of your current version of ubuntu
2. Calm
3. The tutorial below.

[https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB2]("https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB2")



also bad person , stealing Microsofts proprietary code :P

---

### Post by winslowevan on 2011-06-10
My Ubuntu seems not to have grub...

---

### Post by nzjethro on 2011-06-10
> 2. Calm
Haha.

Try reinstalling your Grub.
[http://ubuntuforums.org/archive/index.php/t-24113.html](http://ubuntuforums.org/archive/index.php/t-24113.html)

---

### Post by CryptSphinx on 2011-06-10
Did you

boot live cd               y/n

open terminal              y/n

sudo fdisk -l              y/n 

sudo mount /dev/sdXY /mnt  y/n 

get to the point of running the grub reinstallation:
sudo grub-install --root-directory=/mnt /dev/sdX        y/n

what point did you get to and how did you arrive at your conclusion.

be VERBOSE please . :)

---

### Post by winslowevan on 2011-06-10
Well I'm sort of confused but, here is what is happening, I am now running 'Try Ubuntu' on the install cd, I am now attempting the boot repair install.

---

### Post by winslowevan on 2011-06-10
Thanks to all, If anyone needs a simple way to do this follow the instructions from boot-repair page. It also doesn't hurt to format that partition. UNLESS YOU HAVE THINGS  YOU NEED ON THERE!

---

### Post by jtarin on 2011-06-10
Mark this thread as solved please.

---

### Post by CryptSphinx on 2011-06-11
Hilarious , I wasn't aware of a graphical utility to fix boot issues , rock on canonical .

Glad to hear its sorted -

---

