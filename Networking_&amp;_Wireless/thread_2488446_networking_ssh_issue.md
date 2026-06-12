---
title: "networking ssh issue"
date: 2023-07-04
forum: Networking &amp; Wireless
---

### Post by krazykanuk36 on 2023-07-04
I am a long time slackware user, who just switched to ubuntu (Ubuntu 22.04.2 LTS). Once installed I renamed the first wired ethernet card to eth0 (simplicity for what I am use to). I can ssh from a windows computer (securecrt) to the lan IP address with no issue. I have a port forward in my internet providers modem/router to the ubuntu ip address. When I try to ssh to my external ip I get  "Hostname lookup failed: host not found" I log in to the internal ip and then try to ssh to external ip and it works like a charm. In past set up /etc/hosts /etc/resolv.conf make sure ethernet card was up and working with static ip and routes were correct and it was a done deal. Any help on this matter would be greatly appreciated.

---

### Post by ixeous on 2023-07-04
When you try to connect, you aren't by chance on the lan network you were describing that works were you?  I have seen weirdness with that.  Your client system is NATing out to get to the external which is trying to loop back to itself.  There are ways to make it work, but I don't think they are usually worth it.

---

### Post by SeijiSensei on 2023-07-05
You may need to enable IP packet forwarding. By default, Ubuntu and many other distros do not pass packets between interfaces for security reasons.

Check the file /etc/sysctl.conf and remove the hash mark from 
```
#net.ipv4.ip_forward=1
```
to enable forwarding. If you run "sudo sysctl -p" the kernel will read the new configuration. See if it works any better after that.

If that doesn't help, we'll need to look into routing.

---

### Post by TheFu on 2023-07-05
Some routers think that packets from the LAN side trying to access the WAN port are an attack vector and the router blocks those.  Most routers have a way to disable that.

Rather than describe what you are doing, please post the exact commands and the output. Please use code tags.  It is fine to change the public IP, if you like, but leave everything else as is.  It would also help if you turn up the verbosity for the connection. For example, 

```
$ ssh -vv username@IP
```

What would tell us much.

Also, if you have any ~/.ssh/config settings that could be impacting the connection, that would be good to know too.  I use that file to make ssh connections to different userids, non-standard ports and to remote servers easy. Basically, I never need to actually know those things once I setup a stanza in the config file.  All libssh tools honor it - so ssh, scp, rsync, rdiff-backup, x2go, and 50 other tools all honor what is in the ~/.ssh/config file.

---

### Post by krazykanuk36 on 2023-07-05
It seems to be working once I enabled ip packet forwarding.

---

### Post by TheFu on 2023-07-06
> **krazykanuk36 said:**
> It seems to be working once I enabled ip packet forwarding.

There are some huge security implications in allowing a router on a Linux system that isn't also a firewall.  Please be careful. If you have a router and computers on the same LAN, enabling forwarding isn't required.

---

