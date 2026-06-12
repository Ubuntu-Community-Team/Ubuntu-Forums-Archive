---
title: "Can't get to LAN name any more."
date: 2008-01-11
forum: Networking &amp; Wireless
---

### Post by Raymond Day on 2008-01-11
I hope some one knows what is wrong.

I had a netgear router doing DHCP but tunred it off about 3 days ago and let my Ubuntu server 7.04 Kernel Version 2.6.20-16-server (SMP) do DHCP between 192.168.2.3 and 192.168.2.100

I have some computers with a static IP out side the 192.168.2.100 addess. Like 192.168.2.109 is the Ubuntu server.

I named the Ubuntu server small. I could go to [http://small](http://small) and it all ways go there. But after about 3 days I got page can not be displayed! I can go to it's IP [http://192.168.2.109](http://192.168.2.109) but not's it's name any more.

I can't "View workgroup computers" any more too. It errors. I did not get this before using the Netgear router as a DHCP server.

I did this because the Netgear would not give my RIO music player a IP. But ubuntu server did.

Looked on google for help. But I guess I don't know the right wording.

This my help. Here is my dhcpd.conf file:

```
root@small:~# cat /etc/dhcp3/dhcpd.conf
authoritative;

subnet 192.168.2.0 netmask 255.255.255.0 {
range 192.168.2.3 192.168.2.100;
option domain-name-servers 192.168.2.1, 192.168.2.1;
option domain-name "rday";
option routers 192.168.2.1;
option static-routes 192.168.2.101 192.168.2.230;
option broadcast-address 192.168.2.255;
}

host HP-Photo-smart-2610-printer {
        hardware ethernet 00:0d:9d:12:52:43;
        fixed-address 192.168.2.2;
        }
host RIO {
        hardware ethernet 00:90:00:11:47:fc;
        fixed-address 192.168.2.125;
        }
host small {
        hardware ethernet 00:D0:09:5B:5E:A8;
        fixed-address 192.168.2.109;
        }
host HPMEDIAVAULT {
        hardware ethernet 00:18:F3:2B:50:53;
        fixed-address 192.168.2.105;
        }
root@small:~#
```

I hope some one knows how to fix this?

I only found the fix in putting the ip and name in the windows host file at C:\WINDOWS\system32\drivers\etc\hosts

But I don't want to do this on every LAN computer. I did not have to do it with the Netgear being a DHCP server.

-Raymond Day

---

### Post by Raymond Day on 2008-01-11
I just tested this on another windows PC and it can get to the name.

I don't know maybe in 3 days from now it will error too.

-Raymond Day

---

### Post by evanchu on 2008-01-11
I think this problem is a simple hostname lookup problem.  Your Netgear router was probably serving as DNS server; in addition to DHCP server.  Therefore, all your machines were able to resolve hostnames.

Go to each of your machine and ping a few other machines by hostname.  What get resolved and what does not?

---

