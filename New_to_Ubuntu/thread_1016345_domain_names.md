---
title: "domain names"
date: 2008-12-19
forum: New to Ubuntu
---

### Post by Archer Troy on 2008-12-19
im trying to setup ssh with my netowrked computers.

Im using this guide: [http://www.cyberciti.biz/faq/ubuntu-linux-openssh-server-installation-and-configuration/](http://www.cyberciti.biz/faq/ubuntu-linux-openssh-server-installation-and-configuration/)

In it it says i need a domain:
[B]
Assuming that your server hostname is userver.mydomain.com and username is vivek, you need to type the following command:[/B]

# ssh [email]vivek@userver.mydomain.com[/email]

what dopes that mean. whats my domain. can i use my network ip address (ex. 192.168.1.101)

any help would be greatly appreciated..thanks

---

### Post by bodhi.zazen on 2008-12-19
Yes you can use your ip address.

you domain is the name you give your computer. This will work on your LAN if you have a local DNS server or update your /etc/hosts on your clients.

A domain name is a public name for your ip address, like say ubuntuforums.org

If you want a public domain you need to use a free service like DynDNS or purchase one.

---

