---
title: "Problem mounting windows share"
date: 2008-06-06
forum: Networking &amp; Wireless
---

### Post by rextor on 2008-06-06
Now i am not sure if this problem is typical to me, but the archives here only solved half of my problem.

I am running Ubuntu 8.04 on my desktop. I need to connect to a windows share. Here's what i did - Installed smbfs and then run this command...

```
rex@006509:~/Desktop$ sudo smbmount //10.8.51.242/groups/ismfrwl/ /media/ism_share/ -o workgroup=IN,username=my.username,dir_mode=0777,file_mode=0777 --verbose
parsing options: workgroup=IN,username=my.username,dir_mode=0777,file_mode=0777
Password: 

mount.cifs kernel mount options unc=//10.8.51.242\groups,ip=10.8.51.242,pass=123456,ver=1,workgroup=IN,username=my.username,dir_mode=0777,file_mode=0777,prefixpath=ismfrwl/ 
rex@006509:~/Desktop$ ls /media/ism_share/ls: cannot access /media/ism_share/: Not a directory
n
```

Among the options above, IN is not the workgroup, but my domain name. (However one of the posts here instructed it to be done this way)

When i do an ls, this is what i see...
```
rex@006509:~/Desktop$ ls /media/ -l
total 12
drwxrwxrwt 1 root root     0 2008-06-06 12:33 ism_share
drwxrwxrwx 1 root root 12288 2008-06-04 11:36 win_c
rex@006509:~/Desktop$ 

```

The permissions for the folder ism_share were actually dr-------t. I modified it in some hope (which did not work :-P)

Why am i getting this error "/media/ism_share/: Not a directory" ?!

As a test i created a share on a PC adjacent to mine and the above method worked perfectly for that, however its not working for this share on the server.

---

### Post by rextor on 2008-06-10
bump...
can anyone help?

---

### Post by jonandrews on 2008-06-10
I've put an illustrated guide to integrating Ubuntu PC's into a Windows home network onto a website:

[www.europe.eclipse.co.uk/Ubuntu/](www.europe.eclipse.co.uk/Ubuntu/)

It is aimed at beginners, but may still be of help to you.

---

