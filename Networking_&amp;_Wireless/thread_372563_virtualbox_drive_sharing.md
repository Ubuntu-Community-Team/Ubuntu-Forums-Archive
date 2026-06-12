---
title: "virtualbox ?drive sharing"
date: 2007-02-28
forum: Networking &amp; Wireless
---

### Post by tompouce on 2007-02-28
Hi!

I want to know if there a way to access my files from a virtual machine on virtualbox

---

### Post by Karl S. on 2007-02-28
Not sure what you mean. 

Do you mean can your host machine access files saved in your virtual machine? (I think the answer is no. Save them to a shared directory on the host machine instead)

---

### Post by tompouce on 2007-02-28
No the oposite, I want to access my host's file from my virtual.

Thanks!

---

### Post by qpieus on 2007-03-01
see here:
[http://ubuntuforums.org/showthread.php?t=367155](http://ubuntuforums.org/showthread.php?t=367155)

It's also discussed in the virtualbox manual section 5.4 "Folder Sharing".
Note that thread discusses setup for a windows guest. If you have a linux guest, the code to use within the guest would be:
sudo mount -t vboxsf "VirtualFiles" /"path to mount point" (using the poster's example shared folder).

This thread discusses it better:
[http://www.ubuntuforums.org/showpost.php?p=2020413&postcount=35]("http://www.ubuntuforums.org/showpost.php?p=2020413&postcount=35")

---

### Post by bob-aptllc on 2007-03-03
The VirtualBox manual's approach didn't work for my system. Instead, I setup a Samba server from the host (Ubuntu) to the guest (W2K). The result is being able to share folder(s) from the host to the guest. See [http://www.ubuntuforums.org/showthread.php?t=76647](http://www.ubuntuforums.org/showthread.php?t=76647). This has also been helpful in that my CD and USB drives don't work in VB, so I copy data to my shared folder on the host, then from the guest copy it into the guest system.

---

