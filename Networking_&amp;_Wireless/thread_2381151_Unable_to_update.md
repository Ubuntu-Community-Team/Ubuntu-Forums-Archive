---
title: "Unable to update"
date: 2017-12-27
forum: Networking &amp; Wireless
---

### Post by sachinthorat050989 on 2017-12-27
hey guys, i have upgraded my ubuntu version to 17.10 from 16.04. Had to install - reinstall quite a few times to configure the SSD of my workstation. And now I am not able to update the system. The response I get from *sudo apt update* is posted in the context below. It basically says that the machine can not establish internet connections even though I can access the internet through browsers. please help me figure this out. The wireless info file too is attached herewith

```
skg@skg-HP-Z240-Tower-Workstation:~$ sudo apt update
[sudo] password for skg: 
Err:1 [http://in.archive.ubuntu.com/ubuntu](http://in.archive.ubuntu.com/ubuntu) artful InRelease                  
  Cannot initiate the connection to in.archive.ubuntu.com:80 (2001:67c:1360:8001::17). - connect (101: Network is unreachable) [IP: 2001:67c:1360:8001::17 80]
Err:2 [http://in.archive.ubuntu.com/ubuntu](http://in.archive.ubuntu.com/ubuntu) artful-updates InRelease          
  Cannot initiate the connection to in.archive.ubuntu.com:80 (2001:67c:1360:8001::17). - connect (101: Network is unreachable) [IP: 2001:67c:1360:8001::17 80]
Err:3 [http://in.archive.ubuntu.com/ubuntu](http://in.archive.ubuntu.com/ubuntu) artful-backports InRelease
  Cannot initiate the connection to in.archive.ubuntu.com:80 (2001:67c:1360:8001::17). - connect (101: Network is unreachable) [IP: 2001:67c:1360:8001::17 80]
Err:4 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) artful-security InRelease
  Cannot initiate the connection to security.ubuntu.com:80 (2001:67c:1360:8001::17). - connect (101: Network is unreachable) [IP: 2001:67c:1360:8001::17 80]
Reading package lists... Done                         
Building dependency tree       
Reading state information... Done
All packages are up to date.
W: Failed to fetch [http://in.archive.ubuntu.com/ubuntu/dists/artful/InRelease](http://in.archive.ubuntu.com/ubuntu/dists/artful/InRelease)  Cannot initiate the connection to in.archive.ubuntu.com:80 (2001:67c:1360:8001::17). - connect (101: Network is unreachable) [IP: 2001:67c:1360:8001::17 80]
W: Failed to fetch [http://in.archive.ubuntu.com/ubuntu/dists/artful-updates/InRelease](http://in.archive.ubuntu.com/ubuntu/dists/artful-updates/InRelease)  Cannot initiate the connection to in.archive.ubuntu.com:80 (2001:67c:1360:8001::17). - connect (101: Network is unreachable) [IP: 2001:67c:1360:8001::17 80]
W: Failed to fetch [http://in.archive.ubuntu.com/ubuntu/dists/artful-backports/InRelease](http://in.archive.ubuntu.com/ubuntu/dists/artful-backports/InRelease)  Cannot initiate the connection to in.archive.ubuntu.com:80 (2001:67c:1360:8001::17). - connect (101: Network is unreachable) [IP: 2001:67c:1360:8001::17 80]
W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/artful-security/InRelease](http://security.ubuntu.com/ubuntu/dists/artful-security/InRelease)  Cannot initiate the connection to security.ubuntu.com:80 (2001:67c:1360:8001::17). - connect (101: Network is unreachable) [IP: 2001:67c:1360:8001::17 80]
W: Some index files failed to download. They have been ignored, or old ones used instead.
```

---

### Post by ian-weisser on 2017-12-27
Looks like you are trying to connect using IPv6. Is that intentional?

---

### Post by sachinthorat050989 on 2017-12-28
Well thats what the institute provides. So its really not by my choice.

---

### Post by ian-weisser on 2017-12-28
Does the institute use a proxy on your network? If so, have you told apt about the proxy?

---

