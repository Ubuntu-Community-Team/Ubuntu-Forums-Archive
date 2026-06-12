---
title: "D-Link DSL-504T &amp; Ubuntu (6.06, IPv6): Problem solution"
date: 2006-07-22
forum: Networking &amp; Wireless
---

### Post by alexus_fs on 2006-07-22
My sister had problems using Ubuntu (6.06, IPv6) with the D-Link DSL-504T router. The DDNS did not work.
Some people seems to have the same problem, as I have found in many posts.
Here is a simply solution that do not require to disable IPv6.
It is a summary of all the suggestions I have found in posts (thanks to pyton [see: [http://ubuntuforums.org/showpost.php?p=50664&postcount=2]](http://ubuntuforums.org/showpost.php?p=50664&postcount=2]) and others) plus a bit of my workaround.

===============================================
GNU/Linux Ubuntu (6.06, IPv6) + D-Link DSL-504T
===============================================

---------------
D-Link DSL-504T
---------------
(configure it by typing the router's IP address in your browser)

- DHCP: 
Enable DHCP server and configure it as you need.

- DNS:  Set it this way:
* DNS relay = Use User Discovered DNS Server Only
* Preferred DNS server = xxx.xxx.xxx.xxx (the IP of your ISP dns1 server)
* Alternate DNS server = yyy.yyy.yyy.yyy (the IP of your ISP dns2 server)

-----------------------------
GNU/Linux Ubuntu (6.06, IPv6)
-----------------------------
(you have to act as root)

- NETWORKING:
(from: Computer->System configuration->Networking)
* DHCP: Enable
* DNS:  Add these two entries:
        xxx.xxx.xxx.xxx (the IP of your ISP's dns1 server)
        yyy.yyy.yyy.yyy (the IP of your ISP's dns2 server)
        and delete all the others !!!

- FILE /etc/resolv.conf
Edit (from a terminal: $ sudo gedit /etc/resolv.conf) this file adding these two entries:

   nameserver xxx.xxx.xxx.xxx (the IP of your ISP's dns1 server)
   nameserver yyy.yyy.yyy.yyy (the IP of your ISP's dns2 server)

and comment out (put a # preceeding rows) all other entries.

- FILE /etc/dhcp3/dhclient-script
Edit (from a terminal: $ sudo gedit /etc/dhcp3/dhclient-script) this file commenting out all the rows of the whole make_resolv_conf() function:

#make_resolv_conf() {
# if [ -n "$new_domain_name" -o -n "$new_domain_name_servers" ]; then
# local new_resolv_conf=/etc/resolv.conf.dhclient-new
# rm -f $new_resolv_conf
#
# ...
# ...
# ...
#
#}

- CHECK
Finally restart all to check if it works (it sould work!!!).

---

### Post by Anthraxx on 2006-08-11
I gave this a try but couldn't get it to work. I couldn't restart it though, as I'm on Live CD. Is it totaly necessary to restart, or just "recommended"?

---

