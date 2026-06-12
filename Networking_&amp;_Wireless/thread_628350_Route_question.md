---
title: "Route question"
date: 2007-12-01
forum: Networking &amp; Wireless
---

### Post by hazam on 2007-12-01
Hi to everyone, this is my first post.

I got my desktop installed but now I want to install ubuntu on my laptop also and it doesn't have cd-rom drive.
Ok here is what I have done and what I have.

I have workin pxe setup I can boot ubuntu network install, but it wont find internet servers.
So I guess my routing is wrong, I haven't touched it. Should I?

I have adsl router that has IP 192.168.1.1(so thats my route to wild internet)
My desktop ip is 192.168.1.7(got it from adsl router dhcp) and network card is eth0
then I have second network card eth1 and I have set it manually 192.168.2.1 mask 255.255.255.0 gw 192.168.2.1

Also I made dhcp server for eth1 this is the config
 allow booting;
 allow bootp;
 option domain-name "ubuntu";
 option domain-name-servers 192.168.1.1;
 option routers 192.168.1.1,192.168.2.1;
 ddns-update-style interim;
 ignore client-updates;
 default-lease-time 14400;
 subnet 192.168.2.0 netmask 255.255.255.0 {
   option subnet-mask 255.255.255.0;
   range 192.168.2.0 192.168.2.200;
   default-lease-time 21600;
   max-lease-time 43200;
 }
 host kt {
     filename "pxelinux.0";
     hardware ethernet xx:xx:xx:xx:xx:xx;
 }

So please help me how to get my laptop to see internet. I dont want to setup ubuntu mirror on my desktop.

Thanks masa

---

### Post by mellowd on 2007-12-01
> **hazam said:**
> Hi to everyone, this is my first post.

I got my desktop installed but now I want to install ubuntu on my laptop also and it doesn't have cd-rom drive.
Ok here is what I have done and what I have.

I have workin pxe setup I can boot ubuntu network install, but it wont find internet servers.
So I guess my routing is wrong, I haven't touched it. Should I?

I have adsl router that has IP 192.168.1.1(so thats my route to wild internet)
My desktop ip is 192.168.1.7(got it from adsl router dhcp) and network card is eth0
then I have second network card eth1 and I have set it manually 192.168.2.1 mask 255.255.255.0 gw 192.168.2.1

Also I made dhcp server for eth1 this is the config
 allow booting;
 allow bootp;
 option domain-name "ubuntu";
 option domain-name-servers 192.168.1.1;
 option routers 192.168.1.1,192.168.2.1;
 ddns-update-style interim;
 ignore client-updates;
 default-lease-time 14400;
 subnet 192.168.2.0 netmask 255.255.255.0 {
   option subnet-mask 255.255.255.0;
   range 192.168.2.0 192.168.2.200;
   default-lease-time 21600;
   max-lease-time 43200;
 }
 host kt {
     filename "pxelinux.0";
     hardware ethernet xx:xx:xx:xx:xx:xx;
 }

So please help me how to get my laptop to see internet. I dont want to setup ubuntu mirror on my desktop.

Thanks masa


You haven't mentioned, but are you connecting your laptop to the desktop to route to the internet?  Why don't you connect your laptop directly just for the install?

---

