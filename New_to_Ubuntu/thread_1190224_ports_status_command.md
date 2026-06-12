---
title: "ports status command"
date: 2009-06-17
forum: New to Ubuntu
---

### Post by akkad on 2009-06-17
is there a command for listing each app/process with its associated listening port?

---

### Post by The Cog on 2009-06-17
sudo netstat -plntu

---

### Post by Cheesemill on 2009-06-17
Or you can install nmap (apt-get install nmap) and then run:
```
 sudo nmap -p- -sV 127.0.0.1
```The -p- means scan all ports and the -sV attempts to figure out the service that's running.
It's a hugely powerful tool for network scanning, take a look at the man pages for more options.

---

### Post by porchrat on 2009-06-17
netcat could work too.

Type "man netcat" to read the manual for netcat.

I belive it is installed by default in Ubuntu.

---

### Post by scorp123 on 2009-06-18
> **akkad said:**
> is there a command for listing each app/process with its associated listening port? ```
sudo lsof -n -i -P
``` .. This should produce what you want.

If I do that here I get:

```
> sudo lsof -n -i -P

COMMAND     PID  USER   FD   TYPE DEVICE SIZE NODE NAME
sshd       2708  root    3u  IPv4   7142       TCP *:22 (LISTEN)
sshd       2708  root    4u  IPv6   7144       TCP *:22 (LISTEN)
avahi-dae  3333 avahi   14u  IPv4   8681       UDP *:5353 
avahi-dae  3333 avahi   15u  IPv4   8682       UDP *:50469 
cupsd      3361  root    2u  IPv6 635382       TCP [::1]:631 (LISTEN)
cupsd      3361  root    3u  IPv4 635383       TCP 127.0.0.1:631 (LISTEN)
cupsd      3361  root    5u  IPv4 635386       UDP *:631 
vino-serv  3983  john   17u  IPv6  12237       TCP *:5900 (LISTEN)
firefox   11720  john   70u  IPv4 819736       TCP 10.26.8.191:39583->172.16.221.18:443 (ESTABLISHED)
firefox   11720  john   77u  IPv4 819978       TCP 10.26.8.191:39585->172.16.221.18:443 (ESTABLISHED)
exaile    17276  john   11u  IPv4 134331       TCP 127.0.0.1:1881 (LISTEN)
exaile    17276  john   32u  IPv4 582693       TCP 10.26.8.191:50733->192.168.233.57:80 (CLOSE_WAIT)
dhclient  24168  root    5w  IPv4 775323       UDP *:68

```

The process names are on the left, followed by their process ID ("PID") (useful if you need to kill it because it's misbehaving or something like that) and then followed by protocol type and what port it is listening to and what activity is going on there.

---

### Post by bodhi.zazen on 2009-06-18
```
cat /etc/services
```

 I prefer ```
sudo lsof -n -i -P
``` as posted by scorp123

Nothing wrong with the other suggestions either.

---

