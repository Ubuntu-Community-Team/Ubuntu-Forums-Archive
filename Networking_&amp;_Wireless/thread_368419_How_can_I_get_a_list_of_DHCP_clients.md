---
title: "How can I get a list of DHCP clients?"
date: 2007-02-23
forum: Networking &amp; Wireless
---

### Post by pebkac on 2007-02-23
Hello

I have a recently-installed Ubuntu-edgy distribution on a new server. This server has NO GUI. 

I would like to make it the DHCP server for our network (this is currently being handled by the server that this one will be replacing.) the old server is Mandrake MNF that has a web-interface you can log into and print off a sheet of your DHCP clients.

How would I do this on Ubuntu? I assume that I would have to console in. What would be the commands to type or file to look in? I use the VIM editor.

Any advice on setting up DHCP via the command interface would also be appreciated.

---

### Post by Strider on 2007-02-23
Take a look here: 
[http://ubuntuguide.org/wiki/Ubuntu_Edgy#DHCP_Server](http://ubuntuguide.org/wiki/Ubuntu_Edgy#DHCP_Server)

-Mike

---

### Post by koenn on 2007-02-23
setting up a dhcp server is as easy as installing the package and editing /etc/dhcp3/dhcpd.conf 

this could give you an idea:
[http://users.telenet.be/mydotcom/howto/linuxsbs/intro.htm#dhcp](http://users.telenet.be/mydotcom/howto/linuxsbs/intro.htm#dhcp)


dhcp leases are recorded in /var/lib/dhcp3/dhcpd.leases so you can find who got what addrss there

---

### Post by pebkac on 2007-02-23
> **Strider said:**
> Take a look here: 
[http://ubuntuguide.org/wiki/Ubuntu_Edgy#DHCP_Server](http://ubuntuguide.org/wiki/Ubuntu_Edgy#DHCP_Server)

-Mike

Mike, Wow, that is fantastic... and I even learned that there is a Web Administration tool that I did not know about. Thanks for that link.

Koenn, thanks, that file is what I needed.

---

### Post by Strider on 2007-02-23
Glad to help. :)

---

