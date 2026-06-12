---
title: "What Happened to the Network Manager in 13.10?"
date: 2014-02-01
forum: Networking &amp; Wireless
---

### Post by sam30 on 2014-02-01
In Kubuntu 11.10 there was a program called Network Manager that allowed you to scan for wifi points. It was accessible through the wifi beacon in the system tray.

On 13.10, what is the comparable program? It seems that the Network Manager is gone. What I want to do is look at the configuration options for my wi-fi points.

---

### Post by varunendra on 2014-02-02
It is still there in Ubuntu 13.10, not sure about Kubuntu. Does this bring up the configuration box ? -
**Alt-F2 > nm-connection-editor**

Is NetworkManager installed? Check with -
```
dpkg -l | grep network-manager
```
If yes, are there any problems in its loading? Check with -
```
cat /var/log/syslog | grep NetworkManager
```
..or probably full output of syslog (don't post here, just take a look yourself) without filtering with grep.

In Ubuntu, when sometimes (not normally) the applet fails to load, it can be manually loaded with -
**Alt-F2 > nm-applet**

---

