---
title: "How to starting iptables on startup? Some my experience and you advices..."
date: 2008-03-29
forum: Networking &amp; Wireless
---

### Post by Igor_from_Nsk on 2008-03-29
Hello
At first  i want to tell beginers how to run iptables on startup 
and then to ask a question to programmers!

Steps for running iptables on startup:
1. Create filtering rules for iptables and place them /etc/iptables.conf
 ```
sudo gedit /etc/iptables.conf
```
2. Build file iptable in the startup catalog
       sudo gedit /etc/init.d/iptables - this file consists just :
      ```
 #!/bin/bash
        iptables-restore < /etc/iptables.conf
```
3. Make this file  executable
```
 sudo chmod +x /etc/init.d/iptables
```
4. Create links in the start catalogs rs.&#8470;.d
```
sudo update-rc.d -n iptables  start 40 S . stop 89 0 6 .
```

But i do not understand why script  /etc/init.d/iptables  do not restore filtering rules from refered file iptables.conf !!! It is my question to expert-coders. How it may be resolve?

---

