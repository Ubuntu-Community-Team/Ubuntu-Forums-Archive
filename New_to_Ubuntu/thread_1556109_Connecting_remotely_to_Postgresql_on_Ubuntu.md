---
title: "Connecting remotely to Postgresql on Ubuntu"
date: 2010-08-19
forum: New to Ubuntu
---

### Post by SteelCore on 2010-08-19
I've just installed Postgresql on an Ubuntu  virtual machine and am trying to connect to it (remotely) from my desktop but its failing
```
me@my-desktop:~$ psql -h 10.0.2.15 -d template1
psql: could not connect to server: Connection timed out
	Is the server running on host "10.0.2.15" and accepting
	TCP/IP connections on port 5432?
me@my-desktop:~$ 
```
I remember once reading that Ubuntu's default installation does not accept any outer connections. I'd appreciate any help on how to allow this connection on that port. Thanks in advance.

---

### Post by jtarin on 2010-08-19
> Is the server running on host "10.0.2.15" and accepting
	TCP/IP connections on port **5432?**And how would anything accept connections on a port configured as such, eg: "?".

---

### Post by SteelCore on 2010-08-19
> **jtarin said:**
> And how would anything accept connections on a port configured as such, eg: "?".

If I knew I wouldn't have asked.

---

### Post by nbkr on 2010-08-19
The default PostgreSQL installation only listens to connections from localhost.

Have a look at /etc/postgresql/<version>/main/postgresql.conf

There is a section with the option "listen_address". Modify this as appropriate and restart the database.

Postgresql should now listen to the network address specified.

You probably will have to reconfigure pg_hba.conf as well to allow your user to access the databases of the server via network.

---

### Post by SteelCore on 2010-08-19
I started the server process on the remote machine with this command:
```
$ /usr/local/pgsql/bin/postmaster -i -D /usr/local/pgsql/bin/data
```
according to the book I'm reading* the -i option enables remote clients which is equivalent to configuring postgresql.conf with listen_address='*' to allow all remote connections.

*Beginning Databases with PostgreSQL

---

### Post by nbkr on 2010-08-19
> **SteelCore said:**
> 
according to the book I'm reading* the -i option enables remote clients which is equivalent to configuring postgresql.conf with listen_address='*' to allow all remote connections.

That is true, however the information is outdated, see the manpage of postmaster:

> 
This option is deprecated since it does not allow access to the full functionality of listen_addresses. It's usually better to set listen_addresses directly.


However there is still the need to reconfigure pg_hba.conf. With the current setup, Postgres will listen not requests via network, but won't allow access to specific databases if it is not configured to do so.

---

### Post by jtarin on 2010-08-19
Iptables is a firewall, installed by default on all official Ubuntu distributions (Ubuntu, Kubuntu, Xubuntu). When you install Ubuntu, iptables is there, but it allows all traffic by default. Do you have a router by any chance?

Try the command ```
netstat -an | grep "LISTEN "
```

If you still think its a firewall issue you can run  this command to open that port.
```
ptables -A INPUT -p tcp -d 0/0 -s 0/0 --dport 5432 -j ACCEPT
```

---

