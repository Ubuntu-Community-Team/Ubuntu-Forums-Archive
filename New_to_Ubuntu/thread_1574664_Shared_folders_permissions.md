---
title: "Shared folders permissions"
date: 2010-09-14
forum: New to Ubuntu
---

### Post by donescamillo on 2010-09-14
Hi,

I have Windows host, Virtual box and Ubuntu 10.04 in it. There is shared folder between Windows and Ubuntu. My problem is that I constantly have problems copying/pasting (i.e. writing) into this shared folder. I tried to change owner to my account name but could not, apparently you can't change shared folders' permissions. Is there a way to become an owner of this folder or at least to be able to write in it?

---

### Post by bodhi.zazen on 2010-09-14
Where is the shared folder, windows or Ubuntu ? What kind of partition is it ? NTFS ?

IMO it is often easier to use a standard network protocol for sharing such as samba or ssh (scp) or similar.

---

### Post by endotherm on 2010-09-14
I set GID on my samba folders, and make sure my users are in the "users" group, which is the owner group on the samba folder. that way, anyone who is a member of group users, can r/w from the directory, but any files they add get automatically owned by <username>:users .
there several levels of permissions for samba. there are the permissions of the actual file, and those of the share. share permissiosn can also be extended by sambas DirectoryMask settings.
generally as a rule, I try to make share permissions loose, and folder permissions tight.

---

### Post by papibe on 2010-09-14
Did you install the Guest Additions?

Did you try this (from the VittualBox site):
> **Long delays when accessing shared folders**

The performance for accesses to shared folders from a Windows guest might be decreased due to delays during the resolution of the VirtualBox shared folders name service. To fix these delays, add the following entries to the file \windows\system32\drivers\etc\lmhosts of the Windows guest:

255.255.255.255        VBOXSVR #PRE
255.255.255.255        VBOXSRV #PRE

After doing this change, a reboot of the guest is required.

---

