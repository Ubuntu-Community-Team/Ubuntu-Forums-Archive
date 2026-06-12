---
title: "Grub 1.97"
date: 2010-01-04
forum: New to Ubuntu
---

### Post by javadog on 2010-01-04
Hi All

I have hit a bit of a wall with this one.

When we install 9.10 onto a machine and run the updates, we initially install with Wubi and a 9.10 iso and from there then do the updates etc. After we ran the 'all upgrades' function and reboot we get the following error. 

GNU Grub Version 1.97~beta 4

it gives me some description about using TAB etc.

It pulls up a form of command prommt however from there I am at a loss. 

What must I do to either rebuild or roll back to the working function and why would this only happen to one machine?

Thanks
Java

---

### Post by duanedesign on 2010-01-04
There is currently a [bug report]("https://bugs.launchpad.net/ubuntu/+bug/477169") on this. Until it is solved for Wubi installations, do not run any upgrades that might touch Grub2 or initrd (typically these will involve kernel updates.)

---

