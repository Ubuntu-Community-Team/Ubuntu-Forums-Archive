---
title: "Problem in connecting to internet"
date: 2008-07-15
forum: Networking &amp; Wireless
---

### Post by kimiboy on 2008-07-15
**I'm a linux newbie. I installed ubuntu 8.04 in my laptop today along with WinXP. I've a Cable modem connection at home and all I need to do is just plug the RJ45 connector to the Ethernet port for internet. I'm getting internet in my Desktop PC without any problem. This is what I get when I type ipconfig /all in my Desktop PC.**

<!-- Windows XP (Desktop) ipconfig Begins -->		
Microsoft Windows XP [Version 5.1.2600]
(C) Copyright 1985-2001 Microsoft Corp.

C:\Documents and Settings\Suman>ipconfig /all

Windows IP Configuration

        Host Name . . . . . . . . . . . . : Desktop
        Primary Dns Suffix  . . . . . . . :
        Node Type . . . . . . . . . . . . : Unknown
        IP Routing Enabled. . . . . . . . : No
        WINS Proxy Enabled. . . . . . . . : No

Ethernet adapter Local Area Connection:

        Connection-specific DNS Suffix  . :
        Description . . . . . . . . . . . : Intel(R) PRO/100 VE Network Connecti
on
        Physical Address. . . . . . . . . : 00-16-76-BD-CA-0E
        Dhcp Enabled. . . . . . . . . . . : Yes
        Autoconfiguration Enabled . . . . : Yes
        IP Address. . . . . . . . . . . . : 116.68.73.13
        Subnet Mask . . . . . . . . . . . : 255.255.248.0
        Default Gateway . . . . . . . . . : 116.68.72.1
        DHCP Server . . . . . . . . . . . : 202.88.238.16
        DNS Servers . . . . . . . . . . . : 202.88.238.3
                                            202.88.238.5
                                            165.21.83.88
        Lease Obtained. . . . . . . . . . : Tuesday, July 15, 2008 6:43:56 PM
        Lease Expires . . . . . . . . . . : Tuesday, July 15, 2008 7:03:56 PM

Tunnel adapter 6to4 Tunneling Pseudo-Interface:

        Connection-specific DNS Suffix  . :
        Description . . . . . . . . . . . : 6to4 Tunneling Pseudo-Interface
        Physical Address. . . . . . . . . : 74-44-49-0D
        Dhcp Enabled. . . . . . . . . . . : No
        IP Address. . . . . . . . . . . . : 2002:7444:490d::7444:490d
        Default Gateway . . . . . . . . . : 2002:c058:6301::c058:6301
        DNS Servers . . . . . . . . . . . : fec0:0:0:ffff::1%1
                                            fec0:0:0:ffff::2%1
                                            fec0:0:0:ffff::3%1
        NetBIOS over Tcpip. . . . . . . . : Disabled

Tunnel adapter Automatic Tunneling Pseudo-Interface:

        Connection-specific DNS Suffix  . :
        Description . . . . . . . . . . . : Automatic Tunneling Pseudo-Interface

        Physical Address. . . . . . . . . : 74-44-49-0D
        Dhcp Enabled. . . . . . . . . . . : No
        IP Address. . . . . . . . . . . . : fe80::5efe:116.68.73.13%2
        Default Gateway . . . . . . . . . :
        DNS Servers . . . . . . . . . . . : fec0:0:0:ffff::1%1
                                            fec0:0:0:ffff::2%1
                                            fec0:0:0:ffff::3%1
        NetBIOS over Tcpip. . . . . . . . : Disabled

C:\Documents and Settings\Suman>
<!-- Windows XP (Desktop) ipconfig Ends -->



**But I'm not getting internet in my laptop. I was getting internet earlier but not now. This is what I get when I type ifconfig in Ubuntu 8.04.**


<!-- ifconfig Ubuntu 8.04 LTS Begins -->
suman@suman-laptop:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:16:d3:aa:5b:5a  
          inet6 addr: fe80::216:d3ff:feaa:5b5a/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:18986 errors:0 dropped:0 overruns:0 frame:0
          TX packets:34 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1186880 (1.1 MB)  TX bytes:5615 (5.4 KB)

eth0:avahi Link encap:Ethernet  HWaddr 00:16:d3:aa:5b:5a  
          inet addr:169.254.6.233  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:1616 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1616 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:84288 (82.3 KB)  TX bytes:84288 (82.3 KB)

suman@suman-laptop:~$
<!-- Ubuntu 8.04 LTS Ends -->


**and this is what I get when I type ipconfig in Windows XP installed in my laptop.**



<!-- Windows XP (Laptop) ipconfig Begins -->
Microsoft Windows XP [Version 5.1.2600]
(C) Copyright 1985-2001 Microsoft Corp.

C:\Documents and Settings\Suman>ipconfig /all

Windows IP Configuration

        Host Name . . . . . . . . . . . . : Laptop
        Primary Dns Suffix  . . . . . . . :
        Node Type . . . . . . . . . . . . : Unknown
        IP Routing Enabled. . . . . . . . : No
        WINS Proxy Enabled. . . . . . . . : No

Ethernet adapter Local Area Connection:

        Connection-specific DNS Suffix  . :
        Description . . . . . . . . . . . : Intel(R) PRO/100 VE Network Connecti
on
        Physical Address. . . . . . . . . : 00-16-D3-AA-5B-5A
        Dhcp Enabled. . . . . . . . . . . : Yes
        Autoconfiguration Enabled . . . . : Yes
        Autoconfiguration IP Address. . . : 169.254.55.183
        Subnet Mask . . . . . . . . . . . : 255.255.0.0
        Default Gateway . . . . . . . . . : 169.254.55.183
<!-- Windows XP (Laptop) ipconfig Ends -->


**What to do now?**

---

### Post by Loukisgr on 2008-07-15
As i see you have different default gateway. Is it the isp's? If not then that's a problem.
Another think is that you don;t have an valid ip address in ubuntu. You have wrong subnet mask Can you re configure it? (System > system administrator > networking) (sorry i have them in greek ;) )

---

### Post by kimiboy on 2008-07-15
In my Desktop PC the settings are like this

**Obtain an IP address automatically**
**Obtain DNS server address automatically**

It's working well in Desktop PC (Windows XP only) and not in laptop (dualboot Ubuntu & XP).

My Ubuntu settings are like this

Enable Roaming Mode - **Unchecked**
Configuration - **Automatic Configuration (DHCP)**

---

### Post by issih on 2008-07-15
I'm fairly sure you are having dhcp issues, as your laptop is recieving a 169.xxxxx ip address which basically means dhcp failed to assign you an address.

Not exactly sure why, but the fact its happening in ubuntu and xp suggests a configuration issue somewhere.

---

### Post by kimiboy on 2008-07-15
I also think that it's DHCP issue. This is the physical address of my Desktop PC **00-16-76-BD-CA-0E** and this is the physical address of my laptop **00-16-D3-AA-5B-5A**. I think the cable modem is allowing only one physical address ie my desktop's. My doubt is, Can the ISP enable a setting like that so that only one system will be allowed to use internet? Is it possible? If it's possible then how to resolve this?

---

### Post by Loukisgr on 2008-07-15
enable the roaming ;) That should fix your problem

---

### Post by kimiboy on 2008-07-15
Well, I tried that. It did nt solve the problem :(

---

### Post by Loukisgr on 2008-07-15
mmm  put your dns manually.(your router's ip) with the roaming option.

It should work if you wait for 30 secs

---

### Post by kimiboy on 2008-07-15
I tried that too. But the result is the same :(. The problem might be with the ISP. I think they must have enabled some settings to allow only one system to use the internet. Something with the mac address.

---

### Post by Loukisgr on 2008-07-15
nop that cant be. The mac they can see is the router's mac only. Tell me is the nat enabled in your router? Pls after the changes we havbe made post me your new ip

---

### Post by kimiboy on 2008-07-15
This is my new setting

Enable Roaming Mode - **Checked**
Added DNS Servers - **202.88.238.3**, **202.88.238.5**, **165.21.83.88**

But the result is the same, No Internet :(.

This is the new ifconfig after enabling the settings mentioned above.


suman@suman-laptop:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:16:d3:aa:5b:5a  
          inet6 addr: fe80::216:d3ff:feaa:5b5a/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:7846 errors:0 dropped:0 overruns:0 frame:0
          TX packets:58 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:481817 (470.5 KB)  TX bytes:6543 (6.3 KB)

eth0:avahi Link encap:Ethernet  HWaddr 00:16:d3:aa:5b:5a  
          inet addr:169.254.6.233  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:1500 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1500 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:75304 (73.5 KB)  TX bytes:75304 (73.5 KB)


**How to find out whether NAT is enabled or not in my cable modem?**

---

