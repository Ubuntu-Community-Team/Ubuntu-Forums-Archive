---
title: "Get servers error: 99"
date: 2018-12-31
forum: Networking &amp; Wireless
---

### Post by Robbyx on 2018-12-31
Get servers error: 99  / error creating SSL context (error: 140A...:SSL routines:func(169):reason(196))

Does this make sense to anyone? Sudo apt update is not showing an error.

---

### Post by TheFu on 2019-01-01
No. It doesn't make any sense without any context.

---

### Post by Robbyx on 2019-01-01
It seems to come up every time I start the computer. 

Could you suggest some logs to look at that might give us context?

---

### Post by TheFu on 2019-01-01
> **Robbyx said:**
> It seems to come up every time I start the computer. 

Could you suggest some logs to look at that might give us context?

"come up" is a little vague?  
Is this a desktop or a server?  
Is the message in a window or inside a terminal or on the console?
What is the system supposed to be doing?  
Checking email?  
Surfing the web?  
Serving web pages?  
Connecting to other systems using ssh, sftp, scp, rsync, or something else?
Does a VPN get used?
Is this a home system or a work system?
Any specialized software on it?

The logs are in /var/log/ ... search there for any that have errors or warnings.  I'd use **egrep -i 'error|warning' /var/log/*log**, but there must be 50 other ways.

---

### Post by Robbyx on 2019-01-02
I have contacted my VPN supplier in case the fault is with them.

---

