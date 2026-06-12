---
title: "static ip within dynamic ip network"
date: 2014-06-21
forum: Networking &amp; Wireless
---

### Post by cmcanulty on 2014-06-21
I am trying to set up remote control of a network for a library that has several win 7 machines and several xubuntu 14.04 machines. To make it a bit easier I would like to give each machine a static ip within the network but we have a dynamic ip for the network due to cost. Is this possible? If so please explain. I do have remote enabled on every machine and xrdp, vino, open shh installed already, also installed vnc4server and remmina. I will be doing this over a WAN powered by an ASUS RT-AC68U router. This is a big project and I am sure to have more questions as I proceed. If anyone is willing to spend a bit of time helping me on this project to promote ubuntu I would appreciate it. I get numerous people coming in for me to switch their computer from xp or vista or win 8 to ubuntu as they use our public xubuntu machines and want it  on their own computer.

---

### Post by The Cog on 2014-06-21
There are a couple of ways to do this. 

Firstly, you could configure the network DHCP server to only issue addresses within a certain part of the network range. So for example, if your network is 192.168.1.0/24 then it has space for host addresses 192.168.0.1 to 192.168.0.254 (0 and 255 are reserved). If you configure the DHCP server to only issue addresses in the range 192.168.0.1-192.168.0.199 then you can use 200-254 for your own servers and assign them statically.

Secondly, you can give static reservations to the DHCP server - configuring it to always give a particular address to a particular MAC address. The MAC address is unique for each computer on the network. So for instance you could configure the DHCP server to always allocate address 192.168.0.123 to MAC address 24:83:f2:82:9e:17. 

I use this second technique at home. That way all PCs are configured for DHCP but some are always on known addresses anyway.

---

### Post by cmcanulty on 2014-06-21
I am afraid you lost me, I am a total beginner as far as networking is concerned. I am pretty competent at desktop admin.  I can't set the dns as it is dynamic through charter. I need to somehow go into each computer and set an internal static ip without affecting the external dynamic ip for the whole system. Then I need to remote into the router, I think to remotely access each computer. So far I can get to one win 7 remotely but not to any others. Another option would be to add all the computers to the win 7 network from one win 7 machine and get at everything that way. But I prefer working through xubunu unless that will make it much more difficult. You maybe explained that but I don't get it.

---

### Post by steeldriver on 2014-06-21
Since the OP mentions cost, I think they are asking about how to handle having a dynamic **public** IP (rather than about mixing static and dynamic IP assignments on the LAN side)

---

### Post by cmcanulty on 2014-06-21
yes I just want to set internal static ips within a dynamic outside ip. I know how to set up the dyns work through. To be more clear I need to access the graphical desktops of all win and xubuntu machines for more the admin and limited user accounts. Our tech budjet is zero. We run by volunteers and I am the system admin though by no means am I a pro. We don't have a server but I plan to add a machine to access all the remotes and do nothing else on that one.

---

### Post by chili555 on 2014-06-21
I assume you have a **public** IP address from the internet service provider due to cost. Most of us do, since the service provider assumes that if you want a static IP address, you are running a server for gaming or whatever and will get tremendous amounts of traffic. The router gets that address from the cable or DSL modem.

That is, however, different from the addresses behind the router. Usually, the addresses behind the router are **private** addresses in the form of 192.168.x.y or 10.1.x.y. The router then uses network address translation (NAT) to translate requests from within the network. If, for example, computer 192.168.1.101 wants the web page for [www.amazon.com](www.amazon.com), the router requests it from the internet service provider and, when it arrives, passes it along to 192.168.1.101.

You may absolutely have static addresses *behind* the router which itself gets a dynamic address from the internet service provider's cable or DSL modem. I suggest you turn off the DHCP server in the router. Then, use addresses in some logical plan and keep notes so you know which computer is which address.

If you are setting the addresses in Network Manager, you may find this useful: [http://www.liberiangeek.net/wp-content/uploads/2011/05/1029141aa483_8FD2/natty_windows_static_ip_7_thumb.png](http://www.liberiangeek.net/wp-content/uploads/2011/05/1029141aa483_8FD2/natty_windows_static_ip_7_thumb.png)  This example is for ethernet, but the process is the same.

Please ask us if you have more questions.

---

### Post by capscrew on 2014-06-21
> **cmcanulty said:**
> yes I just want to set internal static ips within a dynamic outside ip. 
It might be helpful to you to clarify a few things.  You do not mix the two networks (LAN and WAN) administration.  Your router is the connection point between the ISP's network (Wide Area Network) and your network (the Local Area Network).  The router is what handles the movement of information to and from the to different networks.  It is the interconnection.  

You don't administrate the WAN at all.  You have complete control of the LAN however.  As you are also using a private range of IP addresses on the LAN the router also uses a technique called Network Address Translation.  This NAT is automatic and you don't really have to worry about its function for what you want to do.

To summarize; the fixed ip addresses in the LAN have no effect upon the WAN side network.  The router will function with all IP addresses you use in the LAN as long as they are in the same Local Area Network. >  

  
I can't set the dns as it is dynamic through charter. 

Are you going to use hostname resolution to IP addressing for the LAN?  This is really a side issue to setting fixed ip addressing on various computers in a LAN.
> 
I need to somehow go into each computer and set an internal static ip without affecting the external dynamic ip for the whole system. 

Are we talking apples and oranges here?  There is only one *external IP address*.  This is the IP address on the upstream (WAN) side of the router.  All all the machines in the LAN can have either a fixed IP address or a variable one.  Fixed IP addressing can be by either configuring a file on each machine (this is static IP addressing) or via an IP address reservation at the DHCP server which in most cases is hosted at the router.  Using the reservation system means you do not have to go to each computer in the LAN.  You set this all up at one place; the router.
> 
Then I need to remote into the router, I think to remotely access each computer. 

You should be able to remotly access any computer in the LAN directly from the computer that you set up.  You should not have to visit the router after the initial set up of fixed IP addressing via IP address reservations. 
> 
So far I can get to one win 7 remotely but not to any others. Another option would be to add all the computers to the win 7 network from one win 7 machine and get at everything that way. But I prefer working through xubunu unless that will make it much more difficult. You maybe explained that but I don't get it. 

The Windows and Xubuntu computers can all exist on the same LAN network.  If you have public and administrative computers, you probably should have them on different networks however.

---

