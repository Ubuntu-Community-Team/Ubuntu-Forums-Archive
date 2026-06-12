---
title: "ssh tunnel at boot  how to"
date: 2008-11-09
forum: Networking &amp; Wireless
---

### Post by pdc124 on 2008-11-09
i maintain my sisters' machine , and ive just put Hardy Heron on,  to replace  the WinXP that has fallen over. 

I want access to the machine for maintainence etc.
I can set up a reverse SSH tunnel 

ssh  -i /home/sis/.ssh/key_sis  -l sis -R 24:localhost:22 myserver.com
and then I ssh to my server
   
ssh -p 24 [email]sis@myserver.com[/email] 

and up comes  her machine 

im not familiar with ubuntu. Where does the ssh  line go to start the tunnel on boot ?

---

### Post by maxhax on 2008-11-09
I would put it in:

> /etc/rc.local

---

### Post by pdc124 on 2008-11-11
and the identity file shouldnt go in /tmp!

---

