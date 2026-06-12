---
title: "Very WEIRD problem with SSH ! :("
date: 2007-03-10
forum: Networking &amp; Wireless
---

### Post by asbesto on 2007-03-10
Hi all, i'm becoming MAD.

I can SSH on this server, but from it I can't SSH to anyone:

> 
asbesto@commercialista5:~$ ssh dante
Host key verification failed.
asbesto@commercialista5:~$ ssh gemini
Host key verification failed.
asbesto@commercialista5:~$ ssh corazzini 
Host key verification failed.
asbesto@commercialista5:~$ ssh borg


YES, i already removed .ssh/known_hosts.

I removed and reinstalled packages openssh_server and ssh...

no way, i have the same problem.

nothing appear in log files.

ssh -vvvvvvvvvvvvvvvvvvvvvvvv says :

> 
debug1: kex: client->server aes128-cbc hmac-md5 none
debug1: SSH2_MSG_KEX_DH_GEX_REQUEST(1024<1024<8192) sent
debug1: expecting SSH2_MSG_KEX_DH_GEX_GROUP
debug2: dh_gen_key: priv key bits set: 126/256
debug2: bits set: 510/1024
debug1: SSH2_MSG_KEX_DH_GEX_INIT sent
debug1: expecting SSH2_MSG_KEX_DH_GEX_REPLY
debug3: check_host_in_hostfile: filename /home/asbesto/.ssh/known_hosts
debug3: check_host_in_hostfile: filename /etc/ssh/ssh_known_hosts
debug3: check_host_in_hostfile: filename /home/asbesto/.ssh/known_hosts
debug3: check_host_in_hostfile: filename /etc/ssh/ssh_known_hosts
debug3: check_host_in_hostfile: filename /home/asbesto/.ssh/known_hosts
debug3: check_host_in_hostfile: filename /etc/ssh/ssh_known_hosts
debug2: no key of type 0 for host dante
debug3: check_host_in_hostfile: filename /home/asbesto/.ssh/known_hosts2
debug3: check_host_in_hostfile: filename /etc/ssh/ssh_known_hosts2
debug3: check_host_in_hostfile: filename /home/asbesto/.ssh/known_hosts
debug3: check_host_in_hostfile: filename /etc/ssh/ssh_known_hosts
debug2: no key of type 2 for host dante
debug1: read_passphrase: can't open /dev/tty: Permission denied
Host key verification failed.
asbesto@commercialista5:~$ 


I'm asking what the HELL is /dev/tty and why it try to open.

I will kill myself soon. 

](*,) ](*,) ](*,)

---

### Post by asbesto on 2007-03-10
This was the problem:

> 
root@commercialista5:/dev# v tty
-rw-r--r-- 1 root root 5, 0 2007-03-10 15:46 tty


Incredibly, /dev/tty was a file, instead of a device. :confused: 

So, now:

> 
root@commercialista5:/dev# ssh dante
The authenticity of host 'dante (10.10.1.2)' can't be established.
RSA key fingerprint is a6:55:ce:af:35:cf:57:78:bc:e3:24:47:33:fd:cf:9b.
Are you sure you want to continue connecting (yes/no)? 


there are no words for a problem like this. Never seen in years!
:confused: :confused: :confused: :confused: :confused:

---

### Post by motin on 2008-03-13
It would be great if you included the solution you found as well. That way others can benefit from the troubles you had and solved.

---

### Post by handydan918 on 2008-03-13
> **asbesto said:**
> This was the problem:



Incredibly, /dev/tty was a file, instead of a device. :confused: 

So, now:



there are no words for a problem like this. Never seen in years!
:confused: :confused: :confused: :confused: :confused:
Old Unix maxim say:
"In Unix, everything is a file."
Including devices....

---

### Post by koenn on 2008-03-13
> **asbesto said:**
> 
root@commercialista5:/dev# ssh dante
The authenticity of host 'dante (10.10.1.2)' can't be established.
RSA key fingerprint is a6:55:ce:af:35:cf:57:78:bc:e3:24:47:33:fd:cf:9b.
Are you sure you want to continue connecting (yes/no)?

there are no words for a problem like this. Never seen in years!
:confused: :confused: :confused: :confused: :confused:

This is not a problem, this is ssh asking if you are sure that the system with  RSA key fingerprint a6:55:ce:af:35:cf:57:78:bc:e3:24:47:33:fd:cf:9b  is the 'dante' you want to connect to. It's basic ssh security

---

