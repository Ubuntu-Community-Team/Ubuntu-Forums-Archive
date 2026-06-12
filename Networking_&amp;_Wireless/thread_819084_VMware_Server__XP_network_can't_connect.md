---
title: "VMware Server:  XP network can't connect"
date: 2008-06-05
forum: Networking &amp; Wireless
---

### Post by Blind Tiger on 2008-06-05
I am running Ubuntu 7.10 as a guest OS for a virtual XP Pro machine on VMware Server 1.0.5.  The install went fine, yet I cannot connect to the internet.  

[LIST]
[*]I am using bridged networking.
[*]I have disabled the XP firewall.
[*]I have allowed network sharing on the host OS (Gutsy) using Firestarter.
[*]My network is wired cable modem on device etho.
[/LIST]

I have read multiple threads but have not found a solution.  Any tips would be greatly appreciated.

---

### Post by superprash2003 on 2008-06-05
please post ifconfig output from the terminal in your ubuntu machine

---

### Post by Blind Tiger on 2008-06-05
Thank you for the response.  I am currently at work but will post the output from ifconfig upon my return home to my Ubuntu box.

---

### Post by Nikayah on 2008-06-05
I'm not the same person, but im having the same problem. Ive posted both ipconfig and ipconfig /all. I've tried both bridged and NAT but to no avail. I installed the VMWare tools.
```
C:\Documents and Settings\USER>ipconfig

Windows IP Configuration


Ethernet adapter Local Area Connection:

        Connection-specific DNS Suffix  . :
        Autoconfiguration IP Address. . . : 169.254.94.39
        Subnet Mask . . . . . . . . . . . : 255.255.0.0
        Default Gateway . . . . . . . . . :

C:\Documents and Settings\USER>ipconfig /all

Windows IP Configuration

        Host Name . . . . . . . . . . . . : xp-1
        Primary Dns Suffix  . . . . . . . :
        Node Type . . . . . . . . . . . . : Unknown
        IP Routing Enabled. . . . . . . . : No
        WINS Proxy Enabled. . . . . . . . : No

Ethernet adapter Local Area Connection:

        Connection-specific DNS Suffix  . :
        Description . . . . . . . . . . . : VMware Accelerated AMD PCNet Adapter

        Physical Address. . . . . . . . . : 00-0C-29-2A-CE-16
        Dhcp Enabled. . . . . . . . . . . : Yes
        Autoconfiguration Enabled . . . . : Yes
        Autoconfiguration IP Address. . . : 169.254.94.39
        Subnet Mask . . . . . . . . . . . : 255.255.0.0
        Default Gateway . . . . . . . . . :
```

---

### Post by superprash2003 on 2008-06-05
@nikayah
   is windows xp your Guest OS? are you trying to run windows xp under ubuntu or vice versa?

---

### Post by SuzuZaku on 2008-06-05
I'm having a similar problem, only mine is because my vmnet files do not exist, how do I make them?

---

### Post by Blind Tiger on 2008-06-06
@ Superprash:
from Ubuntu terminal:
> ~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:13:D3:A6:D6:8B  
          inet addr:76.105.183.226  Bcast:255.255.255.255  Mask:255.255.248.0
          inet6 addr: fe80::213:d3ff:fea6:d68b/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:2618843 errors:0 dropped:0 overruns:0 frame:0
          TX packets:122857 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:279653842 (266.6 MB)  TX bytes:18868552 (17.9 MB)
          Interrupt:17 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:89 errors:0 dropped:0 overruns:0 frame:0
          TX packets:89 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:6262 (6.1 KB)  TX bytes:6262 (6.1 KB)

vmnet1    Link encap:Ethernet  HWaddr 00:50:56:C0:00:01  
          inet addr:192.168.33.1  Bcast:192.168.33.255  Mask:255.255.255.0
          inet6 addr: fe80::250:56ff:fec0:1/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:259 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

vmnet8    Link encap:Ethernet  HWaddr 00:50:56:C0:00:08  
          inet addr:172.16.27.1  Bcast:172.16.27.255  Mask:255.255.255.0
          inet6 addr: fe80::250:56ff:fec0:8/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:4 errors:0 dropped:0 overruns:0 frame:0
          TX packets:260 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

wlan0     Link encap:Ethernet  HWaddr 00:19:DB:0B:24:5F  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

wmaster0  Link encap:UNSPEC  HWaddr 00-19-DB-0B-24-5F-00-00-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

---

### Post by superprash2003 on 2008-06-06
this looks good.. you are getting an ip.. have you manually typed those ips? is vmnet8 or vmnet1 the xp machine? could you go to the xp machine and type ipconfig in the command prompt and post a screenshot here?

---

### Post by Blind Tiger on 2008-06-06
I thought it looked good also, to the limited extent of my knowledge.  The results were derived from DHCP settings.  I am not sure which vmnet adapter is my XP machine.  I have run ipconfig from command prompt in XP and noticed that only ip address and subnet mask had values.  I will post a screenshot later tonight.  Thanks.

---

### Post by Nikayah on 2008-06-06
XX I am running XP as my guest operating system, my host is ubuntu, and if i haven't said it already I'm running on an x64 computer.XX

NEVRMIND I fixed it!!

---

### Post by Blind Tiger on 2008-06-06
Nikayah -- what was your solution?

---

### Post by Blind Tiger on 2008-06-06
Superprash -- I took a look at my XP machine settings and discovered that my ethernet device was /dev/vmnet0.  I then added an ethernet adapter for both vmnet1 and vmnet8 through the custom option in 'add new device' of 'edit machine settings.'  I created a successful network connection using vmnet8.  Thanks for prompting me to post the output of ifconfig -- it spawned the solution to my network issue.  vmnet8 is the virtual adapter used with NAT -- this is the only way I can establish a functional network on the XP guest.

---

