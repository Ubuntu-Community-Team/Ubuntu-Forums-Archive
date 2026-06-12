---
title: "Harden Ubuntu Linux Web Server"
date: 2008-03-13
forum: Networking &amp; Wireless
---

### Post by ubuntoexpert on 2008-03-13
I have a fresh copy of ubuntu linux on my box, running, and Ive just installed xampp webserver.... Can someone describe the next steps as too administer this system? I will be installing webmin next.... I have used the security script to lock down the xampp server (mysql passowrd, phpmyadmin...etc etc) What do I nned to know....logging, security etc etc...

---

### Post by Paul Weaver on 2008-03-13
If you run a web server, the only port that should be open is 80 (and possibly ssh for remote access). By default Ubuntu won't have any ports open. 

MySQL should be configured to only accept connections from 127.0.0.1. PHPmyadmin, if needed, should be installed in a non-obvious location just in case, preferably only accepting connections from known IPs, and secured with a decent password.

To be honest I'm not a fan of the XAMPP product (or any product that's not in the multiverse), I prefer something like /apt-get install phpmyadmin mysql-server/, which installs Apache, php, mysql etc and configures those nice things like log rotation.

---

### Post by Oldsoldier2003 on 2008-03-13
> **ubuntoexpert said:**
> I have a fresh copy of ubuntu linux on my box, running, and Ive just installed xampp webserver.... Can someone describe the next steps as too administer this system? I will be installing webmin next.... I have used the security script to lock down the xampp server (mysql passowrd, phpmyadmin...etc etc) What do I nned to know....logging, security etc etc...

some thoughts on hardening the server after you are finished...

never run the telnet service, its insecure because passwords are sent clear text- use ssh instead

ftp is the same way, the only way i would consider running ftp is for an anonymous ftp download only site.- SFTP is a better solution

disable root login over ssh

set roots shell to bin/false to prevent interactive sudo sessions

adjust sudo permissions for any additional sudoer you allow on the system.

install and run bastille, if you want you can also use it to initially set up your iptables.

Install DenyHosts to protect yourself from ssh brute force attacks.

consider jailkit or some other chroot protections to keep your ssh users where they belong.

---

### Post by OffAxis on 2008-03-13
Don't forget your router! 
If you're running a hardware firewall there and are only forwarding port 80 through to your server then you're pretty well protected.
Head over to [www.grc.com](www.grc.com) and run a port scan of your address to make sure.

---

### Post by ubuntoexpert on 2008-03-13
>>Don't forget your router! 
what do u mean exactly by this ?

---

### Post by SpaceTeddy on 2008-03-13
basicially turn everything off that is listening on any network port...
to figure out what is listening
```
sudo netstat -lnp
```

right at the top is a list of the programms that listen on network ports at the moment - stop anything that you do not know what it is or what it does or you have not started by yourself! also, make sure they do not come back after a reboot (try this also ! you never know when you might have a reboot).
as for open ports - i'd say 80 and 443 (http and https) are ok, also maybe 22 (ssh) on external network cards. On the loopback, you also want to allow 3306 (mysql).
anything else gets closed down. 

set your default rules for the paket filter to drop - not reject (or so i do it) and only allow inbound connections to the ports you use. Allow outbound only on port 53 udp (DNS) and 80 tcp (http) to get updates for your machine - it should not do anything else than that !!!

also, set your root password. I know this is not recommended in ubuntu, but if you are running a server, it does not matte really, and gives you a tiny bit of advantage if someone cracks your password - then they still need roots password ! (obviously, make them different !)

make sure that apache is running under a user that has no rights except the one it needs (this is usualy the standard setup, but one never knows - checking is better than believing)

set your mysql root password. don't use root connections to the mysql server aswell. make sure the sql server is only bound to localhost (127.0.0.1).

always check for updates regularly on a server - bugs get fixed every day

That is all i can think of quickly in securing the server itself... :)

---

