---
title: "No adsl connection"
date: 2008-07-31
forum: Networking &amp; Wireless
---

### Post by westidan on 2008-07-31
Hi I can't seem to get the internet working with 7.10 or 8.04. I have a D-Link g604t adsl router with a atheros ethernet card as a dhcp server to a PC. However when I try to configure ubuntu with dhcp it doesn't seem to work, although Fedora does.

My ifconfig from ubuntu is:
eth0 Link encap:Ethernet HWaddr 00:1e:8c:cf:ae:f0
     UP BROADCAST MULTICAST MTU:1500 metric:1
     RX packets:0 errors:0 dropped:0 overruns:0 frames:0
     TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
     collisions:0 txqueuelen:1000
     RX bytes:0 (0.0 b) TX bytes:0 (0.0 b)
     Memory:dffc0000-e0000000 

eth0:avh Link encap:Ethernet HWaddr 00:1e:8c:cf:ae:f0
         inet addr:19.254.11.12 Bcast:169.254.255.255 mask:255.255.0.0
         UP BROADCAST MULTICAST MTU:1500 metric:1
         Memory:dffc0000-e0000000

lo   Link encap:Local loopback
     inet addr:127.0.0.1 mask:255.0.0.0
     UP LOOPBACK RUNNING MTU:16436 metric:1
     RX packets:81 errors:0
     TX packets:81 errors:0
     collisions:0 txqueuelen:0
     RX bytes:6236 (6.0 kb) Tx bytes:6236 (6.0 kb)

However my ifconfig from Fedora is:  
eth0 Link encap:Ethernet HWaddr 00:1e:8c:cf:ae:f0
     inet addr:10.1.1.3 Bcast 10.255.255.255 Mask:255.0.0.0
     inet6 addr:fe80:21e:8cff:fecf:aef0/64 Scope:Link  
     UP BROADCAST MULTICAST MTU:1500 metric:1
     RX packets:2615 errors:0 dropped:0 overruns:0 frames:0
     TX packets:2758 errors:0 dropped:0 overruns:0 carrier:0
     collisions:0 txqueuelen:1000
     RX bytes:2363028 (2.2 Mib) TX bytes:0 (0.0 b)
     Memory:dffc0000-e0000000 

lo   Link encap:Local loopback
     inet addr:127.0.0.1 mask:255.0.0.0
     inet6 addr: ::1/128 Scope:Host
     UP LOOPBACK RUNNING MTU:16436 metric:1
     RX packets:9139 errors:0
     TX packets:9139 errors:0
     collisions:0 txqueuelen:0
     RX bytes:75380688 (71.8 Mib) Tx bytes:75380688 (71.8 Mib)

When I try to ping with ubuntu I get destination host unreachable and when I try to do dhclient I get no dchpservers found. Also the light for the lan
cable that connects to adsl router does not appear, whereas with Fedora it does, another hint maybe that for Fedora I have to disable ipv6 in mozilla 
to surf the net.
Any help would be much appreciated, thanks!

---

### Post by superprash2003 on 2008-07-31
try this.. go to system->admin->network and go to eth0(wired connection) properties and set it to DHCP mode instead of Roaming mode

---

### Post by westidan on 2008-07-31
It is set dhcp.

---

### Post by superprash2003 on 2008-07-31
then try static ip and see if it works..(instead of DHCP)

---

### Post by westidan on 2008-08-01
I have tried this too with no success. I've tried quite a few things but to me it seems to be avahi that's the problem however I do not know how to disable this, I might try googling to try and find out, but thought somebody on this forum might know. Cheers.

---

### Post by superprash2003 on 2008-08-01
post an output of lshw -C network

---

### Post by westidan on 2008-08-02
Um nevermind got it working found on another forum for Gentoo that with windows xp dual boot windows tells the lan to go to sleep on shutdown so going into windows start->settings->control panel->system->hardware->device manager and right clicking on the ethernet connection then under the advanced tab turning shutdown wake up to on got the connection working for Ubuntu. 

I have both Xp,Ubuntu & Fedora on the same machine. Seems that Fedora is able to wake up the connection automatically whereas Ubuntu can't.

Thought I'd post the solution on this thread just in case anybody else has the same problems maybe they'll stumble upon this thread.

---

