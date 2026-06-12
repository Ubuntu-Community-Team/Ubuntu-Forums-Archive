---
title: "azureus not downloading"
date: 2008-11-05
forum: Networking &amp; Wireless
---

### Post by guest_user on 2008-11-05
I'm trying to download kubuntu intrepid ibex through torrenting but the speed is close to nil although there are 511 seeders. I have guarddog firewall installed but have enabled the bittorrent tracker and peer options, what's wrong and how do I correct this problem? :confused::confused:

thanks.

---

### Post by rlzyoner on 2008-11-05
You should make sure that the required ports on your router have been opened.
Once you do that, use a port scanner like nmap to ensure that they are opened.

```
sudo apt-get install nmap
```

Then run command like 

```
nmap 192.168.2.1
``` or whatever the IP addy of your router is.

Not too sure what the ports for azereus are but their website should mention that somewhere

---

### Post by guest_user on 2008-11-05
when I do a firewall test using azureus, I get the following results:

Testing port 60640 ... 
NAT Error - Connection to <censored IP>:60640 (your computer) refused
Proxy IP is '<censored IP>', original is '<censored IP> ('Forwarded-For' request header was '<censored IP>').

I'm using port 60640 for both tcp udp listening port

nmap router IP yields:

PORT     STATE  SERVICE
21/tcp   closed ftp
25/tcp   closed smtp
53/tcp   closed domain
80/tcp   open   http
110/tcp  closed pop3
143/tcp  closed imap
443/tcp  open   https
465/tcp  closed smtps
993/tcp  closed imaps
6881/tcp closed bittorent-tracker (I'm using 60640 not 6881 for azureus)
6969/tcp closed acmsoda
8080/tcp closed http-proxy
8888/tcp closed sun-answerbook

when I do nmap 127.0.0.1, here are the results, what's the issue?

Not shown: 1708 closed ports
PORT     STATE SERVICE
22/tcp   open  ssh
80/tcp   open  http
631/tcp  open  ipp
3306/tcp open  mysql
8118/tcp open  privoxy
9050/tcp open  tor-socksport

btw, I have mysql and apache installed but I don't want to run it at the moment, why are the ports open and how do I close it?
EDIT: Ok nvm I disabled the services already for apache and sql, glad I checked myself lol

---

### Post by guest_user on 2008-11-05
ups for help

---

