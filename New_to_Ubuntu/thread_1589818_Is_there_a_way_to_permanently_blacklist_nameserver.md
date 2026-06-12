---
title: "Is there a way to permanently blacklist nameservers in resolv.conf?"
date: 2010-10-07
forum: New to Ubuntu
---

### Post by venom104 on 2010-10-07
Whenever I login to my system my computer is extremely slow at loading pages. Whenever I blacklist my router in /etc/resolv.conf (using a #) my computer seems to load pages faster. However, this file is overwritten every time I log into my system (I'm guessing networkmanager automatically generates this file). Is there a way of permanently blacklisting my routers nameserver in resolv.conf?

---

### Post by kreggz on 2010-10-07
Make a change on your DHCP server to only provide name servers you want.

---

### Post by jtarin on 2010-10-07
/etc/dhcp3/dhclient.conf 
  ```
 1.

      Backup your resolv.conf

      sudo cp /etc/resolv.conf /etc/resolv.conf.auto
   2.

      Edit /etc/dhcp3/dhclient.conf:

      sudo gedit /etc/dhcp3/dhclient.conf
   3.

      If there are any nameservers, you may want to write them down for future reference.
   4.

      Replace the reference line, or add...

      **prepend domain-name-servers 1.2.3.4,4.3.2.1;**
   
   

   5.

      Save and exit!
   6.

      Restart any internet clients, services
   7.

      And test your new settings.
```Line 4 use your own nameservers and watch the commas and semi-colon as my example

---

### Post by venom104 on 2010-10-10
there is no reference like, moreover everything is totally commented out. Here is what is in that file ```
# Configuration file for /sbin/dhclient, which is included in Debian's
#    dhcp3-client package.
#
# This is a sample configuration file for dhclient. See dhclient.conf's
#    man page for more information about the syntax of this file
#    and a more comprehensive list of the parameters understood by
#    dhclient.
#
# Normally, if the DHCP server provides reasonable information and does
#    not leave anything out (like the domain name, for example), then
#    few changes must be made to this file, if any.
#

option rfc3442-classless-static-routes code 121 = array of unsigned integer 8;

send host-name "<hostname>";
#send dhcp-client-identifier 1:0:a0:24:ab:fb:9c;
#send dhcp-lease-time 3600;
#supersede domain-name "fugue.com home.vix.com";
#prepend domain-name-servers 127.0.0.1;
request subnet-mask, broadcast-address, time-offset, routers,
    domain-name, domain-name-servers, domain-search, host-name,
    netbios-name-servers, netbios-scope, interface-mtu,
    rfc3442-classless-static-routes, ntp-servers;
#require subnet-mask, domain-name-servers;
#timeout 60;
#retry 60;
#reboot 10;
#select-timeout 5;
#initial-interval 2;
#script "/etc/dhcp3/dhclient-script";
#media "-link0 -link1 -link2", "link0 link1";
#reject 192.33.137.209;

#alias {
#  interface "eth0";
#  fixed-address 192.5.5.213;
#  option subnet-mask 255.255.255.255;
#}

#lease {
#  interface "eth0";
#  fixed-address 192.33.137.200;
#  medium "link0 link1";
#  option host-name "andare.swiftmedia.com";
#  option subnet-mask 255.255.255.0;
#  option broadcast-address 192.33.137.255;
#  option routers 192.33.137.250;
#  option domain-name-servers 127.0.0.1;
#  renew 2 2000/1/12 00:00:01;
#  rebind 2 2000/1/12 00:00:01;
#  expire 2 2000/1/12 00:00:01;
#}
```
> **jtarin said:**
> /etc/dhcp3/dhclient.conf 
  ```
 1.

      Backup your resolv.conf

      sudo cp /etc/resolv.conf /etc/resolv.conf.auto
   2.

      Edit /etc/dhcp3/dhclient.conf:

      sudo gedit /etc/dhcp3/dhclient.conf
   3.

      If there are any nameservers, you may want to write them down for future reference.
   4.

      Replace the reference line, or add...

      **prepend domain-name-servers 1.2.3.4,4.3.2.1;**
   
   

   5.

      Save and exit!
   6.

      Restart any internet clients, services
   7.

      And test your new settings.
```Line 4 use your own nameservers and watch the commas and semi-colon as my example

---

### Post by venom104 on 2010-10-10
I forgot to say that this did not work.

> **venom104 said:**
> there is no reference like, moreover everything is totally commented out. Here is what is in that file ```
# Configuration file for /sbin/dhclient, which is included in Debian's
#    dhcp3-client package.
#
# This is a sample configuration file for dhclient. See dhclient.conf's
#    man page for more information about the syntax of this file
#    and a more comprehensive list of the parameters understood by
#    dhclient.
#
# Normally, if the DHCP server provides reasonable information and does
#    not leave anything out (like the domain name, for example), then
#    few changes must be made to this file, if any.
#

option rfc3442-classless-static-routes code 121 = array of unsigned integer 8;

send host-name "<hostname>";
#send dhcp-client-identifier 1:0:a0:24:ab:fb:9c;
#send dhcp-lease-time 3600;
#supersede domain-name "fugue.com home.vix.com";
#prepend domain-name-servers 127.0.0.1;
request subnet-mask, broadcast-address, time-offset, routers,
    domain-name, domain-name-servers, domain-search, host-name,
    netbios-name-servers, netbios-scope, interface-mtu,
    rfc3442-classless-static-routes, ntp-servers;
#require subnet-mask, domain-name-servers;
#timeout 60;
#retry 60;
#reboot 10;
#select-timeout 5;
#initial-interval 2;
#script "/etc/dhcp3/dhclient-script";
#media "-link0 -link1 -link2", "link0 link1";
#reject 192.33.137.209;

#alias {
#  interface "eth0";
#  fixed-address 192.5.5.213;
#  option subnet-mask 255.255.255.255;
#}

#lease {
#  interface "eth0";
#  fixed-address 192.33.137.200;
#  medium "link0 link1";
#  option host-name "andare.swiftmedia.com";
#  option subnet-mask 255.255.255.0;
#  option broadcast-address 192.33.137.255;
#  option routers 192.33.137.250;
#  option domain-name-servers 127.0.0.1;
#  renew 2 2000/1/12 00:00:01;
#  rebind 2 2000/1/12 00:00:01;
#  expire 2 2000/1/12 00:00:01;
#}
```

---

### Post by venom104 on 2010-10-10
> **venom104 said:**
> Whenever I login to my system my computer is extremely slow at loading pages. Whenever I blacklist my router in /etc/resolv.conf (using a #) my computer seems to load pages faster. However, this file is overwritten every time I log into my system (I'm guessing networkmanager automatically generates this file). Is there a way of permanently blacklisting my routers nameserver in resolv.conf?


I found a fix. I edited the connection in the network manager applet and set the ipv4 mode setting to DHCP addresses only and specified my DNS servers.

---

### Post by jtarin on 2010-10-10
The line is clearly there.In your file I have changed it to use google servers.What could be easier, I ask. :)```
send host-name "<hostname>";
#send dhcp-client-identifier 1:0:a0:24:ab:fb:9c;
#send dhcp-lease-time 3600;
#supersede domain-name "fugue.com home.vix.com";
[COLOR="Red"]prepend domain-name-servers 8.8.8.8,8.8.4.4;[/COLOR]
request subnet-mask, broadcast-address, time-offset, routers,
    domain-name, domain-name-servers, domain-search, host-name,
    netbios-name-servers, netbios-scope, interface-mtu,
    rfc3442-classless-static-routes, ntp-servers;
```

---

