---
title: "Way to  avoid Grub error 18 when installing"
date: 2010-07-08
forum: New to Ubuntu
---

### Post by kgeil on 2010-07-08
Hi, I'm trying to get a dual boot of backtrack and windows xp to work.  I've tried multiple things and ways of installing, but always get grub error 18.  

I'm working on a Dell inspiron 600m, with bios revision a17.  

Can anyone point me toward an easy to read tutorial for installing these 2 operating systems so that I can dual boot?

Thanks,

Kevin

---

### Post by kgeil on 2010-07-08
So, I'm a little closer to answering my own question, or so I think:

I have a 298 Mb partition at the beginning of my drive that's empty.  From what I have read, I'll need to move /boot to that partition, and install grub to start from there.  Can anyone help me with the specifics on how to do this?

Thanks again,

Kevin

---

### Post by oldfred on 2010-07-08
I think when I created a /boot I just copied the entire /boot directory over, edited fstab and reinstalled  grub pointing to the new partition. 

I decided I did not want (nor need) a /boot so I moved the boot back but kept it as a /grub partition.

[http://members.iinet.net.au/~herman546/p15.html#18](http://members.iinet.net.au/~herman546/p15.html#18)

[http://members.iinet.net.au/~herman546/p15.html#How_to_make_a_separate_boot_partition](http://members.iinet.net.au/~herman546/p15.html#How_to_make_a_separate_boot_partition)

---

### Post by kgeil on 2010-07-09
OK, I'm getting closer.  I moved /boot, as per Herman's instructions, now I'm faced with a grub error 15:

File not found

I think it's trying to boot the wrong OS now.  My first guess is to look in FStab, if I'm barking up the wrong tree, let me know.

Kevin

---

### Post by oldfred on 2010-07-09
error 15 often is the two grub's conflicting. Grub2 and grub legacy do not like each other. Or old grub cannot find its files. This probably is before fstab has a chance to be an issue.

[http://members.iinet.net.au/~herman546/p15.html#15](http://members.iinet.net.au/~herman546/p15.html#15)

---

