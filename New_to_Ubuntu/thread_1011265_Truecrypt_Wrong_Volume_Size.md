---
title: "Truecrypt Wrong Volume Size"
date: 2008-12-14
forum: New to Ubuntu
---

### Post by sempsteen on 2008-12-14
Hi everyone,
I cannot setup an encrypted partition with Truecrypt v6.1a. If you help me I'd be very glad. Here is my problem:
First I've resized my primary partition by using GParted to open up a 10GB space for a new partition that is going to be secured:

[[IMG]http://img515.imageshack.us/img515/1288/truecrypt01pm2.th.jpg[/IMG]](http://img515.imageshack.us/my.php?image=truecrypt01pm2.jpg)

Then I'm starting Truecrypt GUI with admin:
```
$sudo truecrypt
```

I'm following the Truecrypt GUI installation instructions located on Ubuntu Help Section. In "Volume Location" screen I'm typing /dev/sda3. When it comes to "Outer Volume Size" screen it displays available free space as 1008M despite of having a 10GB free partition:

[[IMG]http://img267.imageshack.us/img267/3803/truecrypt02sd6.th.jpg[/IMG]](http://img267.imageshack.us/my.php?image=truecrypt02sd6.jpg)

Although I haven't finished the whole process it seems like working fine if I enter a value less than 1008M here but of course 1GB is not enough for me. If I enter a bigger value than or equal value of 1008M it doesn't warn about it and it starts formatting, and it formats until it came to the 1008M level and then gives error: "Resource temporarily unavailable: /dev/sda3":

[[IMG]http://img241.imageshack.us/img241/9753/truecrypt03tm2.th.jpg[/IMG]](http://img241.imageshack.us/my.php?image=truecrypt03tm2.jpg)

After this point I can't go any further, I exit the application.

Thanks a lot

---

### Post by Michaelg14 on 2008-12-14
I have done this in Ubuntu but don't remember much about it.  I think you have to create the partition first.

Without the partition, when trying to create an outer volume I think it wants to use the whole device.

---

### Post by sempsteen on 2008-12-15
Thank you very much, your post helped me to solve my problem and I successfully created everything.

But now I have another problem with file permissions. When TrueCrypt mounts a partition, it creates a mount point with read,write and execute permissions to user (drwx------), and every file or folder that I copy to the encrypted drive gets the same permissions (-rwx------ or drwx------).

Is there a way to fix this?
Thanks.

---

### Post by Michaelg14 on 2008-12-15
Afraid I don't know much about permissions.  I think you can set levels by file, directory, or device.  Try setting different permissions on a directory level.

You probably need a new question with a different topic.

---

### Post by gTinker on 2008-12-15
[QUOTE=sempsteen]
But now I have another problem with file permissions. When TrueCrypt mounts a partition, it creates a mount point with read,write and execute permissions to user (drwx------), and every file or folder that I copy to the encrypted drive gets the same permissions (-rwx------ or drwx------).

Is there a way to fix this?
Thanks.[/QUOTE]

What is it that you think needs to be fixed? It seems to me the owner of a file should have those permissions.

---

### Post by sempsteen on 2008-12-15
I want the system to preserve permissions when I copy them to the encrypted drive. If a file permission is 644 then it should remain the same.

---

### Post by yankee83 on 2009-06-20
Sorry, did you find any solution for the permissions problem? I have the same one with an outer volume; the hidden one is working fine, though.

---

### Post by Francewhoa on 2012-01-07
Same here. When creating a new Truecrypt volume, at the end of the process it returns the error message *"Resource temporarily unavailable:"*

To fix that I re-started over but **reduced the Truecrypt volume size about 6% or more.** Truecrypt version 6.x usually needs around 6% more space than the current drive free space. For example, if your physical drive says 1000GB free space but Truecrypt returns an error message while creating a 1000GB Truecrypt volume, then try again with a Truecrypt volume at 940GB or less. It works.

---

### Post by sleepingdragon on 2012-01-09
Truecrypt 7.1 is available which may help resolve some problems. There's been a lot of bug fixes between 6.1 and 7.1

[truecrypt.org]("http://truecrypt.org")

---

