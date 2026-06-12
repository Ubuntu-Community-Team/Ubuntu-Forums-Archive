---
title: "[SOLVED] Terminal Remote Control"
date: 2006-10-11
forum: Networking &amp; Wireless
---

### Post by borobudur on 2006-10-11
Hi, I'm trying to find a software where I can have kinda remote control over a terminal prompt. 

I don't want to use the whole graphical desktop of my remote machine, a terminal is just enough. 

I would like to copy files to my local computer for example.

Thanks for your suggestions.

---

### Post by bswilson on 2006-10-11
You want Secure Shell (SSH).  Install the SSH server and client, and you can remotely access your machine.

```
$ sudo apt-get install ssh-server ssh-client
```

---

### Post by borobudur on 2006-10-11
Great! That's what I was looking for. Thanks.

Here is what I did after installing ssh:

```
local_user@local_host:~$ **ssh -l remote_user ip_address**
remote_user@remote_host:~$ **ls /home/remote_user/**

local_user@local_host:~$ **sftp remote_user@ip_address**
sftp> **get /home/remote_user/images/picture.png **
```

---

