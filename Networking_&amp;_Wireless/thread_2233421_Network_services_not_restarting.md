---
title: "Network services not restarting"
date: 2014-07-08
forum: Networking &amp; Wireless
---

### Post by numan2 on 2014-07-08
Hi all,

I'm running Ubuntu server 14.04 and I'm able to ssh into the box.  I'm having a issue with connecting externally.  What I want to do is install gnome and updates.  I did nslookup google.com and it came back with results but I tried it again and it didn't resolve.

I added my network setting by doing: 'sudo vim /etc/network/interfaces'
Below are my network settings:
auto eth0
iface eth0 inet static
address 10.4.1.103
netmask 255.255.255.0
network 10.4.1.0
broadcast 10.4.1.255
gateway 10.4.1.1
#dns-* options are implemented by the resolvconf package, if installed
dns-nameservers 10.4.1.1


When I put these network settings in I did the following command to restart network services: 'sudo /etc/init.d/networking restart'
nothing happened.  It didn't restart networking services.  I did reboot the box so I'm assuming it got restarted that way.

I tried to ping the gateway from the box but was not able to.  

I have a Palo Alto FW and I looked at the policy for DNS and it's setup correctly... although in the logs I need 2 packets were sent and 0 received for DNS.

Any suggestions will be greatly appreciated!

Thanks

---

### Post by TheFu on 2014-07-08
Try: **sudo service networking restart**

Did you check
* ifconfig?
* route?

Would it help to disconnect from ssh after running the command?  Don't know if this will help or not.

---

### Post by numan2 on 2014-07-09
Solved. Issue was on the Palo Alto FW.  I needed to add the DMZ zone to outbound translation rules for DNS to work.

Thanks!

---

