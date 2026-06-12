---
title: "ubuntu Ubuntu 15.10 ssh keybased notworking"
date: 2016-05-24
forum: Networking &amp; Wireless
---

### Post by lance bermudez on 2016-05-24
I'm trying to set up ssh with keys so I do not have to use my user login password.
used
[https://help.ubuntu.com/community/SSH/OpenSSH/Configuring#disable-password-authentication](https://help.ubuntu.com/community/SSH/OpenSSH/Configuring#disable-password-authentication)
[https://help.ubuntu.com/community/SSH/OpenSSH/Keys](https://help.ubuntu.com/community/SSH/OpenSSH/Keys)

To disable password authentication, look for the following line in your sshd_config file:

#PasswordAuthentication yes

replace it with a line that looks like this:

PasswordAuthentication no

then I get 
$ ssh localhost
Permission denied (publickey).

If I leave it #PasswordAuthentication no
then I can ssh into computer.

.ssh
.ssh$ ls -l
-rw-r--r-- 1 lance lance  738 May 24 16:49 authorized_keys
-rw------- 1 lance lance 3326 May 24 16:47 id_rsa
-rw-r--r-- 1 lance lance  738 May 24 16:47 id_rsa.pub
-rw-r--r-- 1 lance lance  222 May 24 16:49 known_hosts

---

