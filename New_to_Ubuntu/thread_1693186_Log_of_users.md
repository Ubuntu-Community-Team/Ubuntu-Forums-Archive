---
title: "Log of users"
date: 2011-02-22
forum: New to Ubuntu
---

### Post by bredsj on 2011-02-22
I have an Ubuntu server and I have to regularly logon via ssh. My router reports all activities at 23h00 everyday and recently I can see a lot of activity and it is reported that some people get pass the router. What I want to know is how to see a record of users that successfully logged onto the server?

I'll appreciate some help.

Thanks

---

### Post by wormyblackburny on 2011-02-22
Details should be in  /var/log/auth.log

[I highly suggest you read this tutorial for setting up openssh]("https://help.ubuntu.com/community/SSH/OpenSSH/Configuring")

---

### Post by fabricator4 on 2011-02-22
Have a look in /var/log and the file auth.log

New entries are at the bottom.  It should show authorized sessions. Others may be able to suggest other log files that you should look at.

Chris

---

### Post by bredsj on 2011-02-22
> **fabricator4 said:**
> Have a look in /var/log and the file auth.log

New entries are at the bottom.  It should show authorized sessions. Others may be able to suggest other log files that you should look at.

Chris

Thanks Chris

It is scary to see how one (or many) people try to continuously log on to my little silly server. However, it seems that the firewall is doing its job.

---

### Post by bredsj on 2011-02-22
> **wormyblackburny said:**
> Details should be in  /var/log/auth.log

[I highly suggest you read this tutorial for setting up openssh]("https://help.ubuntu.com/community/SSH/OpenSSH/Configuring")

Thanks, I actually got a professional (a friend who is a sysadmin) to set up the server including ssh. I'll look at the tutorial.

---

### Post by seawolf167 on 2011-02-22
You can also see who is currently logged in by running the command 

```
w
```

in a terminal

---

### Post by TeoBigusGeekus on 2011-02-22
```
last
```
Show a list of recently logged in users.

---

### Post by fabricator4 on 2011-02-22
> **bredsj said:**
> Thanks Chris

It is scary to see how one (or many) people try to continuously log on to my little silly server. However, it seems that the firewall is doing its job.

Yeah, I feel the same way when I look at the log reports from the firewall in my modem/router.

Just out of curiosity, are they trying to log in as root, or are they trying to guess a valid username and password?

Chris

---

