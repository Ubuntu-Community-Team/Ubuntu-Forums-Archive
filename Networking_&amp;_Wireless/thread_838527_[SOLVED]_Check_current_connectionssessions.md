---
title: "[SOLVED] Check current connections/sessions?"
date: 2008-06-23
forum: Networking &amp; Wireless
---

### Post by jimv on 2008-06-23
I'm curious as to how I could check to see what connections are currently open on my machine.  In particular, I'd like to be able to see who is connected via SSH and what their IP address is.

---

### Post by Zulu-Zeffir on 2008-06-23
netstat -tunva
and better yet you can pipe the command to grep for specific services.
If you know that SSH runs on port 22 then:
netstat -tunva | grep 22
or
if you know what ip address your looking for
netstat -tunva | grep 192.168.1.1

---

