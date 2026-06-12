---
title: "Need help in the Network configuration (ICS - WinXP, Wirenet)"
date: 2008-05-12
forum: Networking &amp; Wireless
---

### Post by bombos on 2008-05-12
Hi,
I have a windows XP ICS network with 5 computers, I put UBUNTU on 2 of them,
in the FIRST computer Everything works great!
in the SECOND I cant see the network, I cant ping, - nothing!
I tryied to fix it throu information I saw in this forum but I didn't succeed.

On the SECOND computer (the one with the problem) all the network settings working fine.
It have 2 Ethernet wire cards:
INTEL - Connected to the ICS & the internet.
CNET - Connected to another Standalone computer (Just for file sharing)

I dont have SAMBA on the second computer & I cant install it until Ill have internet :-(

here are some Deatails:
when I wrote "ifconfig" on the FIRST computer (with the working net) I got this massage:

eth0      Link encap:Ethernet  HWaddr 00:0e:7f:a8:d1:2b  
          inet addr:192.168.0.174  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::20e:7fff:fea8:d12b/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:13394 errors:0 dropped:0 overruns:0 frame:0
          TX packets:9992 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:14278802 (13.6 MB)  TX bytes:1242398 (1.1 MB)
          Interrupt:20 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:10434 errors:0 dropped:0 overruns:0 frame:0
          TX packets:10434 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:521700 (509.4 KB)  TX bytes:521700 (509.4 KB)


when I write it on the SECOND computer I get this massage:

eth0      Link encap:Ethernet  HWaddr 00:80:ad:07:17:62  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:19 Base address:0xb800 

eth1      Link encap:Ethernet  HWaddr 00:11:11:25:49:61  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:12 errors:0 dropped:0 overruns:0 frame:0
          TX packets:167 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1562 (1.5 KB)  TX bytes:19849 (19.3 KB)

eth1:avahi Link encap:Ethernet  HWaddr 00:11:11:25:49:61  
          inet addr:169.254.3.172  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:1176 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1176 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:62698 (61.2 KB)  TX bytes:62698 (61.2 KB)

---------
I dont know what is the "eth1:avahi" & the IP 169.254.3.172 Is not related to any of my computers.
I tryied to config the network throu DHCP & Static IP 
I didnt succeed :-(

Can someone please help me???
Thanks,

---

### Post by bombos on 2008-05-13
...is there any way???
in Windows everything works great....

---

### Post by superprash2003 on 2008-05-13
try this go to system->administration->network and select the network card which is connected to the network.. either eth0 or eth1.. then select properties and ensure that DHCP mode is selected instead of Roaming mode.if you are not sure whehter its eth0 or eth1 do the same for both

---

### Post by bombos on 2008-05-13
I did it already & UBUNTU still not recognize the network
When I go to system->administration->network tools
I see that I have an AVAHI Connection to my eth0 & eth1
I dont have avahi, never had one....

What 2 do, Plese???

---

### Post by superprash2003 on 2008-05-13
PLease go to System->administration ->**NETWORK **
 NOT NETWORK TOOLS

---

### Post by bombos on 2008-05-13
I did what you told me on NETWORK,
It didnt work,
I just wanted to add information about the avahi in the networktools...
Ps, when I go to network tools I cannot open the Configure button - There's an error...
maby there is connection betwine the problems?

---

### Post by superprash2003 on 2008-05-13
you dont seem to be getting an ip.. so you could try setting up the ip address manually
 go to system->administration->network and select the network card which is connected to the network.. either eth0 or eth1.. then select properties and select static ip address and enter ip as 192.168.0.175 and enter gateway ip as ip address of server.if you are not sure whehter its eth0 or eth1 do the same for both

---

### Post by bombos on 2008-05-14
I did the static IP for both eth0 & eth1 together & after speratly,
& still I cant even ping to the server :-(
what else can I do?

---

### Post by bombos on 2008-05-20
Is it possible that the UBUNTU didnt recognise mt Ethernet card properly?
can anyone help me with this???
please...

---

