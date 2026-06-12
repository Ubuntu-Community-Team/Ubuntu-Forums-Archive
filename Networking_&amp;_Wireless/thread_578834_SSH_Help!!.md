---
title: "SSH Help!!"
date: 2007-10-17
forum: Networking &amp; Wireless
---

### Post by herbster on 2007-10-17
I am trying to SSH into my box, I have set a static IP and opened up a port. I keep getting this:

```
bobby:~$ ssh -p3333 192.168.1.10
Connection closed by UNKNOWN
bobby:~$
```

At canyouseeme.org, my port is seen as open, as well as in Port Scan in Network tools.

I think the problem is I don't have SSH **host** keys. I currently have a key for ssh'ing into my website in ~/.ssh, but I need to generate a host key/host keys. For the life of me I can't find it on google, as I tried this: [http://www.lbl.gov/ITSD/CIS/faqs/UNIX_Faq/18.html](http://www.lbl.gov/ITSD/CIS/faqs/UNIX_Faq/18.html)   and got this:

```
bobby:~$ sudo ssh-keygen -b 1024 -f /etc/ssh_host_key -N ''
Generating public/private rsa key pair.
Your identification has been saved in /etc/ssh_host_key.
Your public key has been saved in /etc/ssh_host_key.pub.
The key fingerprint is:
f0:93:44:8f:e5:07:54:e3:33:b2:81:16:fd:76:89:84 root@dabox
bobby:~$
```

I am surely messing up/missing something, but I am at a loss :( Please help!! :(

---

### Post by herbster on 2007-10-17
Okay I just tried sshing into my public IP, and it is working but here is what's happening:

```
bobby:~$ ssh -v -p3333 99.227.xxx.xx
OpenSSH_4.3p2 Debian-8ubuntu1, OpenSSL 0.9.8c 05 Sep 2006
debug1: Reading configuration data /etc/ssh/ssh_config
debug1: Applying options for *
debug1: Connecting to 99.227.xxx.xx [99.227.xxx.xx] port 3333.
debug1: Connection established.
debug1: identity file /home/bobby/.ssh/identity type -1
debug1: identity file /home/bobby/.ssh/id_rsa type 1
debug1: identity file /home/bobby/.ssh/id_dsa type 2
debug1: Remote protocol version 2.0, remote software version OpenSSH_4.3p2 Debian-8ubuntu1
debug1: match: OpenSSH_4.3p2 Debian-8ubuntu1 pat OpenSSH*
debug1: Enabling compatibility mode for protocol 2.0
debug1: Local version string SSH-2.0-OpenSSH_4.3p2 Debian-8ubuntu1
debug1: Miscellaneous failure
No credentials cache found

debug1: Miscellaneous failure
No credentials cache found

debug1: SSH2_MSG_KEXINIT sent
Connection closed by 99.227.xxx.xx
bobby:~$
```

---

