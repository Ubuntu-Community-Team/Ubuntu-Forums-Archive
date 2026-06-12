---
title: "Too many DHCP requests"
date: 2008-01-22
forum: Networking &amp; Wireless
---

### Post by Rocket2DMn on 2008-01-22
I posted this under Hardware and Laptops a week or so ago, but was not able to fix the problem:

I use my laptop on my university's wireless network, but I never had this problem through windows.  I eventually get an email from our IT people telling me my card has been disabled because of too many DHCP requests.
> Network access for [MY MAC ADDRESS] has been disabled at 01/15/08 15:00:09: Disabled because [MY MAC ADDRESS] (your computer's Wired/Wireless card) sent
too many DHCP requests. Your computer attempted and failed to acquire an IP address more than 60 times in 3600 seconds.

This is not due to a weak signal/connection - I get an IP with a steady connection, but for some reason it is still sending DHCP requests.  Is there a way to adjust the DHCP request frequency to help me avoid this problem?
FYI, my wireless card is an Intel PRO/Wireless 2915ABG card with the ipw2200 driver.

Here is my /etc/dhcp3/dhclient.conf file:
> # Configuration file for /sbin/dhclient, which is included in Debian's
# dhcp3-client package.
#
# This is a sample configuration file for dhclient. See dhclient.conf's
# man page for more information about the syntax of this file
# and a more comprehensive list of the parameters understood by
# dhclient.
#
# Normally, if the DHCP server provides reasonable information and does
# not leave anything out (like the domain name, for example), then
# few changes must be made to this file, if any.
#

send host-name "<hostname>";
#send dhcp-client-identifier 1:0:a0:24:ab:fb:9c;
#send dhcp-lease-time 3600;
#supersede domain-name "fugue.com home.vix.com";
#prepend domain-name-servers 127.0.0.1;
request subnet-mask, broadcast-address, time-offset, routers,
domain-name, domain-name-servers, host-name,
netbios-name-servers, netbios-scope;
#require subnet-mask, domain-name-servers;
timeout 30;
#retry 60;
#reboot 10;
#select-timeout 5;
#initial-interval 2;
#script "/etc/dhcp3/dhclient-script";
#media "-link0 -link1 -link2", "link0 link1";
#reject 192.33.137.209;

#alias {
# interface "eth0";
# fixed-address 192.5.5.213;
# option subnet-mask 255.255.255.255;
#}

#lease {
# interface "eth0";
# fixed-address 192.33.137.200;
# medium "link0 link1";
# option host-name "andare.swiftmedia.com";
# option subnet-mask 255.255.255.0;
# option broadcast-address 192.33.137.255;
# option routers 192.33.137.250;
# option domain-name-servers 127.0.0.1;
# renew 2 2000/1/12 00:00:01;
# rebind 2 2000/1/12 00:00:01;
# expire 2 2000/1/12 00:00:01;
#}

---

### Post by HermanAB on 2008-01-23
$ sudo killall dhclient

---

### Post by Rocket2DMn on 2008-01-23
Lol, well I guess as a last ditch option I might have to resort to that.  In the meantime, I submitted a bug report on launchpad
[https://bugs.launchpad.net/ubuntu/+source/dhcp3/+bug/185248](https://bugs.launchpad.net/ubuntu/+source/dhcp3/+bug/185248)
Thanks for the input, I just might have to use that for awhile.

---

