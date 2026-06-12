---
title: "Mounting Samba Share with Read/Write"
date: 2007-02-23
forum: Networking &amp; Wireless
---

### Post by gavinjb on 2007-02-23
Hi,

I am trying to setup my Buffalo Network Drive to be able to be accessed by Linux, I have used the following command to mount the drive:

sudo mount -t smbfs //192.168.1.200/Data /media/Data -o username=gavinjb,passwor
d=mypassword,rw

But when mounted it only has read rights, currently my Buffalo drive is setup not to require logon for the share, but the mount command seems to expect a username and password when mounting smbfs shares.

I have noticed that when accessing through Remote Places (smb://192.168.1.200/Data) in KDE that I can write data to the drive, but when accessing through /media/Data it is read only.

Can someone please help


Gavin,

---

### Post by gavinjb on 2007-02-23
Found the problem, it seems that only root can write to the shares, does anyone know how I can resolve this, I dont want to have to mount under my user as I am going to add the mount points to fstab to mount on boot.


Thanks,


Gavin,

---

### Post by mrlarone on 2007-02-23
i ain't no expert so excuse me if this is dense.

have you tried chmod on the mouned drive:

sudo chmod 777 {hda?}

*WARNING*

777 (binary for 111 111 111) will set rwx on for everyone.  i forget exactly which number controls which group, and what they are called but i'm sure you can find it somewhere.

*/WARNING*

hope that helps

---

### Post by gavinjb on 2007-02-23
Thanks,

I thought I had done that but just double checked, and after setting the permissions, checked it and the permissions seem to go back to default which is read/modify for owner only (root).

---

### Post by gavinjb on 2007-02-26
Hi,

Found the solution all I needed to do was add the dmask=777, fmask=777 I have now setup the entries in fstab and I can write to the share with any user.

```

//192.168.1.200/Data /media/Data smbfs username=myuser,password=mypwd,dmask=777,fmask=777 0 0

```

Only problem now is whenever I write a file I get an error message saying "could not change permissions for <filename>", any idea how to resolve this?

Thanks,



Gavin,

---

