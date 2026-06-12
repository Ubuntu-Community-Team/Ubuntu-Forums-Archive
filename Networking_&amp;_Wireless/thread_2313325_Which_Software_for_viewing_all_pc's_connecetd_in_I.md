---
title: "Which Software for viewing all pc's connecetd in INTRANET"
date: 2016-02-11
forum: Networking &amp; Wireless
---

### Post by midhun4 on 2016-02-11
hello ,

I have a intranet network,I need to know the ip of all pc connecetd in my network and its net usage.how can i do that?pls guide me .I am currently running on ubuntu 12.04.1 LTS
Similar to NET MONITORING I guess,But need to know all the details of PC's connected.Like its Ip adrss,Net Usage etc.

---

### Post by SeijiSensei on 2016-02-11
What are you running as the gateway router out to the Internet?  If it's a Linux box, take a look at [ntop]("http://www.ntop.org/").

For a quick scan of the network for IPs and open ports, you can use [nmap](http://www.nmap.org).  For instance, the command

```
nmap -sP 192.168.1.0/24
```

will return a list of all pingable machines in that subnet.  If you use "-sT" rather than "-sP", you'll also get a list of open ports on each machine.

Both ntop and nmap are in the Ubuntu repositories.

---

