---
title: "Tunnelling Problem"
date: 2007-11-14
forum: Networking &amp; Wireless
---

### Post by the gnome on 2007-11-14
I am running the following command to create a tunnel to my work db:
ssh [email]me@xyz.com[/email] -L3306:localhost:2501

But it appears port 2501 is never opened on my machine.  When I try to test the setup by:
telnet localhost 2501 

I can't get out of my machine.   If I run the portscan for localhost, 2501 is not open.

I then started using gSTM to connect to create the tunnel, while that indeed creates the tunnel, and I can telnet to the database, something is preventing my connection to the db.

I don't believe anything is wrong other than the linux setup as I can do this same setup with vista using putty and it connects just fine.

I am trying to connect using 2 methods:  Ruby on Rails and the mysql Query Browser.

---

