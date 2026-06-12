---
title: "Configuring eth1 to &quot;work&quot; lol"
date: 2008-03-06
forum: Networking &amp; Wireless
---

### Post by ster1988 on 2008-03-06
Ok so my current box is the following: intel Q6600 processor, 4 gb's of RAM, hd radeon 2600 pro and an [[COLOR="Blue"]ASUS P5N32-E SL[/COLOR]I]("http://www.newegg.com/Product/Product.aspx?Item=N82E16813131073") when i run ifconfig here is what it displays:
> eth0      Link encap:Ethernet  HWaddr 00:1E:8C:64:4A:48  
          inet addr:192.168.1.2  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::21e:8cff:fe64:4a48/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:239854 errors:0 dropped:0 overruns:0 frame:0
          TX packets:56804 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:108270220 (103.2 MB)  TX bytes:7208020 (6.8 MB)
          Interrupt:17 Base address:0x6000 

eth1      Link encap:Ethernet  HWaddr 00:1E:8C:64:4E:AC  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:641 errors:0 dropped:0 overruns:0 frame:0
          TX packets:301 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:240071 (234.4 KB)  TX bytes:35172 (34.3 KB)
          Interrupt:18 Base address:0x8000 

eth1:avah Link encap:Ethernet  HWaddr 00:1E:8C:64:4E:AC  
          inet addr:169.254.6.247  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          Interrupt:18 Base address:0x8000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:132 errors:0 dropped:0 overruns:0 frame:0
          TX packets:132 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:13180 (12.8 KB)  TX bytes:13180 (12.8 KB)

i currently have this set up with my physical network 
> [CENTER]Modem
|
|
Router
|
eth0
eth1
|
Dlink switch
|
|__________________|
laptop..............xbox
[/CENTER]

What i am looking to do is getting my eth0 to forward to my eth1 so i can potentially use my own DHCP server to manage my network rather than the one in my router. I tried running firestarter to configure a fire wall, and i selected eth0 for the device supplying the internet, and then it asks for me to supply a device for the LAN and i choose eth1 after i finish the wizard and i get the error " the device eth1 is not ready please check your network device settings and make sure the internet connection is active." as you can see from the ifconfig eth1 is recognized but is not configured so anything. So i am wondering if anything could guide/walk me through configuring the eth1 device properly so i can set up this firewall and get this server rolling.

thank you in advanced
-Sterling

---

### Post by HermanAB on 2008-03-07
Hmm, see the Advanced Routing Howto on tldp.org.

You can try setting both ports to the same subnet and enabling TCP/IP forwarding.

---

### Post by ster1988 on 2008-03-07
I have been reading more and i think the problem comes down to this, how do i configure the internal LAN card so it will send to my switch and from there i can configure everything else?

---

### Post by HermanAB on 2008-03-07
$ man route
$ sudo route add default gw the.router.ip.address dev eth0

Cheers,

Herman

---

### Post by Paris Heng on 2008-03-07
1. Add route in the routing table for the 2 particular interfaces using *route add* ... roughly like this, depend on your network configuration.

> route add -net [COLOR="Red"]<IP>[/COLOR] netmask [COLOR="Red"]<mask>[/COLOR] dev eth0
route add default gw [COLOR="Red"]<IP>[/COLOR] dev eth0

2. Check the routing table, route -n
3. Enable ip forwarding, i think the case mayb ipv4.

> echo 1 > /proc/sys/net/ipv4/ip_forward

4. Using NAT in the PC for private to public address translation, i think your out-going interface will be eth0.

> 
modprobe iptable_nat
iptables -F
iptables -t nat -F
iptables -t nat -A POSTROUTING -o eth0 -j MASQUERADE
iptables-save > /etc/iptables.conf

---

