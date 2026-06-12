---
title: "Cant share folder in NTFS partition - Samba"
date: 2010-10-06
forum: New to Ubuntu
---

### Post by Verbeck on 2010-10-06
I cant change the permissions of files in an ntfs partition so that the other computers can access the files. but i can share files on an ext4 partition. any help :confused:

---

### Post by k33bz on 2010-10-06
How are you trying to change the permissions?

Just found this link, it may be useful to you or someone else.

[http://www.onlineconversion.com/html_chmod_calculator.htm]("http://www.onlineconversion.com/html_chmod_calculator.htm")

---

### Post by Morbius1 on 2010-10-06
2 options:

(1) Change the permissions of the ntfs partition by adding a line or altering the current line in /etc/fstab to accommodate the remote user.

For this we would need to know the output of these commands:
```
sudo blkid -c /dev/null
``````
cat /etc/fstab
``````
mount
```(2) Add a line to /etc/samba/smb.conf that will convert the remote user to you as far as that share is concerned.

For option (2) you would have to add the line:
```
force user = your_user_name
```Where that line goes depends on what method of Samba sharing you are using. There are two methods and the output of the following commands will tell us which one you are using:
```
net usershare info
``````
testparm -s
```

---

### Post by Verbeck on 2010-10-07
thanx, but neither worked so i formated the hard disk as ext4 :-| .so problem solved ...

---

