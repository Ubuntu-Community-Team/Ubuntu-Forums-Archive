---
title: "NXClient not connecting over the Internet to my Ubuntu box."
date: 2007-02-09
forum: Networking &amp; Wireless
---

### Post by hebbal1273 on 2007-02-09
Hi,
I have installed NXServer on my Ubuntu Box. My laptop is XP Pro & I have installed NXClient on it. Both from [www.nomachine.com](www.nomachine.com). Both computers have static IP. While I can connect to the Ubuntu using the Laptop. I am unable to do the same over the Net. I have an account in dyndns.com & added the dynamic host (my router). If I try to connect, it gives me ssh connection refused. I have checked the firewall settings & also forwarded port 22 on my router.
If I can do it over my local network why cant I do it over the net?. Am I missing something here. [www.nomachine.com](www.nomachine.com) have a testdrive for testing I can connect to that test machine but not mine.:(

---

### Post by hebbal1273 on 2007-02-09
BTW I am connecting to my machine by giving xxx.dyndns.com where xxx is the router name I have given. I have a web browser administration for my MT841 modem-router. I can access the admin page by giving the above address in my browser. So connectivity is not a problem. Only ssh connection refused is the problem.

---

### Post by benphane on 2007-02-15
hebbal1273,

Now did you resolve this?

thanks,

---

### Post by hebbal1273 on 2007-02-17
No not yet. And nobody has yet answered my queries :(

---

### Post by fxavier on 2008-02-13
Two things come to mind:

1. You are behind a router.  You must forward port 22 on the router to your Ubuntu box.  Go to the router's control panel and change it there.

2. Your ISP is blocking port 22.  This is unlikely.  If this is the case, reassign ssh to another port.

---

### Post by Lisanels on 2008-06-30
I'm running something similar.  I have one network on a fedora 9 router that the firewall rules forward several ports to port 22 on static IP systems.  For example, I can SSH -p 2100 mysys.mydomain.com and the firewall translates 2100 to 22 on a spacific system.  Port 2101 goes to another system etc.

This works GREAT for punching into my network from the internet.

The other setup I use is the same except there's a linksys wrt54g rounter connected.  On that one I use the "Applications/Gaming" section to forward just port 22 to the static IP of the system I want to connect to.  

I use no-ip and nxclient/node/server.

Lisa

By the way, I was really impressed that no-ip identifies the linksys router perfectly!  I didn't have to do a thing.

---

