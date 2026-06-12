---
title: "VWware possibly killed my network"
date: 2008-03-03
forum: Networking &amp; Wireless
---

### Post by apokkalyps on 2008-03-03
Hi all, this is my first post on here!

I'm running 7.10, and recently installed the latest demo of VMware workstation.

Now, my ubuntu box won't hit the internet.  I'm not 100% sure its VMwares fault, but it happened right after that install, and vmware did add two virtual network devices (vmnet1, vmnet8) that show up when I do ifconfig.

My home network is two pcs behind a linksys NAT router/switch.  The strange thing is that right now both computers can get an IP address from the router (DHCP).  And they can BOTH ping the default gateway.   My windows pc can use the internet just fine (like now) but the ubuntu, other than being able to ping the default gateway, cannot ping anything else, neither google.com OR the other PC.  But they can both ping the gateway.  



heres my ifconfig:
[INDENT]eth0      Link encap:Ethernet  HWaddr 00:1E:90:66:A3:30  
          inet addr:192.168.1.102  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::21e:90ff:fe66:a330/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:52171 errors:0 dropped:0 overruns:0 frame:0
          TX packets:3551 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:2570944 (2.4 MB)  TX bytes:1116242 (1.0 MB)
          Interrupt:16 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:36011 errors:0 dropped:0 overruns:0 frame:0
          TX packets:36011 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:12156882 (11.5 MB)  TX bytes:12156882 (11.5 MB)

vmnet1    Link encap:Ethernet  HWaddr 00:50:56:C0:00:01  
          inet addr:192.168.1.1  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::250:56ff:fec0:1/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:172 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

vmnet8    Link encap:Ethernet  HWaddr 00:50:56:C0:00:08  
          inet addr:192.168.143.1  Bcast:192.168.143.255  Mask:255.255.255.0
          inet6 addr: fe80::250:56ff:fec0:8/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:7069 errors:0 dropped:0 overruns:0 frame:0
          TX packets:33 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

[/INDENT]

If anyone even has any guesses about how to try troubleshooting this, please let me know, im dead in the water. :???:
thx

---

### Post by unutbu on 2008-03-03
Try pinging google this way:
```

ping 72.14.207.99

```

If you can do this, but can't ping

```

ping google.com

```

then the problem is in your /etc/resolv.conf.
If you can't ping 72.14.207.99, then read on:

What is the ip address of the default gateway?

Please post
```

cat /etc/resolv.conf
cat /etc/hosts
route
```

Is your default gateway 192.168.1.1? If so, it appears vmnet1 has grabbed that address. If vmnet1 is not supposed to be the gateway, then that's your problem. If this is the problem, you'll want to reconfigure VMWare so vmnet1's address is something else. You might have to edit /etc/hosts.

You might also find something helpful by reading (Near the end there is a list of useful commands.)

[http://ubuntuforums.org/showthread.php?t=684495](http://ubuntuforums.org/showthread.php?t=684495)

---

### Post by apokkalyps on 2008-03-03
I think you're on the right track with the vmnet1.  The gateway *is* 192.168.1.1.  I shoulda noticed that ;p  I did some research and vmnet1 is the virtual switch for the NAT communication within the virtual network.  So the linux machine wasn't really pinging the gateway it was pinging the virtual gateway on VMware. which now that I read about it I dont even want.  I want bridged.  Heh, I just clicked next through it all out of laziness.

I'm currently looking into changing from NAT to Bridged mode in VMware.  Here's that code tho:

[INDENT]
ping 72.14.207.99:
connect: Network is unreachable


resolv.conf:
nameserver 66.169.221.10
nameserver 68.113.206.10


hosts:
127.0.0.1	localhost
127.0.1.1	barrett-desktop


route:
# The following lines are desirable for IPv6 capable hosts
::1     ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.1.0     *               255.255.255.0   U     0      0        0 vmnet1
192.168.1.0     *               255.255.255.0   U     0      0        0 eth0
192.168.143.0   *               255.255.255.0   U     0      0        0 vmnet8
[/INDENT]

---

### Post by apokkalyps on 2008-03-03
I'm now back up and running!
I couldn't figure out how to reconfigure vmnet1 or get rid of it, so I just changed my router to 192.168.1.10.  now it works fine... Thanks!

---

