---
title: "Firestarter and LAN"
date: 2006-07-22
forum: Networking &amp; Wireless
---

### Post by jrjr on 2006-07-22
I installed Firestarter a while ago and took it off due to this. When I removed it Samba was also removed and I had to reinstall Samba again to get things working... no biggie just a nuisance. 

My home network includes a win2000 web server. The router has ports 25, 80. and 110 open. Before installing Firestarter I did a check at the shields up website.
[https://www.grc.com/x/ne.dll?bh0bkyd2](https://www.grc.com/x/ne.dll?bh0bkyd2)
Also Tried it with another. These tests show that the 3 ports are open on my machine.

After installing Firestarter again the same 3 ports show open. Now, I assume that they are really closed on this machine and the firewall is doing its job. The website is looking at the IP of my router and gets through the ports to my server... correct? The local IP of this box is of course not known to the outside world, just the main IP of my connection.

Another item - with firestarter installed I cannot browse my home network. The Windows Network icon comes up but when double clicking it the workgroup does not come up like normal. How would I configure this so it works again?

I tried shutting off the firewall with the stop firewall button and this seems to work but it takes a while for things to start working. What do I do to keep it working and still browse locally? Do I just add a rule that allows connections from the IP's of the machines on my LAN? OR...... do I even need Firestarter since I have a router with hardware firewall?

---

### Post by jrjr on 2006-07-22
Oh well I just removed it again.

---

### Post by moore.bryan on 2006-07-22
firestarter is just the gui to iptables, the real firewall.  i'm not an expert, but your hardwall should be fine.

---

