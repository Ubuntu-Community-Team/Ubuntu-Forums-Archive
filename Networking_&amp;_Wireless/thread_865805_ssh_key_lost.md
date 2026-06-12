---
title: "ssh key lost"
date: 2008-07-21
forum: Networking &amp; Wireless
---

### Post by Ntweat on 2008-07-21
I have a network server which i used to control via ssh but i had formatted my computer to go from gutsy to hardy now the the key is lost and the server still has the old key of the client now how should i reconnect to it this is what i get when i m trying to connect

```

ntweat@IBM:~$ ssh bit@172.16.4.19 -p 9999
Read from socket failed: Connection reset by peer

```

---

### Post by Ntweat on 2008-07-21
**********************bump***************

---

### Post by kevdog on 2008-07-21
There is no way to recover the lost key, however the timeout error seems to suggest a different type of error.

What does ssh -vvv <user>@<serverip> output.  I think however you will have to physically be at the computer to reinstall your publick key (or have someone else do it for you).

---

### Post by Ntweat on 2008-07-21
here is the out put i have access to the server cant i delete the key from there and regenerate it???

```

ntweat@IBM:~$ ssh -vvv bit@172.16.4.19 -p 9999
OpenSSH_4.7p1 Debian-8ubuntu1.2, OpenSSL 0.9.8g 19 Oct 2007
debug1: Reading configuration data /etc/ssh/ssh_config
debug1: Applying options for *
debug2: ssh_connect: needpriv 0
debug1: Connecting to 172.16.4.19 [172.16.4.19] port 9999.
debug1: Connection established.
debug1: identity file /home/ntweat/.ssh/identity type -1
debug1: identity file /home/ntweat/.ssh/id_rsa type -1
debug1: identity file /home/ntweat/.ssh/id_dsa type -1
debug1: Remote protocol version 2.0, remote software version OpenSSH_4.6p1 Debian-5ubuntu0.5
debug1: match: OpenSSH_4.6p1 Debian-5ubuntu0.5 pat OpenSSH*
debug1: Enabling compatibility mode for protocol 2.0
debug1: Local version string SSH-2.0-OpenSSH_4.7p1 Debian-8ubuntu1.2
debug2: fd 3 setting O_NONBLOCK
debug1: SSH2_MSG_KEXINIT sent
Read from socket failed: Connection reset by peer

```

---

### Post by Ntweat on 2008-07-22
****************bump********************

---

### Post by Ntweat on 2008-07-24
got the solution 
run this at the server

sudo dpkg --configure -a

after that login from the client yipeeeeeeee

---

