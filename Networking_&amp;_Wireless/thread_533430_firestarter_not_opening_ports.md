---
title: "firestarter not opening ports"
date: 2007-08-23
forum: Networking &amp; Wireless
---

### Post by ymirscorpse on 2007-08-23
When I had Ubuntu 6.*, I had no problems with firestarter -- the problems started after doing a fresh install of version 7.04.  I use Nicotine as a soulseek substitute, and need to enable a range of ports to allow others to download from me.  As I did previously, I opened ports 2234-2239 in the "Allow Service" section of "Inbound Traffic Policy" -- however, I soon noticed nobody was downloading from me.  A port scan revealed that only 2234 was open and that the rest of range was not.  As a test, I enabled port 21 for FTP service and applied the change.  The port scan indicated that port 21 was still closed.  I managed to fix my immediate problem with Nicotine by adding the soulseek server to "Allow connections from host", but that only makes me wonder why that worked and opening the ports did not.  There are other ports that I will need to enable.

Here is the relevant output from "iptables -L | less":

```

ACCEPT     0    --  sk6.slsknet.org      anywhere            
ACCEPT     tcp  --  anywhere             anywhere            tcp dpts:2234:2239 
ACCEPT     udp  --  anywhere             anywhere            udp dpts:2234:2239 
ACCEPT     tcp  --  anywhere             anywhere            tcp dpt:ftp 

```

Any ideas?

--Chris

---

### Post by laeg_ on 2008-04-24
I have encountered some issues with firestarter not opening ports which I have applied polices to, some of which I could force it to open by adding and removing the policy starting/stopping the firewall and I do have 'apply police changes immediately' checked in prefs.

Even when I think I have fixed it through the tedious method outlined above ports will periodically fail the uTorrent port checker and websites like [Shields Up]("https://www.grc.com/x/ne.dll?bh0bkyd2"). Oh and if you restart uTorrent you have to change the port number and apply a new policy or it definitely won't work. 

The images below are screenshots I sent to a firestarter dev a few days ago outlining my concerns but I have as yet not received a response.

[http://www.uploadgeek.com/uploads456/0/testport1.png]("http://www.uploadgeek.com/uploads456/0/testport1.png")

[http://www.uploadgeek.com/uploads456/0/testport2.png]("http://www.uploadgeek.com/uploads456/0/testport2.png")

---

