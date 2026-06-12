---
title: "Trying/failing to connect two Ubuntu computers. One has new USB-C to ethernet dongle."
date: 2020-11-07
forum: Networking &amp; Wireless
---

### Post by crazybear on 2020-11-07
Networking is my weakest hand in Linux, I must admit. I'm trying to connect with a LAN cable between a desktop [connected to the internet by LAN] to a laptop. The laptop didn't come with a LAN connection, but I just purchased a good [I think/hope] iTek USB-C to ethernet connector. It had a driver that I think [?] I installed using make - but don't know. There is nothing connecting the two. The laptop has Ubuntu 20.04 and the desktop 16.04 which have quite different network interfaces.
I think first I must convince myself that the driver is installed properly and working and then worry about the IP addresses etc. I do not know how to test the driver. Yes, a new ethernet device shows up on ifconfig....but everything is 0 [no activity]. The idea was to keep certain files on the two updated to the newest using Unison.

For some reason I can't login to this forum on the laptop now, but can on the desktop....so will try to find the problem and post the ifconfig of the laptop with the dongle USB-C to ethernet. When I sign in, it briefly says 'welcome crazybear', but in the forum I have no permission to do anything and am not signed in?!?!? 

In 20.04 I see fewer options to set anything regarding network compared to 16.04. I'm sure I'm wrong, but can not find the correct or more detailed network setting area. The laptop has wifi, but the desktop does NOT.

Below, it is enx00e04c6809c2 that did not exist before I plugged in the dongle.

```

 $ ifconfig
 enx00e04c6809c2: flags=4163<UP,BROADCAST,RUNNING,MULTICAST>  mtu 1500
         inet6 fe80::5628:fe9f:a44d:813  prefixlen 64  scopeid 0x20<link>
         ether aa:4b:68:6e:a1:56  txqueuelen 1000  (Ethernet)
         RX packets 156  bytes 37013 (37.0 KB)
         RX errors 0  dropped 0  overruns 0  frame 0
         TX packets 417  bytes 85145 (85.1 KB)
         TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0
 
 
 lo: flags=73<UP,LOOPBACK,RUNNING>  mtu 65536
         inet 127.0.0.1  netmask 255.0.0.0
         inet6 ::1  prefixlen 128  scopeid 0x10<host>
         loop  txqueuelen 1000  (Local Loopback)
         RX packets 3335  bytes 398024 (398.0 KB)
         RX errors 0  dropped 0  overruns 0  frame 0
         TX packets 3335  bytes 398024 (398.0 KB)
         TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0
 
 
 wlp2s0: flags=4163<UP,BROADCAST,RUNNING,MULTICAST>  mtu 1500
         inet 10.0.0.13  netmask 255.255.255.0  broadcast 10.0.0.255
         inet6 fe80::7051:d512:47ef:df6a  prefixlen 64  scopeid 0x20<link>
         ether 48:e2:44:f5:f5:79  txqueuelen 1000  (Ethernet)
         RX packets 3007  bytes 1352395 (1.3 MB)
         RX errors 0  dropped 0  overruns 0  frame 0
         TX packets 3331  bytes 620210 (620.2 KB)
         TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0

 *-network                  
        description: Wireless interface
        product: BCM43602 802.11ac Wireless LAN SoC
        vendor: Broadcom Inc. and subsidiaries
        physical id: 0
        bus info: pci@0000:02:00.0
        logical name: wlp2s0
        version: 01
        serial: 48:e2:44:f5:f5:79
        width: 64 bits
        clock: 33MHz
        capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
        configuration: broadcast=yes driver=brcmfmac driverversion=7.35.177.61 firmware=01-ea662a8c ip=10.0.0.13 latency=0 multicast=yes wireless=IEEE 802.11
        resources: irq:147 memory:dd800000-dd807fff memory:dd400000-dd7fffff
   *-network
        description: Ethernet interface
        physical id: 2
        bus info: usb@4:1
        logical name: enx00e04c6809c2
        serial: aa:4b:68:6e:a1:56
        size: 1Gbit/s
        capacity: 1Gbit/s
        capabilities: ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
        configuration: autonegotiation=on broadcast=yes driver=r8152 driverversion=v1.10.11 duplex=full link=yes multicast=yes port=MII speed=1Gbit/s
  
  

```

---

### Post by crazybear on 2020-11-07
Here is the ifconfig of the desktop:

```

$ ifconfig
enp6s0    Link encap:Ethernet  HWaddr 6c:f0:49:5e:db:13  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:568 errors:0 dropped:0 overruns:0 frame:0
          TX packets:3857 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:175254 (175.2 KB)  TX bytes:777536 (777.5 KB)

enp7s0    Link encap:Ethernet  HWaddr 6c:f0:49:5e:db:03  
          inet addr:10.0.0.3  Bcast:10.0.0.255  Mask:255.255.255.0
          inet6 addr: fe80::997b:3d1a:70cd:dbb9/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:12679209 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4679736 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:18277857639 (18.2 GB)  TX bytes:341688383 (341.6 MB)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:943847 errors:0 dropped:0 overruns:0 frame:0
          TX packets:943847 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:94445245 (94.4 MB)  TX bytes:94445245 (94.4 MB)

virbr0    Link encap:Ethernet  HWaddr 00:00:00:00:00:00  
          inet addr:192.168.122.1  Bcast:192.168.122.255  Mask:255.255.255.0
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

sudo lshw -class network
[sudo] password for peter-and-crazybear: 
  *-network               
       description: Ethernet interface
       product: RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:06:00.0
       logical name: enp6s0
       version: 03
       serial: 6c:f0:49:5e:db:13
       size: 1Gbit/s
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=full firmware=rtl_nic/rtl8168d-2.fw latency=0 link=yes multicast=yes port=MII speed=1Gbit/s
       resources: irq:16 ioport:de00(size=256) memory:fbbff000-fbbfffff memory:fbbf8000-fbbfbfff memory:fbc00000-fbc1ffff
  *-network
       description: Ethernet interface
       product: RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:07:00.0
       logical name: enp7s0
       version: 03
       serial: 6c:f0:49:5e:db:03
       size: 1Gbit/s
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=full firmware=rtl_nic/rtl8168d-2.fw ip=10.0.0.3 latency=0 link=yes multicast=yes port=MII speed=1Gbit/s
       resources: irq:17 ioport:ce00(size=256) memory:fb9ff000-fb9fffff memory:fb9f8000-fb9fbfff memory:fba00000-fba1ffff
  *-network DISABLED
       description: Ethernet interface
       physical id: 1
       logical name: virbr0-nic
       serial: 52:54:00:2b:2f:a7
       size: 10Mbit/s
       capabilities: ethernet physical
       configuration: autonegotiation=off broadcast=yes driver=tun driverversion=1.6 duplex=full link=no multicast=yes port=twisted pair speed=10Mbit/s




```

However, though plugged together, the two computers do not see each other. On the Ubuntu 20.04 I do NOT see how to change the IP address anywhere.

---

### Post by ajgreeny on 2020-11-07
Can both machines connect to the internet and are they both using the same LAN, ie, both connected to the same router?

Assuming they are, it may be a lot simpler to use ssh to connect them than mess about with cables.
Install ***openssh-server*** on both and you should have all you need, the openssh-client is already installed as default in all *ubuntu family OSs.

There is no point me saying much more in this thread other than pointing you to the wiki at [https://help.ubuntu.com/community/SSH](https://help.ubuntu.com/community/SSH) which will tell you everything.
Don't ignore the part about disabling password as that is definitely most secure and the best way to use this method of connecting machines.

---

### Post by crazybear on 2020-11-08
Last year and for many years I had two desktops connected directly. A friend did it. I liked the configuration. So the desktop is already set up to connect to another computer plugged into the other LAN port. I thought I would just have to recreate the correct settings on the new laptop that existed on the now stolen other computer. Reading the openssh guide the password situation makes me very hesitant. It suggests a 2048 bit key password - or something like that. Only these two computer will ever need to be connected - the other desktop if I ever get it back after it was stolen by my former landlord [we are in court over that now, but in this country, this legal matter will take many years!]. I see no advantage to connecting both to a router - is there any? I do want good security for both and I am a target more than most for hacking due to the kind of research I do - so good to great security is a priority....so why would I want to disable password and how in the hell could I recover a lost 2048 bit key character password? This computer geek who set up the original pairing of the two computers said that no hacker except the BIG BOYS [govt.] could see the second computer - so the most sensitive data could be stored on that, and that appealed to me.

---

### Post by ajgreeny on 2020-11-08
I think you are totally misunderstanding what is meant by disabling password connections over ssh, so I suggest that you read again the page at [https://help.ubuntu.com/community/SSH/OpenSSH/Keys](https://help.ubuntu.com/community/SSH/OpenSSH/Keys) which may appear complicated but once set up is incredibly secure and offers a separate security layer to the normal user password.

This has nothing to do with your user password being disabled and I would always recommend that autologin to your user session is a terrible idea for security of your system.

Also note that when I asked if both machines were connected to the same router I was not asking about cable connections but just checking they were on the same LAN, ie router.  I am assuming that they both have a network connection but having re-read your original post I think I may be incorrect about that; if I'm wrong then forget about this second part of this post.

Unfortunately I have no experience or knowledge of connecting machines using LAN cables between machines so will have to leave this to others.

---

### Post by crazybear on 2020-11-10
I have only one router and one  internet connection at this time....but I am forced to move often, and need a system that is flexible to all situations I might encounter. What you claim is so simple and obvious looks quite complex and somewhat confusing to me. If I mess up, and neither computer can get online, then I have NO device with which to even ask for help or look for help - none. That is why I was hoping someone could help lead me through the steps, and make sure I was not about to make a mistake that could not easily be undone. That guide you point to doesn't mention undoing things and I assume assumes one would know how to undo a mistake. I would not.

 I also ask if anyone has experience with connecting directly two computers [as I had it set up before]. My friend did it in ten minutes, but he did it so quickly, I was unable to note down or even catch what he was doing. In the future I might put into the desktop a wifi board....but that is not the immediate problem nor solution. Now both can get internet, but they do not see each other and can not exchange information.

---

### Post by crazybear on 2020-11-15
Sorry, but as I knew and now am experiencing, I am getting nowhere to connecting. The laptop is listening to 0.0.0.0 and I believe there are other problems. I can not set up a wired connection in 20.04...the option doesn't appear anywhere I can find. I don't know if the exact or almost the exact same things need to be done on both computers and I really wanted to connect the two computers directly. I will never connect from one to another remotely. This is the way it was set up before, but for now, I'll settle for any connection. My confusion is such I can't really list all the problems.

---

### Post by crazybear on 2020-11-16
Again, I'm going to need help beyond pointing me to webpages [which I had searched for, seen, and been confused by] before you pointed to one of many. There are others that give a much simpler solution for connecting two computers together, but even on those I will need help. Here is an example of a suggested connection between two computers directly with a LAN cable: [https://itectec.com/ubuntu/ubuntu-how-to-network-two-ubuntu-computers-using-ethernet-without-a-router/](https://itectec.com/ubuntu/ubuntu-how-to-network-two-ubuntu-computers-using-ethernet-without-a-router/)
This is the way the system was set up before my other computer was seized by my landlord [illegally]. Now I have a new laptop with 20.04, but given the problems I mentioned, I can't even try to do this without fixing the 20.04 first. Thanks in advance.

The computers will NEVER be connected [exchanging information] except when in the same room without ANY other computer involved - and I want/need a reasonably high degree of security from hacking into them.....such as exists today [little].

---

### Post by crazybear on 2020-11-17
I am totaly lost [as I said at the first post] when it comes to networking. I understand almost nothing despite reading lots of websites and 'fixes', which only get me more confused. Please someone help!

```

this is the desktop:
$ route -n
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         10.0.0.138      0.0.0.0         UG    100    0        0 enp7s0
10.0.0.0        0.0.0.0         255.255.255.0   U     100    0        0 enp7s0
10.0.0.0        0.0.0.0         255.255.255.0   U     101    0        0 enp6s0
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 virbr0
192.168.122.0   0.0.0.0         255.255.255.0   U     0      0        0 virbr0
$ ip route show
default via 10.0.0.138 dev enp7s0  proto static  metric 100 
10.0.0.0/24 dev enp7s0  proto kernel  scope link  src 10.0.0.3  metric 100 
10.0.0.0/24 dev enp6s0  proto kernel  scope link  src 10.0.0.1  metric 101 
169.254.0.0/16 dev virbr0  scope link  metric 1000 linkdown 
192.168.122.0/24 dev virbr0  proto kernel  scope link  src 192.168.122.1 linkdown 

```
I don't know what to set things to and which not to set. I tried via a modem and failed. Now I'm trying to connect directly and am failing. But without knowing how to configure the second LAN port and the one on the laptop, I'm not surprised I'm failing. Networking is coded Chinese to me. Those who understand it don't understand how complex and confusing it is to someone who doesn't even understand the basic principles, terms, or what needs to be configured [or not configured] and where/when.

The ONLY thing I believe I have done is to configure the driver for the USB-C to ethernet dongle. Beyond that, via either method, I'm hopelessly confused. I come across screens asking for information I do not know the meaning of the terms [even when I look them up], which lines to fill in [or not], nor what to fill them in with - I don't even understand the basic priciples upon which networking is structured - I admit. I really need to connect the two computers to keep them synchronized on some folders. My living situation is NOT stable, I will have to move again soon, and will not have the use of the desktop - only the laptop....so it needs to have the latest info...and when I again can set up the desktop, to transfer that new information back to the desktop.

---

