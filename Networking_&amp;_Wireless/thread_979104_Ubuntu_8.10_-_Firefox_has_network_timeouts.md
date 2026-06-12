---
title: "Ubuntu 8.10 - Firefox has network timeouts"
date: 2008-11-11
forum: Networking &amp; Wireless
---

### Post by lordofduct on 2008-11-11
Hey guys, I'm using the latest Ubuntu 8.10 and Firefox is acting really weird.

See I'll be surfing the web and everything is working just fine. And then randomly the connection just dies out and I can't connect to websites. Sometimes FF reports a network timeout error. But then 60 seconds or so later it just starts working again. It intermitently does this every 10 minutes or so.

The thing is none of the other computers in my house do this. And I have a VMware guest OS running Vista on this machine with the second NIC bridged to it, which doesn't do it as well. I'm in the Vista session right now posting this as a matter of fact.

Further more none of my cross network stuff gets effected. It is only in FF when connecting to the web. I stream videos and music from a server in my house that has a MythTv backend on it whit no hiccups.

Anyone have any ideas what could be happening?

---

### Post by lordofduct on 2008-11-11
Furthermore:

This issue doesn't occur in Konqueror for me... though sound from flash content isn't working in Konqueror. But that's a completely different issue.

Anyways, I like Firefox, it kinda just bugs me this issue effects FF.



Oh this is the version of Firefox that comes with Ubuntu 8.10.

Mozilla/5.0 (X11; U; Linux i686; en-US; rv:1.9.0.3) Gecko/2008101315 Ubuntu/8.10 (intrepid) Firefox/3.0.3

---

### Post by lordofduct on 2008-11-12
crap, it turns out it occurs elsewhere as well. Just started noticing it in Konqueror and when I'm uploading files to my website with gftp.

---

### Post by lordofduct on 2008-11-13
--slice that--

I seemed to fix it, I have 2 NICs and it appears they were acting weird with each other. So I just shut down one of them completely. Now I need to figure out a way to make it work properly, because I do need that NIC.

---

