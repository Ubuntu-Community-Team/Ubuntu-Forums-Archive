---
title: "Host lookups on LAN"
date: 2007-08-29
forum: Networking &amp; Wireless
---

### Post by deanoj on 2007-08-29
Hi everyone

I'm looking for a simple solution to the following problem:

I have 2 machines, both running Ubuntu 7.04 on a home network.

Development Box: 192.168.11.2: hostname: wizard
My Desktop PC: 192.168.11.3: hostname: camelot

Basically, I have several local web sites running such as phpmyadmin, phpldapadmin etc... on wizard. The hostnames follow the format:

   phpmyadmin.wizard
   phpldapadmin.wizard
   othersite.wizard

What's the easiest way to tell 'camelot' to look at the wizard box for *.wizard???

At the moment I use the hosts files and create a separate entry for each one. But I'm looking for a more efficient solution. I really don't want to use something like BIND - which seems complete overkill.

Thanks in advance - deanoj

---

### Post by will71110 on 2007-08-29
I believe all you need to do is add a search domain in the DNS settings.  Are you using GUI or CLI?

---

### Post by deanoj on 2007-08-29
Using both actually.

I have tried adding the line to resolve.conf on the camelot machine:

nameserver 192.168.11.2

camelot cannot find the local sites.....

---

### Post by will71110 on 2007-08-29
well if you add something as in nameserver, then the device need to have DNS install and DHCP or manual entries need to be added.

A search domain just add info to the end of your hosts.  Example

Lets say to ping camelot and DNS says no host was found then it will add
.wizard to the end.

Unless you have a domain or network named wizard of course that wont work.

How do you resolve your host names?  Are you running DHCP?

---

### Post by deanoj on 2007-08-29
I have a router which supports DHCP but with only having the 2 machines I set the IP addresses manually.

When it comes to host name resolving I just used an entry in each machines /etc/hosts for the other machine.

i.e. on camelot:

192.168.11.2   wizard

on wizard:

192.168.11.3   camelot

---

### Post by will71110 on 2007-08-29
Does your router also do the DNS?

---

### Post by deanoj on 2007-08-29
Yes the DNS on my machines is set to the router IP 192.168.11.1

Which is also the gateway

---

### Post by will71110 on 2007-08-29
You should be able to resolve the host name via dns then.  Do you have an option on the router to setup a domain name or a workgroup?

---

### Post by deanoj on 2007-08-29
I have no options like that on my router....it's pretty crap to be fair....

---

### Post by will71110 on 2007-08-29
Well you could run DHCP and DNS on your ubuntu OS.  I dont have much experance setting up that on Ubuntu though.

---

### Post by deanoj on 2007-08-29
As I mentioned seems like a lot of effort for a few local sites.

I'll stick to the host file.

Thanks for your time though ;-)

---

