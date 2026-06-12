---
title: "Mounting Samba Share"
date: 2010-11-26
forum: New to Ubuntu
---

### Post by supraman215 on 2010-11-26
Through the GUI I can connect to my windows share no problem. when I try to add it to fstab that's where I have trouble. I get an error with this line:

//swingline/share /mnt/samba cifs guest,_netdev    0 0

[284237.871252] CIFS VFS: No username specified
[284237.871259] CIFS VFS: cifs_mount failed w/return code = -22

It's weird because I didn't have to enter a password when I connect from the Places Menu

Jef

---

### Post by bananas4370 on 2010-11-26
> **supraman215 said:**
> Through the GUI I can connect to my windows share no problem. when I try to add it to fstab that's where I have trouble. I get an error with this line:

//swingline/share /mnt/samba cifs guest,_netdev    0 0

[284237.871252] CIFS VFS: No username specified
[284237.871259] CIFS VFS: cifs_mount failed w/return code = -22

It's weird because I didn't have to enter a password when I connect from the Places Menu

Jef

You'll need to specify a username and password on the fstab line.

```
//server/share /mnt/samba smbfs username=username,password=password 0 0 
```

Change server to the server name and share to the sharename. And the username and password of the server. Add the above line to the end of /etc/fstab

Cheers
Patrick

---

### Post by supraman215 on 2010-11-26
Thanks Patrick. this is the error I get if I switch it to smbfs. But What username and password do i use if the windows side doesn't have a username or password?

[291363.461245] smbfs: mount_data version 1936029031 is not supported

---

### Post by bananas4370 on 2010-11-26
> **supraman215 said:**
> Thanks Patrick. this is the error I get if I switch it to smbfs. But What username and password do i use if the windows side doesn't have a username or password?

[291363.461245] smbfs: mount_data version 1936029031 is not supported

Try using

```
//server/share /mnt/samba smbfs username=guest,password= 0 0
```

Do you have smbfs installed? I think that's why you are getting that error.

```
sudo apt-get install smbfs
```

Cheers
Bananas

---

### Post by supraman215 on 2010-11-28
> **bananas4370 said:**
> 

Do you have smbfs installed? I think that's why you are getting that error.

```
sudo apt-get install smbfs
```

Cheers
Bananas

that worked fine. i would have thought ubuntu would have come with samba installed. THANKS

---

