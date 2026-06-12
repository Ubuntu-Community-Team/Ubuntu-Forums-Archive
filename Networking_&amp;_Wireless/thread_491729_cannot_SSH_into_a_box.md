---
title: "cannot SSH into a box"
date: 2007-07-04
forum: Networking &amp; Wireless
---

### Post by spiderworm on 2007-07-04
Hi,

I'm running Dapper on a machine and recently sshd broke... or something.  It was working before, but now I cannot ssh in, and running the following on the box:

ssh <user>@localhost 

... returns:

ssh_exchange_identification: Connection closed by remote host

sshd is running on the machine and not reporting any errors that I can see... in /var/log/auth.log, I can see:

refused connect from localhost.localdomain

Soooo wtf?  How do I find out why the connection is refused, or what do I do next?

Thank you,
David

---

### Post by t4thfavor on 2007-07-04
Sometimes when I try to connect to an sshd using the hostname I get no dice. Use the IP and it will probably work.

ssh -l user 192.168.1.1 -p port

---

### Post by cdeel77 on 2007-07-06
I'm having the same problem.  Suddenly I couldn't SSH to my server one day.

But it's only one client I cannot connect from.  Can't SSH from my Mac, but connecting via PuTTY from a windows box still works.

Entry in my auth.log is:
```
Jul  6 02:59:16 woolly sshd[4193]: refused connect from ::ffff:192.168.1.133 (::ffff:192.168.1.133)
```
Is this a problem on the server or client side?  How can I proceed with troubleshooting?

---

### Post by Mr. C. on 2007-07-06
Try using the localhost IP instead of localhost:

ssh user@127.0.0.1

This, and the problems others are experiencing, may be a simple hostname translation problem.  Report back with the results, and we'll go from there.

MrC

---

### Post by cdeel77 on 2007-07-12
No, what it turned out to be:
I was running a daemon called denyhosts, which does ... just what the name says. It adds hosts to the /etc/hosts.deny file.  This is to prevent brute-force ssh breakins, but also apparently affects people who occassionally fat-finger their own password.
I found my client machine's IP address right there in hosts.deny.
I changed the denyhosts.config, so hopefully it will purge the entry and I can log in again...

---

