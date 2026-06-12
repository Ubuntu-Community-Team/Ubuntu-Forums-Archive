---
title: "How to change resolv.conf permanently"
date: 2006-10-31
forum: Networking &amp; Wireless
---

### Post by schmelck on 2006-10-31
How could I change the /etc/resolv.conf permanently? Every time I
reboot it gets resetted.

---

### Post by coppertrail on 2006-10-31
I've been working on this myself. Giving the machine a static IP address seems to correct the problem.  There is a purported solution that involves editing the dhclient.conf file, but that didn't work in my situation.  

Also, it automatically adds a domain in the Search Domains section under the DNS tabs.  This is really annoying, as the internet stops working when this happens, and I have to manually remove it.

---

### Post by miro3 on 2006-10-31
[https://wiki.ubuntu.com/OverrideDNSServers](https://wiki.ubuntu.com/OverrideDNSServers)
[https://wiki.ubuntu.com/StaticDnsWithDhcp](https://wiki.ubuntu.com/StaticDnsWithDhcp)

---

### Post by coppertrail on 2006-10-31
Thank you, that looks like it should take care of the resolv.conf DNS issue.  What about preventing a search domain entry from being added?

---

### Post by schmelck on 2006-10-31
my problem is that after an reboot the system adds an ip to resolv.conf.
And I don't want that.

Any suggestions?

---

