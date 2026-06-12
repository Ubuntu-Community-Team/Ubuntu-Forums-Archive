---
title: "Connection problems (Cable)"
date: 2008-10-08
forum: Networking &amp; Wireless
---

### Post by JensS on 2008-10-08
Hello! 
I have just installed Ubuntu 8.04 in dualboot with XP. Everything runs smoothly but I can't connect to the internet. In windows I'm using DHCP, and everything is working great. In Ubuntu I get 100% packetloss to my gateway. When running ifconfig i only get an IPv6 and no IPv4, if that helps at all.
Help or suggestions will be very much apreciated, as I'm really eager to start using Ubuntu :)

---

### Post by yogensha on 2008-10-10
Are you using DHCP in Ubuntu?  Most ISPs require you to complete a DHCP transaction before you can connect.

If you are using DHCP in Ubuntu and you're not able to obtain an IP address (try running ifconfig to see), try running an ipconfig/release command from the windows command prompt before you boot to Ubuntu.

---

