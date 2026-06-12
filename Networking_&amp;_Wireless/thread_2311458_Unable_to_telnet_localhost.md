---
title: "Unable to telnet localhost"
date: 2016-01-27
forum: Networking &amp; Wireless
---

### Post by AnuragSatish.P on 2016-01-27
Hi,

I've installed telnet using 'sudo apt-get install xinetd telnetd'

service xinetd restart

But when I try to telnet to my localhost it isn't working....

Output error:
telnet localhost 
Trying 127.0.0.1...
telnet: Unable to connect to remote host: Connection refused

I'm doing this task as part of my python programming to use telnet module and extract few cli commands output. Kindly, help me on how to resolve this issue.

---

### Post by AnuragSatish.P on 2016-01-29
Is there anyone who can address this issue.

Please....

---

### Post by slickymaster on 2016-01-29
*Moved to the ***Networking & Wireless*** sub-forum*

---

### Post by steeldriver on 2016-01-29
Did you configure xinetd to allow telnet?

I don't run telnetd / xinetd myself (and I'm skeptical why you would need to) but I think if you run xinetd you need to explicitly allow telnet connections: see [http://askubuntu.com/a/448930/178692](http://askubuntu.com/a/448930/178692)

If you don't install xinetd, then telnetd should just work right out of the box - which might be OK if you are just testing this on a box that is suitably isolated (firewall on and behind a NAT router for example)

---

### Post by leith98b on 2016-01-29
You show that you restarted the service, but is it actually running?  If you do a "netstat -an | grep 23" do you see a "*.23" or 127.0.0.1:23 ?  Or, possibly iptables is blocking access to telnet?

---

