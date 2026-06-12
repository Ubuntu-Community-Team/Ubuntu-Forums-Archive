---
title: "vpnc blocks internet access"
date: 2007-01-20
forum: Networking &amp; Wireless
---

### Post by Ulrich Scholz on 2007-01-20
Dear all,

I'm using vpnc version 0.3.3 on Kubuntu 6.10.

vpnc-connect works fine and I can connect to the private network - that's not a problem.

But I cannot access the internet anymore: For example Opera does not load any website - they just stay blank.

After vpnc-disconnect everything works fine again.

What is going on here?

Thank you,

Ulrich

---

### Post by jtp51 on 2008-03-03
Ulrich, I have the exact same problem.

I connect with:

[FONT="Courier New"]sudo vpnc-connect MyCompany-Outside[/FONT]

then I am unable to connect to the internet. I disconnect with:

[FONT="Courier New"]sudo vpnc-disconnect[/FONT]

then my internet connect is just fine.

Have you managed to find a solution?

---

### Post by netztier on 2008-03-03
> **Ulrich Scholz said:**
> 

After vpnc-disconnect everything works fine again.

What is going on here?



vpnc is modifying the routing table. Compare the output of **netstat -nr** when connected via VPN and when disconnected. By default, the default route is pointing through the tunnel interface towards the private network once the connection is there. If you configure other routes, these are put in place instead of the default route.

I am using network-manager's vpnc-plugin which does not have a config file in /etc/vpnc. So I had to add two statements in System Tools -> Configuration Editor, in /system/networking/vpn_connections/<connection name>/routes, in "192.168.1.100/25" notation.

You might want to check vpnc's documentation about routing table modifications.

regards

Marc


PS: Connecting to a VPN probably also modifies your /etc/resolv.conf, normally in a way that while connected, you're using the private network's DNS.

---

### Post by jtp51 on 2008-03-04
> **netztier said:**
> I am using network-manager's vpnc-plugin which does not have a config file in /etc/vpnc. So I had to add two statements in System Tools -> Configuration Editor, in /system/networking/vpn_connections/<connection name>/routes, in "192.168.1.100/25" notation.

Marc:

To make sure I understand this statement. You added 192.168.1.100/25 to:

1.) /system/networking/vpn_connections/<connection name>/routes

And

2.) System Tools -> Configuration Editor

Did you mean two places or two statements?

Thanks,

---

### Post by netztier on 2008-03-04
> **jtp51 said:**
> Marc:

To make sure I understand this statement. You added 192.168.1.100/25 to:

1.) /system/networking/vpn_connections/<connection name>/routes

And

2.) System Tools -> Configuration Editor

Did you mean two places or two statements?

Thanks,

Configuration Editor (gconf-editor) is somewhat like Windows' Regedit, and this is the place you have to "navigate" to:

/system/networking/vpn_connections/<connection name>/routes

In the right window pane, you'll see the "routes" entry which is still empty (two square brackets []). Double-click it and add the routes you need to be set for your private network(s). Mine has two routes, therefore I had to add two entries.

regards

Marc

---

### Post by The Cog on 2008-03-04
I believe that the Cisco VPN client actually disables your ethernet interface for packets other than the VPN itself when you log in. This is done in the name of security in that you cannot then act as a bridge between the corporate network and the Internet.

That's if you are using the Cisco client of course.

---

### Post by jtp51 on 2008-03-04
That fixed the issue. Thank you!

---

### Post by netztier on 2008-04-29
> **The Cog said:**
> 

That's if you are using the Cisco client of course.

... and the Checkbox "allow local LAN access" is disabled ;-), or if your VPN client got a local policy  pushed-upon by the VPN concentrator that forbids all non-VPN traffic.


regards

Marc

---

