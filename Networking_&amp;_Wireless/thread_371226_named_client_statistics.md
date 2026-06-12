---
title: "named client statistics"
date: 2007-02-26
forum: Networking &amp; Wireless
---

### Post by b4nsh33 on 2007-02-26
i need to know my top clients and destination hosts, how can be this done with bind 9?

something like this 


top 10 clients:

IP                           # query                 %
--------------------------------------------------
192.168.10.11    5256                     35
192.168.10.163  2561                    12
...
etc

top 10 hosts
name                        # query                 %
----------------------------------------------------
yahoo.com              15624                    35
hotmail.com           1144                      2
...
etc 


thanks

---

### Post by kidders on 2007-02-27
Hi there,

I've never tried to do this (so there might be a smarter way), but I would turn up Bind's logging verbosity, and throw together something to parse the log files.

If you felt like it, you could use syslog-ng's MySQL integration to have all queries logged to a database, and use a PHP script to make an informational web page out of the results.

---

### Post by b4nsh33 on 2007-02-27
hi, i was thinking the same, logging and a perl script, just wondering if someone had made it already so i dont have to reinvent the wheel, am i so lucky?

---

### Post by kidders on 2007-02-27
Now that you mention it, Google throws up a few promising possibilities. Many of them seem to be SNMP-based solutions.

---

