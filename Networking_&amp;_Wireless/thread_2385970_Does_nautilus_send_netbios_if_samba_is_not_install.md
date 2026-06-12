---
title: "Does nautilus send netbios if samba is not installed?"
date: 2018-02-27
forum: Networking &amp; Wireless
---

### Post by allan.w.macdonald on 2018-02-27
Hello,

I have a linux box connected to our company network.  The network sysadmin (he's a Windows guy) has been complaining to me that my computer has been sending netbios packets which he claims are bad for security and against corporate policy.  I thought I had uninstalled samba on my machine but there still seemed to be some samba-related items on my machine.  I then removed all packages that had samba in the name ("sudo apt-get purge --auto-remove samba*") and deleted any file or directory with samba in the name.  Since I did that, it seems the netbios traffic has stopped.; however, I can no longer use nautilus to sftp into the linux server (i.e. Connect to Server no longer works).  I must have broken something.

If I repair nautilus (i.e. sudo apt-get remove --purge nautilus && sudo apt-get install ubuntu-desktop), without installing samba, and create an sftp connection, will netbios packets start being sent again?

Thanks in advance!

---

### Post by Morbius1 on 2018-02-27
Removing all things samba removes gvfs-backends which also enables "Connect to Server" to do something like sftp://xxxx. 

What you might consider is disable the invoking of the samba client from browsing the network in the first place:
```
sudo chmod 744 /usr/lib/gvfs/gvfsd-smb-browse
```

---

### Post by allan.w.macdonald on 2018-02-27
Thanks Morbius1!  I intend to apt-get install ubuntu-desktop using the -d option, unplug the network cable and then run apt-get install again to complete the installation.  After I do this, I expect to perform the suggested command before I reboot and reconnect the network.  Does this sound right to you?

---

### Post by Morbius1 on 2018-02-27
At the moment I don't see how you have any other choice.

---

### Post by allan.w.macdonald on 2018-02-27
Thanks again.  I will try this and report back with results.

---

### Post by allan.w.macdonald on 2018-02-27
OK I'm back and I can now do sftp again.  I am now waiting to see if our sysadmin is still complaining about netbios traffic.  I will give this a couple of days and if I don't hear from him I will mark this as solved.

Thanks again Morbius1 for your help.

Cheers,
Allan

---

