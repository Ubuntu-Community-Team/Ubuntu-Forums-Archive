---
title: "DNS and wireless internet problem"
date: 2007-02-04
forum: Networking &amp; Wireless
---

### Post by spamzilla on 2007-02-04
The DNS setting on my laptop keeps changing to my routers default gateway, and because of this, I cannot connect to the internet. When I change the DNS to 203.8.183.1, I can connect to the internet fine.

I am using Dapper and my wireless card is SMC2635w.

Does anyone know how to fix this problem?

Cheers :KS

---

### Post by gradedcheese on 2007-02-04
You can edit /etc/resolv.conf or use the 'Networking' tool under the 'Administration' menu.  If the DNS server that your router uses is unreliable, you can pick some other one.  For example, you can make your /etc/resolv.conf look like this:

search opendns.com
nameserver 208.67.222.222
nameserver 208.67.220.220

to have opendns.com for DNS (just as an example).  Then the setting in your router becomes irrelevant.

---

### Post by spamzilla on 2007-02-04
Ok I have made the change to the /etc/resolv.conf file, and I'm going to hope that the file doesn't keep getting overwritten!

---

### Post by spamzilla on 2007-02-04
I have just turned on my laptop and the DNS setting had reverted back to my routers default gateway address. How do I stop this from happening?

---

### Post by Belfast on 2007-02-06
By default, the dhclient.conf file will overwrite the resolv.conf file each reboot, so you need to edit the dhclient.conf file:

1. Backup the file first:


sudo cp /etc/dhcp3/dhclient.conf /etc/dhcp3/dhclient.conf.bak

2. Edit the dhclient.conf file:


sudo gedit /etc/dhcp3/dhclient.conf

3. Look for the following line:


#prepend domain-name-servers 127.0.0.1;

Remove the comment (#) and change it to the ip address of your dns servers:
example:

prepend domain-name-servers 194.168.8.100,194.168.4.100;

4. Restart your network


sudo/etc/init.d/networking restart

---

### Post by spamzilla on 2007-02-06
That seemed to work, thanks :)

---

### Post by spamzilla on 2007-02-14
I have just upgraded to Edgy and this doesn't seem to work anymore. The DNS setting keeps reverting back to my routers default gateway, and I cannot connect to the internet.

---

