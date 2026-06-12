---
title: "Where is the sshd_config file in Ubuntu?"
date: 2010-03-01
forum: New to Ubuntu
---

### Post by Xeoncross on 2010-03-01
I'm trying to change the SSH port but I can't find the file.

```
/etc/ssh/sshd_config
```


The only thing listed in */etc/ssh/* is 

```
drwxr-xr-x   2 root root   4096 2009-10-27 13:09 .
drwxr-xr-x 143 root root  12288 2010-03-01 11:50 ..
-rw-r--r--   1 root root 125749 2009-10-22 14:58 moduli
-rw-r--r--   1 root root   1595 2009-10-22 14:58 ssh_config

```

---

### Post by ikt on 2010-03-01
> **Xeoncross said:**
> I'm trying to change the SSH port but I can't find the file.

```
/etc/ssh/sshd_config
```


The only thing listed in */etc/ssh/* is 

```
drwxr-xr-x   2 root root   4096 2009-10-27 13:09 .
drwxr-xr-x 143 root root  12288 2010-03-01 11:50 ..
-rw-r--r--   1 root root 125749 2009-10-22 14:58 moduli
-rw-r--r--   1 root root   1595 2009-10-22 14:58 ssh_config

```

Which version of ubuntu are you using and how did you install ssh?

On my 9.04 server I see this:

```
total 164
drwxr-xr-x   2 root root   4096 2009-10-23 13:50 .
drwxr-xr-x 136 root root  12288 2010-02-28 17:20 ..
-rw-r--r--   1 root root 125749 2009-01-29 07:31 moduli
-rw-r--r--   1 root root   1595 2009-01-29 07:31 ssh_config
-rw-r--r--   1 root root   1877 2009-09-06 21:37 sshd_config
-rw-------   1 root root    668 2009-09-06 21:29 ssh_host_dsa_key
-rw-r--r--   1 root root    600 2009-09-06 21:29 ssh_host_dsa_key.pub
-rw-------   1 root root   1675 2009-09-06 21:29 ssh_host_rsa_key
-rw-r--r--   1 root root    392 2009-09-06 21:29 ssh_host_rsa_key.pub 
```

---

### Post by Xeoncross on 2010-03-01
I am running Ubuntu 9.10 and SSH was already installed by the OS on first load.

---

### Post by Neezer on 2010-03-01
If I recall, sshd isn't installed by default on the desktop version, you need to install ssh-server. then you will have /etc/sshd/sshd_config file.

sudo apt-get install openssh-server I think will install the ssh server and set up a default config for sshd.

I'm not 100% sure though, about 98%.

---

### Post by ikt on 2010-03-01
> **Neezer said:**
> If I recall, sshd isn't installed by default on the desktop version, you need to install ssh-server. then you will have /etc/sshd/sshd_config file.


I'm running 9.04 server and I don't think it's installed by default on it either,

sudo apt-get install ssh 

will install it.

```
ikt@ikt-910:~$ sudo apt-get install ssh
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  openssh-server
Suggested packages:
  rssh molly-guard openssh-blacklist openssh-blacklist-extra
The following NEW packages will be installed:
  openssh-server ssh
0 upgraded, 2 newly installed, 0 to remove and 0 not upgraded.
Need to get 305kB of archives.
After this operation, 840kB of additional disk space will be used.
Do you want to continue [Y/n]? 
```

---

### Post by Neezer on 2010-03-01
So I just tracked down the wiki that I used to install it and it worked perfectly for me. I even have an RSA key authentication set up now.

[https://help.ubuntu.com/9.04/serverguide/C/openssh-server.html](https://help.ubuntu.com/9.04/serverguide/C/openssh-server.html)

Good luck.

---

### Post by Xeoncross on 2010-03-01
Ok, that makes sense. I still need to install a SSH daemon (hence the ssh**d**) in order to allow outside SSH connections. Thanks guys.

---

