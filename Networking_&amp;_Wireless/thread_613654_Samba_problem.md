---
title: "Samba problem"
date: 2007-11-15
forum: Networking &amp; Wireless
---

### Post by santhosh23 on 2007-11-15
Hi,

I am Using Ubuntu 7.10 Gutsy and have installed samba. When i mount a windows share i am able to see the share but when i click on the Dir it gives an error to check the spelling of the dir and that dir disappers but when i login to the share with smbclient it looks fine - i can see all the folders and files.

Thanks,
Santhosh

---

### Post by mikesignguy on 2007-11-15
we need more info ... what commands did you use to mount it .. is it a NTFS drive or fat 32.. or was it mounted automatically... were permssions set ... did  you a password to mount the drive.. is it local or a remote mount?

---

### Post by santhosh23 on 2007-11-15
Thanks for your Reply .

The command used to mount the drive is 

mount -t smbfs -o username=<UN>,password=<passwd> //ipaddress/dir /mountpoint

and the drive is ntfs partition. As posted earlier i can see the contents of the drive after its gets mounted but when i click on the icon it throws error "Could not find the dir,please check the spelling"and that icons disappears .However when i try to list the contents of the  share dir with :smbclient ¨ after i login into the samba prompt.

it is remount mount and the password is the domain controllers adminstrator&#347; password.


Thanks,
Santhosh

---

