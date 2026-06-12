---
title: "in my lan I cannot see subdomain"
date: 2018-11-04
forum: Networking &amp; Wireless
---

### Post by nos30 on 2018-11-04
in my lan have 2 computers
comp 1 installed apache 
hostname is ben
from comp 2 i can see [http://ben](http://ben)

I created a subdomain test.ben
edited hosts add
127.0.0.1 test.ben

created virtual host in apache
<VirtualHost *:80>
    ServerName test.ben
    DocumentRoot /http/test.ben
#        <Directory /http/test.ben/>
#                Options Indexes FollowSymLinks MultiViews
#                AllowOverride All
#                Require all granted
#        </Directory>
</VirtualHost>


  if I access [http://test.ben](http://test.ben) from server(comp 1) is visible and working
if I access from computer 2 is not , only [http://ben](http://ben) can be viewed 

what is need more to make it functional ?

---

### Post by TheFu on 2018-11-05
You need to fix IP name resolution.  That can be accomplished in 3 different ways.

* edit the /etc/hosts file on each computer
* setup a DNS server and tell all devices and computers on the network to use it.
* Use the DNS capabilities of your router to provide DNS services.

Regardless the web server will need to have a static IP so the other devices/computers and DNS will know where it is supposed to be on the IP network.

This is how all IP networks work the least 40+ yrs.
[http://blog.jdpfu.com/2011/07/18/use-your-router-to-centralize-your-network-device-management](http://blog.jdpfu.com/2011/07/18/use-your-router-to-centralize-your-network-device-management) will try to explain a little more. Not all home routers support DHCP reservations or provide DNS.  If yours doesn't, then just edit the /etc/hosts file on each after you setup static IPs.  I use static IPs on all non-portable devices - that's servers and desktops.

---

