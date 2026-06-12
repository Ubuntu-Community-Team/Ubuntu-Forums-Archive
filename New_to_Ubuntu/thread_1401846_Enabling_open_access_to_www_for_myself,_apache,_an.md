---
title: "Enabling open access to www for myself, apache, and apps"
date: 2010-02-08
forum: New to Ubuntu
---

### Post by Xeoncross on 2010-02-08
I want to allow access to the www directory for myself and any of the languages or applications (eclipse) that I use. This is for a personal development PC and not production.

By default the www directory was owned by **root root**. This was causing PHP to receive a permission error when trying to run .php files. So to fix this,

```
sudo chmod -R 0777 /var/www
```

However, when I would create new directories then PHP would have the same problem again since the chmod only works for directories that exist at the time it is run. So then I changed myself to the owner (leaving the group still as root).

```
sudo chown -R david /var/www
```

However, I'm not sure this fixes the problem and I also am not sure this is the right way to handle this. I would much rather do something like assign the files to a group both myself (and my apps) and the server apache/php would be in. My guesses is that would be a better practice. However, since I am new to linux I'm not sure what I should be doing so I would appreciate a best-practices reply. Also, is apache another user account? Or does it run under my account?

---

### Post by ggaaron on 2010-02-08
Apache has it's own user, I don't really remember what it is called under Ubuntu. ps aux | grep apache will give you the name (in the first column). You can set ACL that your/apache user will be automatically allowed to access any new files in www directory. See man setfacl.

---

### Post by Xeoncross on 2010-02-08
I'm not sure what to make of the output - does this mean apache runs under root..?

```
david@desktop:/$ ps aux | grep apache
root      1677  0.0  0.2 188040  9040 ?        Ss   12:05   0:00 /usr/sbin/apache2 -k start
www-data  1682  0.0  0.1 188564  7416 ?        S    12:05   0:00 /usr/sbin/apache2 -k start
www-data  1683  0.0  0.1 188724  7604 ?        S    12:05   0:00 /usr/sbin/apache2 -k start
www-data  1684  0.0  0.1 188132  7012 ?        S    12:05   0:00 /usr/sbin/apache2 -k start
www-data  1685  0.0  0.1 188132  6792 ?        S    12:05   0:00 /usr/sbin/apache2 -k start
www-data  1686  0.0  0.1 188132  6792 ?        S    12:05   0:00 /usr/sbin/apache2 -k start
www-data  4203  0.0  0.1 188132  7008 ?        S    12:12   0:00 /usr/sbin/apache2 -k start
david     5836  0.0  0.0   7336   876 pts/0    R+   13:41   0:00 grep --color=auto apache

```

and trying the second command returned an error

```
No manual entry for setfacl
```

---

### Post by ggaaron on 2010-02-08
Apache runs as www-data. For setfacl it seems that you'll have to install acl package. Here is this manual online: [http://manpages.ubuntu.com/manpages/karmic/man1/setfacl.1.html](http://manpages.ubuntu.com/manpages/karmic/man1/setfacl.1.html)

---

### Post by Xeoncross on 2010-02-08
So does that mean that I should make myself a member of www-data and then change the group owner of /var/www to www-data? Or is it fine how I have it?

---

### Post by ggaaron on 2010-02-08
You can do it in many ways. ACL would be most flexible. Adding yourself to www-data and changing owner of www to www-data will probably work, but keep in mind that newly created files will be owned by your user, not www-data. Still usually by default new files are accessible by anyone so it should work. You can also use mod_userdir and get rid of permission problems altogether=)

---

