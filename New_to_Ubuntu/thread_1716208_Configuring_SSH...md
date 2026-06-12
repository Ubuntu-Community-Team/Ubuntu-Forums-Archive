---
title: "Configuring SSH.."
date: 2011-03-28
forum: New to Ubuntu
---

### Post by mmautner on 2011-03-28
I'm working on configuring my server for SSH remote access by editing my /etc/ssh/sshd_config file to include the following:

```
Port <3000>
PasswordAuthentication no
AllowUsers <myaccount>
```I assume that "PasswordAuthentication no" means that I won't be able to login by typing a password--I'll have to have an SSH key.
I also assume that "Port XXX" means that if I wish to connect to my server using SSH, I have to specify this port number.

When I connect to my server using Putty on a Windows box, I use port 22, and I login with my username/password as normal--it works. How is this possible with the settings above in my sshd_config file?

Am I reading [this]("http://www.manpagez.com/man/5/sshd_config/") wrong?

 **PasswordAuthentication**
             Specifies whether password authentication is allowed.  The
             default is ``yes''.

 **Port**    Specifies the port number that **[sshd(8)]("http://www.manpagez.com/man/8/sshd/")** listens on.  The default
             is 22.  Multiple options of this type are permitted.  See also
             **ListenAddress**.

Is there some other config file that's superceding /etc/ssh/sshd_config?

---

### Post by aaaaalex on 2011-03-28
[Here]("http://lani78.wordpress.com/2008/08/08/generate-a-ssh-key-and-disable-password-authentication-on-ubuntu-server/") is a tut that should give you the answer (Step 9).

---

### Post by seawolf167 on 2011-03-29
Ensure you restart the service after you've made your changes

```
sudo service ssh restart
```

---

