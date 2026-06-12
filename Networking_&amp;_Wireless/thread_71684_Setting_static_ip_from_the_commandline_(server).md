---
title: "Setting static ip from the commandline (server)"
date: 2005-10-04
forum: Networking &amp; Wireless
---

### Post by zenslug on 2005-10-04
I'm trying to set up a server using Breezy, but I want to use a static IP. On installation (server) I wasn't offered an opportunity to set the IP, and now I would like to make sure it is static and also change it.
How can I change the addresss from the commandline? Thanks

---

### Post by zenslug on 2005-10-04
Allow me to answer my own question...

[http://ubuntuforums.org/archive/index.php/t-18619.html](http://ubuntuforums.org/archive/index.php/t-18619.html)

**alastair** has the answer, which I'm reposting here:

> **alastair**
03-08-2005, 05:12 PM
The network config is given in the file :

/etc/network/interfaces

see : man interfaces

It is perfectly acceptable to rquest the same IP address from a DHCP server - or have it assign the same IP address to you (via MAC address say). This is something best configured via the DHCP server I think.

For static addressing, by all means stop "dhclient" (or whatever) from running and manually assign an ip address e.g.

ifconfig eth0 down
ifconfig eth0 <ip address> netmask <mask>

e.g.

ifconfig eth0 192.168.0.10 netmask 255.255.255.0

Check with "ifconfig eth0".

Or, in the "interfaces" file :

iface eth0 inet static
address 192.168.0.10
netmask 255.255.255.0
network 192.168.0.0
broadcast 192.168.0.255
gateway 192.168.0.1

Adjust to your needs.

I ran (as root) "ifconfig eth0 192.168.0.10 netmask 255.255.255.0" after changing it to the IP addr that I wanted to use. Voila, worked like a charm.

---

### Post by Jan Wilkens on 2005-11-07
Hello, i am a little new to UBUNTU server but speeding up.
Installed on a old PC and working ok with DHCP.
But because it's a server and it should be connectable from internet i would like to give the ubuntu server a static Ip adres.

I have read the most of the posts about STATIC IP but i can't get it working.

iface eth0 inet static
address 192.168.1.81
netmask 255.255.255.0
network 192.168.1.0
broadcast 192.168.1.255
gateway 192.168.1.1

when i call: sudo ifup eth0  i get the message: Don't seem to be have all the variables for eth0/inet. Failed to bring up eth0

if i use: sudo ifconfig eth0 192.168.1.81 it works fine.

what is needed to edit interfaces as to give the eth0 the static IP during booting?
Thanks in advance.
jan Wilkens

---

### Post by Jan Wilkens on 2005-11-08
Yes i believe that works.
But when you start the machine again you have to do the same trick again and again.

I would like that the ETH0 starts every time with the same STATIC IP adres. I don't want to replace it after each reboot from ubuntu.
How do i fix that?
Thanks Jan Wilkens

---

### Post by Jan Wilkens on 2005-11-09
Well at last i found out what was the problem.
I missed the last S from address.
After surching it was clear it must be my definitions, and yep it was.
I changed  addres to address and it was running after  /etc/init.d/networking restart.
I like it.....

---

