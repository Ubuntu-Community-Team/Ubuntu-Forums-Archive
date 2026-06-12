---
title: "OpenSSH server welcome message config"
date: 2008-10-16
forum: Networking &amp; Wireless
---

### Post by Tobywuk on 2008-10-16
Hello,

Im just wondering how to change the welcome message on the openSSH server which the users will see when trying to log in?

thanks.

---

### Post by iponeverything on 2008-10-16
edit:

/etc/motd

---

### Post by DataMatrix on 2008-10-16
in /etc/ssh/sshd_config there is a line:
```
#Banner /etc/issue.net
```
You can remove the "#" (uncomment) the line and then edit /etc/issue.net.
The only thing is that this message will be displayed after starting ssh connection and before asking the password for the user. The message that is showed after user has logged in successfully is in /etc/motd and /etc/motd.tail

Remember to restart sshd (~$ sudo /etc/init.d/ssh restart) (this doesn't interrupt current ssh session).

Strangely, I always get something like this on login:
```
user@client:~$ ssh user@server
Ubuntu 8.04.1 (from file /etc/issue.net)
user's password: *********
....(from file /etc/motd)
Last login .... (say last loggin)
....(from file /etc/motd)
....(from file /etc/motd.tail)
user@server:~$ _
```

I hope I've been helpful [-o< 8-[

---

### Post by Tobywuk on 2008-10-16
very helpful, thank you :)

---

