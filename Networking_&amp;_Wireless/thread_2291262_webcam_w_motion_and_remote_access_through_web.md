---
title: "webcam w/ motion and remote access through web"
date: 2015-08-18
forum: Networking &amp; Wireless
---

### Post by rawlins02 on 2015-08-18
I'm trying to set up a laptop with webcam so that I can access images from a remote connection. I have motion installed and have made modification to the motion.conf file. I can see images with [http://localhost:8081/](http://localhost:8081/) in a bowser. Not sure how to enable the port forwarding using router’s external Internet IP address. I'm pretty sure my ISP is giving out address dynamically, but I should be able to set this up using the IP address at the time, and then leave it while I travel. I've used gufw a bit but don't know much about firewalls, rules, and ports. Here's the current rules.

```

sudo ufw status verbose

```

```

Status: active
Logging: on (low)
Default: deny (incoming), allow (outgoing), disabled (routed)
New profiles: skip

To                         Action      From
--                         ------      ----
80/tcp                     ALLOW IN    Anywhere
80                         ALLOW IN    Anywhere
80/tcp (v6)                ALLOW IN    Anywhere (v6)
80 (v6)                    ALLOW IN    Anywhere (v6)

25,53,80,110,443/tcp       ALLOW OUT   Anywhere
25,53,80,110,443/tcp (v6)  ALLOW OUT   Anywhere (v6)



```

 I'm guessing other rules need to be added to enable port forwarding and remote access to webcam images. I should add that a secure setup is desired.

---

### Post by scottbomb on 2015-12-15
This question is a little old but if anyone still has it, please post the contents of ~/.motion/motion.conf or /etc/motion/motion.conf.

---

