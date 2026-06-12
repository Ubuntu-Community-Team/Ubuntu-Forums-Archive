---
title: "editing files owned by groups"
date: 2009-06-22
forum: New to Ubuntu
---

### Post by RavUn on 2009-06-22
I'm a member of the apache group and I'm trying to modify httpd.conf.

ls -l shows:
```
-rw-r--r-- 1 apache apache 33726 May 10 11:16 httpd.conf

```
and groups shows:
```
$ groups
hWebUser apache

```

Shouldn't I be able to just open the file and edit it or is there some command I have to use to open it as an apache user?  When I open with vim it says it's read only.

---

### Post by Mornedhel on 2009-06-22
The group rights are the second cluster of permissions : rw-**r--**r--

It's only normal it's read-only for you. You need to set it to rw for the group : ```
sudo chmod g+w httpd.conf
```

---

### Post by tarps87 on 2009-06-22
-rw-r--r-- 1 apache apache 33726 May 10 11:16 httpd.conf

first rw- = read write user
second r-- = read group
third r-- = other

```
sudo chmod g+w httpd.conf
```
Should do the trick

---

### Post by t0p on 2009-06-22
Only the user apache (ie the program) has read and write permission for the file httpd.conf.  The *group* apache has just read-only permission.  You're a member of the group, which means you only have read-only access.

You need to change the permissions so the group apache has read and write access.  You need to open a terminal and give the command:

```
sudo chmod g+w httpd.conf
```

---

### Post by RavUn on 2009-06-22
oh ok.  I noticed it was user | group | everybody but I didn't know the difference between the user and the group I guess.  Thanks.


EDIT: They made me a member of the apache group so I could modify some apache settings when needed since I'm doing the web development.  Can anyone think of anything else I need write permissions for to be able to edit the apache settings?  It's a hassle trying to go through the IT dept and it's better to have everything up front.

---

### Post by tarps87 on 2009-06-22
If I remember correctly you will want write access to the www folder or if the config has been changed were ever the web content will be stored.

---

### Post by halitech on 2009-06-22
if you just need to make a one time change, just use sudo to give you rights to write to it

```
gksudo gedit /etc/apache2/http.conf
```or
```
sudo nano /etc/apache2/http.conf
```

---

