---
title: "Port 3306 connection refused.  Opening this port for SQL."
date: 2017-12-18
forum: Networking &amp; Wireless
---

### Post by timothylegg on 2017-12-18
Hello, I am running Ubuntu 16.04 as a virtual machine on a host system managed by another department.

 I want MariaDB to be remotely accessible on port 3306.

On the console, I can telnet localhost 3306 and see that I could hypothetically interact with the SQL server.

```
$ telnet localhost 3306
Trying 127.0.0.1...
Connected to localhost.
Escape character is '^]'.
j
5.5.5-10.0.31-MariaDB-0ubuntu0.16.04.2Dquwtcq08-?f{X'U[F-Lv20mysql_native_password

```
On the same console, I can use the machine's IP address and I get "Connection refused".

```

$ telnet 10.204.x.y 3306
Trying 10.201.x.y...
telnet: Unable to connect to remote host: Connection refused

```

To the best of my knowledge the firewall is disabled, but I cannot promise that there is only one firewall installed.  The network and virtual machine admins tell me the packets are blocked within my machine.  From this, I ask for two approaches to this.  How can I either:

 
[LIST]
[*]Prove that my machine is listening on 3306? 
[*]Determine the fault on my system? 
[/LIST]
 
Being a virtual machine, I lack the convenience of carrying in my Linksys SOHO router and plugging this machine and my laptop into it to eliminate my machine as the source of the fault.  I only have a highly awkward access to the host system admin panel (imagine a crowd of system admins standing behind my shoulders and snooper-vising as I attempt to tinker with VMWare on a Microsoft product).  I am open to using network diagnosis tools, but lack expertise in their operation.

This problem may also be related to a separate issue that appeared last week on Tuesday: outgoing port 80/443 requests also not working as of Tuesday morning last week.

```
$ openssl s_client -connect google.com:443
connect: Connection refused
connect:errno=111
```

```
$ telnet www.google.com 80
Trying 172.217.21.100...
Trying 2a00:1450:4016:80a::2004...
telnet: Unable to connect to remote host: Network is unreachable
```

In fact the only port 80 addresses that I've verified to work are either localhost or the inet address 10.201.x.y...

Any ideas?

---

### Post by spjackson on 2017-12-19
> **timothylegg said:**
> Hello, I am running Ubuntu 16.04 as a virtual machine on a host system managed by another department.

 I want MariaDB to be remotely accessible on port 3306.

On the console, I can telnet localhost 3306 and see that I could hypothetically interact with the SQL server.

```
$ telnet localhost 3306
Trying 127.0.0.1...
Connected to localhost.
Escape character is '^]'.
j
5.5.5-10.0.31-MariaDB-0ubuntu0.16.04.2Dquwtcq08-?f{X'U[F-Lv20mysql_native_password

```
On the same console, I can use the machine's IP address and I get "Connection refused".

```

$ telnet 10.204.x.y 3306
Trying 10.201.x.y...
telnet: Unable to connect to remote host: Connection refused

```

The above looks like MariaDB is configured to listen on localhost only. Does my.cnf contain the following line?
```

bind-address = 127.0.0.1

```
See [https://mariadb.com/kb/en/library/configuring-mariadb-for-remote-client-access/](https://mariadb.com/kb/en/library/configuring-mariadb-for-remote-client-access/)
> 
To the best of my knowledge the firewall is disabled, but I cannot promise that there is only one firewall installed.  The network and virtual machine admins tell me the packets are blocked within my machine.  From this, I ask for two approaches to this.  How can I either:

 
[LIST]
[*]Prove that my machine is listening on 3306? 
[*]Determine the fault on my system? 
[/LIST]
 
Being a virtual machine, I lack the convenience of carrying in my Linksys SOHO router and plugging this machine and my laptop into it to eliminate my machine as the source of the fault.  I only have a highly awkward access to the host system admin panel (imagine a crowd of system admins standing behind my shoulders and snooper-vising as I attempt to tinker with VMWare on a Microsoft product).  I am open to using network diagnosis tools, but lack expertise in their operation.

This problem may also be related to a separate issue that appeared last week on Tuesday: outgoing port 80/443 requests also not working as of Tuesday morning last week.

```
$ openssl s_client -connect google.com:443
connect: Connection refused
connect:errno=111
```

I'm not sure about that.
> 
```
$ telnet www.google.com 80
Trying 172.217.21.100...
Trying 2a00:1450:4016:80a::2004...
telnet: Unable to connect to remote host: Network is unreachable
```

In fact the only port 80 addresses that I've verified to work are either localhost or the inet address 10.201.x.y...

That looks like a firewall issue.

Also, is your VM successfully accepting any inbound connections, e.g. ssh or http? I mention this because with VirtualBox (I don't know about VMWare) the default networking type is NAT but it needs to be Bridged for inbound connections to work.

---

### Post by timothylegg on 2017-12-19
Yes, bind-address = 127.0.0.1 is in a file included in the my.cnf  I independently found that same MariaDB page.  I have tried commenting that line and restarting the server.  The same behavior continues.

As far as the firewall goes, it appears that both ufw and iptables are used on this machine.  The ufw service is verified to be disabled and iptables appears to be wide open.

```
# iptables -L -n -v

Chain INPUT (policy ACCEPT 0 packets, 0 bytes)
 pkts bytes target     prot opt in     out     source               destination         
 259K  230M ACCEPT     all  --  *      *       0.0.0.0/0            0.0.0.0/0           
   49  2660 ACCEPT     tcp  --  *      *       0.0.0.0/0            0.0.0.0/0            tcp dpt:3306 flags:0x17/0x02

Chain FORWARD (policy ACCEPT 0 packets, 0 bytes)
 pkts bytes target     prot opt in     out     source               destination         

Chain OUTPUT (policy ACCEPT 130K packets, 129M bytes)
 pkts bytes target     prot opt in     out     source               destination 
```

Be advised: That is a typo in the original posting where the IP address changed  between 201 and 204 in the telnet command.  I originally decided to privacy-mod the IP, but finding that a bit of effort, I simply substituted with 'x' and 'y'.  I missed one.  Being an internally assigned static IP, it doesn't even matter, but I'm just adhering to privacy concerns that others here have.

---

### Post by SeijiSensei on 2017-12-19
> **timothylegg said:**
> Yes, bind-address = 127.0.0.1 is in a file included in the my.cnf  I independently found that same MariaDB page.  I have tried commenting that line and restarting the server.  The same behavior continues.

Try
```
bind-address=*
```

Any better?

---

### Post by Tadaen_Sylvermane on 2017-12-19
Every tutorial I have followed shows doing this rather than *

```
bind-address            = 0.0.0.0
```

Not saying it won't work, just that the above works fine for my mysql server in the living room for remote media centers. I'm sure the mariadb syntax is identical.

---

### Post by timothylegg on 2017-12-20
I tried the bind-address            = 0.0.0.0 yesterday per MariaDB documentation and the bind-address=* that Sensei suggested.  Neither had an effect.

I am increasingly suspecting that the network interface on the VM admin side is faulty (I just can't prove it).  Those things are exasperatingly 'magical'.  Aside from this, I also have two VirtualBox VMs that can't find the network when in "bridged mode".  This is likely attributed to a bug report already filed and I'm using the obsolete Ubuntu package. That issue is it's own thread on an other site but it matches the theme of the past week.

The VM admin is out sick today and I need to personally see the network config at this point.  I'll get back to this thread hopefully tomorrow with an update.

---

### Post by spjackson on 2017-12-20
> **timothylegg said:**
> I tried the bind-address            = 0.0.0.0 yesterday per MariaDB documentation and the bind-address=* that Sensei suggested.  Neither had an effect.
Changing the bind-address from 127.0.0.1 is **necessary** if you want to allow inbound connections. However, if you have other network issues that block the connection, you will of course need to solve those too. Is your VM successfully accepting any inbound connections, e.g. ssh or http?

---

### Post by SeijiSensei on 2017-12-20
bind-address=* applies to both IPv4 and IPv6 interfaces should they both exist.  It is the factory default.

[https://dev.mysql.com/doc/refman/5.7/en/server-options.html#option_mysqld_bind-address](https://dev.mysql.com/doc/refman/5.7/en/server-options.html#option_mysqld_bind-address)

---

### Post by timothylegg on 2017-12-21
> **spjackson said:**
> Changing the bind-address from 127.0.0.1 is **necessary** if you want to allow inbound connections. However, if you have other network issues that block the connection, you will of course need to solve those too. Is your VM successfully accepting any inbound connections, e.g. ssh or http?

I have made this change.  Yes, the machine is serving a helloworld page on port 80 and that is visible.  I connect via ssh, so port 22 is working.

Now, I had an epiphany... There is a wonderful tool called netcat (nc in our Ubuntu world).

I stopped the MariaDB server. I used netcat to listen on 3306 and was able to 'chat' with this machine from another machine.  This proves that 3306 is not blocked on this server.

This is a MariaDB Server issue.  MariaDB is refusing the connection.  Since this is no longer a network related issue, I'm considering wrapping this thread up in a day or so, and posting a new one in a MariaDB specific thread.  I'm practically certain now that the outgoing port 80 requests being blocked is a configuration on hardware that I don't have authority over and will not pursue that any further here either.

---

