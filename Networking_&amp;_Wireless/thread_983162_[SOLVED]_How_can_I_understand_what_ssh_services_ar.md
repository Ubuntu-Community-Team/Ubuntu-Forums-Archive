---
title: "[SOLVED] How can I understand what ssh services are running and who intiated them?"
date: 2008-11-15
forum: Networking &amp; Wireless
---

### Post by bwallum on 2008-11-15
For a while now I have seen a small drop in bandwidth availability. I also see my network icon continuously working intermittently, if that makes sense. That is, not fully continuous over time but periodically and uniformly working, rather like a polling process.

I would like to know what these connections are and how to identify them. Can you help please?

Regards
Bob

---

### Post by iAlta on 2008-11-15
Try the 'netstat' command.
There are several flags you can use, based on your post I think you may be need:
'-a' shows all listening and non-listening sockets
'-p' shows the program id(PID)
'-c' will make it update the output every second

you can roll all the options in one - like this: 'netstat -apc'

'man netstat' show all the various options.

---

### Post by bwallum on 2008-12-03
Sorry its taken so long to get back but spot on with the advice, thank you.

---

