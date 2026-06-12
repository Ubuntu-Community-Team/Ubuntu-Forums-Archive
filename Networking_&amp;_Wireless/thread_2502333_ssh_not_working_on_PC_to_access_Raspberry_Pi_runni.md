---
title: "ssh not working on PC to access Raspberry Pi running ubuntu."
date: 2024-11-10
forum: Networking &amp; Wireless
---

### Post by ujjwalrathod007 on 2024-11-10
I have issue running ssh service. The exact issue is as follows whn I try [HTML]ssh server@ip -vvv[/HTML]. Then I tried some suggestions from the following post but it did not help. I think some weird thing is happening with ssh on my PC

[https://askubuntu.com/questions/311558/ssh-permission-denied-publickey](https://askubuntu.com/questions/311558/ssh-permission-denied-publickey)

> debug3: send packet: type 50
debug2: we sent a publickey packet, wait for reply
debug3: receive packet: type 51
debug1: Authentications that can continue: publickey
debug2: we did not send a packet, disable method
debug1: No more authentication methods to try.
ubuntu@192.168.0.104: Permission denied (publickey).




---

### Post by TheFu on 2024-11-10
[https://blog.jdpfu.com/2015/08/17/troubleshooting-ssh-connections](https://blog.jdpfu.com/2015/08/17/troubleshooting-ssh-connections) is an ssh troubleshooting guide.  Definitely check the file and directory permissions.  Sometimes it is best to wipe the ~/.ssh/ directory on the both systems and start over completely, to ensure any left over keys or authorized host have been left behind.

---

