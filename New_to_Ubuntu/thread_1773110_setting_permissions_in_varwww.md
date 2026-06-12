---
title: "setting permissions in /var/www"
date: 2011-06-01
forum: New to Ubuntu
---

### Post by Pr1der on 2011-06-01
I've just installed Ubuntu 11.04 and am trying to set up a development environment for a pair of websites. I've installed Apache and it correctly serves the default test page. It runs as www-data. I want to place the 2 websites in subdirectories of /var/www and allow several developers to access the files. I tried to do this by creating the subdirectories, setting their permissions to 775, changing their group ownership to www-data (instead of root), setting the guid bit, and placing one of the developer user names into the group www-data. After all of this, I see the following:

jim@MyXPS400:/var/www$ cat /etc/group | grep www
www-data:x:33:jim
jim@MyXPS400:/var/www$ ls -al
total 16
drwxr-xr-x  4 root root     4096 2011-05-31 23:08 .
drwxr-xr-x 16 root root     4096 2011-05-31 11:22 ..
drwxrwsr-x  2 root www-data 4096 2011-05-31 23:08 XPStestbed
jim@MyXPS400:/var/www$ ls -al XPStestbed
total 8
drwxrwsr-x 2 root www-data 4096 2011-05-31 23:08 .
drwxr-xr-x 4 root root     4096 2011-05-31 23:08 ..

All seemed well, but when I tried to create a file in the subdirectory, it failed:

jim@MyXPS400:/var/www/XPStestbed$ touch test
touch: cannot touch `test': Permission denied

Why is that?

Thanks,
jim

---

### Post by wojox on 2011-06-01
You still nedd sudo.

```
sudo touch test
```

---

### Post by Miljet on 2011-06-01
> drwxrwsr-x 2 root www-data 4096 2011-05-31 23:08 XPStestbed

I might be wrong but it seems to me that the permissions should be drwxrwxr-x. In other words, your post is showing an "s" where it should be an "x".

---

### Post by lombardoja on 2011-06-02
The directories and all files should be owned by www-data user and www-data group. Then, you can  add your developers as users and add www-data as secondary groups for them to grant read/write/execute to them. Just make sure to fix the file permissions to be as strict as possible before rolling out in production!

```
sudo chown -R www-data:www-data /var/www
cd /var/www
chmod -R 775 *
```

---

### Post by Pr1der on 2011-06-02
> **wojox said:**
> You still nedd sudo.

```
sudo touch test
```

While that would work, that's not what I was trying to set up. I want any user in the group www-data to be able to create, modify, and delete files in /var/www/XPStestbed. Since I'm in that group, and the subdirectory has group ownership by www-data and has rwx permissions with the setguid bit, it seems to me that I should be able to create a file without using sudo, and the created file should have group www-data (because of the setguid) and be editable by anyone else in the group www-data... and they don't have sudo available to them.

---

### Post by Pr1der on 2011-06-02
> **lombardoja said:**
> The directories and all files should be owned by www-data user and www-data group. Then, you can  add your developers as users and add www-data as secondary groups for them to grant read/write/execute to them. Just make sure to fix the file permissions to be as strict as possible before rolling out in production!

```
sudo chown -R www-data:www-data /var/www
cd /var/www
chmod -R 775 *
```


Why can't /var/www remain owned by root, and just /var/www/XPStestbed be changed? Why isn't it sufficient just to chgrp /var/www/XPtestbed to www-data, and make it rwx for that group? At the moment there are no development files in the subdirectories... I'm just testing the setup. So I didn't do any recursive changes.

---

### Post by Pr1der on 2011-06-02
As a followup, I made /var/www/XPStestbed writeable by everyone; it became 
drwxrwsrwx  2 root www-data 4096 2011-05-31 23:08 XPStestbed
and then I was able to create a file there. Seems to me that this means that the OS didn't think I was in the group www-data, though I had added myself to it first. I'll have to look more closely at that.

---

### Post by Pr1der on 2011-06-02
OK... problem solved. I rebooted the system, and everything works as expected. All I can think of is that when I added myself to group www-dat it wasn't recognized because I was still in the same login session.

Thanks for the suggestions; they made me keep poking at it.

---

