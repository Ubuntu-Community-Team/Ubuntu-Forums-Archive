---
title: "need suggest for Ubuntu Server 14.10 on HP Proliant ML10"
date: 2014-12-14
forum: Networking &amp; Wireless
---

### Post by n3wguys on 2014-12-14
Dear All,

May be this is stupid question but if I'm not ask, I don't know what should I do.
I had one server HP brand (proliant ML10) with high specification. and was installed Ubuntu 14.10 server.
Is the impossible make this server with: 
1. Server as Data center(file server)
2. install mysql as database server.
3. IP DHCP,DNS
4. Mail Server
5.other task server(print server,etc)

And all of application will be installed on one PC.I need suggest from you.

Thanks

---

### Post by tgalati4 on 2014-12-14
Install 14.04 LTS.  Any service that you run, you will want long-term-support.  I like to install *tasksel* and install the services from there:

```
sudo apt-get install tasksel
sudo tasksel
```

You have lots of reading to do:  [https://help.ubuntu.com/community/Servers](https://help.ubuntu.com/community/Servers)

Running a server is not simple.

---

### Post by n3wguys on 2014-12-15
Dear All,

Thank you that your suggest.. 
I had 1TB, and < 100GB for system, and other for Files storage with format NTFS. What do you suggest if space more empty for this server, or what should I do to manage all which all empty space of HDD could be use as maximal.

Thanks

---

