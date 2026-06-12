---
title: "Waiting for NFS mount on boot"
date: 2007-11-23
forum: Networking &amp; Wireless
---

### Post by BillDozer on 2007-11-23
i've got an Ubuntu 7.04 server which serves an NFS folder.

After upgrading my clients to 7.10, the boot process takes a long time at the line when mouting the the folder. The one client reports ok after the wait, the other reports Fails. But after I log in, the folders are mounted correctly on both machines.
I am using the following values when mounting:
```
example.hostname.com:/ubuntu /local/ubuntu nfs rsize=8192,wsize=8192,timeo=14,intr

``` Also tried the 32xxx values for rsize and wsize, but it makes no difference.

---

### Post by tomauty on 2007-11-24
Yeah me too except I have to log in under the recovery mode to get into gdm.

---

### Post by Nikas on 2008-01-08
I have the same problem. I have only used 7.10 so i dont know if the problem has anything to do with that.
Waiting for "FOLDER" a long time and then "Failed" and the computer continues to boot.
The folders are mounted as they should.

No news on this? :)

> 192.168.1.7:/var/lib/mythtv/recordings /var/lib/mythtv/recordings nfs rw,auto 0 0


---

### Post by BillDozer on 2008-01-11
No, unfortunately not. I still have the problem. I haven't tried to have my clients mount to a 7.10 server, maybe I will try that in a few days.

---

### Post by Nikas on 2008-01-11
Both my machines runs 7.10 :/

---

### Post by chewearn on 2008-01-11
Maybe what you guys need is AUTOFS:
[http://ubuntuforums.org/showthread.php?t=249889&highlight=umount+nfs&page=20](http://ubuntuforums.org/showthread.php?t=249889&highlight=umount+nfs&page=20)


Just a thought.

---

