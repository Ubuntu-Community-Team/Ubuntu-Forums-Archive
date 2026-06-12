---
title: "NetworkManager starting/stopping"
date: 2015-09-03
forum: Networking &amp; Wireless
---

### Post by cogset on 2015-09-03
I've been trying to start/stop and check NetworkManager status in Trusty using the old fashion /etc/init.d route and also upstart, to my surprise neither is working: although I can see a traditional network-manager.conf script in /etc/init containing the usual lines   ```
start on (local-filesystems           and started dbus           and static-network-up) stop on stopping dbus 
```  there is no correspondent script in /etc/init.d, whilst the upstart command  *sudo NetworkManager status* returns  this ```
 NetworkManager is already running (pid 646)
```   so what process is actually in control of NetworkManager ?

---

### Post by ian-weisser on 2015-09-04
In Trusty, NM is started by that Upstart job (/etc/init/network-manager.conf), not sysvinit (/etc/init.d/).

> start on (**local-filesystems**           and **started dbus**           and **static-network-up**)
stop on stopping dbus
NM is automatically started by init when those three conditions are satisfied.

There are several ways to check NM's status.
One is the nm-applet.
Another is the 'service' command. Try 'service network-manager status'
Another is the 'nmcli' command. See 'man nmcli'
Another, more appropriate for other applications, is dbus. [Some examples]("http://cheesehead-techblog.blogspot.com/2012/09/dbus-tutorial-fun-with-network-manager.html").

---

### Post by cogset on 2015-09-14
> **ian-weisser said:**
> 

There are several ways to check NM's status.
One is the nm-applet.
Another is the 'service' command. Try 'service network-manager status'
Another is the 'nmcli' command. See 'man nmcli'
Another, more appropriate for other applications, is dbus. [Some examples]("http://cheesehead-techblog.blogspot.com/2012/09/dbus-tutorial-fun-with-network-manager.html").

Thanks, the nm-applet is not what I was after (I wanted to place a command in rc.local to disable networking on start up in order to re-enble it later on manually when I do actually need it) .

As for *service network-manager status*, no joy either, it yields the same result as status [I] NetworkManager status.

[/I]Finally, nmcli works nicely and allows me to disable the network at boot and enable it later on.

---

