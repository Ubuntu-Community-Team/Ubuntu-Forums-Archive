---
title: "[SOLVED] no upload"
date: 2008-07-06
forum: Networking &amp; Wireless
---

### Post by Mehrab1131 on 2008-07-06
the problem is, I can't upload any thing via my browser except very small files. uplaod is ok in transmission or via ftp but I can't upload files via firefox, nor konqueror or opera. and I should say that I've tested it with many online storage websites.
so anyone have any idea about this problem?

---

### Post by nixscripter on 2008-07-06
A simple explaination without any diagnostics: your ISP is being stupid and blocking HTTP uploads. Normally, things are done with outgoing connections (e.g. POSTs on web forms), but if you're trying to upload directly (out of port 80), it might require some sort of incoming connection. 

The way to test this theory would be to try using a tunneled web proxy of some sort and see if that works then.

---

### Post by Mehrab1131 on 2008-07-06
thats right. I used freegate and it works.
thank you for this help

---

### Post by nixscripter on 2008-07-08
No problem. Please mark this thread as SOLVED (under the Thread Tools Menu).

---

