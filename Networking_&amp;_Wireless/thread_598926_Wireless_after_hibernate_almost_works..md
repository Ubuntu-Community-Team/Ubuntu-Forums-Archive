---
title: "Wireless after hibernate almost works."
date: 2007-10-31
forum: Networking &amp; Wireless
---

### Post by mohnkern on 2007-10-31
I've read the postings on the issue with wireless networking, and how hibernate kills it.  I'm able to restart wireless with

sudo /etc/init.d/networking stop
sudo /etc/init.d/networking start

and it works, almost.

Everything except my local area network connections work.  My NFS mounts won't mount, I can't ping other machines in my lan, and I can't ssh directly to my server (though If I go out,  and then come back in through the firewall I can which is amusing.

So it looks like the wireless card is coming up right but there's something else strange going on.  

I did an ifconfig after bringing up the connection, and I've got the same static ip address.  It's king of a mystery.

Oh, and I can't ping the machines "around me" in my network either.

---

