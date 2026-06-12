---
title: "SSH Ports Blocked + Proxies dont work = WEB FILTER OWNED"
date: 2008-10-17
forum: Networking &amp; Wireless
---

### Post by hmahadik on 2008-10-17
Hey guys, 

I can't get free proxies to work for some reason.:(

Also, I tried SSH tunneling and they've blocked all ports...:mad:

Any suggestions? :confused:

Thanks.

Btw, I am using putty to ssh.

---

### Post by iponeverything on 2008-10-17
In a market where jobs are so hard to find.. just seems a bit odd.

---

### Post by jimv on 2008-10-17
If you have internet access, set up an SSH server at home, and set your router to forward port 80 to port 22 on the SSH machine.  Port 80 shouldn't be blocked by your web filter.  Then set Putty to use yourserver:80 for the tunnel instead of yourserver:22.

Also, if you're behind a proxy, make sure that you set your proxy settings in Putty as well.

---

