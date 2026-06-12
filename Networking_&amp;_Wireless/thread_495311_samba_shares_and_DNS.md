---
title: "samba shares and DNS"
date: 2007-07-07
forum: Networking &amp; Wireless
---

### Post by dvenardos on 2007-07-07
I have a new Ubuntu installation and am having trouble with samba shares and DNS resolution.
I set up my Ubuntu home folder to be shared via samba with read/write access. 

I can access this share via the the Ubuntu network browser (i.e. it is shared to itself), but I am unable to access the share from a networked mac OS 10.4 and via VMWare Player Win 2K running on the Ubuntu box. I get invalid username/password.

In addition, the Ubuntu box sees a samba share on the Mac OS 10.4 box and on the VMPlayer, but when viewing with the Ubuntu Network viewer no files show up. The VMware player is able to see the Mac OS 10.4 share without any issues and the Mac OS 10.4 is able to connect to the share on the VMWare player.

The Mac OS 10.4 and the VMWare player can ping each other and the Ubuntu box via network name, but Ubuntu can only ping by ipaddress.

Internet access works fine on the ubuntu box.

I am stumped.

ifconfig:
eth0      Link encap:Ethernet  HWaddr 00:1B:FC:00:A2:F5  
          inet addr:192.168.1.39  Bcast:255.255.255.255  Mask:255.255.255.0
          inet6 addr: fe80::21b:fcff:fe00:a2f5/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1943 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1694 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1727455 (1.6 MiB)  TX bytes:237341 (231.7 KiB)
          Interrupt:16 

eth1      Link encap:Ethernet  HWaddr 00:1B:FC:00:A5:1C  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:17 Base address:0x4000 

eth1:avah Link encap:Ethernet  HWaddr 00:1B:FC:00:A5:1C  
          inet addr:169.254.5.52  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          Interrupt:17 Base address:0x4000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:981 errors:0 dropped:0 overruns:0 frame:0
          TX packets:981 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:139221 (135.9 KiB)  TX bytes:139221 (135.9 KiB)

vmnet1    Link encap:Ethernet  HWaddr 00:50:56:C0:00:01  
          inet addr:192.168.30.1  Bcast:192.168.30.255  Mask:255.255.255.0
          inet6 addr: fe80::250:56ff:fec0:1/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:102 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

vmnet8    Link encap:Ethernet  HWaddr 00:50:56:C0:00:08  
          inet addr:192.168.179.1  Bcast:192.168.179.255  Mask:255.255.255.0
          inet6 addr: fe80::250:56ff:fec0:8/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:102 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

---

### Post by dvenardos on 2007-07-08
Okay, all the Ubuntu click and work had me tricked. I had to add my username for samba via the command line, I thought it would use my username and password. So I can connect from my mac, but no luck connecting from the VMPlayer and still cannot view other shares from Ubuntu.

I can no longer ping the Ubuntu box by name only by IP address.

I really need to get samba working both ways before I can make this switch...

Perhaps it is time to start over from scratch?

---

### Post by kevdog on 2007-07-08
Look for a post in the network forums and search by the name "winbind".  I cant remember the author but he did an excellent job explaining how to install Samba so you could search by computer name rather than IP number.

---

### Post by dvenardos on 2007-07-08
> **kevdog said:**
> Look for a post in the network forums and search by the name "winbind".  I cant remember the author but he did an excellent job explaining how to install Samba so you could search by computer name rather than IP number.

Couldn't find the post you were talking about, but I did discover that in the File browser by switching the location bar to text and appending the share to the path I can now view the files on the Mac, but not on the PC. So the file browser appears to have a bug in that it can't display the available shares. 

When I use the cmd line smbclient --list PCName I get protocol negotiation failed.
smclient --list MacName works properly.
So linux to unix samba is working, but not linux to windows.

---

