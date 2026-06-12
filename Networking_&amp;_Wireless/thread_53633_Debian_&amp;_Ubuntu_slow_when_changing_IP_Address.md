---
title: "Debian &amp; Ubuntu slow when changing IP Address"
date: 2005-08-01
forum: Networking &amp; Wireless
---

### Post by lee_connell on 2005-08-01
Ok,

I build debian email, proxy servers from my work office.  I configure them using my local lan's ip scheme.  192.168.x.x.

Everything is working fine and snappy!

When I deploy the debian box to it's new home, I have to change the network scheme to match it's new home.  207.185.x.x or whatever it be.

When I change the ip scheme on the network card through /etc/network/interfaces and then attempt a connection either by "ssh" or "smtp" or "pop3" I get a delay.  it connects right away but i then wait for either the banner for "smtp" or the password request from "ssh".

If i bring the box back to my work office and set it back to the 192.168.x.x scheme it's back to snappy.

I have looked through all possibilities as far as cisco hardware in place at the clients site and that is not causing the issue, no firewall or switching issues here.

I hooked my laptop into the back of the debian box via cross-over cable and i do still get the delay while it's on the 207.185.x.x network.

this happens with both debian and ubuntu so it's something i'm missing that debian is looking at.

Any ideas?

---

### Post by gruepig on 2005-08-01
It might be a DNS issue. Check /etc/resolv.conf and /etc/hosts.  (In particular, if you have added entries for machines in /etc/hosts, make sure they get updated when your IPs change.)  Mailservers and the like may also store your IP in config files.  Try grepping for your IP in /etc ('grep -r <ip> /etc/'). 

For debugging the ssh problem in particular, run 'ssh -v <hostname>' (or -vv or -vvv).  This will give you verbose output so you can see where ssh is hanging, which might give you a better idea what's causing the problem and how to fix it.

---

### Post by lee_connell on 2005-08-01
hey it was a dns issue, i had the primary set to a dns server i was running locally at my office, and i forgot to change it went off-site which was causing the delay.

THANKS!!!!!!

---

