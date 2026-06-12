---
title: "HOWTO: Run openssh-server sshd from xinetd"
date: 2008-01-07
forum: Networking &amp; Wireless
---

### Post by djtm on 2008-01-07
Ever wanted to run sshd from xinetd under Ubuntu? Sometimes worked, sometimes not? Here's the fix!

First the xinetd config file:
```
service ssh
{
        socket_type     = stream
        protocol        = tcp
        wait            = no
        user            = root
#       server          = /usr/sbin/sshd
        server          = /usr/local/sbin/sshd_start
        server_args     = -i
}
```
Save it as /etc/xinetd.d/ssh

If you directly use sshd you might get the following problem shown in /var/log/auth.log:
```
sshd[8771]: fatal: Missing privilege separation directory: /var/run/sshd
```

So you save the following file as /usr/local/sbin/sshd_start
```
#!/bin/sh


if [ ! -d /var/run/sshd ]; then
        mkdir /var/run/sshd
        chmod 0755 /var/run/sshd
    fi

/usr/sbin/sshd $*

```
and make it executable:

```
#sudo chmod u+x /usr/local/sbin/sshd_start
```

Now simply reload xinetd with

```
#sudo /etc/init.d/xinetd restart
```

Done,
Enjoy!

ps.
Security considerations are not part of this Howto.
Thanks to [https://bugs.launchpad.net/ubuntu/+source/openssh/+bug/45234](https://bugs.launchpad.net/ubuntu/+source/openssh/+bug/45234) and [http://www.mail-archive.com/debian-bugs-closed@lists.debian.org/msg155044.html](http://www.mail-archive.com/debian-bugs-closed@lists.debian.org/msg155044.html)
Also try [http://ubuntuforums.org/showthread.php?t=86995](http://ubuntuforums.org/showthread.php?t=86995)

---

