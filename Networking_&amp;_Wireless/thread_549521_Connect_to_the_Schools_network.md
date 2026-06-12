---
title: "Connect to the Schools network"
date: 2007-09-12
forum: Networking &amp; Wireless
---

### Post by Christ_Guard on 2007-09-12
Hi,
   I am still new to this whole Linux thing so please help me out. I need to conect 6 computers ruing Ubuntu DD to our university's network (I am a network Admin). I can not figure out how, we are running wired connections BTW and the domain name is labpcs.spu.local can you help me figure this out?

Thanks
-Christian

---

### Post by noob12 on 2007-09-12
If you have a typical network with a DHCP server running on it, then you can usually  just plug them in.

Are they identical boxes?  Have you tried with one?

Can you run
```

lspci -nn

```
on one and post what Ethernet controller you have on the boxes?

---

### Post by Christ_Guard on 2007-09-13
This is what that returns. The boxes are all similar, but not Identical, most are running XP and our network is run off a windows server (NT I Think)

```
student@CS223A-L-001:~$ lspci -nn
00:00.0 Host bridge [0600]: Intel Corporation 82945G/GZ/P/PL Memory Controller Hub [8086:2770] (rev 02)
00:02.0 VGA compatible controller [0300]: Intel Corporation 82945G/GZ Integrated Graphics Controller [8086:2772] (rev 02)
00:02.1 Display controller [0380]: Intel Corporation 82945G/GZ Integrated Graphics Controller [8086:2776] (rev 02)
00:1c.0 PCI bridge [0604]: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 [8086:27d0] (rev 01)
00:1c.1 PCI bridge [0604]: Intel Corporation 82801G (ICH7 Family) PCI Express Port 2 [8086:27d2] (rev 01)
00:1d.0 USB Controller [0c03]: Intel Corporation 82801G (ICH7 Family) USB UHCI #1 [8086:27c8] (rev 01)
00:1d.1 USB Controller [0c03]: Intel Corporation 82801G (ICH7 Family) USB UHCI #2 [8086:27c9] (rev 01)
00:1d.2 USB Controller [0c03]: Intel Corporation 82801G (ICH7 Family) USB UHCI #3 [8086:27ca] (rev 01)
00:1d.3 USB Controller [0c03]: Intel Corporation 82801G (ICH7 Family) USB UHCI #4 [8086:27cb] (rev 01)
00:1d.7 USB Controller [0c03]: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller [8086:27cc] (rev 01)
00:1e.0 PCI bridge [0604]: Intel Corporation 82801 PCI Bridge [8086:244e] (rev e1)
00:1e.2 Multimedia audio controller [0401]: Intel Corporation 82801G (ICH7 Family) AC'97 Audio Controller [8086:27de] (rev 01)
00:1f.0 ISA bridge [0601]: Intel Corporation 82801GB/GR (ICH7 Family) LPC Interface Bridge [8086:27b8] (rev 01)
00:1f.1 IDE interface [0101]: Intel Corporation 82801G (ICH7 Family) IDE Controller [8086:27df] (rev 01)
00:1f.2 IDE interface [0101]: Intel Corporation 82801GB/GR/GH (ICH7 Family) Serial ATA Storage Controller IDE [8086:27c0] (rev 01)
00:1f.3 SMBus [0c05]: Intel Corporation 82801G (ICH7 Family) SMBus Controller [8086:27da] (rev 01)
01:00.0 Ethernet controller [0200]: Broadcom Corporation NetXtreme BCM5751 Gigabit Ethernet PCI Express [14e4:1677] (rev 01)
student@CS223A-L-001:~$ 

```

---

### Post by noob12 on 2007-09-13
Are the windows boxes set up using DHCP?   What will be useful is if you can post the output from **ipconfig /all** and **route print** from one of the Windows XP boxes booted in Windows.  This will tell us how the network looks, and that can help provide suggestions on what you need to do on Ubuntu.

Here's a basic suggestion.  Put one Windows box on the net next to one box you want to run Ubuntu.
Have a jump drive handy in case you need to transfer files to the Ubuntu host until you get it on the net.


Can you please post the output of these commands from the Ubuntu host (with the box plugged into the net).
```

sudo lshw -C network

ifconfig -a

sudo ethtool eth0

```

---

### Post by Christ_Guard on 2007-09-13
Sure thing:

IPCONFIG:

```
Microsoft Windows XP [Version 5.1.2600]
(C) Copyright 1985-2001 Microsoft Corp.

C:\Documents and Settings\labsshielc>ipconfig /all

Windows IP Configuration

        Host Name . . . . . . . . . . . . : CS253-004
        Primary Dns Suffix  . . . . . . . : labpcs.spu.local
        Node Type . . . . . . . . . . . . : Hybrid
        IP Routing Enabled. . . . . . . . : No
        WINS Proxy Enabled. . . . . . . . : No
        DNS Suffix Search List. . . . . . : labpcs.spu.local
                                            spu.edu
                                            spu.local

Ethernet adapter Local Area Connection:

        Connection-specific DNS Suffix  . : spu.edu
        Description . . . . . . . . . . . : Intel(R) 82566DM Gigabit Network Con
nection
        Physical Address. . . . . . . . . : 00-19-B9-2B-D0-D1
        Dhcp Enabled. . . . . . . . . . . : Yes
        Autoconfiguration Enabled . . . . : Yes
        IP Address. . . . . . . . . . . . : 199.237.188.192
        Subnet Mask . . . . . . . . . . . : 255.255.254.0
        Default Gateway . . . . . . . . . : 199.237.188.1
        DHCP Server . . . . . . . . . . . : 192.190.33.39
        DNS Servers . . . . . . . . . . . : 192.190.33.38
                                            192.190.33.36
                                            192.190.33.37
        Lease Obtained. . . . . . . . . . : Thursday, September 13, 2007 2:06:06
 AM
        Lease Expires . . . . . . . . . . : Friday, September 14, 2007 2:06:06 A
M

C:\Documents and Settings\labsshielc>



```


Route Print
```
C:\Documents and Settings\labsshielc>route print
===========================================================================
Interface List
0x1 ........................... MS TCP Loopback interface
0x2 ...00 19 b9 2b d0 d1 ...... Intel(R) 82566DM Gigabit Network Connection - Pa
cket Scheduler Miniport
===========================================================================
===========================================================================
Active Routes:
Network Destination        Netmask          Gateway       Interface  Metric
          0.0.0.0          0.0.0.0    199.237.188.1  199.237.188.192      20
        127.0.0.0        255.0.0.0        127.0.0.1       127.0.0.1       1
    199.237.188.0    255.255.254.0  199.237.188.192  199.237.188.192      20
  199.237.188.192  255.255.255.255        127.0.0.1       127.0.0.1       20
  199.237.188.255  255.255.255.255  199.237.188.192  199.237.188.192      20
        224.0.0.0        240.0.0.0  199.237.188.192  199.237.188.192      20
  255.255.255.255  255.255.255.255  199.237.188.192  199.237.188.192      1
Default Gateway:     199.237.188.1
===========================================================================
Persistent Routes:
  None

C:\Documents and Settings\labsshielc>
```

---

### Post by noob12 on 2007-09-13
I added some more instructions probably after you had already read the last postiing.  Can you review that (sorry) and run those commands too?

---

### Post by noob12 on 2007-09-13
I found that your card is supported by the tg3 driver in Feisty (7.04 release), but I am not sure about the level of support in the Dapper release (will try to check, please do provide the output from those commands).

---

### Post by Christ_Guard on 2007-09-13
I have 2 boxs running side by side now, here are the other outputs you asked for:


sudo lshw -C network:
```
  *-network               
       description: Ethernet interface
       product: NetXtreme BCM5751 Gigabit Ethernet PCI Express
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@01:00.0
       logical name: eth0
       version: 01
       serial: 00:12:3f:63:05:99
       size: 100MB/s
       capacity: 1GB/s
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=tg3 driverversion=3.72 duplex=full firmware=5751-v3.44a ip=199.237.188.55 latency=0 link=yes multicast=yes port=twisted pair speed=100MB/s
       resources: iomemory:efdf0000-efdfffff irq:16
```


ifconfig -a
```
student@CS223A-L-001:~$ ifconfig -a
eth0      Link encap:Ethernet  HWaddr 00:12:3F:63:05:99  
          inet addr:199.237.188.55  Bcast:199.237.189.255  Mask:255.255.254.0
          inet6 addr: fe80::212:3fff:fe63:599/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:903372 errors:0 dropped:0 overruns:0 frame:0
          TX packets:116651 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:625778275 (596.7 MiB)  TX bytes:9362090 (8.9 MiB)
          Interrupt:16 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:12 errors:0 dropped:0 overruns:0 frame:0
          TX packets:12 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:600 (600.0 b)  TX bytes:600 (600.0 b)

student@CS223A-L-001:~$ 

```

sudu ethtool eth0:
```
Settings for eth0:
        Supported ports: [ MII ]
        Supported link modes:   10baseT/Half 10baseT/Full 
                                100baseT/Half 100baseT/Full 
                                1000baseT/Half 1000baseT/Full 
        Supports auto-negotiation: Yes
        Advertised link modes:  10baseT/Half 10baseT/Full 
                                100baseT/Half 100baseT/Full 
                                1000baseT/Half 1000baseT/Full 
        Advertised auto-negotiation: Yes
        Speed: 100Mb/s
        Duplex: Full
        Port: Twisted Pair
        PHYAD: 1
        Transceiver: internal
        Auto-negotiation: on
        Supports Wake-on: g
        Wake-on: d
        Current message level: 0x000000ff (255)
        Link detected: yes

```

---

### Post by noob12 on 2007-09-13
Hey, you're running on the net.  Your box has acquired an address by DHCP already.  

Let's make sure it has a default gateway, and DNS servers, and you should be good to go.  You are almost there.

Have you tried opening firefox on that Ubuntu host and seeing if you can get to google or something?

If it works you're good.  If not, we need to look at the following:
```

route -n

cat /etc/resolv.conf

```

---

### Post by Christ_Guard on 2007-09-13
Well now I feel dumb, the problem was not that I need internet, it's that I am not connected to the schools network domain (Or workgroup or whatever) I should be able to log in with different network acounts on this box but I cant because it is not connected to the scghools network.

---

### Post by Synflux on 2007-09-13
Hi,

I've never tried it myself but I found [this ]("https://help.ubuntu.com/community/ActiveDirectoryWinbindHowto") which you might find useful?

---

### Post by noob12 on 2007-09-13
Oh, my fault too. I totally misinterpreted things.  I thought you were having trouble getting basic network connectivity working, but now after running in a big circle, we find you're all set there.  

Connecting to your Windows domain for authentication is a whole different ballgame, and I don't think I'll be much help in that area.  There are some HOWTOs that you will find out on the web but you will need to know the specifics to distinguish which ones apply to you. 

You should at least find out if you using an NT4 domain controller or Active Directory for authentication, and it may be useful to know what version of server (I'm not sure). If you can't find a HOWTO on the net that matches your specifics, try posting a new thread with the specifics.

EDIT:  synflux's tip looks good for the AD case!

---

