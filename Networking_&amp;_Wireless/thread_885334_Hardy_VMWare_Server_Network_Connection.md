---
title: "Hardy VMWare Server Network Connection"
date: 2008-08-10
forum: Networking &amp; Wireless
---

### Post by Blind Tiger on 2008-08-10
I successfully installed XP Pro as a guest OS on Ubuntu 8.04.1 using VMWare Server 1.0.6, yet I cannot connect to the internet using the bridged network.  
[LIST]
[*]During intallation, the terminal correctly returned ". vmnet0 is bridged to eth0"
[*]the network adapter in virtual machine settings is set to bridged
[*]my host os connectivity is fine
[/LIST]

Output from ifconfig is:
> ~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:13:d3:a6:d6:8b  
          inet addr:76.105.183.226  Bcast:255.255.255.255  Mask:255.255.248.0
          inet6 addr: fe80::213:d3ff:fea6:d68b/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:145865 errors:0 dropped:0 overruns:0 frame:0
          TX packets:98463 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:109959559 (104.8 MB)  TX bytes:72502700 (69.1 MB)
          Interrupt:19 Base address:0x2000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:13537 errors:0 dropped:0 overruns:0 frame:0
          TX packets:13537 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:17825644 (16.9 MB)  TX bytes:17825644 (16.9 MB)

wlan0     Link encap:Ethernet  HWaddr 00:19:db:0b:24:5f  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

wmaster0  Link encap:UNSPEC  HWaddr 00-19-DB-0B-24-5F-00-00-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

I  do not see any vmnet adapters listed, and this worries me.  Does anyone have any suggestions or solutions?

---

### Post by jimv on 2008-08-10
I used to use VMWare until I found VirtualBox...I much recommend it over VMWare.

You can get the DEB here:
[https://cds.sun.com/is-bin/INTERSHOP.enfinity/WFS/CDS-CDS_SMI-Site/en_US/-/USD/ViewProductDetail-Start?ProductRef=innotek-1.6-G-F@CDS-CDS_SMI](https://cds.sun.com/is-bin/INTERSHOP.enfinity/WFS/CDS-CDS_SMI-Site/en_US/-/USD/ViewProductDetail-Start?ProductRef=innotek-1.6-G-F@CDS-CDS_SMI)

(This isn't the opensource version, but it's still free, and supports USB and virtual SATA drives.)

---

### Post by Blind Tiger on 2008-08-10
jimv -- i have tried virtualbox also, briefly, after no success with vmware on gutsy, but aborted an install as it appeared to hang/fail, and consequently corrupted the data partition i had installed the virtual machine to!  

anyway, i reconfigured vmware network setup to include nat and host only.  i can connect with the nat adapter.  my next bit of work is to install sonicwall vpn on the xp pro guest and connect to my office network.  previously i could not acquire an ip address.

i am curious to know what you feel the advantages of virtualbox are, or in general why you prefer it?  i have read many posts/articles on comparisons of the two.

-thanks

---

### Post by jimv on 2008-08-10
It's more just that VirtualBox feels more user friendly than VMWare, and it takes less HD space.

---

### Post by Blind Tiger on 2008-08-10
right on.  well, i can't get my vpn to acquire an ip address yet, so maybe i'll give virtual  box a try.

---

### Post by Blind Tiger on 2008-08-10
I am using VMware AMD PCnet adapter in NAT mode -- that is the only way I can get internet connectivity, but I cannot acquire an ip address with Sonicwall VPN.  Any solutions?

output from ifconfig:

~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:13:d3:a6:d6:8b  
          inet addr:76.105.183.226  Bcast:255.255.255.255  Mask:255.255.248.0
          inet6 addr: fe80::213:d3ff:fea6:d68b/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:164849 errors:0 dropped:0 overruns:0 frame:0
          TX packets:49300 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:108610118 (103.5 MB)  TX bytes:6163998 (5.8 MB)
          Interrupt:19 Base address:0x2000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:2326 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2326 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:112856 (110.2 KB)  TX bytes:112856 (110.2 KB)

vmnet1    Link encap:Ethernet  HWaddr 00:50:56:c0:00:01  
          inet addr:192.168.152.1  Bcast:192.168.152.255  Mask:255.255.255.0
          inet6 addr: fe80::250:56ff:fec0:1/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:70 errors:0 dropped:0 overruns:0 frame:0
          TX packets:49 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

vmnet8    Link encap:Ethernet  HWaddr 00:50:56:c0:00:08  
          inet addr:172.16.14.1  Bcast:172.16.14.255  Mask:255.255.255.0
          inet6 addr: fe80::250:56ff:fec0:8/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:807 errors:0 dropped:0 overruns:0 frame:0
          TX packets:40 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

wlan0     Link encap:Ethernet  HWaddr 00:19:db:0b:24:5f  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

wmaster0  Link encap:UNSPEC  HWaddr 00-19-DB-0B-24-5F-00-00-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)


----------------
Now playing: [Weezer - Say It Ain't So](http://www.foxytunes.com/artist/weezer/track/say+it+aint+so)
via [FoxyTunes](http://www.foxytunes.com/signatunes/)

----------------
Now playing: [Weezer - Say It Ain't So](http://www.foxytunes.com/artist/weezer/track/say+it+aint+so)
via [FoxyTunes](http://www.foxytunes.com/signatunes/)

---

### Post by Blind Tiger on 2008-08-15
jimv -- I decided to give Virtualbox a try.  After using both VMware and Virtualbox, I have to say I agree with you on the feel of Vbox's interface.  I did have the same difficulty with networking Vbox though -- it defaults to NAT networking, and that did not allow for acquiring a DHCP lease using my Sonicwall VPN client.  I tried multiple configurations to manually create a bridged network using Host Only adapter in Vbox, but to no success.  In the end, it amounted to checking the box next to Enable NAT Traversal in the Advanced settings of the VPN menu in Sonicwall's web  administration page!

I am assuming this will work with VMware also, using NAT mode for the adapter (virtual adapter vmnet8).  I will test this to be sure.

---

