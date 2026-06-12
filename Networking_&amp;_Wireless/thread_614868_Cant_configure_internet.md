---
title: "Cant configure internet"
date: 2007-11-16
forum: Networking &amp; Wireless
---

### Post by allbecool on 2007-11-16
Hi. First of all i must tell that i`m not good speak in english.
I have problem with connect to the inetrnet. 
that is my ifconfig in Ubuntu 7.04

eth0      Link encap:Ethernet  HWaddr 00:E0:4C:51:22:14 
          inet addr:89.107.117.152  Bcast:89.107.117.255  Mask:255.255.255.128
          inet6 addr: fe80::2e0:4cff:fe51:2214/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:16 Base address:0x4c00 
		  
lo        Link encap:Local Loopback 
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:12 errors:0 dropped:0 overruns:0 frame:0
          TX packets:12 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:904 (904.0 b)  TX bytes:904 (904.0 b)

this is route -n

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
89.107.117.128  0.0.0.0         255.255.255.128 U     0      0        0 eth0
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 eth0
0.0.0.0         89.107.117.129  0.0.0.0         UG    0      0        0 eth0

this is /etc/network/interfaces

auto lo
iface lo inet loopback

iface eth0 inet static
address 89.107.117.152
netmask 255.255.255.128
gateway 89.107.117.129

iface eth1 inet dhcp

auto ath0
iface ath0 inet dhcp

auto wlan0
iface wlan0 inet dhcp


auto eth0
  
  in the resolv.conf :
  
  nameserver 89.107.115.1
nameserver 80.78.115.1
  
  But i`m have internet in the Windows XP
  
that is ipconfig /all in the Windows XP
        MAC. . . . . . . . . : 00-E0-4C-51-22-14
        Dhcp . . . . . . . . . . . : no
        IP . . . . . . . . . . . . : 89.107.117.152
        NetMask . . . . . . . . . . : 255.255.255.128
        GateWay . . . . . . . . . . : 89.107.117.129
        DNS . . . . . . . . . . . : 89.107.115.1
                                            80.78.115.1
this is route print in the Windows:

addres                       mask         gateway          interfaces  metrick   
          0.0.0.0          0.0.0.0   89.107.117.129  89.107.117.152	  30
   89.107.117.128  255.255.255.128   89.107.117.152  89.107.117.152	  30
   89.107.117.152  255.255.255.255        127.0.0.1       127.0.0.1	  30
   89.255.255.255  255.255.255.255   89.107.117.152  89.107.117.152	  30
        127.0.0.0        255.0.0.0        127.0.0.1       127.0.0.1	  1
        224.0.0.0        240.0.0.0   89.107.117.152  89.107.117.152	  30
  255.255.255.255  255.255.255.255   89.107.117.152  89.107.117.152	  1

											

so in the same internet adapter on the Windows XP i`m can ping my gateway (89.107.117.129). but in the ubuntu i`m can`t do it :( 
but i`m can ping my IP addres (89.107.117.152) and localhost.
When i`m ping my gateway (89.107.117.129) ubuntu tell me : Unreacheble.
why, what i`m do wrang ? please tell me what i must do )
PS please forgive me for my bad english

---

### Post by noob12 on 2007-11-17
Do you have link detected?
```

sudo ethtool eth0

```
Check the 'Link Detected' line.

---

### Post by allbecool on 2007-11-17
>$: sudo ethtool eth0:

> Settings for eth0:
	Supported ports: [ TP MII ]
	Supported link modes:   10baseT/Half 10baseT/Full 
	                        100baseT/Half 100baseT/Full 
	Supports auto-negotiation: Yes
	Advertised link modes:  10baseT/Half 10baseT/Full 
	                        100baseT/Half 100baseT/Full 
	Advertised auto-negotiation: Yes
	Speed: 100Mb/s
	Duplex: Full
	Port: MII
	PHYAD: 32
	Transceiver: internal
	Auto-negotiation: on
	Supports Wake-on: pumbg
	Wake-on: d
	Current message level: 0x00000007 (7)
	Link detected: yes

So ? my network card work  normal ?
but i`m again cant ping my gateway (89.107.117.129)

---

### Post by noob12 on 2007-11-17
Everything you've posted looks correct.

When you ping, do you see any errors on **tail /var/log/kern.log** ?

Can you please indicate what card and driver you are using?
```

lspci -nn

sudo lshw -C network

```

---

### Post by allbecool on 2007-11-18
I`m use Acorp network card with realtek chipset
it`s lspci -nn:
> 00:00.0 Host bridge [0600]: Intel Corporation 82946GZ/PL/GL Memory Controller Hub [8086:2970] (rev 02)
00:01.0 PCI bridge [0604]: Intel Corporation 82946GZ/PL/GL PCI Express Root Port [8086:2971] (rev 02)
00:1b.0 Audio device [0403]: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller [8086:27d8] (rev 01)
00:1c.0 PCI bridge [0604]: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 [8086:27d0] (rev 01)
00:1c.2 PCI bridge [0604]: Intel Corporation 82801G (ICH7 Family) PCI Express Port 3 [8086:27d4] (rev 01)
00:1d.0 USB Controller [0c03]: Intel Corporation 82801G (ICH7 Family) USB UHCI #1 [8086:27c8] (rev 01)
00:1d.1 USB Controller [0c03]: Intel Corporation 82801G (ICH7 Family) USB UHCI #2 [8086:27c9] (rev 01)
00:1d.2 USB Controller [0c03]: Intel Corporation 82801G (ICH7 Family) USB UHCI #3 [8086:27ca] (rev 01)
00:1d.3 USB Controller [0c03]: Intel Corporation 82801G (ICH7 Family) USB UHCI #4 [8086:27cb] (rev 01)
00:1d.7 USB Controller [0c03]: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller [8086:27cc] (rev 01)
00:1e.0 PCI bridge [0604]: Intel Corporation 82801 PCI Bridge [8086:244e] (rev e1)
00:1f.0 ISA bridge [0601]: Intel Corporation 82801GB/GR (ICH7 Family) LPC Interface Bridge [8086:27b8] (rev 01)
00:1f.1 IDE interface [0101]: Intel Corporation 82801G (ICH7 Family) IDE Controller [8086:27df] (rev 01)
00:1f.2 IDE interface [0101]: Intel Corporation 82801GB/GR/GH (ICH7 Family) Serial ATA Storage Controller IDE [8086:27c0] (rev 01)
00:1f.3 SMBus [0c05]: Intel Corporation 82801G (ICH7 Family) SMBus Controller [8086:27da] (rev 01)
01:00.0 VGA compatible controller [0300]: nVidia Corporation G70 [GeForce 7300 GT] [10de:0393] (rev a1)
02:00.0 Ethernet controller [0200]: Atheros Communications, Inc. Unknown device [168c:001c] (rev 01)
04:01.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ [10ec:8139] (rev 10)

it`s lshw -C network

```
  *-network UNCLAIMED
       description: Ethernet controller
       product: Atheros Communications, Inc.
       vendor: Atheros Communications, Inc.
       physical id: 0
       bus info: pci@02:00.0
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: cap_list
       configuration: latency=0
       resources: iomemory:feaf0000-feafffff irq:17
  *-network
       description: Ethernet interface
       product: RTL-8139/8139C/8139C+
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 1
       bus info: pci@04:01.0
       logical name: eth0
       version: 10
       serial: 00:e0:4c:51:22:14
       size: 100MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=8139too driverversion=0.9.28 duplex=full ip=89.107.117.152 latency=64 link=yes maxlatency=64 mingnt=32 multicast=yes port=MII speed=100MB/s
       resources: ioport:e800-e8ff iomemory:febffc00-febffcff irq:16

```

when i`m trying ping my gateway. I do not see anything about it  in /var/log/kern.log . No warning no fails nothing :)

---

### Post by noob12 on 2007-11-18
I don't see anything wrong at all.  If you don't see any errors in **dmesg** or **/var/kern.log**  one thing you might try is disabling IPV6 as follows.

Edit **/etc/modprobe.d/aliases** as root
Find the line
```

alias net-pf-10 ipv6

```

Replace it with this block which is also intended to remind you how to re-enable it if needed.
```

# disable IPV6
#alias net-pf-10 ipv6
alias net-pf-10 off
alias ipv6 off
# end disable IPV6

```

Reboot.

I don't have any other ideas.

---

### Post by allbecool on 2007-11-19
> **noob12 said:**
> I don't see anything wrong at all.  If you don't see any errors in **dmesg** or **/var/kern.log**  one thing you might try is disabling IPV6 as follows.

Edit **/etc/modprobe.d/aliases** as root
Find the line
```

alias net-pf-10 ipv6

```

Replace it with this block which is also intended to remind you how to re-enable it if needed.
```

# disable IPV6
#alias net-pf-10 ipv6
alias net-pf-10 off
alias ipv6 off
# end disable IPV6

```

Reboot.

I don't have any other ideas.
 
i`m try it , and this idea don`t help me :) 
But i`m see something that i`m thing wrang :)
when i`m try ping my gateway Ubutntu tell me that Host Unreacheble .
 But after ping i see in ifconfig that my Lo interfaces have some RX and TX packets, and it`s count grow as more as i`m ping , but eth0 don`t have any RX or TX packets. It`s normal ?. So i`m thing that problem in my route`s . 
> lo Link encap:Local Loopback 
inet addr:127.0.0.1 Mask:255.0.0.0
UP LOOPBACK RUNNING MTU:16436 Metric:1
RX packets:[COLOR="Red"][SIZE="3"]12[/SIZE][/COLOR] errors:0 dropped:0 overruns:0 frame:0
TX packets:[COLOR="#ff0000"][SIZE="3"]12[/SIZE][/COLOR] errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:0
RX bytes:[COLOR="#ff0000"]904 (904.0 b)[/COLOR] TX bytes:[COLOR="#ff0000"]904 (904.0 b)[/COLOR] [COLOR="#8b0000"][SIZE="4"]Why it` no 0 ?[/SIZE][/COLOR] 

> eth0 Link encap:Ethernet HWaddr 00:E0:4C:51:22:14 
inet addr:89.107.117.152 Bcast:89.107.117.255 Mask:255.255.255.128
UP BROADCAST RUNNING MULTICAST MTU:1500 Metric:1
RX packets:[COLOR="SandyBrown"][SIZE="3"]0[/SIZE][/COLOR] errors:0 dropped:0 overruns:0 frame:0
TX packets[COLOR="#f4a460"][SIZE="3"]:0[/SIZE][/COLOR] errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:1000
RX bytes:0 (0.0 b) TX bytes:0 (0.0 b) [COLOR="DarkRed"][SIZE="4"]Whay it`s 0 ?[/SIZE][/COLOR]
Interrupt:16 Base address:0x4c00

Please help me :) i`m don`t whant  more see Windows !! i`m want Linux !!! :) Save me from this evil ) save my soul.

---

### Post by noob12 on 2007-11-19
That is odd, but the **route -n** output that you showed earlier looked correct.  Has it changed?

Can you post the output of these commands as well
```

cat /etc/hosts

sudo iptables -nL

```

---

### Post by allbecool on 2007-11-20
That is /etc/hosts :

> 127.0.0.1 localhost
127.0.1.1 daimyo-desktop

# The following lines are desirable for IPv6 capable hosts

that - iptables -Ln :

```
Chain INPUT (policy ACCEPT)
target     prot opt source               destination         

Chain FORWARD (policy ACCEPT)
target     prot opt source               destination         

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination         

```

---

### Post by noob12 on 2007-11-21
I still see no problem at all.  Everything looks right.  

Do you see any entries in your arp table?
```

arp -an

```

---

### Post by allbecool on 2007-11-21
It`s Ubuntu tell me when i`m type command arp -an

> ? (89.107.117.129) at <incomplete> eth0


---

### Post by noob12 on 2007-11-21
Well that means the host thinks it sent an ARP request but hasn't received anything.  That's consistent with not sending  the ARP request properly or with not getting a response.

Do you have LED activity lights on the card?  Can you see evidence that you have a link and that you are seeing ethernet activity there?

---

### Post by allbecool on 2007-11-21
Ho Ho Ho !! 
You are right !!!. i can`t see any LED activity on the card in Ubuntu !. But in the Windows all good ).
What i`m must do chief ? ) What command will help me ? ) 

We so close to solve this problem , i`m think so . ) 
And why i`m can`t see any activity ? I`m dont understand it...

---

### Post by noob12 on 2007-11-22
OK.  I've never seen this problem with ethtool reporting link detected but the lights off, but it may be a variant of the one described here: [http://ubuntuforums.org/showthread.php?t=538448](http://ubuntuforums.org/showthread.php?t=538448)
Try that and see if it helps.

---

### Post by allbecool on 2007-11-23
It`s Work !!! i`m dont be leave it!!!
Thanks you ! for help me )
Very Very big thanks )

---

