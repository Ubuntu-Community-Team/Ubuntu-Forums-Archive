---
title: "wifi not working"
date: 2017-06-12
forum: Networking &amp; Wireless
---

### Post by ramyar22 on 2017-06-12
I am having Ubuntu 16.04 and during upgrading due to no charge my laptop turned off. when i opened later to start updating again it's not connecting to wifi or even when i plugged in directly with Ethernet cable. Please help

---

### Post by wildmanne39 on 2017-06-12
Please click on the wireless script in my signature and follow the directions to run it and paste the output to pastebin, then the link back here.

---

### Post by ramyar22 on 2017-06-12
Thanks for replying.
I dont understand what pastebin is. But this is what i got with the first command.
#ramya@ubuntu:~$ sudo apt updateErr:1 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) xenial-security InRelease
  Could not resolve 'security.ubuntu.com'
Err:2 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) xenial InRelease
  Could not resolve 'us.archive.ubuntu.com'
Err:3 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) xenial-backports InRelease
  Could not resolve 'us.archive.ubuntu.com'
Err:4 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) xenial-updates InRelease
  Could not resolve 'us.archive.ubuntu.com'
Reading package lists... Done
Building dependency tree       
Reading state information... Done
50 packages can be upgraded. Run 'apt list --upgradable' to see them.
W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/xenial/InRelease](http://us.archive.ubuntu.com/ubuntu/dists/xenial/InRelease)  Could not resolve 'us.archive.ubuntu.com'
W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/xenial-backports/InRelease](http://us.archive.ubuntu.com/ubuntu/dists/xenial-backports/InRelease)  Could not resolve 'us.archive.ubuntu.com'
W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/xenial-security/InRelease](http://security.ubuntu.com/ubuntu/dists/xenial-security/InRelease)  Could not resolve 'security.ubuntu.com'
W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/xenial-updates/InRelease](http://us.archive.ubuntu.com/ubuntu/dists/xenial-updates/InRelease)  Could not resolve 'us.archive.ubuntu.com'
W: Some index files failed to download. They have been ignored, or old ones used instead.
#

---

### Post by ramyar22 on 2017-06-12
```
ramya@ubuntu:~$ sudo apt updateErr:1 http://security.ubuntu.com/ubuntu xenial-security InRelease
  Could not resolve 'security.ubuntu.com'
Err:2 http://us.archive.ubuntu.com/ubuntu xenial InRelease
  Could not resolve 'us.archive.ubuntu.com'
Err:3 http://us.archive.ubuntu.com/ubuntu xenial-backports InRelease
  Could not resolve 'us.archive.ubuntu.com'
Err:4 http://us.archive.ubuntu.com/ubuntu xenial-updates InRelease
  Could not resolve 'us.archive.ubuntu.com'
Reading package lists... Done
Building dependency tree       
Reading state information... Done
50 packages can be upgraded. Run 'apt list --upgradable' to see them.
W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/xenial/InRelease  Could not resolve 'us.archive.ubuntu.com'
W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/xenial-backports/InRelease  Could not resolve 'us.archive.ubuntu.com'
W: Failed to fetch http://security.ubuntu.com/ubuntu/dists/xenial-security/InRelease  Could not resolve 'security.ubuntu.com'
W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/xenial-updates/InRelease  Could not resolve 'us.archive.ubuntu.com'
W: Some index files failed to download. They have been ignored, or old ones used instead.

```

---

