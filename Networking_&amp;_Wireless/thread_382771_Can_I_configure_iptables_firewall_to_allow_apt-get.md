---
title: "Can I configure iptables firewall to allow apt-get?"
date: 2007-03-12
forum: Networking &amp; Wireless
---

### Post by mikestefff on 2007-03-12
Hi,

I recently configured iptables to drop all incoming traffic except for a few things like, ssh, web traffic, webpanel, smtp, local traffic, and my dns servers. The problem is, I just realized that apt-get doesnt work unless I disable the iptables. Is there a certain entry I can make into the tables to allow all of the software sources in apt to work with my machine? I have cron checking for updates every week so I need it to always be able to work. What is the best thing to do while still ensuring maximum security?

Thanks
Mike

---

### Post by mikestefff on 2007-03-12
I believe I solved this : i allowed access from us.archive.ubuntu.com and security.ubuntu.com..

no problems with that right?

---

### Post by koenn on 2007-03-12
if your using http sources, it should work by allowing outward traffic to port 80 (lots of  people just allow all outgoing traffic - easier) and allow "established" inbound traffic, i.e. replies to your apt-get requests.

That you explicitly have to allow (new) connections comming from the repo servers only makes sense if you use ftp. Is that the case ? 
Anyway, if you limited the incoming traffic to only those servers, its a reasonably secure sollution.

---

