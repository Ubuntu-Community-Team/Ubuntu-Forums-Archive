---
title: "* Is there any way to open my windows os, through ubuntu"
date: 2009-10-03
forum: New to Ubuntu
---

### Post by R3fr4cti0n on 2009-10-03
i don't want to Build a new Vbox i want to access my Windows Partition through ubuntu, i want to be able to get to my Photoshop cs4, Sketchbook Pro, Art Rage, Painter x, and Quick books, WITHOUT rebooting. these programs are NOT negotiable i have all the ubuntu studio programs however these apps are simply superior for what i need to do. I am not looking to argue about why  ubuntu programs are better or what ever i just HAVE to use these particular progrms and if i could use them through Ubuntu my life would be 68% easyer

so any one have a walk through or howto?
thanks!

---

### Post by theozzlives on 2009-10-03
Other than Wine, you cannot run a Windows program in Ubuntu. Linux is not Windows, therefore does not run Windows programs. If the aforementioned vendors come out with Linux versions, then it would be a different story. Til then, dual boot or VM is the only option. I sympathize with you, I have programs I run in Windows but I chose VirtualBox.

---

### Post by grturner on 2009-10-03
look into wine... it should let you run windows programs. no guarantees though

[https://help.ubuntu.com/community/Wine](https://help.ubuntu.com/community/Wine)
[http://appdb.winehq.org/](http://appdb.winehq.org/)

---

### Post by R3fr4cti0n on 2009-10-03
can i open my Windows partition Through an Ubuntu->Vbox perhaps?

---

### Post by credobyte on 2009-10-03
You can give a try to Wine, however, I'm not really sure about it's ability to use software that's installed somewhere else, not in it's native *virtual image*.

---

### Post by R3fr4cti0n on 2009-10-03
Just to let everyone know wine will not work with most of these programs, i want to use vbox i just want to get to my partition through it.

---

### Post by sandyd on 2009-10-03
Virtualbox can share folders with the host OS.

so, you can mount the windows partition to a directory that you own, then share the folder with windows using virtualbox.

---

### Post by R3fr4cti0n on 2009-10-04
so with this i will be able to access all my host Windows apps? and i will be able to do this through Ubuntu?

do you have a link to a walkthrough?

---

### Post by DGortze380 on 2009-10-04
It is possible (though rather risky) to mount an actual partition as a virtual machine using VirtualBox.

[http://mesbalivernes.blogspot.com/2008/01/virtual-box-booting-from-existing.html](http://mesbalivernes.blogspot.com/2008/01/virtual-box-booting-from-existing.html)

---

### Post by kieran_uk on 2009-10-05
Cheers for the link :)

---

### Post by random turnip on 2009-10-05
You should eb able to get into your partition and get data from there through Ubuntu, but not run programs.  If you're 100% sure Wine won't run them, you can try [Virtual Box]("http://www.virtualbox.org/") (which is something i know nothing about) or simply dual boot and just use XP when there is something you need to do on those programs.

---

### Post by R3fr4cti0n on 2009-10-05
> **DGortze380 said:**
> It is possible (though rather risky) to mount an actual partition as a virtual machine using VirtualBox.

[http://mesbalivernes.blogspot.com/2008/01/virtual-box-booting-from-existing.html](http://mesbalivernes.blogspot.com/2008/01/virtual-box-booting-from-existing.html)

thanks!

---

### Post by praveesh on 2009-10-05
It is possible to convert a real partition to a virtual machine , with the help of vmware.

---

### Post by miwaypet on 2009-10-05
If you just want to access files and other data, you can mount the windows partition in /etc/fstab. You cannot run the programs, but you can access all of your data. Virtual Box not required. If interested you can do the following:

Create a new directory in either your /home partition or in /. If you do not mind an icon on your desktop, making the directory in /home is as simple as a right click and create new folder. Give it a name....WinXp or some such. To mount in / use this command in terminal:

$sudo mkdir $directory name$

Next open /etc/fstab with your favorite text editor:

$sudo gedit /etc/fstab

At the bottom of the list, may need to open to full screen here, add the following line:

/dev/sda2    /path_to/mount_point    ntfs-3g    uid=1000,gid=100,umask=0022    0 0

Make "sda2" whatever the windows partition number is. Probably it will be your first partition, thus "sda1". Path to mount point should be obvious, but just in case, "/home/your login/directory name", or "/directory", depending on where it was created. The uid=1000 is your personal user group number, so no one else can access the mounted partition but you.

Finally:

$sudo mount -a

And you are done. Hope this helps, and I wish you a great day.

---

### Post by R3fr4cti0n on 2009-10-05
> **praveesh said:**
> It is possible to convert a real partition to a virtual machine , with the help of vmware.

that what i want to do, you said it better tho

---

