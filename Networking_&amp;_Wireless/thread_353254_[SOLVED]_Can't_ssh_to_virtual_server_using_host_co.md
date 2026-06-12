---
title: "[SOLVED] Can't ssh to virtual server using host computer"
date: 2007-02-04
forum: Networking &amp; Wireless
---

### Post by altonbr on 2007-02-04
I can't seem to ssh to my virtual server, or else I get this:

> [FONT="Courier New"]@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@
@    WARNING: REMOTE HOST IDENTIFICATION HAS CHANGED!     @
@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@
IT IS POSSIBLE THAT SOMEONE IS DOING SOMETHING NASTY!
Someone could be eavesdropping on you right now (man-in-the-middle attack)!
It is also possible that the RSA host key has just been changed.
The fingerprint for the RSA key sent by the remote host is
a5:72:04:1c:16:2a:00:56:97:61:05:59:81:01:c6:88.
Please contact your system administrator.
Add correct host key in /home/brett/.ssh/known_hosts to get rid of this message.Offending key in /home/brett/.ssh/known_hosts:4
RSA host key for 192.168.2.103 has changed and you have requested strict checking.
Host key verification failed.[/FONT]

I have used aptitude to purge, clean, reinstall (or install) ssh on both computers, and I've even removed everything in /etc/ssh so ssh is forced to create new DSA and RSA keys. But I still can not connect to 192.168.2.103. I can connect to 192.168.2.102 FROM 192.168.2.103 and I can connect to 192.168.2.103 using any other machine, including Windows/WinSCP.

I know I'm changed the IP for 192.168.2.103 because it used to be on a virtual network, but now it's bridged on the back of 192.168.2.102... is that why it can not connect, or is there an easy way to 'rid of the configuration files so I can start fresh?

I know no one is getting in between, so it's not a "man-in-the-middle attack"

---

### Post by altonbr on 2007-02-04
Sorry, I guess it says it right in the error message: you just have to clean out ~/.ssh/known_hosts

```
sudo rm ~/.ssh/known_hosts
```

Problem solved.

---

