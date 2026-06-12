---
title: "unable to get connectivity on a school network"
date: 2008-04-22
forum: Networking &amp; Wireless
---

### Post by fyrelizard on 2008-04-22
I am a CS teacher at a high school. I had an old machine donated for my class. I am trying to get Ubutu working. I had a disk of the Ubuntu 5.10 release and I installed the server version, because of my lack of memory and hard drive space. The network was not plugged in when I installed, but I hooked it up later. I added 
iface eth0 inet dhcp
to my /etc/network/interfaces file. When I do an ifconfig, I do have an ip address and my resolv.conf file has the same nameservers that I can see on the various Windows boxes I have available to me. 

The problem is, I can't seem to connect to anything. I tried an apt-get update and got a message that includes:
Failed to fetch [http://us.archive.ubuntu.com/ubutu/dists/breezy](http://us.archive.ubuntu.com/ubutu/dists/breezy) /(whatever it is looking for) 404 Not Found [IP: 91.189.88.45 00]

I can't ping, even from a Windows box, something I'm guessing the school network has shutdown, so I can't use that as a resource for discovering the problem. I also notice starting up that synchronize clock with ntp.ubutlinux.org fails. I've read several of the forums and have tried various solutions given there, but my problem doesn't seem to match anything that I've found exactly so far and nothing has worked. Any ideas? Could my school's network have something blocked so I can't use apt-get?  My IT staff is totally clueless, so I can't ask them. Anything else I could try? I'm fairly new to Linux - my husband has slightly more experience and he's stuck too - but I can follow directions really well.

---

### Post by jetsam on 2008-04-23
I think your distribution may have fallen into the no longer supported category.  I'm not very familiar with the details of the support scheduling, but I looked around the archive server, and the dists directory has subdirectories for dapper, edgy, feisty, gutsy, and hardy-- no breezy.  

I'd recommend you download and install the hardy server release, as it's going to be a long term support release.  You could also go for dapper (the last long term support release, a bit old now), or gutsy (out for a while so generally stable).

---

### Post by superprash2003 on 2008-04-23
can you please post your ifconfig results here? also type ping google.com and post results here

---

### Post by jetsam on 2008-04-23
I probably could have written my post clearer.  

The 404 result is because there is no breezy repository to download.  It's gone.  

There may be a connectivity problem as well, but even if so, fixing it would still leave an unmaintainable distro.

---

