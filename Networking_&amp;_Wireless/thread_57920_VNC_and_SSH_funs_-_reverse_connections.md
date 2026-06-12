---
title: "VNC and SSH funs - reverse connections"
date: 2005-08-18
forum: Networking &amp; Wireless
---

### Post by JGJones on 2005-08-18
Here is the layout that I would like to do:

Windows PC - VNC Server started in reverse connection (port 1234 (example)) to linux server

Linux server listen for incoming vnc traffic and then forwards it via SSH over the internet to remote office.

Remote office listens for incoming SSH and have listening vncviewer.

However the remote office also ssh into the server so I assume I would have to use a different port for reverse connecting ssh tunnel apart from 22? Since I would like to be able to ssh into the server.

I've tried to find out how to do this with not very much luck. I presume some ideas I have are:

On the linux server, runnig this command as daemon (how to do that?)

ssh -R 1234:localhost:1234 my-PC

Then on my PC I run the command:

ssh -p 1234 localhost

and then vncviewer to listen to localhost port 1234?

Would that work?

Many thanks if anyone could help me out.

---

