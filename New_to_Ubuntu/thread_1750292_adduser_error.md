---
title: "adduser error"
date: 2011-05-05
forum: New to Ubuntu
---

### Post by fabio__ on 2011-05-05
Hi all,
I've got a problem managing users on ubuntu server.

When I try to create a new user I receive the following errors:
  sudo adduser test
 Adding user 'test' ...
 Adding new group 'test' (1009) ...
 Adding new user 'test' (1008) with froup 'test' ...
 Creating home directory '/home/test' ...
 Copying files from /etc/skel' ...
 passwd: Authentication token manipulation error
 passwd: password unchanged
 Try again? [y/N]


The same problem occured when I try to change the password of an existing user.

These the errors:
  sudo passwd <username>
  [sudo] password for <user>:
  Error
  passwd: Authentication token manipulation error
  passwd: password unchanged

Seems that these errors were caused by wrong chmod on /var directory but I'm not sure.

Anyone can help me?

Thanks in advance.

Fabio

---

### Post by blind2314 on 2011-05-05
> **fabio__ said:**
> Hi all,
I've got a problem managing users on ubuntu server.
 
When I try to create a new user I receive the following errors:
sudo adduser test
Adding user 'test' ...
Adding new group 'test' (1009) ...
Adding new user 'test' (1008) with froup 'test' ...
Creating home directory '/home/test' ...
Copying files from /etc/skel' ...
passwd: Authentication token manipulation error
passwd: password unchanged
Try again? [y/N]
 
 
The same problem occured when I try to change the password of an existing user.
 
These the errors:
sudo passwd <username>
[sudo] password for <user>:
Error
passwd: Authentication token manipulation error
passwd: password unchanged
 
Seems that these errors were caused by wrong chmod on /var directory but I'm not sure.
 
Anyone can help me?
 
Thanks in advance.
 
Fabio
 
 
Well, if you think that's the issue, let's check the permissions on /var. Post the output of ```
ls -l /
``` from a terminal window.

---

### Post by fabio__ on 2011-05-06
That's the output of "ls -l /".

drwxr-xr-x  30 root  root      4096 2010-12-15 11:10 var

Thanks,
Fabio

---

### Post by fabio__ on 2011-05-06
I' see that the passwd and shadow files contain the new user

passwd:
test:x:1008:1009::/home/test:/bin/bash

shadow:
test:!:15099:0:99999:7:::

I've got the same result trying to change password using "sudo - su test".

That is the code output:

fabio@ubuntu:/etc$ sudo su - test
test@ubuntu:~$ passwd
Changing password for test.
(current) UNIX password:
passwd: Authentication token manipulation error
passwd: password unchanged
test@ubuntu:~$ passwd
Changing password for test.
(current) UNIX password:
passwd: Authentication token manipulation error
passwd: password unchanged

Which files use passwd command?

---

