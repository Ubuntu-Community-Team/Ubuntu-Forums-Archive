---
title: "Fstab and SSH service in Raspbian Stretch Lite"
date: 2018-09-04
forum: Networking &amp; Wireless
---

### Post by sed_faster on 2018-09-04
Hello folks,

I have two doubts relative raspbery pi (Raspbian Stretch Lite).

First is, when I power on and try access this machine through IP "ssh pi@192.168.100.1" I receive this message error: "ssh: connect to host 192.168.1.16 port 22: Connection refused". I need turn on monitor in RPI and run this command "sudo service ssh restart". There is way restart or start ssh service after boot system?

Secondly, when I configure fstab like this:
```

UUID=CC5dffdgdfgdfgddfg496A    /media/folder   auto    defaults,uid=1000,gid=1000,umask=022   0       0

```

I can't write in /media/folder, I receive this message error:
```

$ ls -la /media/folder/
total 12
drwxr-xr-x 1 pi   pi   4096 Sep  2 23:20 .
drwxr-xr-x 3 root root 4096 Sep  4 19:23 ..
drwxr-xr-x 1 pi   pi   4096 Jun 28 08:39 System Volume Information

$ cd folder/
pi@raspberrypi:/media/folder $ ls
System Volume Information
pi@raspberrypi:/media/folder $ mkdir test
mkdir: cannot create directory 'test': Operation not permitted

```

Why this happen? But If I umount this drive I can write inside folder.

Thanks

---

### Post by sed_faster on 2018-09-04
If I umount usb drive and plug another computer and create any file, for example, sdfsdf.html. After this I'll turn the pen back on in RPI and the result it is this:

```

user@rpi:/media/folder $ sudo mount -a
user@rpi:/media/folder $ ls
index.html
user@rpi:/media/folder $ cd ..
user@rpi:/media $ ls
folder
user@rpi:/media $ ls -la folder/
total 12
drwxr-xr-x 1 pi   pi   4096 Sep  4 20:13 .
drwxr-xr-x 3 root root 4096 Sep  4 19:23 ..
drwxr-xr-x 1 pi   pi   4096 Jun 28 08:39 System Volume Information
-rwxr-xr-x 1 pi   pi      4 Sep  4 20:13 index.html
user@rpi:/media $ cd folder/
user@rpi:/media/folder $ ls
System Volume Information  index.html
user@rpi:/media/folder $ touch sdfdf.html
touch: cannot touch 'sdfdf.html': Permission denied
user@rpi:/media/folder $ sudo touch sdfdf.html
touch: cannot touch 'sdfdf.html': Permission denied

```

---

### Post by sed_faster on 2018-09-05
Hello,

I can solver the problem with ssh after boot. I followed this article: [https://www.raspberrypi.org/documentation/remote-access/ssh/README.md](https://www.raspberrypi.org/documentation/remote-access/ssh/README.md)

The problem with pen drive I still can't solve....

---

