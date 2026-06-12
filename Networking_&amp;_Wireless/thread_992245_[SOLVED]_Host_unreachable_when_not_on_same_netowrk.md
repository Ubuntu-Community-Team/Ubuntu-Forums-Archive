---
title: "[SOLVED] Host unreachable when not on same netowrk"
date: 2008-11-24
forum: Networking &amp; Wireless
---

### Post by NDPeter on 2008-11-24
I've got a server setup and it works beautifully for everything I use it for.  I send people there from Windows machines and everything works.  I can boot into windows from this computer and everything is fine.  

My problem - At school, where I have the server setup, I can access everything from my ubuntu install...however when I go off that network I can't connect from ubuntu.  

traceroute shows that the first stop is right where I am.

So I think this is an IP routing issue.  To make things a little less abstract here's the basic setup.  The server is at 111.222.333.444 for example.  My laptop i'm able to connect from windows with but not ubuntu must use a static ip when connecting from school and so has an ip of 111.222.333.555.  

In the netstat -nr table I show the final gateway as 111.222.333.1.  Is this what's standing in my way of connecting to my server?  

Any help on how to fix things?  Thanks.

---

### Post by NDPeter on 2008-11-24
I solved this following the edits to /etc/hosts in this thread [http://ubuntuforums.org/showthread.php?t=723361](http://ubuntuforums.org/showthread.php?t=723361)

That fixed both the sudo error I was getting as well as the problems connecting to my server.

---

