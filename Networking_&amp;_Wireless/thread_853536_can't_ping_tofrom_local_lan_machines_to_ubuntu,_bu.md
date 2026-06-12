---
title: "can't ping to/from local lan machines to ubuntu, but internet works fine from all"
date: 2008-07-08
forum: Networking &amp; Wireless
---

### Post by happyoldguy on 2008-07-08
ok, this is really getting to me now....

I have 3 machines connected to my wireless router, all with ip addresses assigned by DHCP in the 192.168.1.x subnet, mask 255.255.255.0

nothing interesting yet right?

Machine 1 is an EeePC 192.168.1.101
Machine 2 is a Mac (OS X 10.4.x?) 192.168.1.102
Machine 3 is my Ubuntu Hardy 8.04 box 192.168.103

router is a Linksys WRT160N 192.168.1.1
network device in the Ubuntu box is a Netgear USB wn121T 

My EeePC and mac can ping each other (and surf the internet)
My Ubuntu box can't be pinged by either, but can also see the internet
running traceroute from the Ubuntu box to the Mac does return, but on ly after 2000-3000ms (which is wrong surely)

output of ifconfig is
lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:1075 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1075 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:1159735 (1.1 MB)  TX bytes:1159735 (1.1 MB)

vmnet1    Link encap:Ethernet  HWaddr "MY Virtual MAC ADDRESS"  
          inet addr:192.168.116.1  Bcast:192.168.116.255  Mask:255.255.255.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:78 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

vmnet8    Link encap:Ethernet  HWaddr "MY Virtual MAC ADDRESS" 
          inet addr:192.168.84.1  Bcast:192.168.84.255  Mask:255.255.255.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:78 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

wlan1     Link encap:Ethernet  HWaddr "MY MAC ADDRESS"  
          inet addr:192.168.1.103  Bcast:192.168.1.255  Mask:255.255.255.0
          UP BROADCAST RUNNING ALLMULTI MULTICAST  MTU:1500  Metric:1
          RX packets:17800 errors:0 dropped:0 overruns:0 frame:0
          TX packets:14395 errors:0 dropped:1 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:21810549 (20.8 MB)  TX bytes:1810149 (1.7 MB)


output of netstat -r is
Kernel IP routing table
Destination     Gateway         Genmask         Flags   MSS Window  irtt Iface
192.168.116.0   *               255.255.255.0   U         0 0          0 vmnet1
192.168.84.0    *               255.255.255.0   U         0 0          0 vmnet8
192.168.1.0     *               255.255.255.0   U         0 0          0 wlan1
link-local      *               255.255.0.0     U         0 0          0 wlan1
default         192.168.1.1     0.0.0.0         UG        0 0          0 wlan1

output of arp -a is
? (192.168.1.1) at "MY routers MAC ADDRESS" [ether] on wlan1
? (192.168.1.102) at <incomplete> on wlan1

I can ping my router ping fine, but pinging the Mac gives

ping 192.168.1.102
PING 192.168.1.102 (192.168.1.102) 56(84) bytes of data.
From 192.168.1.103 icmp_seq=1 Destination Host Unreachable
From 192.168.1.103 icmp_seq=2 Destination Host Unreachable
From 192.168.1.103 icmp_seq=3 Destination Host Unreachable

--- 192.168.1.102 ping statistics ---
4 packets transmitted, 0 received, +3 errors, 100% packet loss, time 3008ms
, pipe 3

Clearly you wouldn't expect - Destination Host Unreachable for a machine on the local subnet, but as there is no MAC address in the ARP table I figure that may be my problem?

Any ideas anyone?

Thanks

---

### Post by superprash2003 on 2008-07-08
could there be some firewall etc blocking the ping..

---

### Post by happyoldguy on 2008-07-09
> **superprash2003 said:**
> could there be some firewall etc blocking the ping..

right I figured that may be an issue - but where to check - I don't think there is a firewall installed on the ubuntu box (at least I have not configured it)

I don't think it can be a firewall issue on either of the other machines as they appear to function ok.

---

### Post by happyoldguy on 2008-07-10
Here's the output of running iptable -L

Chain INPUT (policy ACCEPT)
target     prot opt source               destination         

Chain FORWARD (policy ACCEPT)
target     prot opt source               destination         

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination    

which I think says everything is accepted - so icmp should return something right?

firestarter is not installed

any other thing i should be looking for?

---

### Post by dstanley on 2008-09-29
This fixed it for me:

[http://www.eggheadcafe.com/software/aspnet/29583593/ubuntu-guest-cant-connec.aspx](http://www.eggheadcafe.com/software/aspnet/29583593/ubuntu-guest-cant-connec.aspx)

HTH
/Dave

---

### Post by ml_nelson on 2009-11-01
> **dstanley said:**
> This fixed it for me:
 
[http://www.eggheadcafe.com/software/aspnet/29583593/ubuntu-guest-cant-connec.aspx](http://www.eggheadcafe.com/software/aspnet/29583593/ubuntu-guest-cant-connec.aspx)
 
HTH
/DaveI have a similar problem... The Ubuntu box can ping any of my Windows machines just fine.
 
Problem is the other way around... The Windows boxes can't ping the Ubuntu by name. They can ping it by IP.
 
I see above that someone had the very similar problem. Do I dare follow that lead?
 
Thoughts?
Mike

---

### Post by ml_nelson on 2009-11-01
> **ml_nelson said:**
> I have a similar problem... The Ubuntu box can ping any of my Windows machines just fine.
 
Problem is the other way around... The Windows boxes can't ping the Ubuntu by name. They can ping it by IP.
 
 
Thoughts?
Mike I changed the name of the Ubuntu box to something short.   It was previously mre than 15 characters.  It now appears to work

---

### Post by ml_nelson on 2009-11-02
> **ml_nelson said:**
> I changed the name of the Ubuntu box to something short. It was previously mre than 15 characters. It now appears to work
 
I thought this was fixed as it was all working last night after I changed the name of the Ubuntu box to something short. I turned everything off for the night. Next day, problem is back. I can only ping the Ubuntu box by IP, not by name. In fact, I can even connect to & view files using the IP address, but not the name.
 
I tried changing the name again, just one letter & restart the Ubuntu box. Windows can then see & ping it by name.
 
If I turn the computers off for some hours, & restart... The problem returns!
 
How do I get Windows to reliably find the Ubuntu box by name?
 
Mike

---

### Post by Iowan on 2009-11-03
Turn it on and let it sit for awhile - sometimes Windows browse list takes awhile to update - though that doesn't explain why changing the name would  make it visible immediately.

---

