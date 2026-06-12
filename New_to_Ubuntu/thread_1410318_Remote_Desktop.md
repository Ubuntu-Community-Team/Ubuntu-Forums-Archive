---
title: "Remote Desktop"
date: 2010-02-18
forum: New to Ubuntu
---

### Post by miniil on 2010-02-18
Hi everybody,

I'm new on this forum, i'm new for ubuntu and my english is not good because I'm from belgium :)  So excuse me in advance for my poor english :)

I'll try to explain my problem.

I've installed a version Ubuntu (v9.10 koala) on a computer linked to internet behind a router.

I try to configure this computer to be accessible from outside with the functionality Remote Desktop.

So I've enabled the remote desktop and redirect port 5900 to this computer's local IP.

From my local network it works perfect, i use thightVNC and i can connect to remote desktop and control.

But outside my local network (from my work for example) it does work with IP of my router or with DynDNS. Also, screen Remote Desktop Preferences inform me "Your desktop is only reachable over the local network."

I've tried to open the port 5900 for the firewall ufw but it doesn't work.
I've also tried to desable the firewall (Yes I know it's not a good idea, it's just for test) but it doesn't work.

How can I do?

Thanks for your help.

---

### Post by cariboo on 2010-02-18
Check [canyouseeme]("http://canyouseeme.org") to see if you have your ports properly forwarded. Make sure you use a really, really strong password when using vnc. :)

---

### Post by miniil on 2010-02-19
Yes it works.

Sometimes Remote Preferences inform me that the computer is reachable from the outside (without changing anything) but it isn't.

---

### Post by HughJarse on 2010-08-01
Did anyone find out how to open up access on certain ports?

---

