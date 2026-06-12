---
title: "Problem connecting via ssh"
date: 2019-07-28
forum: Networking &amp; Wireless
---

### Post by ulrichmuc on 2019-07-28
There are two hosts:
Host a running ubuntu 16.4
Host b running ubunto 18.4

I can ssh from a to b without problems.

However, when I try on b ssh user@a, I am asked for the password and provide it.
Then the connection is immediately terminated.
The password is correct: I tried to give a false one and get an appropriate error message.
The correct one is accepted; then I am immediately back to the shell in b.

Any ideas?

---

### Post by SeijiSensei on 2019-07-28
What do you see in /var/log/auth.log and /var/log/syslog on the machine that is refusing connections? Remember, logs are your friends.

On machine b, try using "ssh -vvv user@a" to increase the "verbosity" of the client.  Often that will identify the problem right away.

---

### Post by ulrichmuc on 2019-07-28
The two logfiles do not change when I attempt connection. The lalst entry is an hour old and due to some cron job.
The output of ssh --v is very long. Various authentication methods are tried, finally authentication by password,
which succeeds.(Otherwise I would see an error message, tried this with intentionally wrong password).

I attach the debug output.

MaybeI I should reinstall open ssh.
I did not install myself, it came with a new notebook that is sold with preinstalled ubuntu 18.4

---

### Post by The Cog on 2019-07-28
Maybe a dumb question but is user able to log on locally at machine a?

---

### Post by ulrichmuc on 2019-07-28
login <user> gives "login: Cannot possibly work without effective root",
but 
ssh<user>@<myhost> works as expected.

---

### Post by SeijiSensei on 2019-07-28
It's strange that you have no corresponding entry in /var/log/auth.log.  I use keys rather than a password, and see entries this on the server end when I connect:
```

Jul 28 14:40:22 linux-tv sshd[23523]: Accepted publickey for xxx from 192.168.100.59 port 51000 ssh2: RSA SHA256:FXYyLbgoZMXylGlkbpODbZanuUyGOXwtO1GiTvqw1Jk

```

If you use login at the console on machine a and run "ssh user@localhost" does that work?

---

### Post by ulrichmuc on 2019-07-28
login <user> gives "login: Cannot possibly work without effective root",
but 
ssh<user>@<myhost> works as expected.

---

### Post by ulrichmuc on 2019-07-28
Yes, ssh user@localhost does work and in that case the files auth.log, wtmp, lastlog, and syslog in /var/log are updated.
Also, I am able to connect from host a to three other hosts, Raspberry PI's.
And ssh from a PI into host a also works fine.
So the problem lies in host b.
Shall I reinstall Open SSH on host b?

---

### Post by SeijiSensei on 2019-07-28
Can't hurt.

---

### Post by The Cog on 2019-07-29
Try the ssh connection from B, then on B run the command "ip neighbor". Make sure the MAC address for A matches the MAC address that the command "ip addr" on A. I'm wondering of you have two machines with A's address.

---

### Post by ulrichmuc on 2019-07-30
I attach the output of "ip addr" and "ip neighbor" on both hosts.

Also, I made a new observation:
After ssh user@a I am in a new shell, but ls or hostname show that I am still an host b.
When I exit this shell, get:
logout
Connection to honolulu2 closed
(honolulu2 is the remote host a)

Reinstalling openssh-server did not change anything.

---

### Post by ulrichmuc on 2019-07-30
Another experiment:
As the files - including .-files and .-directories - had been copied from the remote host a,
I suspected this might be the reason for the trouble.
So I created a new user account "test". But ssh from there showed the same behaviour.

---

