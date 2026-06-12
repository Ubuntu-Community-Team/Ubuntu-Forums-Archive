---
title: "Failed attempts to connect MyODBC Connector to MariaDB. Error 10060 on Ubuntu Server"
date: 2023-06-14
forum: Networking &amp; Wireless
---

### Post by zoomiest2 on 2023-06-14
I am trying to make an ODBC connection from a windows deskto to a remote Ubuntu server with MyODBC Connector. 

BACKGROUND:

 
[LIST]
[*]I have configured the /etc/mysql/my.conf (commented out the bind-address, and the skip-networking) 
[*]I have port 3306 open, on my ufw firewall. 
[*]I have granted access on the remote MariaDB with: GRANT ALL ON user1.* TO 'db1'@'%' IDENTIFIED BY '(pwd)’' WITH GRANT OPTION; 
[/LIST]

 Weird responses:

 ```
netstat -ntlp | grep -i mariadb (returns:)
tcp   0   0 127.0.0.1:3306     0.0.0.0:*        LISTEN      964/mariadbd 
```

So, it looks like MariaDB **is** listening on port 3306
 But,
 ```
$ sudo nmap -sT x.x.x.x -p 3306 (returns:)
PORT     STATE  SERVICE
3306/tcp closed mysql

```
 
So it looks like MariaDB is **not** listening to port 3306, hence my 10060 error.
 Am I interpreting this correctly? 
How can I connect to my remote MariaDB on Ubuntu Server 22.04? I have  read all the documentation, and it all seems to come down to these  things, which I have done.

---

