---
title: "Internet connetion"
date: 2009-04-25
forum: New to Ubuntu
---

### Post by johanbo80 on 2009-04-25
Hi,

I installed Ubuntu 9.04 with triple boot yesterday,  Windows xp, windows 7 and Ubuntu. I had some trouble to install the triple boot but finally it is up working.

Yesterday everything in Ubuntu 9.04 worked accurately. Today however the internet connection is lost. When I try the ping control, I get a message that the internet connection cannot be found, either I am not connected or the OS cannot find the server DSN.

I did not change anything in the OS since yesterday. The windows internet connection is working normally.

What is this problem and how can it be solved? I am new to Linux and will appeciate very much any help to solve this problem in terms that can be easily understood by a beginner. I am eager to start to use the Ubuntu 9.04 OS but to do that I need the Internet connection. I am surprised that I should have this Internet connection with Ubuntu when my Internet connection with windows just works fine.

Best wishes from France

Johanbo80

---

### Post by cariboo on 2009-04-25
We need a little more information. Could you open an Applications-->Accessories-->Terminaland type:

```
sudo lshw -C network
```

the above command will ask for your password, it will not be echoed back when you enter it. Please paste the output in your next post using the [noparse]```

```[/noparse] tags.

---

### Post by johanbo80 on 2009-04-25
> **cariboo907 said:**
> We need a little more information. Could you open an Applications-->Accessories-->Terminaland type:

```
sudo lshw -C network
```

the above command will ask for your password, it will not be echoed back when you enter it. Please paste the output in your next post using the [noparse]```

```[/noparse] tags.
Thanks for your answer The answer of the command you gave me is as follows:

" *-network               
       description: Ethernet interface
       product: 88E8056 PCI-E Gigabit Ethernet Controller
       vendor: Marvell Technology Group Ltd.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: 12
       serial: 00:1e:8c:c8:a1:96
       size: 100MB/s
       capacity: 1GB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm vpd msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=sky2 driverversion=1.22 duplex=full firmware=N/A latency=0 link=yes module=sky2 multicast=yes port=twisted pair speed=100MB/s
  *-network:0
       description: Wireless interface
       physical id: 1
       logical name: wlan0
       serial: 00:15:af:64:d0:bc
       capabilities: ethernet physical wireless
       configuration: broadcast=yes multicast=yes wireless=IEEE 802.11bg
  *-network:1 DISABLED
       description: Ethernet interface
       physical id: 2
       logical name: pan0
       serial: 4e:24:b7:d1:5f:94
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes"

If it is useful to you, I also give you the outcome of the ifcommand in windows and Ubuntu.

Windows:

"Windows IP Configuration

        Host Name . . . . . . . . . . . . : bo-arent
        Primary Dns Suffix  . . . . . . . :
        Node Type . . . . . . . . . . . . : Unknown
        IP Routing Enabled. . . . . . . . : No
        WINS Proxy Enabled. . . . . . . . : No
        DNS Suffix Search List. . . . . . : home

Ethernet adapter Local Area Connection:

        Connection-specific DNS Suffix  . : home
        Description . . . . . . . . . . . : Marvell Yukon 88E8056 PCI-E Gigabit
Ethernet Controller
        Physical Address. . . . . . . . . : 00-1E-8C-C8-A1-96
        Dhcp Enabled. . . . . . . . . . . : Yes
        Autoconfiguration Enabled . . . . : Yes
        IP Address. . . . . . . . . . . . : 192.168.1.11
        Subnet Mask . . . . . . . . . . . : 255.255.255.0
        Default Gateway . . . . . . . . . : 192.168.1.1
        DHCP Server . . . . . . . . . . . : 192.168.1.1
        DNS Servers . . . . . . . . . . . : 192.168.1.1
        Lease Obtained. . . . . . . . . . : dimanche 26 avril 2009 00:06:51
        Lease Expires . . . . . . . . . . : lundi 27 avril 2009 00:06:51"

Ubuntu:
eth0      Link encap:Ethernet  HWaddr 00:1e:8c:c8:a1:96  
          inet6 addr: fe80::21e:8cff:fec8:a196/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:66 errors:0 dropped:0 overruns:0 frame:0
          TX packets:22 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:10150 (10.1 KB)  TX bytes:5940 (5.9 KB)
          Interrupt:17"

I really do hope that this information will allow you to help me solve my Internet connexion problem with Ubuntu.

Many thanks for your kind assistance.

Johanbo80 

"

---

