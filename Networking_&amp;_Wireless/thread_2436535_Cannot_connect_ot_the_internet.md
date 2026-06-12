---
title: "Cannot connect ot the internet"
date: 2020-02-08
forum: Networking &amp; Wireless
---

### Post by Semn on 2020-02-08
Hello, I cannot connect to the internet via wifi anymore on Ubuntu 19.04. I shows on google.chrome "NO INTERNET BAD NETWORK CONFIG" and the wifi conenctions only appear as a question mark on the top right logo. I tried to use the resolvconf -related commands, but this version does not have resolvconf at all. How do I solve this?

Thanks!

---

### Post by jeremy31 on 2020-02-08
Moved to Networking and Wireless
See the wireless script link in my signature and post results

---

### Post by ajgreeny on 2020-02-08
And don't forget that 19.04 is out of support so an upgrade or clean install is suggested as soon as you can do so.

---

### Post by guiverc on 2020-02-08
I'll largely just provide links

Ubuntu 19.04 reached EOL
[http://ubuntu-news.org/2020/01/23/ubuntu-19-04-disco-dingo-end-of-life-reached-on-january-23-2020/](http://ubuntu-news.org/2020/01/23/ubuntu-19-04-disco-dingo-end-of-life-reached-on-january-23-2020/)

Info on EOL Upgrades
[https://help.ubuntu.com/community/EOLUpgrades](https://help.ubuntu.com/community/EOLUpgrades)

I'm assuming by reference to `resolv.conf` that you suspect you have DNS issues; it's still there on a standard system, even a 20.04 system I installed today has it, and can be used to temporarily add nameservers.  You mis-typed it's name though, so that alone maybe your issue.

---

### Post by TheFu on 2020-02-10
> **guiverc said:**
> I'm assuming by reference to `resolv.conf` that you suspect you have DNS issues; it's still there on a standard system, even a 20.04 system I installed today has it, and can be used to temporarily add nameservers.  You mis-typed it's name though, so that alone maybe your issue.

resolv.conf is constantly overwritten by whatever DNS management system(s) are active on the machine.  That could be dnsmasq, systemd, resolvconf, or a DNS-over-HTTPS tool. 

Step 1:  The op should move to a supported release which will likely solve this issue.
Step 2: If the problem persists, unlikely, figure out which system I've listed above is controlling the DNS. Usually, a quick check of the process table using **top** or **ps** will do that.

But DNS issues are very different from network connectivity problem.  Network connectivity can be determined by using **ping** to LAN and internet IPs, not DNS names.  ping the LAN router IP.  Ping some well-known internet IPs like 8.8.8.8 or 1.1.1.1 ... if those work, networking is almost always absolutely find.
If ping 8.8.8.8 works, but ping google.com doesn't, it is just a DNS problem.

---

