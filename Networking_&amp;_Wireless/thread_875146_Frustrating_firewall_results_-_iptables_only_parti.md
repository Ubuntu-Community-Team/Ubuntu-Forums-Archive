---
title: "Frustrating firewall results - iptables only partially working"
date: 2008-07-30
forum: Networking &amp; Wireless
---

### Post by ASK47 on 2008-07-30
My iptables rules don't seem to work completely.

```
*filter
:INPUT ACCEPT [8:955]
:FORWARD ACCEPT [0:0]
:OUTPUT ACCEPT [7:955]
#-A INPUT -j LOG --log-level 4
#-A INPUT -j DROP
-A INPUT -i lo -j ACCEPT
-A INPUT -d 127.0.0.0/255.0.0.0 -i ! lo -j REJECT --reject-with icmp-port-unreachable
-A INPUT -m state --state RELATED,ESTABLISHED -j ACCEPT
-A INPUT -p tcp -m tcp --dport 80 -j ACCEPT
-A INPUT -p tcp -m tcp --dport 110 -j ACCEPT
-A INPUT -p tcp -m tcp --dport 443 -j ACCEPT
-A INPUT -p tcp -m tcp --dport 110 -j ACCEPT
-A INPUT -p tcp -m tcp --dport 143 -j ACCEPT
-A INPUT -p tcp -m tcp --dport 25 -j ACCEPT
-A INPUT -p tcp -m tcp --dport 465 -j ACCEPT
-A INPUT -p tcp -m tcp --dport 993 -j ACCEPT
-A INPUT -p tcp -m tcp --dport 995 -j ACCEPT
-A INPUT -p tcp -m state --state NEW -m tcp --dport !!OBSCURED ON PURPOSE!! -j ACCEPT
#Allow pings
-A INPUT -p icmp -m icmp --icmp-type 8 -j ACCEPT
-A INPUT -m limit --limit 5/min -j LOG --log-prefix "denied: " --log-level 7
-A INPUT -j REJECT --reject-with icmp-port-unreachable
-A FORWARD -j REJECT --reject-with icmp-port-unreachable
-A OUTPUT -j ACCEPT
COMMIT
```

If I comment out the port 80 line, it works as expected: no web sites, and port scan won't find it. Or, if I uncomment the DROP line, all connections are refused. So the file works to a degree.

Trouble is, most of the ports specified in iptables seems to be ignored. A complete port scan only reveals 25, 80, and 3306. Which is what netstat returns:

```
...
tcp        0      0 localhost:mysql         *:*                     LISTEN      2177/mysqld     
tcp        0      0 *:www                   *:*                     LISTEN      14085/apache2   
tcp        0      0 *:smtp                  *:*                     LISTEN      23885/master 
...
```

what am I missing? I'm so close to having email, but now I'm hitting my head against the keyboard.

This is on a recent Hardy install, but I figure the answer will apply to other versions.

---

### Post by ASK47 on 2008-07-30
Later, after a reboot, I noticed a module associated with ufw had a problem loading. So I uninstall ufw. And lo and behold, my problem goes away.

The thing is, I didn't even install ufw until after my problem started! I had installed it in the hopes of maybe fixing the above problem, and apparently it did - by uninstalling it!

---

