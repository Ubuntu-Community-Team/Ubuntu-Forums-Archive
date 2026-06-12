---
title: "Remote desktop"
date: 2010-08-18
forum: New to Ubuntu
---

### Post by enenalan on 2010-08-18
Alright...so 10.04 is up and running.  I managed to join my office's Active Directory with Likewise.  I can connect to files on the network, see all of our network printers, etc.  The only problem I seem to be having is connecting to our server using the remote desktop application.  I'm trying to go at this from the GUI rather than the command line.  I'm signed in as myself (i.e. administrator on the Windows 2003 server) on Ubuntu .  The domain is right.  The work group is correct.  Password is legit, etc.  I'm entering the local IP in the little box (no port number...i.e. no :3389....which shouldn't matter, right?).  I keep getting an error message of something like "Browsing for service type _rfb._tcp in domain 'domain' failed: DNS failure:NXDomain"  Doesn't that mean that the domain is nonexistent?  If that's the case, I can't figure why I can access my files and printers......  RDC sees the domain in the drop down menu.  I also tried connecting using just the domain name.  Do I have to append the local IP to that (as in DOMAIN\10.1.32.251)?

No clue!

---

### Post by opticyclic on 2010-08-31
The first thing you should do is see if you can ping the server.
e.g. ```
ping 10.1.32.251
```
However, that DNS error makes me suspect that you can't.

Second, its worth trying out with the correct port as well.

Third, which GUI are you using? It might be worth trying the command line as well
rdesktop

---

