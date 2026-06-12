---
title: "Ubuntu wont let me add files to 2ndary Hard drive"
date: 2009-09-29
forum: New to Ubuntu
---

### Post by timinator94 on 2009-09-29
Ubuntu wont let me add files to 2ndary Hard drive
It says i dont have permissions to add files.....
I used partition editor to format to ext3.....
Please help me!!!!!!!

---

### Post by Ocxic on 2009-09-29
find the mount point with "mount"
then chown the directory:
"sudo chown username /media/mount_point"

---

### Post by timinator94 on 2009-09-29
how do i find the mount point
Sorry im an aspiring 14yr old computer genius who dosnt know much about ubuntu

---

### Post by drs305 on 2009-09-29
> **timinator94 said:**
> how do i find the mount point
Sorry im an aspiring 14yr old computer genius who dosnt know much about ubuntu

Welcome to Ubuntu.

To run the mount command, go to the panel and select Applications, Accessories, Terminal.
In the terminal, type:
```
mount
```

We also can confirm the type of partition (ext3), as the permissions and how you assign them vary depending on the file system. The mount command will tell us this also.

I also highly recommend the free e-book:
[http://www.ubuntupocketguide.com/index_main.html]("http://www.ubuntupocketguide.com/index_main.html")

---

### Post by powel212 on 2009-09-29
The full totorial on adding a new hard drive is 

[here]("https://help.ubuntu.com/community/InstallingANewHardDrive")

Read it through entirely and you'll have a better understanding of what is going on and how to do what you need.

I hope that helps

Powel

---

### Post by timinator94 on 2009-09-29
Yeah,,, I got the ebook thanks

---

