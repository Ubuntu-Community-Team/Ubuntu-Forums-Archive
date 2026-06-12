---
title: "Samba Stopped Working"
date: 2006-11-17
forum: Networking &amp; Wireless
---

### Post by tonyr1988 on 2006-11-17
I am using Samba in-between my Ubuntu Desktop (host) and my Ubuntu Laptop (client), both Dapper. (I know I don't need Samba for this, but Windows needs access to it, too - just not right now). They both go through the same Linksys router - the desktop is corded, and the laptop is wireless.

I had it set up and working perfectly a while ago. However, after moving my desktop, it just stopped. (however, it's been a long time since I've even had the desktop on, so it may have nothing to do with the move)

Both computers can get on the Internet (through the same router), so I'm assuming that's not a problem. I've restarted Samba on the host via:

> sudo /etc/init.d/samba restart

...nothing. smbtree outputs nothing. sudo mount -a doesn't do anything (I have it set for a mount point on the client that worked previously). When I look at Network Servers in Nautilus, I see "Windows Network," but nothing is inside of it. 

As far as I know, I have all the necessary packages on both computers - it worked before. Any idea what could possibly be going wrong? I'm not very knowledgeable about it - I followed a HOWTO, and it worked. :P What are the common problems and solutions for Linux-to-Linux Samba?

---

### Post by tonyr1988 on 2006-11-18
The same thing is still happening to me today. I even went through and re-installed everything, and it still doesn't work. I can ping my desktop just fine, but just can't connect to it.

No ideas?

---

### Post by tonyr1988 on 2006-11-18
One more update: It all works perfectly under Windows (client, off course), but still not Ubuntu. I had thought something was wrong with my desktop, but I guess I'm missing something for my client. Considering it had worked perfectly before, what could be wrong?

I guess I could use NFS for my Ubuntu and Samba for Windows.

---

