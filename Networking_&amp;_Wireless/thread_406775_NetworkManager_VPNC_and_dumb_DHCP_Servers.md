---
title: "NetworkManager VPNC and dumb DHCP Servers"
date: 2007-04-11
forum: Networking &amp; Wireless
---

### Post by jlward4th on 2007-04-11
Some wireless networks have a very low DHCP lease time, so if I am on one of these wireless networks and I connect to a VPN, when the lease ends, my VPN dies.  This is really annoying.  Seems like NetworkManager should disable this when I connect to a VPN.  Any thoughts / ideas?

Thanks.

-James

---

### Post by dbott67 on 2007-04-11
This does not seem right, as DHCP leases are (normally) renewed on the half-life.  Most leases are set around 8 days, so at the 4 day period the system would still detect that the lease is active & renew it again.

Even if the lease time were set artificially low, say 1 day, at the 12 hour period the lease should be renewed if the connection was still active.

After connecting, can you print the output of the following command (replace eth0 with your wireless interface):
```
dbott@feisty:~$ cat /var/lib/dhcp3/dhclient.[COLOR=Red]**eth0**[/COLOR].leases
lease {
  interface "eth0";
  fixed-address 192.168.1.106;
  option subnet-mask 255.255.255.0;
  option dhcp-lease-time 604800;
  option routers 192.168.1.1;
  option dhcp-message-type 5;
  option domain-name-servers 192.168.1.1;
  option dhcp-server-identifier 192.168.1.1;
  renew 5 2007/4/13 05:00:18;
  rebind 0 2007/4/15 21:04:28;
  expire 1 2007/4/16 18:04:28;
}
lease {
  interface "eth0";
  fixed-address 192.168.1.106;
  option subnet-mask 255.255.255.0;
  option routers 192.168.1.1;
  option dhcp-lease-time 604800;
  option dhcp-message-type 5;
  option dhcp-server-identifier 192.168.1.1;
  option domain-name-servers 192.168.1.1;
  renew 4 2007/4/12 14:09:25;
  rebind 0 2007/4/15 21:04:51;
  expire 1 2007/4/16 18:04:51;
}


```There are some options in the dhclient.conf file that appear to be customizable regarding the lease time at the bottom of the file:
```
dbott@feisty:/etc/dhcp3$ cat dhclient.conf
# Configuration file for /sbin/dhclient, which is included in Debian's
#       dhcp3-client package.
#
# This is a sample configuration file for dhclient. See dhclient.conf's
#       man page for more information about the syntax of this file
#       and a more comprehensive list of the parameters understood by
#       dhclient.
#
# Normally, if the DHCP server provides reasonable information and does
#       not leave anything out (like the domain name, for example), then
#       few changes must be made to this file, if any.
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
#  interface "eth0";
#  fixed-address 192.5.5.213;
#  option subnet-mask 255.255.255.255;
#}

[COLOR=Red]#lease {[/COLOR]
#  interface "eth0";
#  fixed-address 192.33.137.200;
#  medium "link0 link1";
#  option host-name "andare.swiftmedia.com";
#  option subnet-mask 255.255.255.0;
#  option broadcast-address 192.33.137.255;
#  option routers 192.33.137.250;
#  option domain-name-servers 127.0.0.1;
[COLOR=Red]#  renew 2 2000/1/12 00:00:01;
#  rebind 2 2000/1/12 00:00:01;
#  expire 2 2000/1/12 00:00:01;
#}[/COLOR]

```Check the man pages for **dhclient**; perhaps there's something that may help in there.

-Dave

---

### Post by jlward4th on 2007-04-11
Thanks Dave for the quick response!  Many wireless networks are beginning to use 30 minute DHCP lease times.  It's totally dumb.  I'm not sure why they are doing it.  Wayport is the one I'm currently on, but there have been others as well.  I will try what you suggest and see what happens.  But it would be great if this was built into NetworkManager or vpnc; If I'm connected to a VPN, do not timeout my DHCP license.  Anyways, thanks again.

-James

---

