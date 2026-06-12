---
title: "VMWare on Ubuntu host -- folder sharing"
date: 2009-02-21
forum: New to Ubuntu
---

### Post by DaveM59 on 2009-02-21
Hi all, first post.

I've done a lot of searching and read the help files but I'm still stuck.

I just got Ubuntu installed on one hard drive on this machine. Installed VMware player in Ubuntu, created a VM at easyvmx and installed WinXP as guest OS.  I also have a native XP installation on the other hard drive.  That drive has two partitions, both NTFS, one is the XP System drive and the other is where I store data.

What I want to do now is allow my guest Windows OS to be able to access some of the folders on the NTFS data partition. It seems that this is done via samba.  Samba is installed and running, and I have installed a little GUI program called Samba Server Configuration.  I mounted the Data partition and used the SSC program to enable file sharing of several folders.  Set the folders as writable and visible, and allowed access to everyone.

Here is where I am stuck.  VMware player can't see the shared folders.  I mount the Data drive, start VMware player and click VMware Player, Shared folders, the window opens up but no shared folders are listed.  Under Folder Sharing, Always enabled is selected and Map as Network Drive in Guest OS is checked, but I can't type anything in the empty Shared Folders box.  Properties button is grayed out.  The help button offers no help with this and my google searches have not turned up any advice on this situation. 

Would appreciate any guidance.

---

### Post by Panzor on 2009-02-21
I use VMware Workstation, but when I want a file from my VM to my host, I just drag the file from the vmware window onto my desktop and do with it what I want from there. I'm fairly certain you'll need VMware Tools installed for this. There are plenty more reasons to install that, anyway.

Good luck.

---

