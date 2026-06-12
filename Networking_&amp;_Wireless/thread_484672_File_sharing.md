---
title: "File sharing"
date: 2007-06-26
forum: Networking &amp; Wireless
---

### Post by satimis on 2007-06-26
Hi folks,

F-7 (router IP add:192.168.0.11)
Ubuntu desktop 7.04 (router IP add: 192.168.0.12)
scp
ssh


I need to transfer files between the above PCs.  But the traffic is one way.

Ubuntu desktop 7.04
$ scp test.txt satimis@192.168.0.11:/path/to/dir```

The authenticity of host '192.168.0.11 (192.168.0.11)' can't be established.
RSA key fingerprint is 73:01:8f:8b:ba:9d:b0:c0:8b:f2:36:e3:47:a6:0e:9e.
Are you sure you want to continue connecting (yes/no)? yes
Warning: Permanently added '192.168.0.11' (RSA) to the list of known hosts.
satimis@192.168.0.11's password: 
test.txt                                      100%   18     0.0KB/s   00:00    

```

File transferred.


F-7
$ scp test-1.txt satimis@192.168.0.12:/path/to/dir```

ssh: connect to host port 22: Connection refused
lost connection

```


# cat /etc/ssh/ssh_config | grep Port```

   Port 22

```
Port 22 already uncommented.


Please help.  TIA


B.R.
satimis

---

### Post by PaulFr on 2007-06-26
**sudo apt-get install openssh-server** should do the trick.

---

### Post by satimis on 2007-06-26
Hi PaulFr,

Tks for your advice.

> 
**sudo apt-get install openssh-server** should do the trick.
I got my problem fixed.  I was surprised why F-7 box can connect other boxes on LAN but failed to communicate with the Ubuntu desktop 7.04 box.  I forgot it is a desktop only with openssl-client installed.

Something I can't understand;

$ sudo /etc/init.d/ssh restart
Password:```

 * Restarting OpenBSD Secure Shell server...                             [ OK ] 

```
It is OpenBSD Secure Shell server ???

$ sudo /usr/sbin/sshd restart```

Extra argument restart.

```

$ sudo /usr/sbin/sshd status```

Extra argument status.

```
Not sshd to start ssh ???


B.R.
satimis

---

### Post by PaulFr on 2007-06-26
Yes, the most popular SSH package for free OSes is OpenSSH (**[http://www.openssh.com](http://www.openssh.com)**) which is part of OpenBSD project.

To stop, start, restart, get status, etc., you have to use the **/etc/init.d/ssh** shell script (not the **/usr/bin/ssh** binary - which is the OpenSSH client). So /etc/init.d/ssh start, /etc/init.d/ssh stop, /etc/init.d/ssh restart, etc... FYI, the /etc/init.d directory contains scripts that are used by the OS to stop and start process during boot up and shutdown.

---

### Post by satimis on 2007-06-26
> **PaulFr said:**
> Yes, the most popular SSH package for free OSes is OpenSSH (**[http://www.openssh.com](http://www.openssh.com)**) which is part of OpenBSD project.

To stop, start, restart, get status, etc., you have to use the **/etc/init.d/ssh** shell script (not the **/usr/bin/ssh** binary - which is the OpenSSH client). So /etc/init.d/ssh start, /etc/init.d/ssh stop, /etc/init.d/ssh restart, etc... FYI, the /etc/init.d directory contains scripts that are used by the OS to stop and start process during boot up and shutdown.
Noted with tks.


satimis

---

