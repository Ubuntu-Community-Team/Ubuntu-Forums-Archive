---
title: "Ubuntu not accepting incoming connections from outside localhost"
date: 2014-02-09
forum: Networking &amp; Wireless
---

### Post by Jesbus on 2014-02-09
**Problem**
My ubuntu 13.10 is not accepting any incoming connection from other sources than 127.0.0.1, or the IP address obtained via DHCP (192.168.0.11)
I'm running an apache server on port 80, and a different HTTP server on port 3490.
On the computer I'm running it on, I can connect to 127.0.0.1:80 and I get the "It works!" and all that.
I can also connect to 127.0.0.1:3490
On all other computers in my LAN I cannot connect to the servers.
I'm not very experienced with GNU/Linux, or with Ubuntu.

**What I've tried**
$ sudo ufw allow 80
$ sudo ufw allow 3490
$ sudo iptables -A INPUT -m conntrack --ctstate NEW,RELATED,ESTABLISHED -j ACCEPT
$ sudo iptables -A INPUT -p tcp -d 0/0 -s 0/0 --dport 80 -j ACCEPT
$ sudo iptables -A INPUT -p tcp -d 0/0 -s 0/0 --dport 3490 -j ACCEPT
$ sudo iptables -A INPUT -p tcp --dport 80 -j ACCEPT
$ sudo iptables -A INPUT -p tcp --dport 3490 -j ACCEPT
$ sudo iptables -A INPUT -p tcp --sport 80 -j ACCEPT
$ sudo iptables -A INPUT -p tcp --sport 3490 -j ACCEPT
$ netstat -ntlup
Active Internet connections (only servers)
Proto Recv-Q Send-Q Local Address           Foreign Address         State       PID/Program name
tcp        0      0 0.0.0.0:3490            0.0.0.0:*               LISTEN      4114/TCPtest    
tcp6       0      0 :::80                   :::*                    LISTEN      1368/apache2
$ sudo iptables -L
Chain INPUT (policy ACCEPT)
target     prot opt source               destination         
ACCEPT     tcp  --  anywhere             anywhere             tcp dpt:http
ACCEPT     tcp  --  anywhere             anywhere             tcp dpt:http
ACCEPT     tcp  --  anywhere             anywhere             tcp dpt:3490
ACCEPT     tcp  --  anywhere             anywhere             tcp dpt:3490
ACCEPT     all  --  anywhere             anywhere             ctstate NEW,RELATED,ESTABLISHED
ACCEPT     tcp  --  anywhere             anywhere             tcp dpt:http
ACCEPT     tcp  --  anywhere             anywhere             tcp dpt:3490
ACCEPT     tcp  --  anywhere             anywhere             tcp dpt:3490
ACCEPT     tcp  --  anywhere             anywhere             tcp spt:3490
ACCEPT     tcp  --  anywhere             anywhere             tcp spt:http
ACCEPT     tcp  --  anywhere             anywhere             tcp dpt:http
ACCEPT     tcp  --  anywhere             anywhere             tcp dpt:http
ACCEPT     tcp  --  anywhere             anywhere             tcp dpt:3490

Chain FORWARD (policy ACCEPT)
target     prot opt source               destination         

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination         

Chain ufw-after-forward (0 references)
target     prot opt source               destination         

Chain ufw-after-input (0 references)
target     prot opt source               destination         

Chain ufw-after-logging-forward (0 references)
target     prot opt source               destination         

Chain ufw-after-logging-input (0 references)
target     prot opt source               destination         

Chain ufw-after-logging-output (0 references)
target     prot opt source               destination         

Chain ufw-after-output (0 references)
target     prot opt source               destination         

Chain ufw-before-forward (0 references)
target     prot opt source               destination         

Chain ufw-before-input (0 references)
target     prot opt source               destination         

Chain ufw-before-logging-forward (0 references)
target     prot opt source               destination         

Chain ufw-before-logging-input (0 references)
target     prot opt source               destination         

Chain ufw-before-logging-output (0 references)
target     prot opt source               destination         

Chain ufw-before-output (0 references)
target     prot opt source               destination         

Chain ufw-reject-forward (0 references)
target     prot opt source               destination         

Chain ufw-reject-input (0 references)
target     prot opt source               destination         

Chain ufw-reject-output (0 references)
target     prot opt source               destination         

Chain ufw-track-input (0 references)
target     prot opt source               destination         

Chain ufw-track-output (0 references)
target     prot opt source               destination 

And I've tried rebooting after all that.

Can anyone help?

---

### Post by TheFu on 2014-02-09
Which interfaces does apache listen on? That is in the /etc/apache2/ directory and could be in a site-specific file.
**<VirtualHost *:80>** is the line you want. If it says anything else, then only that IP will work, I believe.

It doesn't appear that any firewall is active, so you don't need to worry about that.
When you try to access, are you using a hostname or IP?

---

### Post by Jesbus on 2014-02-09
I'm using the IP to try to access it: [http://192.168.0.11](http://192.168.0.11)
This works locally, but not on other machines in the same LAN
There is no such line as **<VirtualHost *:80> **in my /etc/apache2/apache2.conf

---

### Post by Iowan on 2014-02-09
It might be in a site under * /etc/apache2/sites-enabled*
(which are links to sites under */etc/apache2/sites-available*

---

### Post by Jesbus on 2014-02-09
My **/etc/apache2/sites-enabled/000-default.conf **:

<VirtualHost *:80>
    ServerAdmin webmaster@localhost
    DocumentRoot /var/www
    ErrorLog ${APACHE_LOG_DIR}/error.log
    CustomLog ${APACHE_LOG_DIR}/access.log combined
</VirtualHost>

and my [B]/etc/apache2/sites-available/000-default.conf 
[/B]says exactly the same.

---

### Post by Iowan on 2014-02-09
What message do you get if you try to ping the server from another machine?

---

### Post by TheFu on 2014-02-09
Which version of Apache?  2.2 or 2.4?

---

### Post by Jesbus on 2014-02-10
Trying to ping the server (192.168.0.11) from a windows machine (192.168.0.17):
Pinging 192.168.0.11 with 32 bytes of data:
Reply from 192.168.0.17: Destination host unreachable.
Reply from 192.168.0.17: Destination host unreachable.
Reply from 192.168.0.17: Destination host unreachable.
Reply from 192.168.0.17: Destination host unreachable.

Pinging from my android phone (while connected to the same LAN) also fails with the same message.

Trying to ping the server (192.168.0.11) from itself (192.168.0.11):
PING 192.168.0.11 (192.168.0.11) 56(84) bytes of data.
64 bytes from 192.168.0.11: icmp_seq=1 ttl=64 time=0.037 ms
64 bytes from 192.168.0.11: icmp_seq=2 ttl=64 time=0.039 ms
64 bytes from 192.168.0.11: icmp_seq=3 ttl=64 time=0.050 ms
64 bytes from 192.168.0.11: icmp_seq=4 ttl=64 time=0.047 ms

Trying to ping the server (192.168.0.11) from my router (192.168.0.1):
PING 192.168.0.11 with 64 bytes of data:[Complete] 
Reply from 192.168.0.11: bytes = 64, time = 49 ms 
Reply from 192.168.0.11: bytes = 64, time = 49 ms 
Reply from 192.168.0.11: bytes = 64, time = 49 ms 
3/3 replies received. 
min time=10 ms, max time=121 ms, avg time=49 ms

@Thefu
Apache/2.4.6


I have discovered that if I forward port 80 on my router to 192.168.0.11, the outside world can reach the apache server.
Other machines on the same LAN can also reach it using my public IP or a domain name linking to my public IP, but not using [http://192.168.0.11](http://192.168.0.11)
I'm very confused now

---

### Post by TheFu on 2014-02-10
If machines on the same local network cannot ping each other, you have a network setup issue, NOT an apache config problem. For each of those machines, troubleshoot the connection to find what the issue is.  Avoid wifi for this.  
* client settings
* cable problems
* router settings

---

### Post by Jesbus on 2014-02-10
Yes, it has nothing to do with apache.
It also has nothing to do with the cables.
It also has nothing to do with the router settings.
It seems to have to do with the configuration of ubuntu, because if I boot the same machine with another OS everything works fine.

Machines can all ping eachother in my LAN, it's just this ubuntu machine that cannot be pinged by anyone else, except my router.

The ubuntu machine appears to only accept incoming connections from the gateway (192.168.0.1)

The question is now:
- How can I get Ubuntu 13.10 to accept any connections instead of just ones from the gateway/router?

---

