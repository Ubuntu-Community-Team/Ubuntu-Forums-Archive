---
title: "What should the speed be between 2 Ubuntu boxes?"
date: 2007-09-16
forum: Networking &amp; Wireless
---

### Post by MockY on 2007-09-16
I have now finally hardwired my entire apartment and tested the speed via SSH for the first time between my file server and desktop computer. Transferring a file of the size of 1396MB took 2:20 with the average speed of 10.2MB/s, and I now wonder if that is normal or slower than it should be. The only peripheral between them is a Linksys switch.

---

### Post by spd106 on 2007-09-18
That's not bad, remember there is the encryption overhead involved in using SSH, and that's not even mentioning the tcp protocol overhead etc. If you don't need the encryption, SMB/CIFS or NFS might be a better/faster option. 

Try [iperf]("http://dast.nlanr.net/Projects/Iperf/") for a close to wire speed measuring tool, it's available in the universe repos, so you can use your favourite package manager to install it. Check out the man page for correct usage.

---

### Post by malfist on 2007-09-18
I did a wireless transfer with vista, average speed was 2.3 MB/s with the linksys switch the only thing between them.

But how can linux compare to windows? It's soo superior in every aspect!

---

