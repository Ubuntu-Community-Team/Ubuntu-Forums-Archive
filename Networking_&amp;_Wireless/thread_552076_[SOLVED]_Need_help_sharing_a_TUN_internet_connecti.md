---
title: "[SOLVED] Need help sharing a TUN internet connection through a WiFi router"
date: 2007-09-16
forum: Networking &amp; Wireless
---

### Post by spacecoyote on 2007-09-16
Okay, so this *is* a odd situation...but I live in an odd place with no access to DSL and whatnot so the only thing I can do is try to solve it in software. So please, please please don't tell me that my internet connection sucks and that I should get something else! I cannot do that, because I'm not the one paying for the connection (personally I probably can't afford it), and I live in the middle of nowhere so there would be limited options anyway.

I have tried various things and nothing in Linux has worked. WinGate for Windows did the job but my trial expired, so I know this isn't impossible, just difficult and requiring knowledge in the darker arts of networking.

So heres the big picture. I have an AOL (yuck) connection through an external modem using Penggy (the linux AOL dialer), which sets up the connection as a TUN interface (particularly the interface is called tun0). I would like to share this internet connection (which is slow but stable) with the other PCs (and the laptops) in my network. 

I have a WiFi enabled router which has a special port labeled WAN which might be useful. I think it tries to log itself into that connection through DHCP and then NAT it to the rest of the network, so that it can set up the other machines using its own DHCP server (and therefore mirroring the DNS with its own DNS server). 

Either way, when computers connect to that router, they are given an ip address in the form of 192.168.1.X subnet 255.255.255.0 with the gateway and DNS server set as 192.168.1.254 which is the router's IP address.

Thanks for any help anyone can give especially as like I said this situation is very weird.

I probably need to set up a:

NAT/Firewall
DHCP server
DNS server

but I'm a noob at those things.

---

### Post by spacecoyote on 2007-09-16
I think I've got it working somewhat now. I've surprised myself actually. 

The problem now is it isn't automatic. So far it only works after firestarter is starter (in other words not on bootup).

Anyway heres the basic config. I'll post a full tutorial when I have everything working perfectly.

Install firestarter
install dhcp
sudo ln -s /etc/init.d/dhcp /etc/init.d/dhcpd

on firestarter:

internet device: tun0
network: eth0 in my case
enable internet connection sharing
enable DHCP for local network:
lowest ip to assign:   192.168.0.1
highest ip to assign: 192.168.0.254
name server: dynamic

the NIC (eth0 in my case) should be configured to be 192.168.0.1:
ifconfig eth0 192.168.0.1

and it really didn't work until I modified the /etc/dhcpd.conf:
subnet 192.168.0.0 netmask 255.255.255.0 {
        option routers 192.168.0.1;
        option subnet-mask 255.255.255.0;
        option domain-name-servers 205.188.146.145;
        option ip-forwarding off;
        range dynamic-bootp 192.168.0.1 192.168.0.254;
        default-lease-time 21600;
        max-lease-time 43200;
}

Anyway I've just made some changes, I'll post back if I got it to be automatic.

---

### Post by spacecoyote on 2007-09-16
Ok, I got it to be automatic.

All you have to do is add the following to /etc/penggy/ip-up:
/etc/init.d/firestarter restart

I think I'll post a good tutorial tomorrow, with tips on how to improve your gateway's bootup time , and also how to find your access numbers and etc.

I'll see if I can get a DNS cache and package cache running. :)

---

