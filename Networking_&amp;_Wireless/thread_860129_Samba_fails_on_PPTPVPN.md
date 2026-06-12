---
title: "Samba fails on PPTP/VPN"
date: 2008-07-15
forum: Networking &amp; Wireless
---

### Post by Leed on 2008-07-15
We are using a Windows 2003 Small Business Server and a XP Laptop to share files in our office, and all works fine together with my Ubuntu client...

But another Ubuntu client abroad is coming in via VPN using PPTP and can't access the shares on our network. I can access the remote client via VNC, so the connection is definitely there.

Upon connecting to windows shares using samba it get's as far as the username/password request for the shares, so there's definitely a connection, but I just can't get it to show whats in the shares... I just get an error saying it cannot display the contents

can anyone imagine what the problem here is?

---

### Post by Leed on 2008-07-17
Further details:

In Windows this connection works, unfortunately it's my boss using Ubuntu because his Windows crashed. 

If you type in a wrong username/password when connecting to the shares, it recognizes this and tells you to try again. Only if you get it right it brings an error, that it can't display the contents of the share. 

In the other direction, I can see shares on the machine connected to the office over pptp. 

I have a similar problem with VNC, from the office to the external pc's it runs fine (externals connecting via pptp). From the external pc's to an office machine the VNC can move the mouse, but on the external screen the windows stays blank.

---

### Post by noblunts on 2008-07-17
Is the firewall and all of the port forwarding set up right?

---

### Post by Leed on 2008-07-18
Firewall and PPTP Server are both in the same device (Linksys RV042).

While normal LAN connections are in the ip Range 192.168.x.100-200
The VPN PPTP Clients are assigned the ip Range 192.168.x.200-204

So basically they are in the same internal Network when connected, akka behind the firewall. I just seems that either something is being filtered or that samba has some trouble getting the relevant data. 

Intranetpages can be viewed via http
Pinging the Server works

The connection to the share is made, but the contents of it are just not getting in

---

### Post by slimx3m on 2009-02-12
> **Leed said:**
> Firewall and PPTP Server are both in the same device (Linksys RV042).

While normal LAN connections are in the ip Range 192.168.x.100-200
The VPN PPTP Clients are assigned the ip Range 192.168.x.200-204

So basically they are in the same internal Network when connected, akka behind the firewall. I just seems that either something is being filtered or that samba has some trouble getting the relevant data. 

Intranetpages can be viewed via http
Pinging the Server works

The connection to the share is made, but the contents of it are just not getting in

i am kind of having the same problem too.  have you have a chance to resolve it?

---

