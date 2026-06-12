---
title: "Network Help VMware Ubuntu on Vista"
date: 2009-01-15
forum: New to Ubuntu
---

### Post by chucknorrisprogrammer on 2009-01-15
Hi,
  I'm a newby! I just installed the latest version of ubuntu as a virtual machine using vmware workstation on my Vista computer. The installation went smoothly, except networking is not working. If I choose to use 'NAT', then the ubuntu networking icon on the top says it is connected, but i can't ping anything or get firefox to connection to any pages. I have disabled windows firewall. Also, i tried switching to 'Bridged' connection on vmware, but this doesn't work either, and in ubuntu it shows that it cannot connect when I try this.

Does anyone have any ideas?

---

### Post by spikoley on 2009-01-15
Try running these commands with NAT set up.

```
sudo dhclient
```

If that does not work then post the out put of this command.
```
ifconfig
```

---

### Post by chucknorrisprogrammer on 2009-01-15
I tried 'sudo dhclient' but it didn't work.

Here is the output of my ifconfig:

```

eth0      Link encap:Ethernet  HWaddr 00:0c:29:87:04:fe  
          inet addr:192.168.145.130  Bcast:192.168.145.255  Mask:255.255.255.0
          inet6 addr: fe80::20c:29ff:fe87:4fe/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:33 errors:0 dropped:0 overruns:0 frame:0
          TX packets:41 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:5146 (5.1 KB)  TX bytes:5794 (5.7 KB)
          Interrupt:19 Base address:0x2024 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:80 errors:0 dropped:0 overruns:0 frame:0
          TX packets:80 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:4000 (4.0 KB)  TX bytes:4000 (4.0 KB)

pan0      Link encap:Ethernet  HWaddr 52:0c:0e:8d:f2:e0  
          inet6 addr: fe80::500c:eff:fe8d:f2e0/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:32 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 B)  TX bytes:6937 (6.9 KB)

pan0:avahi Link encap:Ethernet  HWaddr 52:0c:0e:8d:f2:e0  
          inet addr:169.254.9.248  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1


```

Thanks!

---

### Post by spikoley on 2009-01-16
You are receiving an IP address (192.168.145.130).  Try pinging by domain name and IP address.

```
ping ubuntuforums.org
```
```
ping 91.189.94.186
```

---

### Post by hyper_ch on 2009-01-16
are you trying to use bridged over a wireless card?

---

### Post by chucknorrisprogrammer on 2009-01-16
I am using a built-in wireless card. When I use NAT, it seems like everything is working, but I can't ping anything and I can't load any pages in the browser. 

I've tried using bridged connection as well but ubuntu is 'disconnected' when I use that; in either case, I get no 'showable' connectivity.

---

### Post by lovelyvik293 on 2009-01-16
If you are using proxy in your network?

---

### Post by hyper_ch on 2009-01-16
vmware has issues with wireless cards for nat and bridging...

---

