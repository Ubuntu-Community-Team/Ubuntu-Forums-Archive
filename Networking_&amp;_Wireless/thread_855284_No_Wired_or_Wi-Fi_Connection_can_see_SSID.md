---
title: "No Wired or Wi-Fi Connection can see SSID"
date: 2008-07-10
forum: Networking &amp; Wireless
---

### Post by JamMasterJ on 2008-07-10
I have an Averatec laptop (cheap, but the most dependable pc I have ever seen). All devices function on the Windows partition so the device is functional. I can see the SSID in the network menu. I cannot connect while wired or to the visible SSID when attempting wireless. Here are some common outputs that I have seen requested in the hundreds of posts I have tried to follow (See Attachments).

[email]jammasterj01@gmail.com[/email]

---

### Post by superprash2003 on 2008-07-10
when connected via wired.. go to the terminal and type ifconfig and post output here

---

### Post by JamMasterJ on 2008-07-10
That report has now been added to the previous attachments. Thanks for your quick response in the issue.

---

### Post by JamMasterJ on 2008-07-10
[B]eth0      Link encap:Ethernet  HWaddr 00:40:45:19:C8:FC  

          inet6 addr: fe80::240:45ff:fe19:c8fc/64 Scope:Link

          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1

          RX packets:2 errors:0 dropped:1629 overruns:0 frame:0

          TX packets:0 errors:3 dropped:0 overruns:0 carrier:0

          collisions:0 txqueuelen:1000 

          RX bytes:303 (303.0 b)  TX bytes:0 (0.0 b)

          Interrupt:11 Base address:0xd800 



eth0:avah Link encap:Ethernet  HWaddr 00:40:45:19:C8:FC  

          inet addr:169.254.9.34  Bcast:169.254.255.255  Mask:255.255.0.0

          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1

          Interrupt:11 Base address:0xd800 



lo        Link encap:Local Loopback  

          inet addr:127.0.0.1  Mask:255.0.0.0

          inet6 addr: ::1/128 Scope:Host

          UP LOOPBACK RUNNING  MTU:16436  Metric:1

          RX packets:16 errors:0 dropped:0 overruns:0 frame:0

          TX packets:16 errors:0 dropped:0 overruns:0 carrier:0

          collisions:0 txqueuelen:0 

          RX bytes:1184 (1.1 KB)  TX bytes:1184 (1.1 KB)



wlan0     Link encap:Ethernet  HWaddr 00:11:09:09:1D:8B  

          UP BROADCAST MULTICAST  MTU:1500  Metric:1

          RX packets:0 errors:0 dropped:0 overruns:0 frame:0

          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0

          collisions:0 txqueuelen:1000 

          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)



wmaster0  Link encap:UNSPEC  HWaddr 00-11-09-09-1D-8B-00-00-00-00-00-00-00-00-00-00  

          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1

          RX packets:0 errors:0 dropped:0 overruns:0 frame:0

          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0

          collisions:0 txqueuelen:1000 

          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)[/B]

---

### Post by superprash2003 on 2008-07-10
go to system->admin->network and go to eth0 properties and set it to DHCP mode and then post ifconfig.. the problem is you arent getting an ip under eth0..

---

### Post by JamMasterJ on 2008-07-11
Here is the output you requested. I did enable DHCP in the network settings. It was using free roaming only until I did so. Now only DHCP under wired connections. By the way, I am on a college campus, I believe that the wired network may "know" the computers that are on the domain and those that are not (mine). But, the wireless is open to all. I also attached a dmesg | more output to see if maybe there is a driver not loading? I'm am new to Linux and am not sure of what I am looking for.

[B]
jeremie@jeremie-onthego:~$ ifconfig 
eth0      Link encap:Ethernet  HWaddr 00:40:45:19:C8:FC   
          inet addr:10.2.9.54  Bcast:10.2.9.255  Mask:255.255.255.0 
          inet6 addr: fe80::240:45ff:fe19:c8fc/64 Scope:Link 
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1 
          RX packets:23 errors:0 dropped:73 overruns:0 frame:0 
          TX packets:24 errors:9 dropped:0 overruns:0 carrier:0 
          collisions:0 txqueuelen:1000  
          RX bytes:2228 (2.1 KB)  TX bytes:3503 (3.4 KB) 
          Interrupt:11 Base address:0xd800  
 
lo        Link encap:Local Loopback   
          inet addr:127.0.0.1  Mask:255.0.0.0 
          inet6 addr: ::1/128 Scope:Host 
          UP LOOPBACK RUNNING  MTU:16436  Metric:1 
          RX packets:56 errors:0 dropped:0 overruns:0 frame:0 
          TX packets:56 errors:0 dropped:0 overruns:0 carrier:0 
          collisions:0 txqueuelen:0  
          RX bytes:5249 (5.1 KB)  TX bytes:5249 (5.1 KB) 
 
wlan0     Link encap:Ethernet  HWaddr 00:11:09:09:1D:8B   
          UP BROADCAST MULTICAST  MTU:1500  Metric:1 
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0 
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0 
          collisions:0 txqueuelen:1000  
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b) 
 
wmaster0  Link encap:UNSPEC  HWaddr 00-11-09-09-1D-8B-00-00-00-00-00-00-00-00-00-00   
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1 
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0 
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0 
          collisions:0 txqueuelen:1000  
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b) [/B]

---

### Post by JamMasterJ on 2008-07-11
Is there better support for network devices in 8.10? Would it benefit me to install the latest version.

---

### Post by superprash2003 on 2008-07-11
hey you seem to be connected,your eth0 is getting an ip.. in your terminal type ping google.com and post output here

---

### Post by JamMasterJ on 2008-07-12
Does not recognize the host [www.google.com](www.google.com)

---

### Post by superprash2003 on 2008-07-12
are you able to ping the router?

---

### Post by JamMasterJ on 2008-07-12
I have a Linksys Wireless-G that the wireless see's (but will not connect to), but here is the result from pinging it in terminal while wired to the NIC.

The IP from my Windows laptop is 192.168.1.122, the IP given to my Ubuntu laptop seems way off from what it should be don't you think?

Thanks again.

---

### Post by superprash2003 on 2008-07-12
ok.. when wired.. go to system->admin->network and then go to eth0 properties.. there select STATIC ip address.. then enter ip as 192.168.1.10 and gateway as 192.168.1.1 .. then try pinging 192.168.1.1

---

### Post by JamMasterJ on 2008-07-12
Im not sure if DHCP got taken off somehow (maybe after reboot)from when I ran the ping earlier, but when I went into network setting it was, I re-enabled it, and now it will not reach the host using ping 192.168.1.1 "Network is Unreachable"....

---

### Post by JamMasterJ on 2008-07-12
Here is the output from the static attempt.

The first two attempts were as I described earlier, DHCP had been taken away somehow...

---

### Post by superprash2003 on 2008-07-12
hmm.. try DHCP again.. since your windows is getting 192.168.1.122 .. it mostly is cause DHCP is enabled in your router.. so try with dhcp again.. and do an ifconfig and see if you are getting an ip of the form 192.168.1.x

---

### Post by JamMasterJ on 2008-07-13
It looks for the site for about 3-4 min. and then times out.

Here is the latest ifconfig:

[B]jeremie@jeremie-onthego:~$ ifconfig 
eth0      Link encap:Ethernet  HWaddr 00:40:45:19:C8:FC   
          inet addr:192.168.1.101  Bcast:192.168.1.255  Mask:255.255.255.0 
          inet6 addr: fe80::240:45ff:fe19:c8fc/64 Scope:Link 
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1 
          RX packets:5 errors:0 dropped:0 overruns:0 frame:0 
          TX packets:23 errors:3 dropped:0 overruns:0 carrier:0 
          collisions:0 txqueuelen:1000  
          RX bytes:1435 (1.4 KB)  TX bytes:3682 (3.5 KB) 
          Interrupt:11 Base address:0xd800  
 
lo        Link encap:Local Loopback   
          inet addr:127.0.0.1  Mask:255.0.0.0 
          inet6 addr: ::1/128 Scope:Host 
          UP LOOPBACK RUNNING  MTU:16436  Metric:1 
          RX packets:9 errors:0 dropped:0 overruns:0 frame:0 
          TX packets:9 errors:0 dropped:0 overruns:0 carrier:0 
          collisions:0 txqueuelen:0  
          RX bytes:876 (876.0 b)  TX bytes:876 (876.0 b) 
 
wlan0     Link encap:Ethernet  HWaddr 00:11:09:09:1D:8B   
          UP BROADCAST MULTICAST  MTU:1500  Metric:1 
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0 
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0 
          collisions:0 txqueuelen:1000  
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b) 
 
wmaster0  Link encap:UNSPEC  HWaddr 00-11-09-09-1D-8B-00-00-00-00-00-00-00-00-00-00   
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1 
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0 
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0 
          collisions:0 txqueuelen:1000  
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b) 
 
[/B]

---

### Post by superprash2003 on 2008-07-15
try pinging a site.. in the terminal type ping google.com and post results

---

