---
title: "[SOLVED] Viewing shares of other computers"
date: 2008-05-13
forum: Networking &amp; Wireless
---

### Post by Jordanwb on 2008-05-13
I installed Xubuntu 8.04 onto my ~8 year old laptop replacing Ubuntu 8.04. So there are differences between the two and I take a learning curve head on however I can't find a menu item on viewing the shares of other computers, and the computers in my workgroup. I remember in Ubuntu I would go to Places->Network or something like that. Where do I go to view network devices and their shares?

On a unrelated note, what command do I type to restart Samba?

Thanks.

---

### Post by Iowan on 2008-05-13
To restart Samba: ** sudo /etc/init.d/samba restart**

---

### Post by ryanhaigh on 2008-05-13
Xubuntus default file manager thunar doesn't support browsing samba/windows shares, you can however mount a fusesmb filesystem at some location in your system and use that to access these shares. [Heres one howto]("http://ubuntuforums.org/showthread.php?t=304131"), there should be a few with similar content.

There are other alternatives such as mounting a specific share at boot, or using applications such as pyNeighbourhood for browsing the network, of course these are not as integrated as the first solution. Finally you can install and use nautilus (ubuntus file manager) on xubuntu, but that may cause other issues.

---

### Post by InsaneBeast on 2008-05-19
How do you set xubuntu to mount a shared folder on a windows machine at boot using /etc/fstab?

---

### Post by Jordanwb on 2008-05-19
That may not be a good idea. I don't know what will happen if the Windows machine isn't on. All hell may break loose.

---

### Post by jtrindle on 2008-05-19
It's not a disaster, at most you'll get a (long-ish) delay on boot and then no access to the remote drive.

You might have to install the smbfs package.

The syntax should be in your mount.cifs man page. 

man mount.cifs

The fstab syntax should be something like

//servername/sharename /mnt/pnt auto user=fred,password=fredpw 0 0

---

### Post by ryanhaigh on 2008-05-19
This should contain everything you need to mount windows shares at boot: [https://help.ubuntu.com/community/MountWindowsSharesPermanently](https://help.ubuntu.com/community/MountWindowsSharesPermanently)

---

### Post by Iowan on 2008-05-19
[Here ]("http://ubuntuforums.org/showthread.php?t=800313&highlight=cifs")is a new mounting method for Hardy.

---

