---
title: "How to install ubuntu through LAN"
date: 2011-07-13
forum: New to Ubuntu
---

### Post by DooMFeaR on 2011-07-13
Sorry for bothering you guys but I have this old Dell Latitude C400 series and It doesn't have an optical drive or the option to boot from USB so the only way to install any OS is by LAN. Can anyone guide me step by step how to install ubuntu from LAN with other PC?

---

### Post by skatinjj on 2011-07-13
Not sure what your setup is like, but there are many ways to accomplish this task here:

[https://help.ubuntu.com/community/Installation#Server and network installations]("https://help.ubuntu.com/community/Installation#Server and network installations")

---

### Post by Mark Phelps on 2011-07-13
From what I read in the links, you must have a SERVER available to do network installation.  

You can not simply have the install files sitting in a folder somewhere on a PC accessible over the network.

It also looks like you have to be able to boot the installing PC into something that will read GRUB.

---

### Post by skatinjj on 2011-07-13
What OS do you have installed on your other PC?

This is easiest if that PC has Linux:

[https://help.ubuntu.com/community/Installation/LocalNet]("https://help.ubuntu.com/community/Installation/LocalNet")

If the OS is Windows, I suggest:

[https://help.ubuntu.com/community/Installation/WindowsServerNetboot]("https://help.ubuntu.com/community/Installation/WindowsServerNetboot")

---

### Post by DooMFeaR on 2011-07-14
1. I've got a laptop without any OS, without CD-ROM, without the option to boot from USB, just boot from LAN.
2. I've got a second laptop with Windows 7 64-Bit which I want to use as server.
3. I've got a network cross-over cable between them.

 I followed the steps from [https://help.ubuntu.com/community/In...sServerNetboot]("https://help.ubuntu.com/community/Installation/WindowsServerNetboot") and now I get:
[IMG]http://lookpic.com/c1/i2/2498/X2St8NsR.jpeg[/IMG]
[IMG]http://img269.imageshack.us/img269/7952/14072011387.jpg[/IMG]


 The thing is, the vesamenu.c32 is in the ubuntu-installer/i386/boot-screens/ , but why he couldn't find it?
 [IMG]http://lookpic.com/c1/i2/2498/X2St8NsR.jpeg[/IMG]

---

### Post by Lars Noodén on 2011-07-14
The package dnsmasq is the easiest to set up for PXE booting and TFTP.  The files for netbooting are on the Ubuntu installation CD in the folder install/netboot

---

