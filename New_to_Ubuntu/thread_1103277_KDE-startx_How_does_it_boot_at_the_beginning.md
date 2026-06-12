---
title: "KDE-startx How does it boot at the beginning?"
date: 2009-03-22
forum: New to Ubuntu
---

### Post by Feidias on 2009-03-22
Hello!

I have installed Kubuntu 7.10.

I had a problem that I couldn't mount my VAIO disks.I was getting 

hal-storage-removable-mount-all-options refused uid 1000

So I tried to install synaptic (sudo apt-get install synaptic), and then ntfs-config (sudo apt-get install ntfs-config).

But...the system stuck so I rebooted.

After that I can't load the graphical environment.

Even if I have tried to install KDE again (sudo apt-get install KDE).

I am taking Ubuntu 7.10 A1 tty1

A1 login.

I give name and password.

But then I have to type startx to run the graphical environment.

How can I configure it to run while booting?

Also the 2 hard drive disks are now mounted.


Thanks

---

### Post by llamabr on 2009-03-22
If I understand, you were halfway through installing, and then quit?  Finish the install.

Also, try running

 sudo dpkg-reconfigure -phigh xserver-xorg

---

