---
title: "user creastrated folders owners automatically set to root"
date: 2008-03-21
forum: Networking &amp; Wireless
---

### Post by MasterAslan on 2008-03-21
I am having a very strange issue.  I have a network drive mapped through with cifs.  The network drive is on an ubuntu computer as well.  Whenever as a user I create a new folder on this drive it creates it as root.  I actually log into it as my user name not root.  If I actually umount the folder and I access it through the network icon I can create a folder and its owner is myself.  I don't understand what could be causing this.


This is my fstab entry for the drive.

//192.168.2.2/shared /media/server-shared cifs credentials=/home/brian/.smbcredentials,iocharset=utf8,file_mode=0777,dir_mode=0777 0 0

Any ideas?

---

### Post by Eiríkr on 2008-03-21
Since you do not specify "users" to allow users to mount / umount, the mounting procedure must be carried out by root -- in which case, root owns the mount.  You'll want to also add the "uid" and "gid" options to your fstab file to specify who gets ownership.  [More details here](http://linux.die.net/man/8/mount.cifs).  Let us know if that works.

Cheers,

Eiríkr

---

### Post by MasterAslan on 2008-03-22
yes setting the uid and gid in fstab worked.  Thanks a million.

---

### Post by Eiríkr on 2008-03-22
Brilliant, glad that helped!  :D  Since this seems to fix your issue, please also remember to mark the thread as SOLVED in the Thread Tools dropdown towards the top of the page.  :)

Thanks,

Eiríkr

---

