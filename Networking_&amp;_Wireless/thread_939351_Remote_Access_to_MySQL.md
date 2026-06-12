---
title: "Remote Access to MySQL"
date: 2008-10-05
forum: Networking &amp; Wireless
---

### Post by naugiedoggie on 2008-10-05
Hello,

I set up the MySQL server on U 7.10.  I can log in fine on 'localhost' only.  I can't connect remotely from another machine, and also I can't connect locally if I use the machine name or IP address instead of 'localhost' or 127.0.0.1.  

I found a suggestion on the net about setting bind-address to the system address, but that didn't solve the problem.

If I log into MySql admin tool, the user shows '@%' for login access, which should give it universal access.  Doesn't.  At the same time, root shows the machine name as one of its login access options ... that doesn't work either.

For grins, I logged in through mysql client and put in 'grant all *.* user@'%'', but it had no effect.

This problem seems to be machine/system specific.  I have MySql running on a Windows system that is accessible remotely and I didn't do anything special, I just added the user in the the admin tool.

Any help would be appreciated.

Thanks.

mp

---

### Post by Drezard on 2008-10-05
First, make sure all the information is configured correctly in Mysql (I'm sure theres a configuration file somewhere).

Second, check and make sure a firewall isn't blocking it. You may have one such as UFW, iptables or such on the server and check NAT on your router.

Hopefully that should help.

Anymore questions... feel free to ask. 

Daniel

---

