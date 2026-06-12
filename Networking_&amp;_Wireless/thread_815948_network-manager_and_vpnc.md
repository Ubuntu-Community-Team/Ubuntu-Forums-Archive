---
title: "network-manager and vpnc"
date: 2008-06-02
forum: Networking &amp; Wireless
---

### Post by dnaxx on 2008-06-02
Hello,
I am trying to connect to a Cisco VPN Network using network-manager-vpnc but I face the following issues:
1.) When I leave the group or user password empty, the network-manager-vpnc disappears from the Gnome panel (but it's still running as a process). How can I redisplay this icon?
2.) Where does network-manager-vpnc stores the connection settings? Under "/etc/vpnc" there is only an example script.

Regards,

---

### Post by netztier on 2008-06-02
> **dnaxx said:**
> Hello,
2.) Where does network-manager-vpnc stores the connection settings? Under "/etc/vpnc" there is only an example script.


See, use or install **gconf-editor**, and you'll find them (or at least some of the information) in [FONT="Courier New"]/system/networking/wireless[/FONT] and [FONT="Courier New"]/system/networking/vpn_connections[/FONT]. 

As far as I know, this is only a graphical representation of what you can find as XML files in your home directory under [FONT="Courier New"]~/.gconf/system/networking/...[/FONT] (and subdirs)

regards

Marc

---

### Post by dnaxx on 2008-06-02
ok, thanks.

---

### Post by achortleaday on 2008-07-22
I have the same exact problem, only when the icon disappears it remains running but still doesn't connect to VPN at all. I used to use KVpnc, but it didn't work with firefox and now doesn't connect at all. How can I make the icon reappear, and how can I actually connect to vpn??

---

