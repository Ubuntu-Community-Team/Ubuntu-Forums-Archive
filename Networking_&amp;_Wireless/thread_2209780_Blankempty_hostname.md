---
title: "Blank/empty hostname"
date: 2014-03-07
forum: Networking &amp; Wireless
---

### Post by Wesdec on 2014-03-07
Hi. I am using Ubuntu 12.10 and i was wondering if there is way to not  send my hostname when connecting to a router? For example when I connect  to my router I can see my laptop hostname when I log on the router,  under "DHCP Leases". 

  I dont want to change my hostname, I would just like to not send  anything so that under "Hostname" in my router my laptop mac address  appears with no name. Is that possible? I have noticed sometimes that  blank hostnames do appear for some connected devices.

I have tried to edit /etc/dhcp/dhclient.conf and commenting the following line out:  

send host-name = gethostname();

but i can still see my hostname.

---

### Post by Lars Noodén on 2014-03-07
My guess would be to modify /etc/dhcp/[dhclient.conf](http://manpages.ubuntu.com/manpages/saucy/en/man5/dhclient.conf.5.html) to send a blank hostname.

```

send host-name "";

```

Maybe that works, maybe not.

---

### Post by steeldriver on 2014-03-07
Commenting out the line appeared to be sufficient when I tried it on 12.04 - you may need to reboot the computer (and possibly even the router) for the change to propagate through

---

### Post by Wesdec on 2014-03-07
I have tried the following, none of which work:

send host-name "";
send host-name = "";
send host-name = ;
#send host-name = "";

I have also tried to reboot and change my mac address before connecting, but the hostname still appears under the new mac.

---

### Post by Wesdec on 2014-03-07
This is my dhclient.conf:

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

#send host-name "andare.fugue.com";
#send host-name = ;#gethostname();
#send dhcp-client-identifier 1:0:a0:24:ab:fb:9c;
#send dhcp-lease-time 3600;
#supersede domain-name "fugue.com home.vix.com";
#prepend domain-name-servers 127.0.0.1;
request subnet-mask, broadcast-address, time-offset, routers,
    domain-name, domain-name-servers, domain-search, host-name,
    netbios-name-servers, netbios-scope, interface-mtu,
    rfc3442-classless-static-routes, ntp-servers,
    dhcp6.domain-search, dhcp6.fqdn,
    dhcp6.name-servers, dhcp6.sntp-servers;
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

---

