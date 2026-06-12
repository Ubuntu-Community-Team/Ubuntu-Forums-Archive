---
title: "Problems with Shorewall"
date: 2008-07-15
forum: Networking &amp; Wireless
---

### Post by Sico2 on 2008-07-15
Hi all,

I try to install Xerobank service on my Acer 5920G with Ubuntu8.04 and follow these instructions:
[http://support.xerobank.com/wiki/doku.php?id=howto_lockdown_debian_ubuntu_openvpn](http://support.xerobank.com/wiki/doku.php?id=howto_lockdown_debian_ubuntu_openvpn)

At the bottom there is a command :

Test Everything

    *      Start Shorewall

/etc/init.d/shorewall restart

After I do that:root@********:~# /etc/init.d/shorewall restart
I get a message :

Restarting "Shorewall firewall": not done (check /var/log/shorewall-init.log).

In the LOG it says...
19:34:51 Determining Zones...
   IPv4 Zones: net vpn loc
   Firewall Zone: fw
19:34:51 Validating interfaces file...
   ERROR: Invalid zone (eth0) in record "eth0 -  "

I checked my ethernet and I am running under eth0. What can I do to solve this please?! Anyone?

---

### Post by toallpointswest on 2008-07-15
The file you need to edit is /etc/shorewall/zones but overall, you should read the documentation on shorewall for a proper setup.

---

### Post by Sico2 on 2008-07-16
My zones file looks like this:

############################################################################### 
#ZONE   TYPE            OPTIONS         IN                      OUT 
#                                       OPTIONS                 OPTIONS 
fw      firewall 
net     ipv4 
vpn     ipv4 
loc     ipv4 

#LAST LINE - ADD YOUR ENTRIES ABOVE THIS ONE - DO NOT REMOVE

and in the documentation everywhere I find in the web, says the same. Still no changes. Has anyone a clue?

---

