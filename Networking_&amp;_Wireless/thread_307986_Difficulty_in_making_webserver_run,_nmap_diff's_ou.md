---
title: "Difficulty in making webserver run, nmap diff's output of ip'nr and localhost"
date: 2006-11-27
forum: Networking &amp; Wireless
---

### Post by Blindulo on 2006-11-27
Hi forum.

I'm trying to set up a web server.

When I use a browser to access localhost localy it works, however when I try from another mashine (or the machine itself with ip'nr instead of localhost in the address field) it doesn't work.

My nmap output is like this (Ubuntu 6.06):
```
:~$ nmap -A -T4 localhost 
```
-----------Output start-------------------
Starting Nmap 4.03 ( [http://www.insecure.org/nmap/](http://www.insecure.org/nmap/) ) at 2006-11-27 17:18 CET
Interesting ports on localhost (127.0.0.1):
(The 1669 ports scanned but not shown below are in state: closed)
PORT     STATE SERVICE    VERSION
22/tcp   open  ssh        OpenSSH 4.2p1 Debian-7ubuntu3.1 (protocol 2.0)
25/tcp   open  smtp       Exim smtpd 4.60
80/tcp   open  http       lighttpd 1.4.11
631/tcp  open  ipp        CUPS 1.2
5432/tcp open  postgresql PostgreSQL DB

Nmap finished: 1 IP address (1 host up) scanned in 6.545 seconds

------------Output end----------------------

And when I try:
```
 :~$ nmap -A -T4 10.0.0.2 
```
------------Output start--------------------
Starting Nmap 4.03 ( [http://www.insecure.org/nmap/](http://www.insecure.org/nmap/) ) at 2006-11-27 17:19 CET
Interesting ports on 10.0.0.2:
(The 1672 ports scanned but not shown below are in state: closed)
PORT   STATE SERVICE VERSION
22/tcp open  ssh     OpenSSH 4.2p1 Debian-7ubuntu3.1 (protocol 2.0)
25/tcp open  smtp    Exim smtpd 4.60
Service Info: Host: localhost

Nmap finished: 1 IP address (1 host up) scanned in 0.230 seconds
------------Output end-----------------------

The output from
```
 :~$ iptables -L 
```
-----------Output start----------------------
Chain INPUT (policy ACCEPT)
target     prot opt source               destination

Chain FORWARD (policy ACCEPT)
target     prot opt source               destination

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination
-----------Output end-------------------------

I'm a little paranoid so I changed my ip-nuber in the above examble however all the other output is correct ...

I realy hope one of you knows how to help me - and I'd gladly rtfm, if you just direct me to the correct manual.

Thanks in advance - Simon

---

### Post by koenn on 2006-11-27
possibly, you need to tell lighttpd its own address.
Apparently it takes 'localhost' (127.0.0.1) but doesn't know 10.0.0.2 is a valid address too. I guess this will need to be added in some config file here or there

I'm not too sure (the documentation says that it listens at all addresses by default) but it's worth a try. 

rt(f)m :) at [http://trac.lighttpd.net/trac/wiki/Docs%3AConfigurationOptions](http://trac.lighttpd.net/trac/wiki/Docs%3AConfigurationOptions)
start with 'core options'

eg re addresses : [http://trac.lighttpd.net/trac/wiki/server.bindDetails](http://trac.lighttpd.net/trac/wiki/server.bindDetails)

have fun

---

### Post by Blindulo on 2006-11-28
Thanks koenn.

You were right, after editing the /etc/lighttpd/lighttpd.conf and introducing the ip there it works.

It seems to have been due to physical network change after install at other location ... one learns a little every time.

Thanks again - Simon :)

---

