---
title: "Wubu and New Linux Distribution"
date: 2010-07-09
forum: New to Ubuntu
---

### Post by rkilburn9837 on 2010-07-09
Hi,

Just a question, i have installed 10.04 onto my laptop using Wubi (just to kinda mess around and its quicker that Windows 7). When a new Ubuntu distrobution comes out. How do I update to it and can I just use the built in updater in the Update Manager. 

Thanks in advance

Ryan

Ooo Smileys >>>:D :)

---

### Post by themusicalduck on 2010-07-09
I'm pretty sure you can update Wubi just like a normal install.

You have to bear in mind though, Wubi is not really meant to be used for permanent installs, but for testing. For the most reliable experience for long term use you should do a proper install to a partition. Also, the disk image for Wubi is installed on the Windows partition, so if something happens to Windows then Wubi might break too.

I'd also recommend if you can to do a fresh install for an upgrade rather than upgrading through the update manager, testing the version beforehand using a live CD session.

edit: forgot to answer your question.

It should come up automatically in the update manager. If you go to System > Administration > Software Sources and Updates tab, check the Release upgrade is set to Normal releases (or LTS if you want long term releases only)

---

### Post by garvinrick4 on 2010-07-09
I have quite a few installs of Ubuntu and one of them is a WUBI and I have gone through quite a few dist-upgrades from the original install. So yes you can do the next upgrade to 10.10 when it comes out. Watch these forums for when it is stable and ready to go though update manager. There are also users that do testing for Wubi.
 It is a folder inside of Windows right next to Users in C: drive. If you ever choose to upgrade and do a fresh install make sure you use that folder and its uninstall rather than
the Windows Add and Delete programs for uninstalling Ubuntu. It attaches itself to Windows bootloader in Vista and 7 it is in bcdedit and is called wubilder and you can see it in the windows bootloader. Uninstalling from Add and Remove programs sometimes leaves the wubilder in Windows bootloader. That is the reason for that suggestion. 
 In the filesystem in Wubi there is a directory (folder) called host. That is your Windows install and you can bring things over to Ubuntu for you Home from there. Cannot copy in Wubi back into Windows though. Runs Windows at same time as Ubuntu takes more Ram to run Wubi than a regular dual boot. Enjoy Ubuntu and when get stuck just asks here and read these forums to learn. When you get the
hang of Linux do a partition dual boot and you will find it faster and easier to use.

---

### Post by bodhi.zazen on 2010-07-09
> **rkilburn9837 said:**
> Hi,

Just a question, i have installed 10.04 onto my laptop using Wubi (just to kinda mess around and its quicker that Windows 7). When a new Ubuntu distrobution comes out. How do I update to it and can I just use the built in updater in the Update Manager. 

Thanks in advance

Ryan

Ooo Smileys >>>:D :)

Honestly, Wubi is for testing. If you are going to stay with Ubuntu I suggest you perform a standard installation including partitioning your hard drive and installing grub.

You do not *need* to do that, but it is not *that* difficult to do so and it is much much easier in the long run.

Otherwise, you should, in theory, be able to update a wubi install in the same way as a standard installation.

---

### Post by steveneddy on 2010-07-09
Wubi is NOT meant to be used long term. It is merely for evaluation purposes only.

Better peformance will be achieved if you partitioned your HD and gave Ubuntu it's own partition or simply used a virtual machine like VirtualBox.

[Download here]("http://www.virtualbox.org/wiki/Downloads")

---

