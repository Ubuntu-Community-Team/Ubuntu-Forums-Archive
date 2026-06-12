---
title: "cannot ping router if once boot WinXP"
date: 2007-11-12
forum: Networking &amp; Wireless
---

### Post by dingding on 2007-11-12
Sorry, repost in networking.

I'm new to Linux and have WinXP and Ubuntu 7.04 dual boot. A strange thing I've seen is that once I boot WinXP then reboot Linux, I can ping neither router nor any other machine. IP is correctly assigned by DHCP. If I power down the router and up again, the problem gone. Linux won't need any reboot or setup. Network manager just found the connection lost and then reconnected.
I can also get it recovered by shut down PC for about 24hours (never tried shorter time), then boot directly into Linux. I'm using D-Link DI-524 wireless router, has been reset to factory setting, without any firewall, IP filtering enabled. When the problem occurs, WinXP can always access network without any problem. The laptop is DELL-640m.
Thanks in advance.
Bin

---

### Post by noob12 on 2007-11-13
Sounds like some kind of ARP confusion perhaps.

You might get a clue by posting the output of 
```

ifconfig -a

```
when booted in Ubuntu

and also posting the output of
```

ipconfig /all

```
when booted in WinXP.

Are the mac addresses showing up the same?

---

### Post by SpiritIsReality on 2007-11-13
Howdy
I have a dlink DI-524 router and a dual boot xp , ubuntu 7.10 pc. All seems to be working well. Can we compare settings in xp, ubuntu, and router, to see if there are differences?
trails

---

### Post by dingding on 2007-11-14
Here's ipconfig outputs under WinXP.

Windows IP Configuration

        Host Name . . . . . . . . . . . . : twodogs
        Primary Dns Suffix  . . . . . . . :
        Node Type . . . . . . . . . . . . : Unknown
        IP Routing Enabled. . . . . . . . : No
        WINS Proxy Enabled. . . . . . . . : No
        DNS Suffix Search List. . . . . . : vc.shawcable.net

Ethernet adapter &#26412;&#22320;&#36830;&#25509;:

        Media State . . . . . . . . . . . : Media disconnected
        Description . . . . . . . . . . . : Broadcom 440x 10/100 Integrated Cont
roller
        Physical Address. . . . . . . . . : 00-15-C5-7C-13-16

Ethernet adapter &#26080;&#32447;&#32593;&#32476;&#36830;&#25509;:

        Connection-specific DNS Suffix  . : vc.shawcable.net
        Description . . . . . . . . . . . : Intel(R) PRO/Wireless 3945ABG Networ
k Connection
        Physical Address. . . . . . . . . : 00-1B-77-52-5F-B8
        Dhcp Enabled. . . . . . . . . . . : Yes
        Autoconfiguration Enabled . . . . : Yes
        IP Address. . . . . . . . . . . . : 192.168.0.101
        Subnet Mask . . . . . . . . . . . : 255.255.255.0
        Default Gateway . . . . . . . . . : 192.168.0.1
        DHCP Server . . . . . . . . . . . : 192.168.0.1
        DNS Servers . . . . . . . . . . . : 192.168.0.1
        Lease Obtained. . . . . . . . . . : 2007&#24180;11&#26376;13&#26085; 22:38:46
        Lease Expires . . . . . . . . . . : 2007&#24180;11&#26376;20&#26085; 22:38:46

---

### Post by dingding on 2007-11-14
Here's ifconfig output. Thanks!
eth0      Link encap:Ethernet  HWaddr 00:15:C5:7C:13:16  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:17 

eth1      Link encap:Ethernet  HWaddr 00:1B:77:52:5F:B8  
          inet addr:192.168.0.101  Bcast:192.168.0.255  Mask:255.255.255.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:29 errors:0 dropped:99 overruns:0 frame:0
          TX packets:47 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:11868 (11.5 KiB)  TX bytes:8796 (8.5 KiB)
          Interrupt:17 Base address:0xe000 Memory:efdff000-efdfffff 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:16 errors:0 dropped:0 overruns:0 frame:0
          TX packets:16 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:1416 (1.3 KiB)  TX bytes:1416 (1.3 KiB)

---

### Post by SpiritIsReality on 2007-11-14
fred@piii:~$ ifconfig -a
eth0      Link encap:Ethernet  HWaddr 00:01:02:28:E2:BA  
          inet addr:192.168.0.140  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::201:2ff:fe28:e2ba/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:44414 errors:0 dropped:0 overruns:0 frame:0
          TX packets:26474 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:45591776 (43.4 MB)  TX bytes:3183448 (3.0 MB)
          Interrupt:11 Base address:0x8000 

eth1      Link encap:Ethernet  HWaddr 00:40:F4:85:FF:65  
          inet addr:192.168.1.1  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::240:f4ff:fe85:ff65/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:639 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:128670 (125.6 KB)
          Interrupt:11 Base address:0xa000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:401 errors:0 dropped:0 overruns:0 frame:0
          TX packets:401 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:26697 (26.0 KB)  TX bytes:26697 (26.0 KB)

fred@piii:~$ route -n
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.1.0     0.0.0.0         255.255.255.0   U     0      0        0 eth1
192.168.0.0     0.0.0.0         255.255.255.0   U     0      0        0 eth0
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 eth1
0.0.0.0         192.168.0.1     0.0.0.0         UG    100    0        0 eth0
fred@piii:~$ lshw -C network
WARNING: you should run this program as super-user.
  *-network:0             
       description: Ethernet interface
       product: 3c450 HomePNA [Tornado]
       vendor: 3Com Corporation
       physical id: 8
       bus info: pci@0000:00:08.0
       logical name: eth0
       version: 30
       serial: 00:01:02:28:e2:ba
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=3c59x ip=192.168.0.140 latency=64 maxlatency=10 mingnt=10 module=3c59x multicast=yes
  *-network:1
       description: Ethernet interface
       product: RTL-8139/8139C/8139C+
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: a
       bus info: pci@0000:00:0a.0
       logical name: eth1
       version: 10
       serial: 00:40:f4:85:ff:65
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=8139too driverversion=0.9.28 ip=192.168.1.1 latency=64 maxlatency=64 mingnt=32 module=8139too multicast=yes
fred@piii:~$

---

### Post by SpiritIsReality on 2007-11-14
haha! Could you please tell me how to get ipconfig of xp to this post?
thankyou

[http://www.google.ca/search?hl=en&q=linux+network+troubleshooting+commands&btnG=Google+Search&meta=](http://www.google.ca/search?hl=en&q=linux+network+troubleshooting+commands&btnG=Google+Search&meta=)
[http://www.google.ca/search?hl=en&q=%22dual+boot+conflicts%22&btnG=Search&meta=](http://www.google.ca/search?hl=en&q=%22dual+boot+conflicts%22&btnG=Search&meta=)

---

### Post by noob12 on 2007-11-14
dingding: I thought you were referring to the wired card and not the wireless.  In your **ifconfig -a** output from Ubuntu.  It looks like you were receiving and transmitting packets.  Was this after a router reset or before?

I'm guessing the issue may be due to the router having earlier negotiated a different wireless session  key with your wireless device while booted in WinXP.  The apparent DHCP assignment may be due to an older lease being reused, and no actual interaction having taken place.

Depending on your revision of the DI-524, you may be able to see log activity on the web interface of the router that will confirm or contradict this hypothesis.

Also, some more questions.  Are you warm-booting across WinXP to Ubuntu or do you shutdown and power off between the reboot?  Do you have the same problems when using the wired connection in XP and then Ubuntu?  Do you have the same problem if you disable wireless encryption on the router?  (This is only to test; I'm not suggesting running that way.)

---

### Post by SpiritIsReality on 2007-11-14
> **noob12 said:**
> dingding: I thought you were referring to the wired card and not the wireless.  In your **ifconfig -a** output from Ubuntu.  It looks like you were receiving and transmitting packets.  Was this after a router reset or before?

I'm guessing the issue may be due to the router having earlier negotiated a different wireless session  key with your wireless device while booted in WinXP.  The apparent DHCP assignment may be due to an older lease being reused, and no actual interaction having taken place.

Depending on your revision of the DI-524, you may be able to see log activity on the web interface of the router that will confirm or contradict this hypothesis.

Also, some more questions.  Are you warm-booting across WinXP to Ubuntu or do you shutdown and power off between the reboot?  Do you have the same problems when using the wired connection in XP and then Ubuntu?  Do you have the same problem if you disable wireless encryption on the router?  (This is only to test; I'm not suggesting running that way.)
thanks. I admire your skill.

---

### Post by dingding on 2007-11-15
My ifconfig post was captured before reset router. I did see router log from another PC, the IP assignment seems real, because the time stamp is later than WinXP shut down.
Power off between reboot doesn't help. I remember I tried wired connection once when the problem occured, it didn't go through. 

arp give following output, I tried "sudo arp -s 192.168.0.1 00:13:46:BC:41:6E", but doesn't work.

Address                  HWtype  HWaddress           Flags Mask            Iface
192.168.0.1                      (incomplete)                              eth1

Thanks!

---

### Post by dingding on 2007-11-15
Tried "arping -I eth1192.168.0.1", seems the router stop response.

ARPING 192.168.0.1 from 192.168.0.101 eth1
Sent 4 probes (4 broadcast(s))
Received 0 response(s)

---

### Post by noob12 on 2007-11-15
Out of ideas here.

---

