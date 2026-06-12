---
title: "Ubuntu secure MySQL by allowing only 2 servers to reach it"
date: 2016-06-09
forum: Networking &amp; Wireless
---

### Post by Nikola_Petkovic on 2016-06-09
Hello.
[COLOR=#242729][FONT=Arial]I own 3 servers, one is a MySQL server, one is a game server, and the third one is the web server. I have enabled remote MySQL, but due to security reasons, i'd like to use iptables to allow only those two servers to connect to MySQL (webserver and game server), how can i do this? Thanks in advance.[/FONT][/COLOR]

---

### Post by Fire_Chief on 2016-06-10
For simplicity in configuration, I'd recommend using UFW to set the rules for iptables. You will have a rule to allow tcp/3306 from your game server to MySQL. Then a second rule to allow tcp/3306 from your web server to MySQL. There is a default deny all rule at the end of the rule set already.
Note that if you want SSH access to the MySQL box or any other network access, you need to add rules for those items as well.

Cheers!

---

### Post by SeijiSensei on 2016-06-10
```

#!/bin/bash
# limit access to MySQL to two remote addresses

SRV1=192.168.1.1
SRV2=192.168.1.2

/sbin/iptables -A INPUT -p tcp -i lo --dport 3306 -j ACCEPT
/sbin/iptables -A INPUT -p tcp -s $SRV1 --dport 3306 -j ACCEPT
/sbin/iptables -A INPUT -p tcp -s $SRV2 --dport 3306 -j ACCEPT
/sbin/iptables -A INPUT -p tcp --dport 3306 -j REJECT

```

Put that in a file using "sudo nano /usr/local/sbin/mysql_rules" with the appropriate IP addresses for SRV1 and SRV2.  Then mark it executable with 
```
sudo chmod a+x /usr/local/sbin/mysql_rules
```
Now add the line "/usr/local/sbin/mysql_rules" to /etc/rc.local above the "exit 0" line.  Now those rules will be run every time you reboot.

The first line grants access to the "localhost" interface so you can connect to the server from the machine itself.  The next two lines permit the specified machines, and the last blocks access from anywhere else.

---

