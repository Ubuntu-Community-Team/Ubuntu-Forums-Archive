---
title: "question about windows to linux internet sharing"
date: 2007-03-29
forum: Networking &amp; Wireless
---

### Post by kaos_frack on 2007-03-29
i have a pc running windows xp connected to the internet (through dialup)
i also have laptop running ubuntu
i need to connect those two computers through lan cable and be able to use internet from ubuntu?
how can i accomplish that?
what setting should i set on two computers?
i'm new to this, so can you please explain like to noob...
thanks

---

### Post by denver on 2007-03-29
If you dont have a router to do all the Routing for you, and you wish to use your XP machine as a gateway there are a few steps you need to take:
1. make sure the 2 computers are networked with one another
2. run network setup wizzard on your windows machine and follow the steps presented to you by the wizzard ( dont forget to specify that "This computer connects directly to the internet" )
At this point your PC network card should be configured to have the IP address 192.168.0.1 and your laptop and PC are linked through a network cable.
3. Boot up your laptop in Ubuntu and enjoy your internet connection. If Ubuntu doesent receave an IP address via DHCP from your XP machine, then go to System-->Administration-->Networking. Click on your network card and then Propreties. The values should be set to:

Configuration: Static
IP address: 192.168.0.2
Netmask: 255.255.255.0
Gateway: 192.168.0.1


Hope this helps. Good luck!

---

### Post by kaos_frack on 2007-03-29
it's not working...
i tried both automatic dhcp configuration and static configuration
what might be the problem? is there anything that might be conflicting, blocking or whatever?

---

### Post by denver on 2007-03-29
on the windows machine try the following in a cmd prompt ( start-->run-->cmd :

```
ipconfig /all
```
and paste it here. In ubuntu type the following in a terminal

```
ifconfig
```

and paste the results here.

---

### Post by kaos_frack on 2007-03-29
i noticed that after i entered the ip address 192.168.0.1 in windows machine the status of the lan connection shows text: "Invalid ip address'
is this because i use dial-up and get ip address assigned?

"ipconfig /all" results:
```

Windows IP Configuration

        Host Name . . . . . . . . . . . . : Khakimov
        Primary Dns Suffix  . . . . . . . :
        Node Type . . . . . . . . . . . . : Unknown
        IP Routing Enabled. . . . . . . . : Yes
        WINS Proxy Enabled. . . . . . . . : No
        DNS Suffix Search List. . . . . . : eng.buffalo.edu
                                            buffalo.edu
                                            cit.buffalo.edu

Ethernet adapter Local Area Connection:

        Connection-specific DNS Suffix  . : eng.buffalo.edu
        Description . . . . . . . . . . . : Intel(R) PRO/1000 MT Mobile Connection
        Physical Address. . . . . . . . . : 00-0D-60-CE-EF-01
        Dhcp Enabled. . . . . . . . . . . : No
        IP Address. . . . . . . . . . . . : 0.0.0.0
        Subnet Mask . . . . . . . . . . . : 0.0.0.0
        Default Gateway . . . . . . . . . :

PPP adapter TPS:

        Connection-specific DNS Suffix  . :
        Description . . . . . . . . . . . : WAN (PPP/SLIP) Interface
        Physical Address. . . . . . . . . : 00-53-45-00-00-00
        Dhcp Enabled. . . . . . . . . . . : No
        IP Address. . . . . . . . . . . . : 80.80.210.199
        Subnet Mask . . . . . . . . . . . : 255.255.255.255
        Default Gateway . . . . . . . . . : 80.80.210.199
        DNS Servers . . . . . . . . . . . : 80.80.208.1
                                            80.80.209.1
        NetBIOS over Tcpip. . . . . . . . : Disabled

```

"ifconfig" results:
```

root@jzk:~# ifconfig
eth0      Link encap:Ethernet  HWaddr 00:C0:9F:76:68:15  
          inet addr:192.168.0.2  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::2c0:9fff:fe76:6815/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:348 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:22788 (22.2 KiB)
          Interrupt:193 Base address:0xc800 

eth1      Link encap:Ethernet  HWaddr 00:0E:35:CF:E5:20  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:185 Base address:0xc000 Memory:e0206000-e0206fff 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:122 errors:0 dropped:0 overruns:0 frame:0
          TX packets:122 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:11312 (11.0 KiB)  TX bytes:11312 (11.0 KiB)


```

note: "TPS" is the name of the dial up connection

---

### Post by kaos_frack on 2007-03-29
maybe i should've set up lan first (setting up the ip address) and then connect to internet???

---

### Post by chewearn on 2007-03-29
On the network icon for your dial up, is there is "sharing" indicator (hand palm facing up)?

If not, select both the icon for your dial up and LAN at the same time, right-click, and select "Bridge connection".

---

### Post by kaos_frack on 2007-03-30
IT WORKED!
> 
select both the icon for your dial up and LAN at the same time, right-click, and select "Bridge connection".

Yeah, that did the trick!

Thanks a lot denver and AstalaVista!

---

