---
title: "pure-ftpd woes"
date: 2007-06-26
forum: Networking &amp; Wireless
---

### Post by nbv4 on 2007-06-26
First I installed pure-ftpd from the repo's.

I now have it running, using this command:

sudo pure-ftpd -S localhost,830 -p 19830:20000

In my router, I have port 830 forwarded to my machine, and ports 19830-20000 forwarded as well.

When I try to connect to the server via "ftp localhost 830", it works fine. But if I try "ftp 84.168.65.22 830" it says "connect refused" (The above IP is the one whatsmyip.org gives)

What am I doing wrong? I know I have my router forwarded properly, as the settings are the same as when I used XP, and they worked fine then.

edit: figured out the problem. Apparently I didn't need to have "localhost" in there. That caused it to only listen to localhost for connections. The command I needed was:

 sudo pure-ftpd -S ,830 -p 19830:20000

---

