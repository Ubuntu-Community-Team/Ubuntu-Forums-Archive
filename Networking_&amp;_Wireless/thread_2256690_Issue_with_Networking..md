---
title: "Issue with Networking."
date: 2014-12-14
forum: Networking &amp; Wireless
---

### Post by anonymous0programmer on 2014-12-14
I am trying to set up an ethernet connection between my laptop and my desktop to share an internet connection over it but something is broken. When I try to add a connection I get an error. This happens with any kind of connection but it works when I use wicd to connect to wifi. This was happening for a while now but when it first started I just decided to install wicd which was working for internet but now I need to manage an ethernet connection to my desktop which seems to require network-manager-gnome to do. 

```
(nm-applet:14792): nm-applet-WARNING **: Failed to register as an agent: (32) Error statting file /var/run/ConsoleKit/database: No such file or directory
```
[IMG]http://i.imgur.com/kOdgdDr.png[/IMG]

---

### Post by SeijiSensei on 2014-12-14
If you're not averse to using the command line and editing text files, you can set up the network connection by editing /etc/network/interfaces as described here: [https://help.ubuntu.com/14.04/serverguide/network-configuration.html#ip-addressing](https://help.ubuntu.com/14.04/serverguide/network-configuration.html#ip-addressing)

---

