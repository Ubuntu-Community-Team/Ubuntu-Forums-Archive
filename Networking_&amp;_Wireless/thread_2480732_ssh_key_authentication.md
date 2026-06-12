---
title: "ssh key authentication"
date: 2022-11-08
forum: Networking &amp; Wireless
---

### Post by zxcvb on 2022-11-08
Greetings all,

I have used plain ssh (username password authentication) successfully. I am trying key authentication.

3 computers:

A: Fedora Desktop  B: Ubuntu server  C: Ubuntu desktop

A connects to B. It is prompted for a **passphrase**; it accepts it. This, to me, means it is checking the key.

A will connect to C  or  C connect to A _Only_ if I enable “PasswordAuthention yes” in *sshd_config*.

This to me means it is NOT checking keys. Both ask for, and accept, a **username password**.

Even though each has the others public key in its *authorized_keys* file.

What can I be missing here?

---

### Post by &amp;KyT$0P# on 2022-11-08
> **zxcvb said:**
> A will connect to C  or  C connect to A _Only_ if I enable “PasswordAuthention yes” in *sshd_config*.

What is the exact error you get in each case when trying to connect with [FONT=Courier New]PasswordAuthentication[/FONT] set to [FONT=Courier New]No[/FONT]?
Do you get any additional useful information when specifying the [FONT=Courier New]-v[/FONT] flag several times in your [FONT=Courier New]ssh[/FONT] command?

---

### Post by TheFu on 2022-11-08
The best way to troubleshoot any ssh-based connectivity issues is to turn up the verbosity.

```
$ ssh -vvvv  user@remote
```

Then review the messages output.  In 20.04 and 22.04, some ciphers were removed and reordered by the openssh team.  This can cause compatibility issues between different released versions of ssh.  Also, in 22.04, rather than having sshd running all the time, they switched to using systemd like the old inet.d system to watch for inbound connections, then spawn the required daemon for the specific port. Some people had issues with that. I haven't noticed any problems, but my testing is fairly limited.

BTW, if you use the same key from the client to all the servers, then the ssh-agent will automatically provide the key, once unlocked, to other ssh-based logins.  I only need to unlock my ssh-keys once per login, thanks to ssh-agent.  Of course, I use the same keys only for systems under the same client's control. Different clients/customers get different ssh-keys.  I use the ~/.ssh/config file to automate which keys are used for each system. It is handy and provides clear documentation of different usernames, different remote DNS/IPs, and which keys are uses for each just by using a specific 'host' alias for each different connection.

---

