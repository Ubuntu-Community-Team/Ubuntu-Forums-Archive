---
title: "nfs with multipule users"
date: 2007-04-25
forum: Networking &amp; Wireless
---

### Post by 25an on 2007-04-25
Hi!

I am having some problem with nfs and the permissions created when a user is creating a file in 
a mounted nfs dir.

The server have two users A and B both these users belong to the group C.
The there is two clients which have the same user accounts and group as above.
I have created a partition on the server workspace that is mounted on /opt and this dir is then share with nfs.
The two clients is mounting the nfs share during boot up after I had configured /etc/fstab everything is fine so far. The mounted nfs share on the clients is mounted on /opt/workspace

drwxrwxr--  6 A C 4096 2007-04-25 14:53 workspace

The problem occues when a user is creating a file or dir in the nfs share then the file will get the permission

-rw-r--r--  1 A A     0 2007-04-25 14:53 test

I would like it be as above so the group C will get rw- on a file and rwx on a dir I dont want to change umask since that will mean that if a user  is creating a file in there /home/ dir then other users can write and in that file.

This is what I am aiming for

-rwxrwxr--  1 A C    0 2007-04-25 14:53 test
drwxrwxr--  1 A C    4096 2007-04-25 14:53 test_dir

How can I solve this so that when a user is creating a file or dir the owners will be the user and the group C instead of the A or B group as it is now.

---

### Post by kidders on 2007-04-26
Hi there,

It looks as though you have two options:[LIST]
[*]Change user A's primary group to C, and alter user A's default umask.
[*]Set the SGID bit on all directories you want to affect, and alter user A's default umask.[/LIST]> **25an said:**
> I dont want to change umask since that will mean that if a user is creating a file in there /home/ dir then other users can write and in that file.I'm not sure I follow you there. Your current umask appears to grant unrestricted read access to new files. Changing it would allow you to prevent this.

> **25an said:**
> The problem occues when a user is creating a file or dir in the nfs share then the file will get the permission

-rw-r--r--  1 A A     0 2007-04-25 14:53 testThis is standard behaviour. The permissions (0644) come from the working environment's umask, and the user & group (A:A) come from /etc/passwd (or wherever your account information is being kept).

---

