---
title: "Ubuntu 16.04 DNS/Networking Issues"
date: 2018-01-10
forum: Networking &amp; Wireless
---

### Post by Daniel_Clarke on 2018-01-10
We recently upgrade one of our web server's from 14.04 to 16.04 LTS. Ever since we upgraded the websites have been going up and down, or timing out. When the websites do this it appears the server which is a VM in Microsoft Hyper-V cluster loses internet connectivity. Pings are unsuccessful, however if I do run a dig command, I can successfully run pings after and the websites return to a working status.  I read an article about Ubuntu Network Manager by default uses dsnmasq and that by disabling it there is a good possibility that it will resolve my issue. I tired the following:

Edit /etc/NetworkManager/NetworkManager.conf with the following command:

sudo nano /etc/NetworkManager/NetworkManager.conf

**Results:**

*Directory 'etc/NetworkManager' does not exist*

Should network manager be installed? When I try to restart it using one of the following commands:

sudo service network-manager restart
or
sudo systemctl restart network-manager

I get the following:

*Failed to restart network-manager.service: Unit network-manager.service not found.*

So now what?


Thanks in advance for any and all help.


-daniel

---

### Post by TheFu on 2018-01-10
Network manager isn't used on server installs.

When troubleshooting any issues on Linux, check the log files first.

---

### Post by Daniel_Clarke on 2018-01-10
TheFu,

Thank you for your response, new Linux user here. Which log would that be specifically? Any addiitonal tips, this is getting really frustrating. The network keeps going up and down, however every other machine in the Hyper V cluster has connectivity. It has to be something on the specific VM causing the issue.

Thanks in advance

-daniel

---

### Post by TheFu on 2018-01-10
There are lots of different log files on Unix system. They are generally placed in /var/log/ - so I'd **grep** in there.  There are lots of little tips for finding issues in log files - you can search for those.  Some distros have a GUI log viewer.  Most of my systems don't have any GUI (only 2 do, all the others do not), so that is useless to me.

I generally just use egrep to search all the current logs.
```
$ egrep -i  'error|warn' /var/log/*g

```
But there are 50+ other methods. Find one that works for you.

I've never touched Hyper-V, but have read about problems with it and Linux. We don't use Windows much (just 1 accounting PC remains).  I figure they had solved most of those, but with all the new Intel/AMD CPU patching this week (and BIOS/firmware + GPUs), anything could be happening. Could easily be a host issue, a client issue or an odd interaction between them.  Or it could be something completely different. The logs would help narrow that down.

I don't consider clustering isn't a topic for noobs, BTW.  What type of 'clustering' are you doing?  Is it simple heartbeat style for multiple services, HPC stuff or just a load balanced front-end?

---

