---
title: "Newbie needing help: Wireless not working on VMware/Ubuntu 7.10"
date: 2008-03-01
forum: Networking &amp; Wireless
---

### Post by PS8 on 2008-03-01
I am running Ubuntu 7.10 (Gutsy) under VMware 6.0.2 with my original OS being XP pro. While I am able to surf using firefox within Ubuntu (using my computer's wired connection – NAT option within VMware). However, when trying to connect to my wireless connection it doesn't seem to be working. 

While surfing through the forums I saw experts asking several questions about things so here some of the primary information. 

Base OS: XP Pro
Ubuntu: 7.10 (Gutsy)
Wireless chipset: Intel pro/wireless 3945 ABG
Driver version: 10.5.1.75 (it was much higher before but in one of the forums they had suggested to bring it down to this one so I did). 

Following information is seen when running the below mentioned commands. 
iwconfig 
lo        no wireless extensions.



eth0      no wireless extensions.



ifconfig
eth0      Link encap:Ethernet  HWaddr 00:0C:29:8D:28:D8  

          inet addr:192.168.88.128  Bcast:192.168.88.255  Mask:255.255.255.0

          inet6 addr: fe80::20c:29ff:fe8d:28d8/64 Scope:Link

          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1

          RX packets:561 errors:0 dropped:0 overruns:0 frame:0

          TX packets:229 errors:0 dropped:0 overruns:0 carrier:0

          collisions:0 txqueuelen:1000 

          RX bytes:56263 (54.9 KB)  TX bytes:38339 (37.4 KB)

          Interrupt:16 Base address:0x2000 



lo        Link encap:Local Loopback  

          inet addr:127.0.0.1  Mask:255.0.0.0

          inet6 addr: ::1/128 Scope:Host

          UP LOOPBACK RUNNING  MTU:16436  Metric:1

          RX packets:0 errors:0 dropped:0 overruns:0 frame:0

          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0

          collisions:0 txqueuelen:0 

          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)


lshw -C network
*-network               

       description: Ethernet interface

       product: 79c970 [PCnet32 LANCE]

       vendor: Advanced Micro Devices [AMD]

       physical id: 0

       bus info: pci@0000:02:00.0

       logical name: eth0

       version: 10

       serial: 00:0c:29:8d:28:d8

       width: 32 bits

       clock: 33MHz

       capabilities: bus_master ethernet physical logical

       configuration: broadcast=yes driver=pcnet32 driverversion=1.33 ip=192.168.88.128 latency=64 maxlatency=255 mingnt=6 module=pcnet32 multicast=yes


I am not sure what the problem is and being an absolute newbie will appreciate any help in terms of how to get my wireless connected.

---

### Post by Liken on 2008-03-02
Vmware with wireless bridge and kernel 2.6.24

[http://liken.otsoa.net/blog/index.php?entry=entry080301-173023](http://liken.otsoa.net/blog/index.php?entry=entry080301-173023)

---

### Post by PS8 on 2008-03-02
I have applied Hauke's patch ([http://www.hauke-m.de/fileadmin/vmware/](http://www.hauke-m.de/fileadmin/vmware/)) however it being VMware ACE edition I am working on the file is called VMXNET.tar instead of VMNET.tar. 

I did rename the file however it still didn't work. 

I have tried this patch also and it has the same problem. 

Thanks again for helping out. Any solution for ACE edition?

---

