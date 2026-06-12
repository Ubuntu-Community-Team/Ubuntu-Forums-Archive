---
title: "Multiple NICs connected to multiple bridges."
date: 2018-02-25
forum: Networking &amp; Wireless
---

### Post by izznogooood on 2018-02-25
I have a server with 4 NICs and need 4 bridges. The bridges would look like this (2 in example):



```
auto lo
iface lo inet loopback


iface ens33 inet manual


iface ens36 inet manual


auto br0
iface br0 inet static
        address  10.0.1.10
        netmask  255.255.255.0
        gateway  10.0.1.1
        bridge_ports ens33
        bridge_stp off
        bridge_fd 0


auto br1
iface br1 inet static
        address  192.168.1.10
        netmask  255.255.255.0
        bridge_ports ens36
        bridge_stp off
        bridge_fd 0




```

How can I specify 2 gateways or add routes for 192.168.1.0/24 ?
Do I need to specify every possible route out from 192.168.1.0/24 or is adding one route to the first gateway enough?
And how do I add this gateways?

I know I can add a bridge without an IP and take care of the gateway manually in the container / VM but then i would not be able to connect to the host from that lan (If this is even possible...).

This is going to be a KVM/Docker/LXC server, if that was not clear ;).

---

### Post by QIII on 2018-02-25
Hello!

With the KVM VMs, you needn't worry about your /etc/network/interfaces too much.  Let VMM/QEMU/KVM worry about it.

If you assign a specific interface to a VM with KVM in bridged mode, the VM will "own" that interface.

On my VM server (with three VMs running at the moment), ifconfig looks like this 

(yes, there are 14 interfaces: two on the mobo and three 4-port NICs. I can run the host and 13 VMs with a Threadripper 1950x and 128GB of memory.  This is a machine I put together for my business.  Don't try this at home!  :) ):

```
enp10s0f0 Link encap:Ethernet  HWaddr 00:26:55:ea:a6:09  
          inet addr:192.168.1.49  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::f811:2dd8:7003:19a1/64 Scope:Link
          inet6 addr: 2601:1c0:4300:930:99b1:8214:a7ec:4ac3/64 Scope:Global
          inet6 addr: 2601:1c0:4300:930:ce85:b18e:96a0:f08a/64 Scope:Global
          inet6 addr: 2601:1c0:4300:930:38e5:ae2f:9753:e45f/64 Scope:Global
          inet6 addr: 2601:1c0:4300:930::11/128 Scope:Global
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:565343 errors:0 dropped:0 overruns:0 frame:0
          TX packets:31042 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:40978324 (40.9 MB)  TX bytes:3490008 (3.4 MB)
          Interrupt:62 Memory:ef720000-ef740000 

enp10s0f1 Link encap:Ethernet  HWaddr 00:26:55:ea:a6:08  
          inet addr:192.168.1.40  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: 2601:1c0:4300:930::f/128 Scope:Global
          inet6 addr: 2601:1c0:4300:930:2970:91ed:135e:b7f6/64 Scope:Global
          inet6 addr: 2601:1c0:4300:930:f7:7410:a165:267/64 Scope:Global
          inet6 addr: 2601:1c0:4300:930:abe:494e:47f2:f97b/64 Scope:Global
          inet6 addr: fe80::37fe:cfc8:14af:12e2/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:566287 errors:0 dropped:0 overruns:0 frame:0
          TX packets:38032 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:41070890 (41.0 MB)  TX bytes:4058219 (4.0 MB)
          Interrupt:72 Memory:ef700000-ef720000 

enp11s0f0 Link encap:Ethernet  HWaddr 00:26:55:ea:a6:0b  
          inet addr:192.168.1.41  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: 2601:1c0:4300:930:f1c7:f862:aa72:aac9/64 Scope:Global
          inet6 addr: 2601:1c0:4300:930:6d5c:fd68:986:b40c/64 Scope:Global
          inet6 addr: 2601:1c0:4300:930:1fe4:6dd2:c88c:682f/64 Scope:Global
          inet6 addr: 2601:1c0:4300:930::a/128 Scope:Global
          inet6 addr: fe80::6bf:4649:c358:ab8/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:577049 errors:0 dropped:0 overruns:0 frame:0
          TX packets:42182 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:42235263 (42.2 MB)  TX bytes:4454473 (4.4 MB)                                    
          Interrupt:86 Memory:ef520000-ef540000                                                     
                                                                                                    
enp11s0f1 Link encap:Ethernet  HWaddr 00:26:55:ea:a6:0a                                             
          inet addr:192.168.1.67  Bcast:192.168.1.255  Mask:255.255.255.0                           
          inet6 addr: 2601:1c0:4300:930:d9ff:f805:1c5a:93ed/64 Scope:Global                         
          inet6 addr: 2601:1c0:4300:930::c/128 Scope:Global                                         
          inet6 addr: 2601:1c0:4300:930:37e4:4a73:40bb:39e0/64 Scope:Global                         
          inet6 addr: fe80::a481:50c3:eb5b:24fa/64 Scope:Link                                       
          inet6 addr: 2601:1c0:4300:930:5908:da4c:638b:6eb3/64 Scope:Global                         
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1                                        
          RX packets:8972692 errors:0 dropped:0 overruns:0 frame:0                                  
          TX packets:3467382 errors:0 dropped:0 overruns:0 carrier:0                                
          collisions:0 txqueuelen:1000                                                              
          RX bytes:12240071149 (12.2 GB)  TX bytes:387161109 (387.1 MB)                             
          Interrupt:32 Memory:ef500000-ef520000                                                     
                                                                                                    
enp14s0f0 Link encap:Ethernet  HWaddr 00:26:55:ea:6d:f5                                             
          inet addr:192.168.1.44  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::7607:21bd:ab2a:4eb2/64 Scope:Link
          inet6 addr: 2601:1c0:4300:930::d/128 Scope:Global
          inet6 addr: 2601:1c0:4300:930:94fd:78c6:5d1a:533f/64 Scope:Global
          inet6 addr: 2601:1c0:4300:930:d02e:9e31:bdd4:338b/64 Scope:Global
          inet6 addr: 2601:1c0:4300:930:b03d:f08e:d5a:7f8a/64 Scope:Global
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:565346 errors:0 dropped:0 overruns:0 frame:0
          TX packets:30989 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:40983499 (40.9 MB)  TX bytes:3484298 (3.4 MB)
          Interrupt:94 Memory:ef320000-ef340000 

enp14s0f1 Link encap:Ethernet  HWaddr 00:26:55:ea:6d:f4  
          inet addr:192.168.1.46  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: 2601:1c0:4300:930:9454:6308:e5e:8fdb/64 Scope:Global
          inet6 addr: 2601:1c0:4300:930::10/128 Scope:Global
          inet6 addr: 2601:1c0:4300:930:a1f1:cccd:618a:f8a7/64 Scope:Global
          inet6 addr: 2601:1c0:4300:930:d50f:b976:c90c:31ea/64 Scope:Global
          inet6 addr: fe80::c394:ea0d:1248:b6ef/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:565477 errors:0 dropped:0 overruns:0 frame:0
          TX packets:31048 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:40990053 (40.9 MB)  TX bytes:3488760 (3.4 MB)
          Interrupt:96 Memory:ef300000-ef320000 

enp15s0f0 Link encap:Ethernet  HWaddr 00:26:55:ea:6d:f7  
          inet addr:192.168.1.66  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: 2601:1c0:4300:930:f51c:557b:90bf:d1d2/64 Scope:Global
          inet6 addr: 2601:1c0:4300:930::e/128 Scope:Global
          inet6 addr: 2601:1c0:4300:930:5d4c:ec20:438c:49e4/64 Scope:Global
          inet6 addr: fe80::1c06:7d63:34c5:af6f/64 Scope:Link
          inet6 addr: 2601:1c0:4300:930:5432:74bd:8b47:fc2c/64 Scope:Global
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:565411 errors:0 dropped:0 overruns:0 frame:0
          TX packets:31064 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:40986353 (40.9 MB)  TX bytes:3491230 (3.4 MB)
          Interrupt:98 Memory:ef120000-ef140000 

enp15s0f1 Link encap:Ethernet  HWaddr 00:26:55:ea:6d:f6  
          inet addr:192.168.1.38  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::fc9f:e4ac:a14d:4af3/64 Scope:Link
          inet6 addr: 2601:1c0:4300:930:9415:1b28:a74c:46f8/64 Scope:Global
          inet6 addr: 2601:1c0:4300:930::9/128 Scope:Global
          inet6 addr: 2601:1c0:4300:930:ce11:3f36:c1de:dca1/64 Scope:Global
          inet6 addr: 2601:1c0:4300:930:d97c:6a1:1d9f:5c8b/64 Scope:Global
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:565257 errors:0 dropped:0 overruns:0 frame:0
          TX packets:30989 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:40966541 (40.9 MB)  TX bytes:3484700 (3.4 MB)
          Interrupt:100 Memory:ef100000-ef120000 

enp4s0    Link encap:Ethernet  HWaddr 70:85:c2:66:59:ea  
          inet addr:192.168.1.43  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::7285:c2ff:fe66:59ea/64 Scope:Link
          inet6 addr: 2601:1c0:4300:930:7285:c2ff:fe66:59ea/64 Scope:Global
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1485148 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1127598 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:910302848 (910.3 MB)  TX bytes:547842451 (547.8 MB)
          Memory:efa00000-efa1ffff 

enp68s0f0 Link encap:Ethernet  HWaddr 00:26:55:ea:a6:89  
          inet addr:192.168.1.65  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::63df:7b6d:599c:61aa/64 Scope:Link
          inet6 addr: 2601:1c0:4300:930::14/128 Scope:Global
          inet6 addr: 2601:1c0:4300:930:ac3b:1d91:f700:8332/64 Scope:Global
          inet6 addr: 2601:1c0:4300:930:f339:1ec2:b6e6:54f1/64 Scope:Global
          inet6 addr: 2601:1c0:4300:930:2195:e9d4:247c:8b0f/64 Scope:Global
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:565370 errors:0 dropped:0 overruns:0 frame:0
          TX packets:31091 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:40977774 (40.9 MB)  TX bytes:3493836 (3.4 MB)
          Interrupt:102 Memory:ec920000-ec940000 

enp68s0f1 Link encap:Ethernet  HWaddr 00:26:55:ea:a6:88  
          inet addr:192.168.1.47  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::755b:7d3e:a053:38dd/64 Scope:Link
          inet6 addr: 2601:1c0:4300:930:5ccd:5e32:2472:9d76/64 Scope:Global
          inet6 addr: 2601:1c0:4300:930:81a5:ea0e:f71e:353d/64 Scope:Global
          inet6 addr: 2601:1c0:4300:930:14b8:487e:2197:4171/64 Scope:Global
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:565446 errors:0 dropped:0 overruns:0 frame:0
          TX packets:31016 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:40990836 (40.9 MB)  TX bytes:3460070 (3.4 MB)
          Interrupt:104 Memory:ec900000-ec920000 

enp69s0f0 Link encap:Ethernet  HWaddr 00:26:55:ea:a6:8b  
          inet addr:192.168.1.42  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: 2601:1c0:4300:930:2d48:3edf:aedb:eb93/64 Scope:Global
          inet6 addr: fe80::21d4:b210:c741:48cb/64 Scope:Link
          inet6 addr: 2601:1c0:4300:930:2003:7a16:7fd1:26a4/64 Scope:Global
          inet6 addr: 2601:1c0:4300:930:4403:c29a:fda0:e77a/64 Scope:Global
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:565368 errors:0 dropped:0 overruns:0 frame:0
          TX packets:31087 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:40976287 (40.9 MB)  TX bytes:3465281 (3.4 MB)
          Interrupt:106 Memory:ec720000-ec740000 

enp69s0f1 Link encap:Ethernet  HWaddr 00:26:55:ea:a6:8a  
          inet addr:192.168.1.39  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::c3c3:5cca:954a:a5ac/64 Scope:Link
          inet6 addr: 2601:1c0:4300:930::b/128 Scope:Global
          inet6 addr: 2601:1c0:4300:930:8424:8e82:8656:dcbb/64 Scope:Global
          inet6 addr: 2601:1c0:4300:930:c5a9:8fc8:8038:1ea9/64 Scope:Global
          inet6 addr: 2601:1c0:4300:930:9acd:7254:4789:db6a/64 Scope:Global
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:565115 errors:0 dropped:0 overruns:0 frame:0
          TX packets:31688 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:40975048 (40.9 MB)  TX bytes:3540278 (3.5 MB)
          Interrupt:52 Memory:ec700000-ec720000 

enp6s0    Link encap:Ethernet  HWaddr 70:85:c2:66:59:ec  
          inet addr:192.168.1.2  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: 2601:1c0:4300:930:b7ad:ab0b:22f7:3f67/64 Scope:Global
          inet6 addr: 2601:1c0:4300:930:540d:334d:f291:3fb/64 Scope:Global
          inet6 addr: 2601:1c0:4300:930:d51b:4f23:ac41:2359/64 Scope:Global
          inet6 addr: fe80::9487:86d:d73b:2742/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:574195 errors:0 dropped:0 overruns:0 frame:0
          TX packets:38959 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:40413849 (40.4 MB)  TX bytes:3821119 (3.8 MB)
          Memory:ef800000-ef81ffff 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:280655 errors:0 dropped:0 overruns:0 frame:0
          TX packets:280655 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:2129879057 (2.1 GB)  TX bytes:2129879057 (2.1 GB)

macvtap0  Link encap:Ethernet  HWaddr 52:54:00:cb:72:34  
          inet6 addr: fe80::5054:ff:fecb:7234/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:529689 errors:1 dropped:1 overruns:0 frame:0
          TX packets:7922 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:500 
          RX bytes:33435013 (33.4 MB)  TX bytes:533682 (533.6 KB)

macvtap1  Link encap:Ethernet  HWaddr 52:54:00:2d:83:0e  
          inet6 addr: fe80::5054:ff:fe2d:830e/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:532779 errors:0 dropped:0 overruns:0 frame:0
          TX packets:11177 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:500 
          RX bytes:32938250 (32.9 MB)  TX bytes:842517 (842.5 KB)

macvtap2  Link encap:Ethernet  HWaddr 52:54:00:cb:c2:b3  
          inet6 addr: fe80::5054:ff:fecb:c2b3/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:529116 errors:0 dropped:0 overruns:0 frame:0
          TX packets:7038 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:500 
          RX bytes:32612547 (32.6 MB)  TX bytes:464926 (464.9 KB)

virbr0    Link encap:Ethernet  HWaddr 00:00:00:00:00:00  
          inet addr:192.168.122.1  Bcast:192.168.122.255  Mask:255.255.255.0
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

```

For the host, /etc/network/interfaces looks like this:

```
# interfaces(5) file used by ifup(8) and ifdown(8)
auto lo
iface lo inet loopback

auto enp4s0
iface enp4s0 inet dhcp
    dns-nameservers 8.8.8.8 8.8.4.4

```

I have it set to dhcp, but I have a crappy Comcast gateway that is a pain to set up static IPs on, so I just set the leases not to expire, effectively making them static.  Each of the VMs is similarly set up, and each is accessible individually from the LAN by its own IP.

I haven't used Docker or LXC on this machine, so your needs may differ with those two.

---

### Post by izznogooood on 2018-02-25
Hey and thanks for your answer ;). (modified the question a bit to)

If I was just using KVM this would not be a problem.

But imagine each bridge would have Containers and VM's connected side by side...

This is not  a problem on the bridge (and NIC) that has a gateway. But the bridge without, none of its connected containers / VMs are reachable (will reach) beyond the first router...
[COLOR=#000000]I know I can add a bridge without an IP and take care of the gateway manually in the container / VM but then i would not be able to connect to the host from that lan (If this is even possible...).
[/COLOR]
PS:
I call your 14 :) ... (Home server, nothing to do with the actual question)

```
anders@harbor:~$ ip addr
1: lo: <LOOPBACK,UP,LOWER_UP> mtu 65536 qdisc noqueue state UNKNOWN group default qlen 1000
    link/loopback 00:00:00:00:00:00 brd 00:00:00:00:00:00
    inet 127.0.0.1/8 scope host lo
       valid_lft forever preferred_lft forever
    inet6 ::1/128 scope host 
       valid_lft forever preferred_lft forever
2: eno1: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc pfifo_fast master br0 state UP group default qlen 1000
    link/ether 90:b1:1c:9d:ed:9d brd ff:ff:ff:ff:ff:ff
    inet6 fe80::92b1:1cff:fe9d:ed9d/64 scope link 
       valid_lft forever preferred_lft forever
3: enp2s0: <NO-CARRIER,BROADCAST,MULTICAST,UP> mtu 1500 qdisc pfifo_fast state DOWN group default qlen 1000
    link/ether 68:05:ca:2a:39:82 brd ff:ff:ff:ff:ff:ff
4: br0: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc noqueue state UP group default qlen 1000
    link/ether 90:b1:1c:9d:ed:9d brd ff:ff:ff:ff:ff:ff
    inet 10.0.1.10/24 brd 10.0.1.255 scope global br0
       valid_lft forever preferred_lft forever
    inet6 2a02:fe0:c620:1a41:4970:52ea:f622:fedb/64 scope global temporary dynamic 
       valid_lft 3600sec preferred_lft 3600sec
    inet6 2a02:fe0:c620:1a41:5c6:dd7f:1d57:c638/64 scope global temporary deprecated dynamic 
       valid_lft 3600sec preferred_lft 0sec
    inet6 2a02:fe0:c620:1a41:92b1:1cff:fe9d:ed9d/64 scope global mngtmpaddr dynamic 
       valid_lft 3600sec preferred_lft 3600sec
    inet6 fe80::92b1:1cff:fe9d:ed9d/64 scope link 
       valid_lft forever preferred_lft forever
5: mac0@br0: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc noqueue state UP group default qlen 1000
    link/ether be:26:79:77:52:0d brd ff:ff:ff:ff:ff:ff
    inet 10.0.1.105/24 brd 10.0.1.255 scope global mac0
       valid_lft forever preferred_lft forever
    inet6 2a02:fe0:c620:1a41:ac96:c5b1:3957:3135/64 scope global temporary dynamic 
       valid_lft 3600sec preferred_lft 3600sec
    inet6 2a02:fe0:c620:1a41:d0e3:67d4:bdb6:1fd5/64 scope global temporary deprecated dynamic 
       valid_lft 3600sec preferred_lft 0sec
    inet6 2a02:fe0:c620:1a41:bc26:79ff:fe77:520d/64 scope global mngtmpaddr dynamic 
       valid_lft 3600sec preferred_lft 3600sec
    inet6 fe80::bc26:79ff:fe77:520d/64 scope link 
       valid_lft forever preferred_lft forever
6: lxcbr0: <NO-CARRIER,BROADCAST,MULTICAST,UP> mtu 1500 qdisc noqueue state DOWN group default qlen 1000
    link/ether 00:16:3e:00:00:00 brd ff:ff:ff:ff:ff:ff
    inet 10.0.3.1/24 scope global lxcbr0
       valid_lft forever preferred_lft forever
7: docker0: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc noqueue state UP group default 
    link/ether 02:42:d6:31:93:4f brd ff:ff:ff:ff:ff:ff
    inet 172.17.0.1/16 brd 172.17.255.255 scope global docker0
       valid_lft forever preferred_lft forever
    inet6 fe80::42:d6ff:fe31:934f/64 scope link 
       valid_lft forever preferred_lft forever
8: virbr0: <NO-CARRIER,BROADCAST,MULTICAST,UP> mtu 1500 qdisc noqueue state DOWN group default qlen 1000
    link/ether 00:00:00:00:00:00 brd ff:ff:ff:ff:ff:ff
    inet 192.168.122.1/24 brd 192.168.122.255 scope global virbr0
       valid_lft forever preferred_lft forever
9: virbr0-nic: <BROADCAST,MULTICAST> mtu 1500 qdisc pfifo_fast state DOWN group default qlen 1000
    link/ether 52:54:00:ea:f2:b1 brd ff:ff:ff:ff:ff:ff
11: vethe47f31b@if10: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc noqueue master docker0 state UP group default 
    link/ether 8a:73:16:52:4c:ab brd ff:ff:ff:ff:ff:ff link-netnsid 0
    inet6 fe80::8873:16ff:fe52:4cab/64 scope link 
       valid_lft forever preferred_lft forever
15: veth1a95f63@if14: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc noqueue master docker0 state UP group default 
    link/ether 9a:40:54:9e:88:92 brd ff:ff:ff:ff:ff:ff link-netnsid 1
    inet6 fe80::9840:54ff:fe9e:8892/64 scope link 
       valid_lft forever preferred_lft forever
17: veth2f9f41d@if16: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc noqueue master docker0 state UP group default 
    link/ether 5a:9b:aa:b2:f0:83 brd ff:ff:ff:ff:ff:ff link-netnsid 2
    inet6 fe80::589b:aaff:feb2:f083/64 scope link 
       valid_lft forever preferred_lft forever
20: veth43c1513@if19: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc noqueue master docker0 state UP group default 
    link/ether 66:c7:a2:be:17:d9 brd ff:ff:ff:ff:ff:ff link-netnsid 3
    inet6 fe80::64c7:a2ff:febe:17d9/64 scope link 
       valid_lft forever preferred_lft forever
22: vethc8e42b1@if21: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc noqueue master docker0 state UP group default 
    link/ether f6:9b:24:3a:6b:8c brd ff:ff:ff:ff:ff:ff link-netnsid 4
    inet6 fe80::f49b:24ff:fe3a:6b8c/64 scope link 
       valid_lft forever preferred_lft forever
24: veth563f490@if23: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc noqueue master docker0 state UP group default 
    link/ether 76:f2:cf:ed:42:d6 brd ff:ff:ff:ff:ff:ff link-netnsid 5
    inet6 fe80::74f2:cfff:feed:42d6/64 scope link 
       valid_lft forever preferred_lft forever
26: veth12b74ab@if25: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc noqueue master docker0 state UP group default 
    link/ether d6:7e:ad:51:8f:da brd ff:ff:ff:ff:ff:ff link-netnsid 7
    inet6 fe80::d47e:adff:fe51:8fda/64 scope link 
       valid_lft forever preferred_lft forever
28: vethf0e9541@if27: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc noqueue master docker0 state UP group default 
    link/ether 72:e5:85:49:f3:54 brd ff:ff:ff:ff:ff:ff link-netnsid 6
    inet6 fe80::70e5:85ff:fe49:f354/64 scope link 
       valid_lft forever preferred_lft forever
30: vethd103465@if29: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc noqueue master docker0 state UP group default 
    link/ether 6e:8c:bd:4d:80:40 brd ff:ff:ff:ff:ff:ff link-netnsid 8
    inet6 fe80::6c8c:bdff:fe4d:8040/64 scope link 
       valid_lft forever preferred_lft forever
32: veth6d9ac4d@if31: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc noqueue master docker0 state UP group default 
    link/ether 16:67:ce:b9:9b:ed brd ff:ff:ff:ff:ff:ff link-netnsid 9

```

---

### Post by The Cog on 2018-02-25
> How can I specify 2 gateways or add routes for 192.168.1.0/24 ?
Do I need to specify every possible route out from 192.168.1.0/24 or is adding one route to the first gateway enough?
And how do I add this gateways?
Don't add another gateway. You should only have one default gateway, which is the router you should send things to when you don't know a better route.

You don't need to add a route to be able to reach anything on 192.168.1.* - this route is automatic because you are connected to that network. Any other networks that you know you can reach **via** a router on (for instance) 192.168.1.1 must be added specifically. But it is sometimes possible to summarise  multiple networks, so for instance you can summarise 192.168.4.0/24 + 192.168.5.0/24 + 192.168.6.0/24 + 192.168.7.0/24 to a single 192.168.4.0/22 network block. 

You can add routes to /etc/network/interface stanzas as shown here: [https://askubuntu.com/questions/168033/how-to-set-static-routes-in-ubuntu-server](https://askubuntu.com/questions/168033/how-to-set-static-routes-in-ubuntu-server) in which one example happens to summarise all 192.168.*.* into a single 192.168.0.0/16 route.

---

### Post by izznogooood on 2018-02-26
Hah, great thanks!

---

