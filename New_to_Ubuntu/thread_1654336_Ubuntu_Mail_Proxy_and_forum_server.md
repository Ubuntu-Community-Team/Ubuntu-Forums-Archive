---
title: "Ubuntu Mail Proxy and forum server"
date: 2010-12-28
forum: New to Ubuntu
---

### Post by enoch99 on 2010-12-28
Hello everybody,
I started using Ubuntu recently, and I fell in love with it. Then, just today I decided having a mail, proxy server. From where do I start? Is there a way an Ubuntu server can work as a mail server and proxy server for Windows workstations? What are the hardware requirements of the server? And can a single server serve as both a mail and proxy server?

---

### Post by davidmohammed on 2010-12-28
welcome to the forums...

diving into the deep end arent you!

[Here]("https://help.ubuntu.com/community/MailServer") is some community info on mail-servers

[Squid]("http://www.ubuntugeek.com/how-to-setup-transparent-squid-proxy-server-in-ubuntu.html") seems to be a popular proxy server

To attach windows clients then pop3 is a simple protocol to use.

IMAP is perhaps better if you are using Windows Outlook.

ubuntu requirements are [here]("https://help.ubuntu.com/community/Installation/SystemRequirements").

Have fun!

---

### Post by enoch99 on 2010-12-31
Thx David. Yes, I'm diving deeper, I think, a little more deeper than I can swim may way up. But let me give it a try. There's nothing that I promised my office. So, it won't be a failure if I don't succeed.

Let me add up more questions, so I can have clarity on what I'll do. What I want besides a proxy server is, a way for employees to communicate with each other through mail and forum(which I think is a mail server??) and a server to share office document with varying user privileges. Users should also be allowed to upload documents. (File server is that it??) If a little programming is required, I can do that as I'm familiar with Java. 

Does that mean I need to have three different servers? Or one will do fine?

Thanks again:)

---

### Post by davidmohammed on 2010-12-31
there is actually no reason why one server cant do all those functions - just depends on the physical characteristics of the server you are using.

If you want a forum type setup - then a standard wiki such as from twiki.org is something you should consider.

You say that you want a file-server.  I presume you need some sort of redundency/failover?  At a minimum you would therefore need a RAID capability.  The secondary question, is how much is to be saved on the server will determine the RAID type.

Again sizing of the server is important - that depends on the expected usage (size of office - what type of office, space, power etc)

... and finally how much money you want to spend...

All difficult questions for a forum type response - that is why businesses such as mine exist!

Hope the above helps in your considerations.

---

