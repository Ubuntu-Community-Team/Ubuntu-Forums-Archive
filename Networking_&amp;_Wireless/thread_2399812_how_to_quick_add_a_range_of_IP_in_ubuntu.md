---
title: "how to quick add a range of IP in ubuntu?"
date: 2018-08-29
forum: Networking &amp; Wireless
---

### Post by johnny-duan on 2018-08-29
i know in centos we can touch a range file like this
ifcfg-eth0-range0 
IPADDR_START=192.168.1.1
IPADDR_END=192.168.1.254
PREFIX=24
CLONENUM_START=0
then it works.

but how to quick add a range of IP in ubuntu?
is there anybody can help me?

---

### Post by TheFu on 2018-08-30
Networking configs have changed in Ubuntu with every LTS release, so how to accomplish it would be entirely dependent on the release you are running.  

18.04 uses netplan. The docs for that are at netplan.io. I've never used it.

For 16.04, I'd use a little bash script to generate files into /etc/network/interfaces.d/

---

### Post by johnny-duan on 2018-08-30
> **TheFu said:**
> Networking configs have changed in Ubuntu with every LTS release, so how to accomplish it would be entirely dependent on the release you are running.  

18.04 uses netplan. The docs for that are at netplan.io. I've never used it.

For 16.04, I'd use a little bash script to generate files into /etc/network/interfaces.d/


can you give me the bash script ?

---

### Post by TheFu on 2018-08-31
> **johnny-duan said:**
> can you give me the bash script ?

I don't have one. It would need to be created.  All it would do is generate the config files, 1 per IP. Any admin should be able to do that, trivially.
Or use a devops tool, like ansible, to do it, if you prefer.

A hint:
```
for i in {10..250} ; do 
   echo $i; 
done
```

---

