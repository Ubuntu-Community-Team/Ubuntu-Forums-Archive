---
title: "Home Networking win7 and 12.04LTS"
date: 2013-12-03
forum: Networking &amp; Wireless
---

### Post by dieseler01 on 2013-12-03
I've got three computers I'm having a hardtime getting to network correctly and could really use some help.  I've searched quite a bit and had some success... until I installed the latest updates!

The network would consist of the following

1) Win7 Desktop with a local printer (Brother MFC-5890CN)
2) Laptop running Ubuntu 12.04
3) Desktop running Ubuntu 12.04

I want to be able to share files and printer between computers.  When I was strictly windows I had this working without a hitch, but I'm having some problems now with Linux in the mix.

As of yesterday, the Win7 machine could see both of the Ubuntu computers and access their shares.  The Ubuntu Desktop could see and access the Win7 shares, but not the laptops.  The laptop couldn't see or access anything.  However, after installing the latest updates, nothing can see or access anything else. 

Any help would be appreciated!

---

### Post by Iowan on 2013-12-03
Does **ping** work?

---

### Post by dieseler01 on 2013-12-04
No, pinging does not appear to work.  When I ping the other computers by  name it simple says "PING computername (ip) 56(84) bytes of data" and  hangs there

---

### Post by The Cog on 2013-12-04
Back to basics then - first let's check the ethernet. Can you run the command **ifconfig** on the 'buntu boxes and pst the output here. I'm looking to check the IP addresses, and that the ethernet interface has the word RUNNING. Also use the command **ipconfig** on the windows box to make sure they agree about the network IP address range.

---

### Post by dieseler01 on 2013-12-04
Basics in simpleton for sure!  It took me about a week to get everything working before... and I really don't remember everything I had to do!

**Win7:**
IPv6 fe80:6568:b50:a161:13fx11
IPv4 10.0.4.5
subnet mask 255.255.255.0
default gateway 10.0.1.1

**Ubuntu Desktop:**
eth0      Link encap:Ethernet  HWaddr 4c:72:b9:62:d8:a1  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:17 

eth1      Link encap:Ethernet  HWaddr 20:68:9d:f0:b9:ab  
          inet addr:10.0.1.14  Bcast:10.0.1.255  Mask:255.255.255.0
          inet6 addr: fe80::2268:9dff:fef0:b9ab/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:11848 errors:0 dropped:0 overruns:0 frame:1085562
          TX packets:9379 errors:35 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:11386096 (11.3 MB)  TX bytes:1459696 (1.4 MB)
          Interrupt:16 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:1564 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1564 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:187432 (187.4 KB)  TX bytes:187432 (187.4 KB)

**Laptop:**
eth0      Link encap:Ethernet  HWaddr 00:1e:33:9a:a0:67  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:2341 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2341 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:229693 (229.6 KB)  TX bytes:229693 (229.6 KB)

wlan0     Link encap:Ethernet  HWaddr 00:22:fa:32:97:b8  
          inet addr:10.0.1.13  Bcast:10.0.1.255  Mask:255.255.255.0
          inet6 addr: fe80::222:faff:fe32:97b8/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:503727 errors:0 dropped:0 overruns:0 frame:0
          TX packets:232146 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:723684435 (723.6 MB)  TX bytes:22903250 (22.9 MB)

---

### Post by oldos2er on 2013-12-05
Moved to Networking & Wireless.

---

### Post by bab1 on 2013-12-05
> **dieseler01 said:**
> Basics in simpleton for sure!  It took me about a week to get everything working before... and I really don't remember everything I had to do!

**Win7:**
```
IPv6 fe80:6568:b50:a161:13fx11
[COLOR="#FF0000"]IPv4 10.0.4.5
subnet mask 255.255.255.0[/COLOR]
[COLOR="#0000FF"]default gateway 10.0.1.1[/COLOR]
```

**Ubuntu Desktop:**
```
eth0      Link encap:Ethernet  HWaddr 4c:72:b9:62:d8:a1  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:17

eth1      Link encap:Ethernet  HWaddr 20:68:9d:f0:b9:ab  
[COLOR="#0000FF"]          inet addr:10.0.1.14  Bcast:10.0.1.255  Mask:255.255.255.0[/COLOR]
          inet6 addr: fe80::2268:9dff:fef0:b9ab/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:11848 errors:0 dropped:0 overruns:0 frame:1085562
          TX packets:9379 errors:35 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:11386096 (11.3 MB)  TX bytes:1459696 (1.4 MB)
          Interrupt:16 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:1564 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1564 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:187432 (187.4 KB)  TX bytes:187432 (187.4 KB)
 
```
**Laptop:**
```
eth0      Link encap:Ethernet  HWaddr 00:1e:33:9a:a0:67  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:2341 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2341 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:229693 (229.6 KB)  TX bytes:229693 (229.6 KB)

wlan0     Link encap:Ethernet  HWaddr 00:22:fa:32:97:b8  
 [COLOR="#0000FF"]         inet addr:10.0.1.13  Bcast:10.0.1.255  Mask:255.255.255.0[/COLOR]
          inet6 addr: fe80::222:faff:fe32:97b8/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:503727 errors:0 dropped:0 overruns:0 frame:0
          TX packets:232146 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:723684435 (723.6 MB)  TX bytes:22903250 (22.9 MB)
```

The Windows machine is on a different network (see red above) than the others (see Blue above).  How did you configure the Windows IP addresse?  Note that the gateway (see green above) is in the same network as the Laptop and Ubuntu Desktop (10.0.1.0 /24 (the blue network))

---

### Post by dieseler01 on 2013-12-06
Humm... I was under the impression that having everything set to DHCP caused the router to handle IP addresses.  So, I never did set any configuration.  What's the correct way to set them all?

---

### Post by Iowan on 2013-12-06
It should. Curious that the IP address and gateway are in different subnets - is the Win7 machine set for DHCP (is there an override on the gateway?)
Also curious that "The laptop couldn't see or access anything",

---

### Post by bab1 on 2013-12-06
> **dieseler01 said:**
> Humm... I was under the impression that having everything set to DHCP caused the router to handle IP addresses.  So, I never did set any configuration.  What's the correct way to set them all?

Having everything set to DHCP is one way of setting up a client to configure it's IP address and gateway.  The DHCP server does not need to be on the router.  I would release  the DHCP lease and then renew it on the Win7 machine.   Then recheck the supplied IP address and gateway.

---

### Post by dieseler01 on 2013-12-11
So, rebooted all three machines and didn't touch any other settings.

Laptop can now see and access both other computers

Ubuntu desktop can see both computers, but can only access the Win7 box.  It gets an "unable to mount location" failure when access the laptop

The Win7 Box cannot not see either of the Ubuntu boxes now and I haven't changed any settings.

Any more thoughts on my revolving problem?

---

### Post by bab1 on 2013-12-11
> **dieseler01 said:**
> So, rebooted all three machines and didn't touch any other settings.

Laptop can now see and access both other computers

Ubuntu desktop can see both computers, but can only access the Win7 box.  It gets an "unable to mount location" failure when access the laptop

The Win7 Box cannot not see either of the Ubuntu boxes now and I haven't changed any settings.

Any more thoughts on my revolving problem?
Repost the settings as they are now.

Edit: On second thought, do this first ```
sudo dhclient -r; sudo dhclient
```...and then post the settings.

See [_here_]("http://askubuntu.com/questions/4014/how-do-i-renew-my-dhcp-lease") for what I'm talking about

---

