---
title: "How do I change the Fully Qualified Domain name?"
date: 2005-09-28
forum: Networking &amp; Wireless
---

### Post by adityanag on 2005-09-28
Hi,
I am trying to setup Ubuntu5.04 as a mailserver for my college. My problem is, all mail that gets sent gets sent as [email]user@localhost.loca[/email]ldomain
Obviously the mail cannot be replied to.
I have tried the obvious things:
1. Changed /etc/hosts so that it looks like this
127.0.0.1 localhost.localdomain localhost <my domain name>
<my public IP> <Fully qualified domain name> mail
# The following lines are desirable for IPv6 capable hosts
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts
2. Changed /etc/hosts so that it contains my FQDN
The problem persists...
I am going batty trying to set the hostname.
Ubuntu and Debian gurus, please help. 
Also, while I was installing the OS, i had give the FQDN when it asked for a machine name.
Thanks.
!!!!!!!!!!!!!!!!!!!!!_________________________!!!!!!!!!!!!!!!!!!!!!!
I figured it out! Edit /etc/mailname and replace localhost.localdomain with the  domain...

---

### Post by mlomker on 2005-09-28
I'd imagine that's actually in the mail server config.  Are you use Postfix or something else?

Look in /etc/postfix/main.cf

---

