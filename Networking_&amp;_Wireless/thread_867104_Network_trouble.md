---
title: "Network trouble"
date: 2008-07-22
forum: Networking &amp; Wireless
---

### Post by v1ND on 2008-07-22
I'm a complete ubuntu newbie. I cannot seem to get the wireless networking to connect to the internet.

On my computer I have a Marvell Yukon 88E8001 Gigabit ethernet Controller. Under hardware testing, ubuntu does reckognise this. Upstairs there is a Belkin G+ wireless router and an ADSL modem connected to the iMac.

Under Network Settings, I have only 2 connection options Wired and Point to Point. Currently I have the ubuntu set to Static IP address with the the IP, subnet and gateway taken from the laptop. When I try to ping the router's IP it works fine however when I try other IP's they won't work.

Is there anything else I should be trying?

---

### Post by mamut0o1 on 2008-07-22
You have ubuntu set to static IP address:
you have configured the IP, Subnet and Gateway.
How about the DNS to resolve names?
code:
sudo vi /etc/resolv.conf
enter here your DNS and restart networking service
code:
sudo /etc/init.d/networking restart

---

### Post by v1ND on 2008-07-22
Still not working.

---

### Post by mamut0o1 on 2008-07-22
so you can see the router but not any websites?
you already enter the DNS settings and restarted the network interface.
have you reboot the router upstairs?
do command ifconfig and check configuration
also cat /etc/resolv.conf
your dns should be here: 
ex:
nameserver 204.x.x.x
Is all of this correct?

---

### Post by v1ND on 2008-07-22
The router currently isn't showing up in the network settings window. I put in the info in under Static IP address.

ifconfig gives the following:

mike@mike-desktop:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:14:2a:7a:07:5d  
          inet addr:192.168.50.3  Bcast:192.168.50.255  Mask:255.255.255.0
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:16 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:1843 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1843 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:96486 (94.2 KB)  TX bytes:96486 (94.2 KB)

The only discrepency I'm seeing is in Bcast. Not sure what that is supposed to be but apart from the last 3 digits, it is identical to the router's IP address and Gateway address.

When I enter cat /etc/resolv.conf it gives me:

20_[COLOR="Red"]5[/COLOR]_.150.58.253

This is right according to the laptop settings however mamut mentioned that it would be a 204.x.x.x

---

### Post by mamut0o1 on 2008-07-22
> **v1ND said:**
> The router currently isn't showing up in the network settings window. I put in the info in under Static IP address.

ifconfig gives the following:

mike@mike-desktop:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:14:2a:7a:07:5d  
          inet addr:192.168.50.3  Bcast:192.168.50.255  Mask:255.255.255.0
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:16 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:1843 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1843 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:96486 (94.2 KB)  TX bytes:96486 (94.2 KB)

The only discrepency I'm seeing is in Bcast. Not sure what that is supposed to be but apart from the last 3 digits, it is identical to the router's IP address and Gateway address.

When I enter cat /etc/resolv.conf it gives me:

20_[COLOR="Red"]5[/COLOR]_.150.58.253

This is right according to the laptop settings however mamut mentioned that it would be a 204.x.x.x


nameserver 204.x.x.x was "a" given example.
May I ask why you are using an static ip instead of using DHCP?

---

### Post by v1ND on 2008-07-22
Only thing that let me put in numbers. :rolleyes:

So i changed over to the dhcp, now what? :(

---

### Post by mamut0o1 on 2008-07-22
restart your PC. you should get an ip automatically.

---

### Post by v1ND on 2008-07-22
I'm seeing a check mark beside dhcp in Network Settings > Connections. An improvement but still no interwebs.

---

### Post by v1ND on 2008-07-23
Anyone got any more ideas?

---

