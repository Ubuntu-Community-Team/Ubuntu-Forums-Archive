---
title: "XDMCP trough SSH..."
date: 2007-03-26
forum: Networking &amp; Wireless
---

### Post by Xealot on 2007-03-26
Hello!

I have a small question,
I have my workstation with XDMCP enabled but no port forwards to that computer so it is still safe, I also have another linux server on the network with ssh (port 22) forwarded to it..

My question is, Is it possible to log on to my workstation at home trough XDMCP by routing my traffic trough my server and if no then are there any other alternatives other than VNC as id like to be able to log on with a completely different user in a separate Xnest

Thanks in advance!,

 - Xealot

---

### Post by kidders on 2007-03-26
Hi there,

What you're describing is possible...
```
ssh -X hostname
Xnest :1 -query localhost
```

> **Xealot said:**
> I have my workstation with XDMCP enabled but no port forwards to that computer so it is still safeThat's not necessarily true, but there's not a lot you can do about it, I suppose!

---

### Post by Xealot on 2007-03-27
Hello.

Wont that line above try to access X available on my server?
My setup would be something like:



[ Internet ] -> [Server] -> [Workstation]


So I need to go trough my server to access my workstation..

---

### Post by kidders on 2007-03-27
Hmm... I may have misread your o/p. Reading it again, you didn't make any mention of having an SSH server running on the workstation.

If that's the case, you could try initiating an SSH connection with your server instead, and setting up a tunnel. Depending on your configuration, something like localhost:5901 -> workstation:5901 should work. You might also need to forward port 177 ... off the top of my head, I'm not certain which ports XDMCP uses.

---

