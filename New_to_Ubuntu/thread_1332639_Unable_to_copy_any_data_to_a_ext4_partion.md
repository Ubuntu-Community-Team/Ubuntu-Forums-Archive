---
title: "Unable to copy any data to a ext4 partion"
date: 2009-11-20
forum: New to Ubuntu
---

### Post by nishanvincent on 2009-11-20
Hi guys,
I have a small issue with one of my ext4 partition. I am unable to copy any data into this partition. Problem is I dont have permission to write any data in this folder. I cannot create any folder, cant copy any data etc. The other filesystem where ubuntu is installed, i have right. I just need some help to enable right to my user to this drive, since i am not able to use this drive in anyways to store data. I am attached a screenshot of the drive. Hope u guys can help.
Thanks

---

### Post by scorp123 on 2009-11-20
For technical reasons the super-user "root" is normally owner of all disks if not stated otherwise. That last part is important. "if not stated otherwise" ...

You could give yourself a folder on that disk, then make yourself owner of that folder. That's how I do it.

```
cd /media/where/the/disk/got/mounted/check/with/your/filemanager
sudo mkdir YourUserName
sudo chown -R YourUsername:YourUsername YourUserName

```

This would give you a folder named after you on that disk. And it would belong to your user and to your account's main group (the two are usually named the same).

So if you want to copy something onto that disk, simpy drop into that folder you just created ...

---

### Post by bodhi.zazen on 2009-11-20
> **nishanvincent said:**
> Hi guys,
I have a small issue with one of my ext4 partition. I am unable to copy any data into this partition. Problem is I dont have permission to write any data in this folder. I cannot create any folder, cant copy any data etc. The other filesystem where ubuntu is installed, i have right. I just need some help to enable right to my user to this drive, since i am not able to use this drive in anyways to store data. I am attached a screenshot of the drive. Hope u guys can help.
Thanks

use chown and chmod to change ownership and permissions.

---

### Post by renkinjutsu on 2009-11-20
here's a nice tutorial done by a member of this forum, kmandla.
[http://kmandla.wordpress.com/2007/03/08/howto-mounting-without-sudo/]("http://kmandla.wordpress.com/2007/03/08/howto-mounting-without-sudo/")

basically, he's telling you to add the device to your fstab with the "user" option

---

### Post by SuperSonic4 on 2009-11-20
```
sudo chown -R user:group /path/to/directory
```

Often user and group are both your username

---

### Post by nishanvincent on 2009-11-20
Thanks guys, the below post helped me to solve my problem.
Thanks again

> For technical reasons the super-user "root" is normally owner of all disks if not stated otherwise. That last part is important. "if not stated otherwise" ...

You could give yourself a folder on that disk, then make yourself owner of that folder. That's how I do it.

Code:

cd /media/where/the/disk/got/mounted/check/with/your/filemanager
sudo mkdir YourUserName
sudo chown -R YourUsername:YourUsername YourUserName

This would give you a folder named after you on that disk. And it would belong to your user and to your account's main group (the two are usually named the same).

So if you want to copy something onto that disk, simpy drop into that folder you just created ...

---

