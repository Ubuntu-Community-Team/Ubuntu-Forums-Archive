---
title: "X over SSH through intermediary"
date: 2008-08-05
forum: Networking &amp; Wireless
---

### Post by cvp on 2008-08-05
I'm a federal employee, and naturally the US government is gung-ho about security. I have an Ubuntu 8.04 machine that I have full admin privileges on, but it's only accessible via intranet. So what I need to do to log in is ssh to another server on the military base, and then ssh from *that* server to my own machine.

I have the basics of X over SSH down already, but is there something different I have to do if I'm remotely logging in from another remote login? Is there a way to tunnel all X-related traffic back to me through that intermediary?

Some **uname**'s:
My laptop:
Linux 2.6.24-19-generic #1 SMP Fri Jul 11 23:41:49 UTC 2008 i686 GNU/Linux
The intermediary machine:
SunOS 5.9 Generic_122300-19 sun4u sparc SUNW,UltraAX-i2
The target machine:
Linux 2.6.24-19-generic #1 SMP Fri Jul 11 23:41:49 UTC 2008 i686 GNU/Linux
(exactly the same as my laptop)

Thanks in advance,
-cvp

---

### Post by pytheas22 on 2008-08-05
I've never done this but I've wanted to sometimes.  The place I used to work had similar policies: to reach my workstation, I had to login through a proxy server.  Unfortunately, since the proxy was a Windows machine, I wasn't sure how to do it and never got the time to really try.

But assuming your proxy server runs Unix, I found this [page]("http://www.sun.com/bigadmin/content/submitted/ssh_port_fwd.html") that looks like it tells you what to do--see **Example: Accessing a Corporate Network Web Server That Allows Logins Through a Proxy Server**.

I'd be interested to hear whether you're successful.

---

