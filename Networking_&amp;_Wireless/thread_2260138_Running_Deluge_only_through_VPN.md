---
title: "Running Deluge only through VPN"
date: 2015-01-09
forum: Networking &amp; Wireless
---

### Post by sayre on 2015-01-09
Hello,

I have deluge installed and would like to have the Deluge daemon traffic go only through the VPN and everything else stay the same. I am having a hard time understanding how to do this.  I am hoping someone can help me to understand and guide me through the process. 

I am running a headless system with Ubuntu 14.04.1 LTS and am using slickvpn for a service.
Everything goes through the eth0 interface. 

My system also has another ethernet port, eth1 if that helps? 

Thanks in advance!

---

### Post by TheFu on 2015-01-09
There's a way to do this with iptables and specific entries for specific userids - sadly, I don't know how, but this [http://bodhizazen.net/Tutorials/iptables#Additional_Tips](http://bodhizazen.net/Tutorials/iptables#Additional_Tips) seems to have it.    The key is to only run the process you want into the specific iptables routing rule with that userid.

Often after I display my ignorance, someone smarter will come along with the answer in a few hours. They seem to wait for me before posting, however. ;)

---

### Post by sayre on 2015-01-10
> **TheFu said:**
> There's a way to do this with iptables and specific entries for specific userids - sadly, I don't know how, but this [http://bodhizazen.net/Tutorials/iptables#Additional_Tips](http://bodhizazen.net/Tutorials/iptables#Additional_Tips) seems to have it.    The key is to only run the process you want into the specific iptables routing rule with that userid.


Thanks I guess i'll have to see if I can figure it out.

---

