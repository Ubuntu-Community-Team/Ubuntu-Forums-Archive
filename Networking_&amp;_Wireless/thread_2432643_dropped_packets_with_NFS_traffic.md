---
title: "dropped packets with NFS traffic"
date: 2019-12-05
forum: Networking &amp; Wireless
---

### Post by meadrocks on 2019-12-05
I have a PCIe Intel Corporation 82572EI Gigabit Ethernet Controller (Copper) (rev 06) NIC.

ampl@ubuntu-kde1:~$ cat /etc/exports
/MOVIES *(ro,insecure)

I have Kodi Amlogic 905x SOC boxes that NFS mount /MOVIES & stream the content to my TV, they have 100mb NICs.[COLOR="#FF0000"][/COLOR]

When streaming I get dropped packets.

ampl@ubuntu-kde1:~$ ifconfig

enp3s0: flags=4163<UP,BROADCAST,RUNNING,MULTICAST>  mtu 1500
        inet 192.168.100.241  netmask 255.255.255.0  broadcast 192.168.100.255
        inet6 fe80::926a:65d2:40b7:a8a  prefixlen 64  scopeid 0x20<link>
        ether 00:15:17:c3:fc:4b  txqueuelen 1000  (Ethernet)
        RX packets 93499  bytes 53276951 (53.2 MB)
        RX errors 0  [COLOR="#FF0000"]dropped 16321 [/COLOR] overruns 0  frame 0
        TX packets 178972  bytes 227372013 (227.3 MB)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0
        device interrupt 16  memory 0xf3120000-f3140000  
[COLOR="#000000"][/COLOR]

ampl@ubuntu-kde1:~$ ethtool enp3s0
Settings for enp3s0:
        Supported ports: [ TP ]
        Supported link modes:   10baseT/Half 10baseT/Full 
                                100baseT/Half 100baseT/Full 
                                1000baseT/Full 
        Supported pause frame use: No
        Supports auto-negotiation: Yes
        Supported FEC modes: Not reported
        Advertised link modes:  10baseT/Half 10baseT/Full 
                                100baseT/Half 100baseT/Full 
                                1000baseT/Full 
        Advertised pause frame use: No
        Advertised auto-negotiation: Yes
        Advertised FEC modes: Not reported
        Speed: 1000Mb/s
        Duplex: Full
        Port: Twisted Pair
        PHYAD: 1
        Transceiver: internal
        Auto-negotiation: on
        MDI-X: on (auto)
Cannot get wake-on-lan settings: Operation not permitted
        Current message level: 0x00000007 (7)
                               drv probe link
        Link detected: yes

I am connected at 1 Gig to my switch, why am I getting dropped packets when using NFS?
I'm running Ubuntu 18.04 64 bit.

Thanks.

---

### Post by SeijiSensei on 2019-12-05
Is the Ethernet controller on a separate card, or is it built into the motherboard? If you have a built-in adapter as well, does that perform any better?  I have a Dell T30 server with a built-in Intel I219-LM adapter. It does NFS and provides other services like an email server and an OpenVPN gateway to my virtual servers at Linode. ifconfig reports

```

eth0      Link encap:Ethernet  HWaddr D8:9E:F3:1A:DD:AF  
          inet addr:192.168.100.100  Bcast:192.168.100.255  Mask:255.255.255.0
          inet6 addr: fe80::da9e:f3ff:fe1a:ddaf/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:2361710270 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1315643724 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:3414436316306 (3.1 TiB)  TX bytes:377508910699 (351.5 GiB)
          Interrupt:16 Memory:df000000-df020000 

```

---

### Post by meadrocks on 2019-12-05
This is a PCIe card.
I dont get dropped packets from any network traffic generated from the pc, reading email, web surfing, etc. Only NFS traffic do I see the dropped packets increase.

---

### Post by SeijiSensei on 2019-12-06
> **meadrocks said:**
> This is a PCIe card.
Yes, I realize that. Since most modern PCs include a built-in Ethernet port, I was asking if that was an option for you.

---

### Post by TheFu on 2019-12-06
No clue on the root issue, but we can force NFS to use TCP, not the default UDP (for NFSv2/3).
Read somewhere that was recommended for GigE networking or faster.

---

### Post by meadrocks on 2019-12-06
How do I do that w/ Ubuntu 18.04 & make it persistent?

From searching it looks to be a client side option on the mount in /etc/fstab. I'd rather force it from the server side if possible, TCP only connections allowed.

---

### Post by TheFu on 2019-12-07
> **meadrocks said:**
> How do I do that w/ Ubuntu 18.04 & make it persistent?

From searching it looks to be a client side option on the mount in /etc/fstab. I'd rather force it from the server side if possible, TCP only connections allowed.

I've only used the client-side setting.  NFSv4 defaults to TCP, but there might be bugs according to this: 
[https://help.ubuntu.com/community/NFSv4Howto](https://help.ubuntu.com/community/NFSv4Howto) unless Kerberos is used.

Perhaps on the server-side, blocking udp on the NFS port (2049) would be sufficient to force tcp?
```
$ netstat -tun |grep 172.22.22.6
tcp        0      0 172.22.22.20:2049       172.22.22.6:796         ESTABLISHED
```

Not seeing any udp here, so it should work.  172.22.22.6 is the nfs-client, 172.22.22.20 is the server.

---

### Post by meadrocks on 2019-12-07
A fellow sys admin has suggested that I run the following on boot to turn auto negotiation off.

/sbin/ethtool &#8211;s enp3s0 speed 1000 duplex full autoneg off

On Centos I would do the following.
Open the file:
# vi /etc/sysconfig/network-scripts/ifcfg-eth0
Append following line:
ETHTOOL_OPTS="speed 100 duplex full autoneg off"

How do I do the same for Ubuntu?

---

### Post by TheFu on 2019-12-07
The GigE spec requires autonegotiation.

I don't use 18.04 mainly because they completely changed the way network interfaces are configured, but it was easy in 16.04 with a post-up stanza in the interfaces file.  That file is gone.
**ethtool** works in Ubuntu, so you just need to get that command run after the network is up.  I wouldn't force a 1000base-tx server to use 100base-tx performance.  I'd get a better switch or update the NFS clients to GigE.
I would be surprised if 18.04 netplan didn't have a way to to post-up commands. A little google should find them - or the Ubuntu Server Guide help pages.  [https://help.ubuntu.com/lts/serverguide/](https://help.ubuntu.com/lts/serverguide/)
Google found this: [https://askubuntu.com/questions/1032153/how-to-execute-post-up-scripts-with-netplan](https://askubuntu.com/questions/1032153/how-to-execute-post-up-scripts-with-netplan)

I've been using NFS with multiple raspberry Pi devices (100base-tx) for streaming, so nothing too important.   Not seeing any issues in over 3 yrs of use with a GigE NFS server.

---

### Post by lensman3 on 2019-12-11
This is a off the wall maybe answer:  Is your switch up to the task?  Most switches if you flood them with packets, shutdown and stop the store and forward function. It falls over to a hub that was the default in 1990 or so.  In other words, any packets hitting the switch during the flood get dumped from the source.  At that point every machine on your network has to be less than 100 meters from every other machine on the network.  The speed of light on the network comes into play because after a 1500 mtu bytes (packet) are put on the network, the network listens to see if it is their turn to transmit.

---

