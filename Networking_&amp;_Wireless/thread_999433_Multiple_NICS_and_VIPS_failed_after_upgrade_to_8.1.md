---
title: "Multiple NICS and VIPS failed after upgrade to 8.10"
date: 2008-12-01
forum: Networking &amp; Wireless
---

### Post by DantePasquale on 2008-12-01
Hi All,

I am really baffled about some network issues that occurred after upgrading from 8.04 to 8.10 over the weekend. I have been battling with my fixed IP addresses on multiple NICs in my server. 

***To recap***:

After upgrade and reboot the first thing I noticed was that no DNS resolution was occurring. I run ISPConfig with my own DNS running in this machine, so that was pretty strange. I checked the /etc/resolv.conf file and it was empty. So I populated it. Success! Or so I thought :(

I could only resolve names that are in my own DNS! There was no forwarding out to Covad's DNS servers! I verified they were up from another computer and things were fine with my network and names could be resolved. Also, if I was on my own network, I could get to websites hosted by ISPConfig on this server! So I thought things were close!

I read other posts about disabling _NetworkManager_ so I tried that but had no luck. Turns out it wasn't really disabled. So I tried to use _NetworkManager_ to configure both NICs with a single static IP address. That kind of worked! So I thought I was onto something :(

I tried many, many ways to plumb up the VIPs (3 per NIC) but couldn't figure out how to do that, so I abandoned _NetworkManager_. This time I made sure it was gone! I renamed the files after running synaptic to remove the packages.

I restored my original _/etc/network/interfaces_ file and my original _/etc/resolv.conf_. Then rebooted.

Things were still messed up. Not really sure why as all physical and virtual IPs were up and running. Plus the netstat -rn output looked fine, but still no DNS resolution. Turns out that ALL traffic was going over NIC 0 (eth0) even though NIC 1 (eth1) was up and running! Not sure what that had to do with DNS resolution, but I would see a DNS Request followed by a DNS Response with the proper IP addresses, but for some unknown reason, this never reached the application layer (dig, nslookup, bind9).

So I ran '**ifdown eth0**' then '**ifdown eth1**'. I stopped all network services (bind9, ntp, ISPConfig and anything else I could find). Then ran '**ifup eth0**'. Still no network services running. Now I could run dig/nslookup and things worked fine!

So, I then ran '**ifup eth1**' and **things broke again**! No clue as to why!!!!

Subsequently, I ran '**ifdown eth1**' and **things worked**! So I started the network services (bind9/ntp/ISPconfig) and they all work fine, including those with IP addresses bound to NIC 1 (eth1).

**What gives? What am I doing wrong that worked up to the upgrade? How can IP addresses on NIC 1 (eth1) be working if I downed them??? How the heck am I going to debug this?????**

Here are the relevant files:

**/etc/network/interfaces:**

```
auto lo
iface lo inet loopback

iface eth0 inet static
address 74.1.46.162
netmask 255.255.255.240
gateway 74.1.46.161

iface eth0:1 inet static
address 74.1.46.163
netmask 255.255.255.240
gateway 74.1.46.161

iface eth0:2 inet static
address 74.1.46.164
netmask 255.255.255.240
gateway 74.1.46.161

iface eth0:3 inet static
address 74.1.46.165
netmask 255.255.255.240
gateway 74.1.46.161

iface eth1 inet static
address 74.1.46.166
netmask 255.255.255.240
gateway 74.1.46.161

iface eth1:1 inet static
address 74.1.46.167
netmask 255.255.255.240
gateway 74.1.46.161

iface eth1:2 inet static
address 74.1.46.168
netmask 255.255.255.240
gateway 74.1.46.161

iface eth1:3 inet static
address 74.1.46.169
netmask 255.255.255.240
gateway 74.1.46.161

iface eth1:4 inet static
address 74.1.46.174
netmask 255.255.255.240
gateway 74.1.46.161


auto eth0
auto eth0:1
auto eth0:2
auto eth0:3
auto eth1
auto eth1:1
auto eth1:2
auto eth1:3
auto eth1:4
```

**here's 'ifconfig -a'**:

```
eth0      Link encap:Ethernet  HWaddr 00:e0:81:72:ed:a4  
          inet addr:74.1.46.162  Bcast:74.1.46.175  Mask:255.255.255.240
          inet6 addr: fe80::2e0:81ff:fe72:eda4/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:92569 errors:0 dropped:0 overruns:0 frame:0
          TX packets:88797 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:14377717 (14.3 MB)  TX bytes:19647713 (19.6 MB)
          Interrupt:249 

eth0:1    Link encap:Ethernet  HWaddr 00:e0:81:72:ed:a4  
          inet addr:74.1.46.163  Bcast:74.1.46.175  Mask:255.255.255.240
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          Interrupt:249 

eth0:2    Link encap:Ethernet  HWaddr 00:e0:81:72:ed:a4  
          inet addr:74.1.46.164  Bcast:74.1.46.175  Mask:255.255.255.240
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          Interrupt:249 

eth0:3    Link encap:Ethernet  HWaddr 00:e0:81:72:ed:a4  
          inet addr:74.1.46.165  Bcast:74.1.46.175  Mask:255.255.255.240
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          Interrupt:249 

eth1      Link encap:Ethernet  HWaddr 00:e0:81:72:ed:a5  
          inet addr:74.1.46.166  Bcast:74.1.46.175  Mask:255.255.255.240
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:31 errors:0 dropped:0 overruns:0 frame:0
          TX packets:54 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:5903 (5.9 KB)  TX bytes:10357 (10.3 KB)
          Interrupt:248 Base address:0x2000 

eth1:1    Link encap:Ethernet  HWaddr 00:e0:81:72:ed:a5  
          inet addr:74.1.46.167  Bcast:74.1.46.175  Mask:255.255.255.240
          BROADCAST MULTICAST  MTU:1500  Metric:1
          Interrupt:248 Base address:0x2000 

eth1:2    Link encap:Ethernet  HWaddr 00:e0:81:72:ed:a5  
          inet addr:74.1.46.168  Bcast:74.1.46.175  Mask:255.255.255.240
          BROADCAST MULTICAST  MTU:1500  Metric:1
          Interrupt:248 Base address:0x2000 

eth1:3    Link encap:Ethernet  HWaddr 00:e0:81:72:ed:a5  
          inet addr:74.1.46.169  Bcast:74.1.46.175  Mask:255.255.255.240
          BROADCAST MULTICAST  MTU:1500  Metric:1
          Interrupt:248 Base address:0x2000 

eth1:4    Link encap:Ethernet  HWaddr 00:e0:81:72:ed:a5  
          inet addr:74.1.46.174  Bcast:74.1.46.175  Mask:255.255.255.240
          BROADCAST MULTICAST  MTU:1500  Metric:1
          Interrupt:248 Base address:0x2000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:2626 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2626 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:1315445 (1.3 MB)  TX bytes:1315445 (1.3 MB)
```

**Here's 'netstat -rn'**:

```
Kernel IP routing table
Destination     Gateway         Genmask         Flags   MSS Window  irtt Iface
74.1.46.160     0.0.0.0         255.255.255.240 U         0 0          0 eth0
169.254.0.0     0.0.0.0         255.255.0.0     U         0 0          0 eth0
0.0.0.0         74.1.46.161     0.0.0.0         UG        0 0          0 eth0
```

**Here's /etc/resolv.conf**:

```
domain cocoanet.us
nameserver 64.105.179.138
nameserver 64.105.189.26
nameserver localhost
search cocoanet.us
```
[B]
Here's 'netstat -tapn'[/B]: 

[COLOR="DarkRed"]BTW, what's npviewer.bin??? I don't remember that being here!!!![/COLOR]

```

Active Internet connections (servers and established)
Proto Recv-Q Send-Q Local Address           Foreign Address         State       PID/Program name
tcp        0      0 0.0.0.0:902             0.0.0.0:*               LISTEN      7254/xinetd     
tcp        0      0 127.0.0.1:3306          0.0.0.0:*               LISTEN      6918/mysqld     
tcp        0      0 0.0.0.0:80              0.0.0.0:*               LISTEN      10217/apache2   
tcp        0      0 0.0.0.0:81              0.0.0.0:*               LISTEN      10173/ispconfig_htt
tcp        0      0 74.1.46.174:53          0.0.0.0:*               LISTEN      10353/named     
tcp        0      0 74.1.46.169:53          0.0.0.0:*               LISTEN      10353/named     
tcp        0      0 74.1.46.168:53          0.0.0.0:*               LISTEN      10353/named     
tcp        0      0 74.1.46.167:53          0.0.0.0:*               LISTEN      10353/named     
tcp        0      0 74.1.46.166:53          0.0.0.0:*               LISTEN      10353/named     
tcp        0      0 74.1.46.165:53          0.0.0.0:*               LISTEN      10353/named     
tcp        0      0 74.1.46.164:53          0.0.0.0:*               LISTEN      10353/named     
tcp        0      0 74.1.46.163:53          0.0.0.0:*               LISTEN      10353/named     
tcp        0      0 74.1.46.162:53          0.0.0.0:*               LISTEN      10353/named     
tcp        0      0 127.0.0.1:53            0.0.0.0:*               LISTEN      10353/named     
tcp        0      0 127.0.0.1:631           0.0.0.0:*               LISTEN      6685/cupsd      
tcp        0      0 127.0.0.1:5432          0.0.0.0:*               LISTEN      7096/postmaster 
tcp        0      0 127.0.0.1:953           0.0.0.0:*               LISTEN      10353/named     
tcp        0      0 0.0.0.0:25              0.0.0.0:*               LISTEN      10311/master    
tcp        0      0 0.0.0.0:443             0.0.0.0:*               LISTEN      10217/apache2   
tcp        0      0 74.1.46.162:59997       199.0.166.79:80         TIME_WAIT   -               
tcp        1      0 74.1.46.162:36437       91.189.94.12:80         CLOSE_WAIT  10657/npviewer.bin
tcp        1      0 74.1.46.162:38757       85.10.226.202:80        CLOSE_WAIT  10657/npviewer.bin
tcp        1      0 74.1.46.162:46843       66.114.53.13:80         CLOSE_WAIT  10657/npviewer.bin
tcp        0      0 74.1.46.162:37550       68.142.205.139:80       CLOSE_WAIT  10657/npviewer.bin
tcp        1      0 74.1.46.162:50048       205.234.175.175:80      CLOSE_WAIT  10657/npviewer.bin
tcp        1      0 74.1.46.162:46841       66.114.53.13:80         CLOSE_WAIT  10657/npviewer.bin
tcp        1      0 74.1.46.162:46844       66.114.53.13:80         CLOSE_WAIT  10657/npviewer.bin
tcp        1      0 74.1.46.162:38686       85.10.226.202:80        CLOSE_WAIT  10657/npviewer.bin
tcp        0      0 74.1.46.162:43569       78.47.159.34:80         CLOSE_WAIT  10657/npviewer.bin
tcp        0      0 74.1.46.162:37549       68.142.205.139:80       CLOSE_WAIT  10657/npviewer.bin
tcp        0      0 74.1.46.162:43570       78.47.159.34:80         CLOSE_WAIT  10657/npviewer.bin
tcp        1      0 74.1.46.162:38756       85.10.226.202:80        CLOSE_WAIT  10657/npviewer.bin
tcp        1      0 74.1.46.162:38755       85.10.226.202:80        CLOSE_WAIT  10657/npviewer.bin
tcp        1      0 74.1.46.162:38758       85.10.226.202:80        CLOSE_WAIT  10657/npviewer.bin
tcp        1      0 74.1.46.162:34457       74.125.67.167:80        CLOSE_WAIT  10657/npviewer.bin
tcp        1      0 74.1.46.162:42227       74.53.45.248:80         CLOSE_WAIT  10657/npviewer.bin
tcp        1      0 74.1.46.162:42157       74.53.45.248:80         CLOSE_WAIT  10657/npviewer.bin
tcp        1      0 74.1.46.162:38759       85.10.226.202:80        CLOSE_WAIT  10657/npviewer.bin
tcp        0      0 74.1.46.163:80          66.249.71.40:56698      ESTABLISHED 16304/apache2   
tcp        1      0 74.1.46.162:46842       66.114.53.13:80         CLOSE_WAIT  10657/npviewer.bin
tcp        1      0 74.1.46.162:47650       97.74.64.45:80          CLOSE_WAIT  10657/npviewer.bin
tcp6       0      0 :::993                  :::*                    LISTEN      6561/couriertcpd
tcp6       0      0 :::995                  :::*                    LISTEN      6614/couriertcpd
tcp6       0      0 :::110                  :::*                    LISTEN      6587/couriertcpd
tcp6       0      0 :::143                  :::*                    LISTEN      6534/couriertcpd
tcp6       0      0 :::21                   :::*                    LISTEN      10403/proftpd: (acc
tcp6       0      0 :::25                   :::*                    LISTEN      10311/master    
tcp6       0      0 74.1.46.163:993         74.1.46.173:50743       ESTABLISHED 17122/couriertls
tcp6       0      0 74.1.46.163:993         74.1.46.173:37964       ESTABLISHED 14551/couriertls
tcp6       0      0 74.1.46.166:993         74.1.46.173:33602       ESTABLISHED 14546/couriertls
tcp6       0      0 74.1.46.163:993         74.1.46.173:37961       ESTABLISHED 14543/couriertls
tcp6       0      0 74.1.46.166:993         74.1.46.173:33600       ESTABLISHED 14542/couriertls
tcp6       0      0 74.1.46.163:993         74.1.46.173:37957       ESTABLISHED 14539/couriertls
tcp6       0      0 74.1.46.163:993         74.1.46.173:37963       ESTABLISHED 14547/couriertls
tcp6       0      0 74.1.46.163:993         74.1.46.173:59713       ESTABLISHED 17912/couriertls
tcp6       0      0 74.1.46.163:993         74.1.46.173:37233       ESTABLISHED 17575/couriertls
tcp6       0      0 74.1.46.163:993         74.1.46.173:46707       ESTABLISHED 17643/couriertls
tcp6       0      0 74.1.46.163:993         74.1.46.173:49567       ESTABLISHED 14894/couriertls
tcp6       0      0 74.1.46.163:993         74.1.46.173:37958       ESTABLISHED 14540/couriertls
tcp6       0      0 74.1.46.163:993         74.1.46.173:42939       ESTABLISHED 17440/couriertls
tcp6       0      0 74.1.46.166:993         74.1.46.173:33599       ESTABLISHED 14541/couriertls
```

Sorry for making this soooo lengthy, but I wanted to vent with the narrative above :)

Thanks, Dante

---

### Post by Iced on 2008-12-05
I might be having similar problems to you except my eth1 is fine and i have to [FONT="Courier New"]ifdown eth0; ifup eth0;[/FONT] for some reason.  My Q was posted [here]("http://ubuntuforums.org/showthread.php?t=1001511")

Any chance you have done some configuration of the [FONT="Courier New"]/etc/udev/rules.d/70-persistent-net.rules[/FONT] file?

---

### Post by DantePasquale on 2008-12-07
Hey Iced,

No, no configuration changes to anything. I compared the MAC addresses I had saved off before the upgrade and they map to eth0 and eth1 correctly.

Oddly with this 2.6 kernel in RH5u2 on our HP Blade Servers we're seeing similar problems. Mostly with eth0 and eth1 being reversed on different blades even though they are presented to each blade in exactly the same way. Makes me think that udev in 2.6 kernel is having issues, but I can't pin it down to anything in particular yet.

---

