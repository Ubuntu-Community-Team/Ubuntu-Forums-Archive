---
title: "Span ports un Ubuntu 20.04 server"
date: 2022-05-04
forum: Networking &amp; Wireless
---

### Post by Mski35 on 2022-05-04
I recently stood up an Ubuntu Server 20.04.4 on an HP DL360 with multiple interfaces and installed KVM hypervisor currently running 5 lab machines.  I updated the 00-installer-config.yaml and added a bridge network so I can access my VMs from my home network and updated the VMs to use the bridge network.  


I want to start testing Zeek however it requires a span port to collect all LAN traffic for analysis.  Since I don't have a switch in my home network, I've been searching for a way to create a span port using netplan but have come up empty so far.   


Can someone shed some light if this can be accomplished? 


Thank you so much for your input!!

---

### Post by TheFu on 2022-05-04
Most home switches will prevent this. In the olden days, we'd use hubs because switches were too expensive. Switches only send traffic down a wire based on the MAC they've seen there already. They don't broadcast everything down all ports.

Someone else with more network knowledge will need to explain in more details, if that is necessary.

---

### Post by Mski35 on 2022-05-05
Thanks for the response @TheFu.  I was looking/hoping for a way to mirror traffic on my KVM bridge interface to capture all LAN traffic for analysis without the use of additional hardware.

I just found Open vSwitch for KVM and just started reading up on it to see if it can do what I'm attempting.

---

### Post by TheFu on 2022-05-05
Typically, openVswitch is used for 10Gbps connections.  It isn't worth the hassle for 1 Gbps, but I don't know if it will replicate a port.

Most people use promiscuous mode with their NICs to capture packets for analysis.  Hopefully, that won't work from a VM, but from the host, it should.  If a VM can capture packets that aren't exclusive to the VM, that's a pretty large security bug.

---

### Post by Doug S on 2022-05-06
Perhaps I misunderstand the requirement. I can observe all my VM traffic on my host bridge, br0. I started 3 VMs for this test:

```
doug@s19:~$ ip addr
1: lo: <LOOPBACK,UP,LOWER_UP> mtu 65536 qdisc noqueue state UNKNOWN group default qlen 1000
    link/loopback 00:00:00:00:00:00 brd 00:00:00:00:00:00
    inet 127.0.0.1/8 scope host lo
       valid_lft forever preferred_lft forever
2: enp3s0: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc mq master br0 state UP group default qlen 1000
    link/ether 3c:7c:3f:0d:99:83 brd ff:ff:ff:ff:ff:ff
3: br0: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc noqueue state UP group default qlen 1000
    link/ether 3c:7c:3f:0d:99:83 brd ff:ff:ff:ff:ff:ff
    inet 192.168.111.136/24 brd 192.168.111.255 scope global dynamic br0
       valid_lft 77285sec preferred_lft 77285sec
4: vnet0: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc fq_codel master br0 state UNKNOWN group default qlen 1000
    link/ether fe:54:00:22:2f:dc brd ff:ff:ff:ff:ff:ff
5: vnet1: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc fq_codel master br0 state UNKNOWN group default qlen 1000
    link/ether fe:54:00:60:ea:3e brd ff:ff:ff:ff:ff:ff
6: vnet2: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc fq_codel master br0 state UNKNOWN group default qlen 1000
    link/ether fe:54:00:60:ea:5e brd ff:ff:ff:ff:ff:ff
```

And started a ping on each to my gateway, then asked tcpdump to monitor br0. VMs at 192.168.111.18, 19 ,20:

```
doug@s19:~$ sudo tcpdump -tttt -n -i br0 icmp
tcpdump: verbose output suppressed, use -v or -vv for full protocol decode
listening on br0, link-type EN10MB (Ethernet), capture size 262144 bytes
2022-05-06 07:56:27.995956 IP 192.168.111.19 > 192.168.111.1: ICMP echo request, id 1, seq 367, length 64
2022-05-06 07:56:27.996175 IP 192.168.111.1 > 192.168.111.19: ICMP echo reply, id 1, seq 367, length 64
2022-05-06 07:56:28.266962 IP 192.168.111.18 > 192.168.111.1: ICMP echo request, id 2, seq 448, length 64
2022-05-06 07:56:28.267164 IP 192.168.111.1 > 192.168.111.18: ICMP echo reply, id 2, seq 448, length 64
2022-05-06 07:56:28.587859 IP 192.168.111.20 > 192.168.111.1: ICMP echo request, id 1, seq 412, length 64
2022-05-06 07:56:28.588105 IP 192.168.111.1 > 192.168.111.20: ICMP echo reply, id 1, seq 412, length 64
2022-05-06 07:56:29.011318 IP 192.168.111.19 > 192.168.111.1: ICMP echo request, id 1, seq 368, length 64
2022-05-06 07:56:29.011559 IP 192.168.111.1 > 192.168.111.19: ICMP echo reply, id 1, seq 368, length 64
2022-05-06 07:56:29.291011 IP 192.168.111.18 > 192.168.111.1: ICMP echo request, id 2, seq 449, length 64
2022-05-06 07:56:29.291214 IP 192.168.111.1 > 192.168.111.18: ICMP echo reply, id 2, seq 449, length 64
2022-05-06 07:56:29.589217 IP 192.168.111.20 > 192.168.111.1: ICMP echo request, id 1, seq 413, length 64
2022-05-06 07:56:29.589439 IP 192.168.111.1 > 192.168.111.20: ICMP echo reply, id 1, seq 413, length 64
2022-05-06 07:56:30.035325 IP 192.168.111.19 > 192.168.111.1: ICMP echo request, id 1, seq 369, length 64
2022-05-06 07:56:30.035548 IP 192.168.111.1 > 192.168.111.19: ICMP echo reply, id 1, seq 369, length 64
2022-05-06 07:56:30.315043 IP 192.168.111.18 > 192.168.111.1: ICMP echo request, id 2, seq 450, length 64
2022-05-06 07:56:30.315338 IP 192.168.111.1 > 192.168.111.18: ICMP echo reply, id 2, seq 450, length 64
```

I limited it to icmp for this just to simplify due to other traffic and to prevent a flood due to ssh to the host.

EDIT: Oh, maybe it is desired to capture communications between the VMs. I did a ping between them:
```
doug@s19:~$ sudo tcpdump -tttt -n -i br0 icmp
tcpdump: verbose output suppressed, use -v or -vv for full protocol decode
listening on br0, link-type EN10MB (Ethernet), capture size 262144 bytes
2022-05-06 08:36:41.371182 IP 192.168.111.19 > 192.168.111.20: ICMP echo request, id 1, seq 14, length 64
2022-05-06 08:36:41.371316 IP 192.168.111.20 > 192.168.111.19: ICMP echo reply, id 1, seq 14, length 64
2022-05-06 08:36:42.395123 IP 192.168.111.19 > 192.168.111.20: ICMP echo request, id 1, seq 15, length 64
2022-05-06 08:36:42.395309 IP 192.168.111.20 > 192.168.111.19: ICMP echo reply, id 1, seq 15, length 64
2022-05-06 08:36:43.419125 IP 192.168.111.19 > 192.168.111.20: ICMP echo request, id 1, seq 16, length 64
2022-05-06 08:36:43.419386 IP 192.168.111.20 > 192.168.111.19: ICMP echo reply, id 1, seq 16, length 64
```

---

### Post by TheFu on 2022-05-06
Great example.

This is why people use PCI passthru for NICs with exclusive use to the VM for internet-facing VMs.

You've just demonstrated the flaw in using a bridge where we wouldn't want to use a hub on a physical network for security reasons. A real switch with computers connected to different switch ports wouldn't let either system see the other systems' target packets.

---

### Post by #&amp;thj^% on 2022-05-06
> **TheFu said:**
> Great example.
 A real switch with computers connected to different switch ports wouldn't let either system see the other systems' target packets.

Absolutely. I'm glad you_ push_ this practice.
I get tired of it, you seem to word it better, I'm just to mater of fact in my old age i guess.

---

### Post by Doug S on 2022-05-08
Hi TheFu and 1fallen,

Thank you for voicing your security concerns.
Just for the record, my application is not internet facing. My example was done on my 20.04 Ubuntu test server host. I assume, but do not know for certain, that the OPs "Lab environment" is similarly isolated.

---

### Post by TheFu on 2022-05-08
> **Doug S said:**
> Hi TheFu and 1fallen,

Thank you for voicing your security concerns.
Just for the record, my application is not internet facing. My example was done on my 20.04 Ubuntu test server host. I assume, but do not know for certain, that the OPs "Lab environment" is similarly isolated.

We never know until it is stated and in 2+ yrs a lurker might find this thread and miss that aspect.  


I figured your setup and probably 90% for the OP that these were on firewalled, LAN segments, not near the internet.

---

### Post by #&amp;thj^% on 2022-05-08
> **Doug S said:**
> Hi TheFu and 1fallen,

Thank you for voicing your security concerns.

Gosh I hope I haven't offended you, wasn't meant that way.
Doug I really never worry over your security practices, you've proven yourself wise enough.
I need to modify my reactions or feelings a tad.
It's just been my experience measured in years that  TheFu is a great security asset to this forum.
Best Regards

---

### Post by Mski35 on 2022-05-11
Hi Doug, 
This is great information, thank you for the details.  

I agree and can see the traffic the br0 network.  I know from a switch perspective, I have configured a SPAN port to mirror traffic from LAN interfaces on a switch to the SPAN port which mirrors the traffic on the designated ports in the past and is necessary when monitoring netflow traffic of configuring an IDS for analysis. 

[https://support.riverbed.com/bin/support/static/tku8mot0iaoa67qben06tukj4h/html/afhi95mcqoa01gcejeafeknach/sc_may2016_dg_html/index.html#page/NPM%20Deployment%20Guide/packet_collection.06.3.html](https://support.riverbed.com/bin/support/static/tku8mot0iaoa67qben06tukj4h/html/afhi95mcqoa01gcejeafeknach/sc_may2016_dg_html/index.html#page/NPM%20Deployment%20Guide/packet_collection.06.3.html)

Thanks everyone for your feedback!

---

### Post by TheFu on 2022-05-11
Some people keep old "hubs" around just for this purpose.  Some ITSEC online shops sell 4-port "star" hubs too.  I know a friend used to at AceHackware, but he sold his business a few years ago. I don't know who or if anyone owns it.  There have to be others selling that stuff.

---

