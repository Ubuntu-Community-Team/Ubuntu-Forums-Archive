---
title: "DHCP Server problems, Webmin &amp; Ubuntu Server 7.10"
date: 2007-12-11
forum: Networking &amp; Wireless
---

### Post by PogMoThoin on 2007-12-11
Hi all,

Firstly, I'm only 2 months using linux, so would stil consider myself a n00b. Be easy on me :D

I've got my server setup using [this]("http://linuxgazette.net/141/lazar.html") guide. All went well except that MySQL Database server wouldn't start automatically after a reboot, so i added this command:
[[IMG]http://img236.imageshack.us/img236/7638/mysql1vc7.th.png[/IMG]](http://img236.imageshack.us/my.php?image=mysql1vc7.png)

Now i need to use the server to handle dhcp, but i cant for the life of me figure out why it wont startup. The server ip is 192.168.10.1 on eth1(lan). I'm trying to add 192.168.10.10 to 10.20 to the dhcp address range. These following pics are my settings.
[[IMG]http://img255.imageshack.us/img255/9986/dhcp1no2.th.png[/IMG]](http://img255.imageshack.us/my.php?image=dhcp1no2.png)
[[IMG]http://img125.imageshack.us/img125/322/dhcp2tp5.th.png[/IMG]](http://img125.imageshack.us/my.php?image=dhcp2tp5.png)
[[IMG]http://img69.imageshack.us/img69/7448/dhcp3yu2.th.png[/IMG]](http://img69.imageshack.us/my.php?image=dhcp3yu2.png)

This is the what my config file looks like:
[[IMG]http://img45.imageshack.us/img45/6896/dhcpconfigsf3.th.png[/IMG]](http://img45.imageshack.us/my.php?image=dhcpconfigsf3.png)

This is what i get when i try to start dhcp:
[[IMG]http://img243.imageshack.us/img243/4489/dhcp4qe4.th.png[/IMG]](http://img243.imageshack.us/my.php?image=dhcp4qe4.png)

Sorry for the long post, but this problem has me tearing my hair out.

Thanks in advance

Pog

---

### Post by nixfaced on 2007-12-11
Hi, 

I suspect that dhcpd is starting on the wrong interface, eth0 rather than eth1.  IIRC, it'll fail if dhcpd.conf doesn't contain a subnet declaration for the network the interface is on.  So if eth0 has your internet IP (or no IP, or isn't even there), and dhcpd tries to start there and what it sees doesn't match its configuration, it keels over.

In any event, try editing /etc/default/dhcp3-server so that it contains INTERFACES="eth1".

Disclaimer:  I'm not running 7.10 or webmin, and I'm not running my dhcp server on ubuntu at all.  This is just what I worked out after installing dhcp3-server on my Dapper box and having a look-see.  Hope this helps.

---

