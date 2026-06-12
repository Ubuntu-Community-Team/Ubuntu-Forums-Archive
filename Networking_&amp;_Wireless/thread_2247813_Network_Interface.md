---
title: "Network Interface"
date: 2014-10-10
forum: Networking &amp; Wireless
---

### Post by shamz_71 on 2014-10-10
When i enter 

[B]$ nano /etc/network/interfaces


[/B]i see no interfaces.
Im running Ubuntu 12.04 in Vmware workstation with network set to use "Bridge" method.
Ubuntu has ip and can reach internet ( i tried to iinstall few packages and it worked) 

I get this screen.

[ATTACH=CONFIG]257106[/ATTACH]

---

### Post by TheFu on 2014-10-10
Network Manager is why.

**ifconfig** will show the interfaces on a running system.

---

### Post by grahammechanical on 2014-10-11
This is what my interfaces file says:

> # interfaces(5) file used by ifup(8) and ifdown(8)
auto lo
iface lo inet loopback


And that is all it needs to say on desktop Ubuntu. Add other things to that file and it will prevent up Network Manager from working. If the system works as it should, then what is the problem? Is this a server? Do you have a need for the interfaces file to have more than the default information?

See this wiki on Network Manager and the section called Issues

[https://help.ubuntu.com/community/NetworkManager](https://help.ubuntu.com/community/NetworkManager)

> [COLOR=#333333][FONT=Ubuntu]If it is not managing your network connections, you'll need to comment out the references to all interfaces (except lo) in /etc/network/interfaces to let Network Manager handle them.[/FONT][/COLOR]

Regards.

---

### Post by TheFu on 2014-10-11
I suspect you are reading some book on managing linux. Those are NOT for current release desktops. They are often 10 yrs out of date.  I know the 2011 LPI book is.  It has some files in it that haven't been used in 30 yrs.

So - you are running 12.04 Desktop or 12.04 server?

---

