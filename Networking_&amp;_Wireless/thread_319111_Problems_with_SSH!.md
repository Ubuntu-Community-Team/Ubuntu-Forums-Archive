---
title: "Problems with SSH!"
date: 2006-12-15
forum: Networking &amp; Wireless
---

### Post by tokkos on 2006-12-15
Hi,

first id like to say that im kinda new to Ubuntu.
I recently installed a ubuntu 1.10 server and im having some troubles using ssh.

I install openssh and a firewall (Ubuntu Linux Firewall [http://rob.pectol.com/](http://rob.pectol.com/)) and in the firewall settings i set ssh on and port to 2222 and also changed this in the sshd config file.

When i try to access my server from my laptop using putty i keep getting Fatal Error Connection refused. ...

Ive read through ssh manuals but no help. Also couldve jumped over something important.

Any ideas on what i could try?

thanks.

---

### Post by pandu.rs on 2006-12-15
Check if u sshd is listening at port 2222 using the following command

netstat -an | egrep '2222|sshd'

if it gives any output paste it here.

---

### Post by tokkos on 2006-12-15
it gives the following:


tcp6    0     0   :::2222     :::*    LISTEN

---

### Post by pandu.rs on 2006-12-15
so the sshd is properly listening on port 2222.

may be the firewall is set not to drop the packet but rather reject it. please check ur firewall settings. (u can also turn it off for sometime and test to see if u r able to connect, but this shld be ur last option)

---

