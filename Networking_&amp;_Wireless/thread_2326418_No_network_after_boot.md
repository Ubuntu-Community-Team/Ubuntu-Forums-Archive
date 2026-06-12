---
title: "No network after boot"
date: 2016-05-31
forum: Networking &amp; Wireless
---

### Post by pjalegria on 2016-05-31
Hi 

After lubuntu upgrade to 16.04 I have this problem, only doing "sudo /etc/init.d/network-manager restart" I have internet, can someone help me please?

Thanks
"

---

### Post by wildmanne39 on 2016-05-31
Hello, it is a bug in network manager.
[https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/1434986](https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/1434986)
There is not a fix for it yet.
You could put that command in rc.local file I believe with out sudo and it should restart network manager automatically.

You will need to have it run about 5 seconds after boot. 
Thanks

---

### Post by pjalegria on 2016-05-31
Ok thanks

---

