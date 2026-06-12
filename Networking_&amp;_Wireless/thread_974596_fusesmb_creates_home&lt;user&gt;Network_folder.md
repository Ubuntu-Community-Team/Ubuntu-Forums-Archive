---
title: "fusesmb creates /home/&lt;user&gt;/Network folder"
date: 2008-11-07
forum: Networking &amp; Wireless
---

### Post by cdysthe on 2008-11-07
Hi,

Every time I log in a /home/<user>/Network folder is created with shares mounted. I can see the entry in mtab:

fusesmb /home/<user>/Network fuse.fusesmb rw,nosuid,nodev,allow_other,max_read=32768 0 0

I have used fusesmbtool to set /media/Network as the mount point for smb shares, but still I have the /home/<user>/Network folder containing workgroups and shares created in my home directory. I can't delete this directory either unless I boot in recovery mode and delete it from the console. And if I do that next time I log into my account the folder is created again.

I can't for the life of me find out how to stop fusesmb to do this. Could someone please let me know where and how this has been set, and how I can stop fusesmb to do it?

//C

---

### Post by EVRAMP on 2008-11-08
/media/Network must be 777 moded.
sudo chmod 777 /media/Network
And dont forget that **N**etwork is not the same as **n**etwork.

..When expecting problems you may also be interested in the smbclient bug which is floating around the linux comminuty: [http://bbs.archlinux.org/viewtopic.php?pid=446263](http://bbs.archlinux.org/viewtopic.php?pid=446263)

---

