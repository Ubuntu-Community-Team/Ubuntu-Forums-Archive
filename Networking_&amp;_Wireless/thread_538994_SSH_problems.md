---
title: "SSH problems"
date: 2007-08-30
forum: Networking &amp; Wireless
---

### Post by Arma on 2007-08-30
Hi,

I've installed the following : Ubuntu Feisty Fawn (native to the machine, been using it since release now), and 2 VMs over VMWare : Windows XP and Ubuntu 7.04 server.

Installed ssh on both ubuntu installations, and got putty on the xp machine. I've also setup a dynamic dns service (as my internet ip isn't static), and also set up a virtual server on the router so that any connection to my public ip on port 22 is redirected to the native machine. Everything works fine till then.

Now, whenever I try connecting from the native machine to the ubuntu vm, or vice-versa, using internal network ips, I don't get a prompt requesting a password, and no errors, just a cursor. If i connect through putty on the xp machine to the ubuntu vm, using private ip it works just fine. If I try to do so to the native ubuntu installation, it doesn't work, I have to do it using my public ip/dns hostname.

Does anyone happen to know how to fix it? 

Thanks in advance

---

### Post by Arma on 2007-09-01
This is the output of ssh -v :

matt@matt-desktop:~$ ssh -v maintain@192.168.2.161
OpenSSH_4.3p2 Debian-8ubuntu1, OpenSSL 0.9.8c 05 Sep 2006
debug1: Reading configuration data /etc/ssh/ssh_config
debug1: Applying options for *
debug1: Connecting to 192.168.2.161 [192.168.2.161] port 22.
debug1: Connection established.
debug1: identity file /home/matt/.ssh/identity type -1
debug1: identity file /home/matt/.ssh/id_rsa type -1
debug1: identity file /home/matt/.ssh/id_dsa type -1
debug1: Remote protocol version 2.0, remote software version OpenSSH_4.3p2 Debian-8ubuntu1
debug1: match: OpenSSH_4.3p2 Debian-8ubuntu1 pat OpenSSH*
debug1: Enabling compatibility mode for protocol 2.0
debug1: Local version string SSH-2.0-OpenSSH_4.3p2 Debian-8ubuntu1
debug1: SSH2_MSG_KEXINIT sent
Connection closed by 192.168.2.161
matt@matt-desktop:~$ 

Any ideas?

---

### Post by wirelessmonkey on 2007-09-01
This is probably a vnmet configuration issue.  Please post the output of ifconfig for each of the listed vmnet adapters.

---

