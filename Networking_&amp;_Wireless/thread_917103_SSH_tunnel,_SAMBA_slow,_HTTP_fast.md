---
title: "SSH tunnel, SAMBA slow, HTTP fast?"
date: 2008-09-11
forum: Networking &amp; Wireless
---

### Post by spiker611 on 2008-09-11
Hey guys,
I have an ubuntu 8.04 server at home with a reasonably fast connection.  Here at school im tunneling SAMBA over SSH to share files inbetween server and client.  Im running windows here, using MyEntunnel to forward port 137 and port 80 over a virtual device (10.0.0.1) so I can test web junk as if i'm local also.  

Now, when I transfer a file from server to client via the samba share (file:\\\10.0.0.1/blah) the speed hovers around 50 KB/s.  If I access [http://10.0.0.1/blah](http://10.0.0.1/blah), the speed is 3x that at around 150 KB/s.  I have no problem using HTTP but i'd love to use SAMBA at the fullest speed possible.
Anyone know how I can fix this?

---

