---
title: "Question about (tomorrow's) Ubuntu Jackalope installation."
date: 2009-04-22
forum: New to Ubuntu
---

### Post by kajman on 2009-04-22
Hi!

I'll be installing Ubuntu (or Kubuntu) 9.04 tomorrow after the final release.

Currently I have Fedora Core 10 installed on two different partitions. I have the system partition on one of them and my /home folder in the other one.

I'd like to install the system on the first partition, but it's important for me that the /home partition stays intact and it'll be used by my freshly installed Ubuntu as my home folder.

Is there a way to do this without any risk of data deletion (for e.g. the installer will format this drive)? I have a lot of important information there, but not enough disk space to make a backup.

---

### Post by Penguin Guy on 2009-04-22
If you have important data then either buy a external HDD for backups or don't install OSs. There will always be some risk.

On the good side, I believe this is done automatically. Ubuntu does not overwrite partitions unless you tell it to.

---

### Post by Paqman on 2009-04-22
You'll have to select manual partitioning. Just select the current Fedora root partition and allow Ubuntu to format it. Then select you current /home partition to be the new /home and make sure that you **don't** format it. Everything will be preserved.

Bear in mind that migrating a Fedora /home partition might cause some slightly odd behaviour in the new Ubuntu. If it does just go into your home and delete the .hidden folder for that particular app. A new one with default settings will be created.

---

### Post by nandemonai on 2009-04-22
It's possible but I'd be wary of reusing your home from a different distro.

Unless you're talking about everything BUT user conf files there could be issues.

If it's just documents, music that kind of thing the what I would suggest is booting the 9.04 installer. Mounting your /home partition and deleting ALL hidden folders (.something files) for all users before attempting to install Jaunty.

Be wary of stuff like virtual machines for virtualbox and wine stuff (if applicable) because they will likely be in hidden folders themselves.

If you plan to do this then when setting up partitioning do it MANUALLY and mount your existing /home as /home and be certain it will not be formated. 

Again this is in theory safe when all precautions are taken but problems do happen. I'd highly suggest a backup before attempting this.

---

### Post by bodhi.zazen on 2009-04-22
You may have problems with your /home partition if you use the same user name on ubuntu as fedora.

Linux identifies users by number, not name. The first user on Fedora is 500 , o nubuntu it is 1000. 

The best solution is to use a unique user name with each distro.

Otherwise you need to relax your permissions and have your primary group be somethig like users. Make files and directories owned by the group "users" with group permission of rw or rwx as needed.

---

