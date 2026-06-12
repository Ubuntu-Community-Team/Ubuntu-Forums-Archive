---
title: "sshd keys - still prompting for root passwd"
date: 2020-06-20
forum: Networking &amp; Wireless
---

### Post by rsteinmetz70112 on 2020-06-20
I'm attempting to set up ras keys for ssh to allow remote rsync backups of all users home directory.

I've set up the keys for a normal user and that works as expected
I've generated keys for the root user and copied them to the server.

I edited /etc/ssh/sshd-config to change

```
#PasswordAuthentication yes
to 
PasswordAuthentication no
```

and
```
PermitRootLogin no
to 
PermitRootLogin without-password
```

But I'm still getting a prompt for a root login, which works.
But I don't want to do that with the crontab

I've obviously missed something.

I generated the root keys in a sudo shell I wonder if that makes a difference in the keys generated.

The goal is to allow root to make the backups via a crontab from a designated machine(s) and not be able to login as root using a password.
I ideally a regular user would be able to login using a password in case I need access and haven't been able to provide a key for the machine I'm logging in from.

---

### Post by rsteinmetz70112 on 2020-06-21
OK I've got one of two machines working. The other isn't working it still prompts for a password which always fails. I cn't figure out what is different between them.

---

### Post by The Cog on 2020-06-21
As far as I know, the two things that need configuring on the destination machine are:
1: /etc/ssh/sshd-config. You clearly know about this. Don't forget to restart the sshd daemon after changing the configuration.
2: ~/.ssh/authorized_keys. This needs to be in the home of the user that you are logging in as (presumably root, so /root/.ssh/authorized_keys). .ssh must have permissions drwx------, and authorized_keys must have permissions -rw-------, both must be owned by the user. They will be ignored if the permissions are not correct.

I frequently forget to tighten up the permissions and wonder why it doesn't work.

---

### Post by rsteinmetz70112 on 2020-06-21
I know I'm doing something wrong but I can't figure our what is is.

---

### Post by rsteinmetz70112 on 2020-07-07
I never did figure out what I did wrong but I simply deleted all of the keys and re installed them on the servers. Everything is working now

---

