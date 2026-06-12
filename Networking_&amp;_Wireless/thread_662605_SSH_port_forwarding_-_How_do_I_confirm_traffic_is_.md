---
title: "SSH port forwarding - How do I confirm traffic is going through the forwarded port?"
date: 2008-01-09
forum: Networking &amp; Wireless
---

### Post by kevdog on 2008-01-09
Ok Ive managed to set up a socks proxy forwarding through a tunneled ssh connection following these instructions:

[http://ubuntu.wordpress.com/2006/12/08/ssh-tunnel-socks-proxy-forwarding-secure-browsing/](http://ubuntu.wordpress.com/2006/12/08/ssh-tunnel-socks-proxy-forwarding-secure-browsing/)

How do I verify all of my firefox traffic is going through the ssh tunnel?

---

### Post by kevdog on 2008-01-09
Anyone ever used tcpdump??

---

### Post by jords on 2008-01-09
One way would be to compare ip addresses seen my the websites.

So go to [www.whatismyip.com](www.whatismyip.com) in firefox with the tunnel setup, and compare with what that website says using another browser without the proxy setup, or just disable it in the firefox options and test again. If the two ips are different, then the proxy is working.

Jordan

---

### Post by kevdog on 2008-01-09
Not that anything is wrong with the showmyip.com method, but there must be another way? (A little bit more diagnostic)

---

