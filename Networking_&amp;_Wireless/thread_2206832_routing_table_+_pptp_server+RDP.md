---
title: "routing table + pptp server+RDP"
date: 2014-02-21
forum: Networking &amp; Wireless
---

### Post by argon2 on 2014-02-21
Hello dear community, this my first post. 

I have Xubuntu 12.04 with installed PPTP server which connects to external VPN server (86.x.x.x) in another city and xubuntu recieve after connection from his DHCP pool addresses like 1.1.1.x. The users in our office connecting via RDP to xubuntu with particular addresses 1.1.1.20 (etc) and recieve remote desktop.

The problem is route to local network to users which i need to insert manually every time when PPTP server disconnects/reconnect.
[CENTER]"sudo ip route add 1.1.1.0/20 dev ppp0"[/CENTER]

When this route is disappear from routing table, PPTP server is connected. So i insert again.
 After reboot route doesnt work.

How i can add 1.1.1.0/20 ppp0 it to kernel or permanent static route and see it after reboot? // I tried to /etc/network/interfaces and /etc/rc.local but not working.

PLEASE HELP GOOD PEOPLE , I spend 2 days to solve this problem!

---

