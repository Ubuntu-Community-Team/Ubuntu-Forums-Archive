---
title: "Problem to connecting to MySQL remotely"
date: 2008-12-18
forum: New to Ubuntu
---

### Post by mafiacooper on 2008-12-18
I'm on Ubuntu8 running MySQL5 which is working as it should locally. However, I cannot connect to the MySQL server remotely. Port 3306 is listening correctly and the firewall on the remote machine is configured correctly. I have also set up a user without a password for testing purposes.

When I try to connect I receive the following error:
```

Unable to connect to MySQL server on <ip> ('10061')

```
I have restarted mysqld several times and have even rebooted the server, but I still can't connect. IPTables is definitely allowing connections to port 3306:
```

-A INPUT -i eth0 -p tcp -m tcp --dport 3306 -j ACCEPT

```
I have been tackling this for over four hours now and am pulling my hair out now, does anyone have any suggestions?

Thanks :)

---

### Post by jespdj on 2008-12-18
I'm not a MySQL expert, but as far as I know MySQL itself by default only accepts local connections. You can change this somewhere in the configuration of MySQL. Have a look in the [MySQL manual](http://dev.mysql.com/doc/refman/5.1/en/).

---

### Post by mafiacooper on 2008-12-18
Yeah, spot on. I had to alter the config slightly, commenting out "skip-networking" and changing the bind-address to the IP of the host machine.

Thanks for the super-swift response :D

---

