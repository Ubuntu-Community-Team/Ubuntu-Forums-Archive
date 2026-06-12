---
title: "SSH on LAN Problems"
date: 2007-03-01
forum: Networking &amp; Wireless
---

### Post by CADMBFan on 2007-03-01
Hey all,

I'm a n00b trying to SSH from my windows XP machine to my Kubuntu system on my home network and I am unable to.  I have verified that sshd is running on the Kubuntu system, and I am able to ping the system at IP 192.168.0.106.

I am using cygwin, and when I attempt the following command:

ssh 192.168.0.106

I get the following error:

ssh: connect to host 192.168.0.106 port 22:  Connection refused

Any tips?  I am just trying to transfer a few files from my Windows XP system to my Kubuntu machine and am getting really frustrated in the process =/

- Chris

---

### Post by colo on 2007-03-01
Try tunning
```
sudo netstat -nlp | fgrep :22
```
on the Ubuntu box. If the output looks somewhat like this:
```
tcp        0      0 0.0.0.0:22              0.0.0.0:*               LISTEN      5005/sshd
```
everything's fine. If not, sshd is not running on its default port, hinting that you have fiddled around with something you shouldn't have. ;)


You should also try increasing the verbosity of your ssh-client by invoking the command with the "-vv"-switch, like
```
ssh -vv 192.168.0.106
```
THat should help you track down problems related to ssh itself.

---

### Post by CADMBFan on 2007-03-01
Hey,

Thanks for the quick reply!  This is what I got back from netstat, which looks a bit different from what you have...

tcp6       0      0 :::22                   :::*                    LISTEN     4              602/sshd

Is there something I need to do to set this up properly?

- Chris

---

### Post by colo on 2007-03-01
Well, you obviously got IPv6 enabled, that should not be harmful though. On a vanilla Ubuntu system you did not tamper with, OpenSSH is supposed to "just work" after you installed the "openssh-server" package... did you anything else when trying to get the daemon running?

Are you sure you're trying to connect to the right host/IP-address?

If the answers to the above questions are "no" and "yes" respecitvely, you might want to post the output of `iptables -vL` (from your ssh-enabled box), and `nmap IPADDRESSOFYOURSSHHOST` from another GNU/Linux-machine on your LAN here.

---

