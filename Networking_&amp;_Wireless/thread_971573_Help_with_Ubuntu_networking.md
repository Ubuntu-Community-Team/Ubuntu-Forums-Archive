---
title: "Help with Ubuntu networking"
date: 2008-11-05
forum: Networking &amp; Wireless
---

### Post by ASolano on 2008-11-05
I am coming from the windows world and interested in moving to Ubuntu, the problems is no one seems to be able to answer any of my questions on this forum (I have made 2 threads, 1 weeks ago with 40 view, the other a hour ago with 2 views, both with no replies)

Anyway, back to this thread, I am able to browse to a PCs (Ubuntu and windows PCs) on my network (Places > Network).  to me this indicates that my client PC is able to resolve the PC names.  That said I am unable to ping the PCs or view a website hosted on the PCs using firefox using the PC names (using the IP address works fine,

What is going on?  How can a PC resolve names via 1 method but not the other?  What do I need to do so that I can resolve the names of the PCs on my network?

---

### Post by ASolano on 2008-11-05
What a surprise! over 20 views and not 1 reply.

I would have thought open source meant a community effort, it's hard to get new members to a community if current members can't even answer the simple questions posted by new or prospective members.

A couple of years ago I tried switching to Linux via red hat and found the same attitude from current members ("geez don't you know how to do that .. I won't even bother answering your question!").  For some reason I thought that thing would be different with ubuntu .. wrong

I've always wondered why people would rather use OSs that cost money over linux which is free and more efficient (so I've heard .. has not been proven yet though), with support like this i can now stop wondering.

---

### Post by nothingspecial on 2008-11-05
I`ll reply.

I don`t know.

The 40 people who viewed your original post probably didn`t know either. 

There is a team who deal with unanswered posts and try to get to all of them if they can.

Trouble is now your post has 2 replies and so they will miss it.

That being said I hope you get it sorted:D

---

### Post by wieman01 on 2008-11-05
Guys, calm down.

**ASolano**, bumping threads is considered rude, please refrain from it in future. You are free to do so after 24 hours (see CoC for details). You'll receive a warning next time. This is a forum of volunteers.

**nothingspecial**, you do have a point, but please refrain from such comments in future as they don't contribute at all. You are free to report the post in question.

Now back on topic!

---

### Post by Mark224 on 2008-11-05
> **nothingspecial said:**
> 
There is a team who deal with unanswered posts and try to get to all of them if they can.

Is it possible to contact this team?  I have a post which isn't really answered.

---

### Post by wieman01 on 2008-11-05
> **Mark224 said:**
> Is it possible to contact this team?  I have a post which isn't really answered.
You can't really. The are trying to tackle unanswered posts, but if they don't have an answer, they don't have an answer if you know what I mean. You can bump your thread after 24 hours, but if you don't get a response you are out of luck.

---

### Post by nothingspecial on 2008-11-05
> **wieman01 said:**
> 

**nothingspecial**, you do have a point, but please refrain from such comments in future as they don't contribute at all. You are free to report the post in question.

Now back on topic!


Sorry

---

### Post by Iowan on 2008-11-05
> **ASolano said:**
> 
What is going on?  How can a PC resolve names via 1 method but not the other?  What do I need to do so that I can resolve the names of the PCs on my network? There *may* be different protocols involved.  One solution is to include hostname/IP address mappings in */etc/hosts*.  This can be problematic if hosts receive IP's via DHCP.  I don't have it installed, but **dnsmasq** is a DNS/DHCP server that supposedly ties the two together so the DNS server knows the hostnames of the DHCP leases.

---

