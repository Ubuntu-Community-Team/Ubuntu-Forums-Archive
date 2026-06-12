---
title: "Configuring home network"
date: 2005-08-15
forum: Networking &amp; Wireless
---

### Post by foxy123 on 2005-08-15
I am completely new to networking, so i am sorry for any stupit questions.

I've got two cmpouters at home: laptop, which I mostly use and desktop, which is used by the rest of the family. My laptop is run solely on Ubuntu, while desktop is dual boot. The trick is that I need the access to the desktop now and then and I need some directories to be mounted.

Currently I do it manually using SMB. The problem is if the desktop is in booted in Windows and  then re-booted in Ubuntu, it freezes everything and I have remount directories or even re-boot my laptop, which is annoying.

I wonder if there is a way to automate the process, so the required directories were mounted no matter in what OS the desktop is booted. Also is it possible to access Linux partitions from my laptop on the desktop, booted in Windows.

Sorry, if it's a bit incoherent...

---

### Post by tonym on 2005-08-15
Have a look at running autofs on the laptop.  This lets you mount NFS and SMB partitions dynamically when you need them.

If you run SAMBA on the laptop you can share directories and access them from Windows on the desktop.

---

### Post by foxy123 on 2005-08-15
[QUOTE=tonym]Have a look at running autofs on the laptop.  This lets you mount NFS and SMB partitions dynamically when you need them.

If you run SAMBA on the laptop you can share directories and access them from Windows on the desktop.[/QUOTE]
thanks a lot for your response. Do you know any good howto for autofs?

---

### Post by DatHak512 on 2005-08-15
I hope i'm not taking this too far offtopic, but i'm wanting to know how to set up Samba on my Ubuntu machine, so that i can read to some shares and read/write to another share. I've got Samba installed, but when i execute "sudo /etc/init.d/samba start", all i get is [fail]. I can't see my computer from either Windows or Mac OS X machines.

System -> Administration -> Shared folders says that i've got a directory shared, but i can't see it from any of my other machines. I can ping my machine from others, though.

---

