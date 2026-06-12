---
title: "Weird: sshd &quot;connection closed&quot; when client IP is not resolvable"
date: 2017-07-15
forum: Networking &amp; Wireless
---

### Post by stlu on 2017-07-15
I have 3 systems running ubuntu, each with an sshd running.  Until a month ago, I was able to connect to all three without any errors.

Now one, and only one of these systems exhibits a weird problem: I cannot reproduce it on the other two, even though the /etc/ssh/sshd_config is identical for all three.

If a client has an IP address which cannot be resolved by the problematic system's /etc/resolv.conf, or its /etc/hosts, the sshd will delay about a minute and then close the connection.  My laptop is the one client that is not resolvable.  Several desktops are able to connect fine.  (the desktops are in /etc/hosts, the laptop is not)

I have seen some answers on other sites telling people to insert "UseDNS no" into sshd_config.  I have found that this makes it possible to ssh into the problematic system.  But WHY should I need to do this all of a sudden, on only one system?  It was working fine for at least two years prior!  I even tried putting "UseDNS yes" into the other two, in an effort to reproduce the problem, and they *still* allowed access from the unresolvable laptop!

Weird.

---

### Post by TheFu on 2017-07-15
There are settings with require the client hostname to be validated for ssh to work. I didn't look those up. 

Also, if the IPs are changing, tcp connections will drop.  In that situation, it is best to use tmux or screen to keep ssh sessions going.

Have you 
a) looked at the log files?
b) enabled verbose output for the ssh connections?
c) enabled debug output on the problem server?

ssh tends to provide excellent debug output that leads to the source of the issue.

---

