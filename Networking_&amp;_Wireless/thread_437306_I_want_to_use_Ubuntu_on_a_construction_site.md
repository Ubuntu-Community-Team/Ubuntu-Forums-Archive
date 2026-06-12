---
title: "I want to use Ubuntu on a construction site"
date: 2007-05-08
forum: Networking &amp; Wireless
---

### Post by mojogil on 2007-05-08
I am a Plumbing superintendant for a large mechanical company in the Minneapolis area.  I'm in the midst of convincing the company of the benefits of giving the lead forman computers.  I use mine for pdf blueprint reading, email, logging into ftp sites, schedule, etc.  In a few months I'll start at my new jobsite which will be a new big hospital.  There will be a big job trailer with 4 to 6 people officing out of it.  We will have phone, fax, and DSL. I will be the head guy for my company onsite and I am the most computer skilled of anyone on the jobsite (but I am really still a noob). Everyone but me will be using WIndows XP (maybe vista on a newer machine)
My questioin is this:

1. What are some ideas as to what I can do to help everyone be streamlined and efficient?  Maybe set up a desktop where all of the updated info is stored and a couple of printers are connected to?

2. If I set up an Ubuntu desktop, can the windows machines print through it, and can the windows machines read and write to the disk?  Do I even want them writing to the disk?

3. If I set up an HP all in one fax scan printer, can the other machines fax or scan through the Ubuntu machine?

I'm sure these are really basic questions but It's new to me.
Thanks for any ideas.
Gil

---

### Post by spd106 on 2007-05-09
3. I suggest that you check the open printing database for the level of functionality you are likely to get from a specific model. It can vary between models from the same manufacturer so don't assume anything.
[http://openprinting.org/printer_list.cgi](http://openprinting.org/printer_list.cgi)

2. You can do file and printer sharing for Windows desktops, usually this is done via Samba and CUPS. There are guides for both of these in the help docs wiki [https://help.ubuntu.com/community/](https://help.ubuntu.com/community/). You can use the Ubuntu PC as a sort of half desktop, half server to provide a space for file storage/backup, though an off-site backup would also be recommended.

1. This is rather more open ended than the other two questions and could run on and on. The best way would be to start small and simple, then you don't have too much work if it all goes wrong. I would start with printer sharing as this sounds like it will quite critical. If you can get it working reliably, then you can add file sharing, then maybe some form of shared external connection with perhaps a proxy, like Squid.

You could even go as far as having your own Jabber(IM) or Asterisk(VoIP) server.

---

### Post by mojogil on 2007-05-09
Thank you,
I'll look into the things you've suggested.
Take care,
Gil

---

### Post by briealeida on 2007-05-16
You also want to look into Squid failing open. I don't recall right now if this is possible but if Squid goes down you still want people to be able to access the Internet.
Try [www.squid-cache.org](www.squid-cache.org) if you haven't already.
Best of luck!

---

