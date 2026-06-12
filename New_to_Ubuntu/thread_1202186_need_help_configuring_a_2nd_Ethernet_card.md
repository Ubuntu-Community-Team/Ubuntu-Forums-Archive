---
title: "need help configuring a 2nd Ethernet card"
date: 2009-07-01
forum: New to Ubuntu
---

### Post by rockerphil on 2009-07-01
ok, the title pretty well sums it up but here's a quick rundown. i'm running a minimal install of 8.10 using Fluxbox as my WM and several other lightweight apps and im trying to configure a 2nd Ethernet card so that my main Internet connection can be shared to a 2nd computer running Fluxbuntu 7.10 (it's the only *buntu i could find that ran decent on the hardware) via the 2nd Card but i'm a little stupmed how to configure the card to do so. so i'm kicking it to you guys to see if i can find a solution. here's the output of "lspci"

```
phil@phillip:~$ lspci
00:00.0 Host bridge: Intel Corporation 82810E DC-133 (GMCH) Graphics Memory Controller Hub (rev 03)
00:01.0 VGA compatible controller: Intel Corporation 82810E DC-133 (CGC) Chipset Graphics Controller (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801AA PCI Bridge (rev 02)
00:1f.0 ISA bridge: Intel Corporation 82801AA ISA Bridge (LPC) (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801AA IDE Controller (rev 02)
00:1f.2 USB Controller: Intel Corporation 82801AA USB Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801AA SMBus Controller (rev 02)
01:08.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8169 Gigabit Ethernet (rev 10)
01:09.0 Multimedia audio controller: C-Media Electronics Inc CM8738 (rev 10)
01:0a.0 Ethernet controller: Unknown device 0113:8210 (rev 08)
01:0b.0 Communication controller: Conexant HCF 56k Data/Fax Modem (rev 08)
phil@phillip:~$ 
```

i'm connecting this machine to the net through the Realtek card and i'm trying to connect the 2nd machine through a D-Link PCI ethernet card which comes up as the "Unknown device 0113:8210 (rev 08)" any suggestions guys? i'm stumped as to where to go from here. much thanx in advance,

Phil

---

### Post by papenpj on 2009-07-02
Im not exactly sure how to go about sharing the internet connection on the second card. but the setup will be somewhat like this.
CompA has the two networks cards. Card one probably has an address like 192.168.1.100
so card two needs to be on a completely different network such as 192.168.2.1

then on computer B you want to be 
192.168.2.2 and use 192.168.1.1 as its gateway. ill check in a second what file

---

### Post by rockerphil on 2009-07-02
also here's the output of "sudo ifconfig"

```
phil@phillip:~$ sudo ifconfig
eth0      Link encap:Ethernet  HWaddr 00:14:d1:11:35:5b  
          inet addr:70.124.122.6  Bcast:255.255.255.255  Mask:255.255.240.0
          inet6 addr: fe80::214:d1ff:fe11:355b/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:109940 errors:0 dropped:0 overruns:0 frame:0
          TX packets:6340 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:12798541 (12.2 MB)  TX bytes:1308326 (1.2 MB)
          Interrupt:11 Base address:0x8c00 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:112 errors:0 dropped:0 overruns:0 frame:0
          TX packets:112 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:5056 (4.9 KB)  TX bytes:5056 (4.9 KB)
```

---

### Post by papenpj on 2009-07-02
ok open a terminal window on the computer with two cards.

run the command "sudo ifconfig" and show the results, then I can direct you to how you want to setup your /etc/network/interfaces file for the needed static ips

Then do the same for the second computer. Most likely your interfaces with be eth0 and eth1, just need to be sure. It would also be helpful if you know which each one physical is when it time to connect the cables. OH, and you will need a crossover cable to connect the two computers together, have you considered a cheap router or switch?

edit:
here is my /etc/network/interfaces
```

auto eth0
iface eth0 inet static
        address 192.168.0.55
        netmask 255.255.255.0
        network 192.168.0.0
        broadcast 192.168.0.255
        gateway 192.168.0.11

## Secondary network interface for sniffing
auto eth1
iface eth1 inet dhcp


```

---

### Post by papenpj on 2009-07-02
Im assuming what you posted was the computer with one card. But to refer to my previous post, What kind of Internet connection do you have? im thinking router will be most efficient route. You can pick them up pretty cheap on e-bay, havn't looked on newegg lately and you get the added benefit of not needing the one computer to run in order to have internet on the second.

However, if you wish to proceccd you need a file such as this on the second comp
```

auto eth0
iface eth0 inet static
        address 192.168.2.2
        netmask 255.255.255.0
        network 192.168.2.0
        broadcast 192.168.2.255
        gateway 192.168.2.1



```

The first comp
```

auto eth0
iface eth0 inet static
        address 192.168.2.1
        netmask 255.255.255.0
        network 192.168.2.0
        broadcast 192.168.2.255
        gateway (probably use the gateway you have from your other card, im not really sure)


auto eth1
iface eth1 inet dhcp



```

---

### Post by rockerphil on 2009-07-13
ok, i finally got back on my little networking project and finally found an old PCI Ethernet card that's auto-detected by Linux lying around. now, to the task at hand, as posted before i want to be able to network my 2nd Linux box in with my primary computer using a 2nd Ethernet card. i currently have all 3 Ethernet cards up and working, i just need some help in getting the two networked together, so here's some quick info that i'm sure will help. here's the output of ifconfig for the box with 2 cards

```
phil@phillip:~$ sudo ifconfig
eth0      Link encap:Ethernet  HWaddr 00:14:d1:11:35:5b  
          inet addr:70.124.123.15  Bcast:255.255.255.255  Mask:255.255.240.0
          inet6 addr: fe80::214:d1ff:fe11:355b/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:49822 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1380 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:4223250 (4.0 MB)  TX bytes:249275 (243.4 KB)
          Interrupt:11 Base address:0x8c00 

eth1      Link encap:Ethernet  HWaddr 00:c0:f0:2b:c4:29  
          inet6 addr: fe80::2c0:f0ff:fe2b:c429/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:144 errors:0 dropped:0 overruns:0 frame:0
          TX packets:23 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:8926 (8.7 KB)  TX bytes:6282 (6.1 KB)
          Interrupt:3 Base address:0xdf80 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:88 errors:0 dropped:0 overruns:0 frame:0
          TX packets:88 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:3696 (3.6 KB)  TX bytes:3696 (3.6 KB)
```

i already have the two boxes wired together via an extra ethernet cable i've got. any help is appreciated, much thanks in advance,

Phil

---

### Post by rockerphil on 2009-07-13
anyone?

---

### Post by papenpj on 2009-07-14
like I mentioned before, you will need a crossover cable to directly connect the Ethernet cards or ELSE THEY CANNOT COMMUNICATE. This is because a crossover cable directly connects the transmit of one card to the receive of the second and vice versa. If you use a standard cable both transmits get connected together which is why they won't communicate.


So unless you use standard cables on both comps to connect to a hub or switch at which point you could manually configure settings of the card. Then in that situation, I still suggest you go out and buy a cheap router or something off e-bay or see if a friend has one they will give you because why spend money on a cross over cable which might be expensive I really don't know I haven't priced them at a store lately as i make my own, when for a little more or even a little less you could have the ability to connect several computers to the same connection.

EDIT:
I still need to know what your internet connection is I'm running under the assumption you have Broadband of some form which in that case im still recommending a router that can be bought anywhere. easily $10 or less if you find the right one on e-bay.

---

