---
title: "internet connected, nothing works"
date: 2008-08-24
forum: Networking &amp; Wireless
---

### Post by wurx on 2008-08-24
Hi there, over the weekend I have established a connection to the internet via my cellphone. I went once on the net and everything went fine. I've sent myself a test mail and then disconnected. But now when I connect my modem opens up and kppp shows that I am connected, but when I try to ping or open web pages nothing happens. I even tried netstat but it doesn't show any out going or incomming data. Ping to [www.yahoo.com](www.yahoo.com) results in ''cannot etsablish connection''

I went into my phone log and it shows the time and duration I was connected. 

Please help.....

---

### Post by wurx on 2008-08-25
Ignore this post.

I've sorted the problem myself. It seemed to be a DNS setting. Switched kppp dns settings to automatic and ticked the box where it says:

''Disable default dns servers on connection''

This solved my problem immediatly.

Just thought I'd add how I've done it in case someone finds this post who's got a similar problem with connecting to the internet.

By the way. I've got connected with a nokia 9300i using kppp.

---

