---
title: "Possible to create multiple localhosts, or virtual LANs?"
date: 2008-02-28
forum: Networking &amp; Wireless
---

### Post by quinthar on 2008-02-28
Is it possible to, in effect, create multiple localhosts?

I have a few different servers (custom, non-Apache), all of which use HTTPS on port 443.  When deployed, they all have different IP addresses, so there's no conflict.  But when I run them all locally, I only have one localhost, so there's a conflict.  Is there any way to create multiple localhosts (127.0.0.1, 127.0.0.2, etc), or somehow create additional virtual LANs (eth2, eth3, etc) so I can assign each server a different IP address?

Ideally I'd have a few different local or virtual IP addresses -- each running a different server on port 443 -- and then I could update my /etc/hosts when testing as follows:

a.testdomain.com 127.0.0.1
b.testdomain.com 127.0.0.2
c.testdomain.com 127.0.0.3

When I'm done testing, I can deploy to my live servers and just comment out those lines from the /etc/hosts file.  Similarly, I could optionally have some of the servers running in the live environment and some locally, and all I'd have to do is update my /etc/hosts file.

Is there any way to do this?

(Note: I realize I could run them all on the same IP address using different ports, but then my test environment is significantly different than my deployment environment.  Furthermore, standard "https://" links in FireFox would fail to work unless I explicitly indicate the target port, which implies that the caller somehow much know a priori whether it's talking to the test or deployed server, etc, etc.  All in all, if I could just fabricate multiple local IP addresses, that'd be best.)

Thanks!

-david

---

### Post by quinthar on 2008-02-28
Turns out this is really easy: just make a virtual interface off of the loopback interface.  So obvious I didn't even think of it.  Nevermind!

dbarrett@LappyReborn:~$ sudo ifconfig lo:2 130.0.0.1 netmask 255.255.255.0
dbarrett@LappyReborn:~$ 
dbarrett@LappyReborn:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 08:00:46:E5:63:A1  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

eth1      Link encap:Ethernet  HWaddr 00:0E:35:3D:10:CB  
          inet addr:192.168.1.26  Bcast:255.255.255.255  Mask:255.255.255.0
          inet6 addr: fe80::20e:35ff:fe3d:10cb/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:8743 errors:0 dropped:0 overruns:0 frame:0
          TX packets:3747 errors:0 dropped:0 overruns:0 carrier:1
          collisions:0 txqueuelen:1000 
          RX bytes:9886435 (9.4 MB)  TX bytes:1672208 (1.5 MB)
          Interrupt:9 Memory:e0201000-e0201fff 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:5539 errors:0 dropped:0 overruns:0 frame:0
          TX packets:5539 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:1312386 (1.2 MB)  TX bytes:1312386 (1.2 MB)

lo:1      Link encap:Local Loopback  
          inet addr:129.0.0.1  Mask:255.255.255.0
          UP LOOPBACK RUNNING  MTU:16436  Metric:1

lo:2      Link encap:Local Loopback  
          inet addr:130.0.0.1  Mask:255.255.255.0
          UP LOOPBACK RUNNING  MTU:16436  Metric:1

---

### Post by quinthar on 2008-03-02
Following up on this, I've found it's a bit trickier than I initially expected.  The command above does successfully create the additional localhost interface.  But that interface seems to spontaneously disappear, such as when I connect to a different wifi network and so forth.  Thus, I'm marking this thread unsolved as my initial solution was incomplete.

So, my updated question is: how do I create additional localhost interfaces that appear at boot and don't spontaneously disappear?

Do I need to add something to /etc/network/interfaces?  I've read through the manpage for that file, but honestly, I can't quite figure it out. Any suggestions?

Thanks!

-david

---

### Post by DaRabman on 2008-04-29
I've found that simply editing /etc/rc.local invokes the commands on boot. I don't know whether this is the most appropriate option, but it works for me (I'm using ifconfig for establishing multiple IPs on my NIC).
Sam.

---

