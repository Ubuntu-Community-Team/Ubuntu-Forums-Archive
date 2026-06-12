---
title: "[SOLVED] Internet Connection Sharing that enables VPN?"
date: 2008-11-24
forum: Networking &amp; Wireless
---

### Post by dasc on 2008-11-24
Hi,

I'm fairly new to ubuntu and so far have had an okay experience with it, but i seem to keep finding it fustrating to get solutions for simple stuff like bridging 2 network cards. or even ICS which is extremely easy in Windows.......

After hours of trying different methods, such as command lines to firestarter then back to command lines...... I finally got my ubuntu server share the internet connection.  Only to find that my VPN doesn't work anymore!  Which I had to switch the server back to windows for the VPN to work!

Current setup is as follows:-

PCs (ubuntu and windows) ----> (eth0, ubuntu acting as router, eth1) ----> internet

Can someone give me some really simple instructions on how to enable internet connection sharing that allows VPN connections to work?

Thanks!

Dasc

---

### Post by superprash2003 on 2008-11-24
could you elaborate on the "VPN doesnt work" part.. do you see any error message?? are you able to connect?? are you able to ping vpn server? are oyu using openvpn?

---

### Post by dasc on 2008-11-24
I currently have Interpid (AMD64) version but also run VMware workstation, and because a lot of my work applications need to use windows I still run windows on top of my system which I then use a VPN connection to connect from my virtual windows to a server.  The error message I got from windows while trying to connect to my vpn was something like "no respond from port".

[IMG]http://www.darevolution.co.uk/myvpn.png[/IMG]

do you think you can give me directions on how to set the vpn on ubuntu?  and also any pointers to make only connections that want to connect to 10.0.1.x goto the vpn connection ip which is dynamically allocated by the server?

the command I currently have to run every single time I connect to the vpn is:-
route add 10.0.1.0 mask 255.255.255.0 197.x.y.z

Thanks

Dasc

---

### Post by dasc on 2008-11-24
Not sure why but my ubuntu router seems to be forwarding the VPN now!

Very ODD!!!!!!!!!!!!!!!!

think the problem was with iptables and the topic to look into was iptables and pptp.

Feel free to delete this thread!

Dasc

---

