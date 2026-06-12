---
title: "SSH logins only work sometimes"
date: 2014-03-27
forum: Networking &amp; Wireless
---

### Post by ygoe on 2014-03-27
I'm running Ubuntu 10.04 LTS on my web server. On Monday (3 days ago) everything was still fine. Today I noticed that SSH logins only work sometimes. For some accounts, it mostly works on the second try, for others I need 20 retries to get a connection. Restarting sshd helps for 1 or 2 connections to work for sure, but that's it. The rest is a lottery.

I have installed the openssh server update of 2 days ago just now, but that didn't help anything. It was up-to-date before that. The logs say nothing but this:

Mar 27 20:56:12 mond init: ssh main process (21278) terminated with status 255

That seems to happen when I close a connection, or when a new one doesn't work, I don't know what it means. It doesn't say. There are no other messages containing "ssh" in the last week.

Does anybody know what's up here and how it can be resolved?

---

### Post by Dave_L on 2014-03-28
The log file you're checking is /var/log/auth.log?

Have you tried changing the LogLevel option in /etc/ssh/sshd_config to display more info?

> LogLevel

             Gives the verbosity level that is used when logging messages from
             sshd(8).  The possible values are: SILENT, QUIET, FATAL, ERROR,
             INFO, VERBOSE, DEBUG, DEBUG1, DEBUG2, and DEBUG3.  The default is
             INFO.  DEBUG and DEBUG1 are equivalent.  DEBUG2 and DEBUG3 each
             specify higher levels of debugging output.  Logging with a DEBUG
             level violates the privacy of users and is not recommended.

[http://manpages.ubuntu.com/manpages/lucid/en/man5/sshd_config.5.html](http://manpages.ubuntu.com/manpages/lucid/en/man5/sshd_config.5.html)

---

### Post by ygoe on 2014-03-28
auth.log. I forgot about that one. syslog contained so much information that I believed that was everything.

Reading the logs of that time, I saw that there was/is an intensive root login attack from a Chinese dial-up connection going on. (Not that they could ever guess my password, I don't even know it myself.) This may have used all resources so that SSH couldn't accept any new connection and threw me out most of the time without even asking for my user name.

Today it works fine again. But I can still find some occasional login requests from that host. I may need to adjust my firewall...

---

### Post by Lars Noodén on 2014-03-28
Definitely keep root login turned off.  

```

PermitRootLogin no

```

You can also do rate limiting in iptables.  This assumes you have other rules in place to allow established and related connections and that the chain defaults to drop or reject:

```

ip6tables -I INPUT -p TCP --dport 22 -m state --state NEW -m limit --limit 4/minute --limit-burst 5 -j ACCEPT
iptables  -I INPUT -p TCP --dport 22 -m state --state NEW -m limit --limit 4/minute --limit-burst 5 -j ACCEPT

```

UFW/GUFW should be able to do it too.

Others will also point to fail2ban.  

You might report the attacker to the ISP where it launched from.

---

### Post by Lars Noodén on 2014-03-28
Also there is some rate limiting in later versions of OpenSSH server regarding the number of unauthenticated connections allowed.   See [MaxStartups](http://manpages.ubuntu.com/manpages/saucy/en/man5/sshd_config.5.html)

```

MaxStartups 10:30:50

```

---

