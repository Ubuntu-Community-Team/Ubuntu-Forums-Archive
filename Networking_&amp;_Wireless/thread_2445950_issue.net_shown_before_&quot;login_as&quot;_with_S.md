---
title: "issue.net shown before &quot;login as:&quot; with SSH"
date: 2020-06-22
forum: Networking &amp; Wireless
---

### Post by christian-franksson on 2020-06-22
Hello.
I hope someone can help me here...
As the topic says. a message before "login as:"

I have edited sshd_config with Banner /etc/issue.net and as I understand it it works like this


(I would like my massage here)
Login as:
(issue.net is shown)
Password:
(motd is shown)

I have done this many years ago but i don't remember how? I have an idea it had something to do with a file that was overwritten everytime the machine was rebooted, and another idea i have is that it was a file to edit that begun with a dot (.) that you had to edit.

If someone could help me with this my head will have much more hair on it in the future.

Regards Christian.

---

### Post by TheFu on 2020-06-22
$ sudoedit /etc/ssh/sshd_config
Edit the path to the banner file:
```
Banner /etc/ssh/sshd-banner
```

---

### Post by christian-franksson on 2020-06-23
This shows the message after entering username. I would like the message before ”login as:”

---

### Post by TheFu on 2020-06-23
> **christian-franksson said:**
> This shows the message after entering username. I would like the message before ”login as:”

Wow. I'm so sorry.  Your post said that you'd tried that already.  I just haven't seen a login for ssh in a long time. We don't allow the use of passwords with ssh, only allow ssh-keys or ssh-certs to be used.

The manpage says:
```
     Banner  The contents of the specified file are sent to the remote user
             before authentication is allowed.  If the argument is none then
             no banner is displayed.  By default, no banner is displayed.
```

There's 
```
     DebianBanner
             Specifies whether the distribution-specified extra version suffix
             is included during initial protocol handshake.  The default is
             yes.
```
Spend the last 15 minutes testing these different options on a VM and cleaning up all the spooge that Canonical adds as they like to logins. 

```
$ ssh jpoe@regulus
jpoe@regulus's password: 
```

Or even better w/ keys:
```
$ ssh regulus
Welcome to Ubuntu 20.04 LTS (GNU/Linux 5.4.0-37-generic x86_64)
Last login: Tue Jun 23 08:24:59 2020 from 172.22.22.6
```

I've been unable to force even a "login: " asking for a userid to be shown.

The "Banner" option seems to be the pre-authentication method to show something before a password.  

Some more searching ... [https://www.cyberciti.biz/tips/change-openssh-sshd-server-login-banner.html](https://www.cyberciti.biz/tips/change-openssh-sshd-server-login-banner.html)  which says that non-openssh clients may not support the banner correctly. They called out Putty.

Sorry, I don't have any answer that uses openssh.

---

