---
title: "Mounting a Wondows share with a space in the name"
date: 2023-08-21
forum: Networking &amp; Wireless
---

### Post by linuxlion2 on 2023-08-21
On my Ubuntu 20.04.6 system I mounted several Windows shares.
That works correct and I can read and write on that shares.

Now. I have mounted a Windows share with a space in the share name.
I used the next mount command:

mount -v -t cifs -o username=administrator,password=xxxxxxx "//winsys1/test data" /mnt/test_data

The mount succeed and I see the mount with the df command.

 However, if I run the command 'ls /mnt/test_data' I get the error message:

ls /mnt/test_data
ls: reading directory 'test_data': Invalid argument

The output of the strace from that ls commando shows that the systems call's stat,openat,fstat and mmap works correct on the mounted direcory /mnt/test_data
However the system call getdents64 give the result: "-1 EINVAL (Invalid argument)"


Could that be because of the space in the Windows share name?
Is there a solution to this?

---

### Post by TheFu on 2023-08-21
Did you happen to create the mount point first?  
```
sudo mkdir /mnt/test_data
```
systemd-mountd will create directories as needed (/etc/fstab or a manually created unit-file), but when you manually use **sudo mount**, the admin has the responsibility to ensure the mountpoint actually exists.

Try using the IP address instead of the hostname.  If you are running avahi, you can try using winsys1.local, but I don't know if that works.

There's also a question of SMB/CIFS versions matching.  If you have other CIFS shares from the same server working connected to this Ubuntu system, then that probably isn't the issue.

Not that this matters, but I generally use these mount options to mount my last MS-Windows system (Win7),
```
iocharset=utf8,rw,vers=2.1,uid=tf,gid=tf,file_mode=0664,dir_mode=0775,credentials=/etc/samba/win7lap-D.credentials  ://172.22.22.14/K
```
I think Win10+ support vers=3 as the minimum. Better security and performance.  Also, rather than putting the username/password in the mount command, it is best to place those into a "credentials" file.  Anything in a command line can be viewed by any user on the system.  Best not to post credentials to other computers for all to see.

Those are all the ideas I have. Try them in order. That's what I think is most likely.

---

