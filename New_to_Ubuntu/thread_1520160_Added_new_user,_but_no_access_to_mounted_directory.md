---
title: "Added new user, but no access to mounted directory"
date: 2010-06-29
forum: New to Ubuntu
---

### Post by mortuk on 2010-06-29
Hey

So I installed ubuntu, and have got a directory mounted using this - [http://ubuntuforums.org/showthread.php?t=288534](http://ubuntuforums.org/showthread.php?t=288534)

This all works fine with my main user (chris), however I have created a new user (cyn) and that user can see the mounted directory, but cannot rename / delete / paste into sub directories (but randomly can into the root directory)

I used the gui add user, and turned on all the admin type tickboxes, so ideally I wanted it to have the same access and permissions as my main user

Any ideas what I have to do to achieve this? Not too hot on users + permissions

---

### Post by mortuk on 2010-06-29
also it has the same issues with other local partitions

any ideas

---

### Post by mortuk on 2010-07-01
anyone? its got both directories as owned by chris, which is probably only that way because the chris account has been setup during installation.

---

### Post by laithbsoul on 2010-07-01
I'd say the problem is the permissions to said directories is not set to the new user idk i'm not much help as i've never created a second user :???: lol

---

### Post by mortuk on 2010-07-01
so i have created a new user just to make sure

```

sudo adduser cyn2
sudo adduser cyn2 admin
sudo adduser cyn2 adm
sudo adduser cyn2 sudo

```

so now that user can access the mounted share, and it doesn't have padlocks on everything which is a good start.

the user has read + write permissions on existing files + folders, however when the user creates a file, that file has a padlock and only read permissions

so now the problem is only on files that the user creates, what am I doing wrong?

---

### Post by Drenriza on 2010-07-01
Are the user in a group that has permissions to the partitions?
 
What is the permissions on the partitions that this user needs to gain access to?
 
have you ensured that this user has minimum read + execute permissions to directoryes, and minimum read permissions to files.

---

### Post by mortuk on 2010-07-02
well its owned by group chris, which I have also added user cyn2 too, and still no joy :(

---

### Post by Drenriza on 2010-07-03
how does the drive permissions look?

---

### Post by mortuk on 2010-07-05
well the mounted network share is set to 777 (but clearly isnt), and the local partitions would be nothing out of the ordinary. this is a freshly installed machine as of a few days ago

anyone?

---

### Post by mortuk on 2010-07-05
my line in /etc/fstab is
```
//192.168.0.40/webserver	/media/webserver	cifs	credentials=/root/.smbcredentials,iocharset=utf8,file_mode=0777,dir_mode=0777,uid=1001,gid=1001,nounix,noserverino,noperm 0 0
```

I added the uid=1001,gid=1001,nounix,noserverino,noperm bits after reading a few threads but now it seems that the owners of the files etc is correct but it wont let me read files I create

---

