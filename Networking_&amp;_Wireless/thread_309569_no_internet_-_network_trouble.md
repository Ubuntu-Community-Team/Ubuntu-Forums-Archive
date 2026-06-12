---
title: "no internet - network trouble"
date: 2006-11-29
forum: Networking &amp; Wireless
---

### Post by jeeptime1 on 2006-11-29
I cannot connect to my home network (windows network) internet is cable modem into netgear router into multiple pcs - I've tried some things from searching other posts and posted the esults below -

all windows machines work fine

my ubuntu is new and so am I - Ubuntu is wired to router - I cannot ping the router - I can ping my ethernet card...

[COLOR="SeaGreen"]PING 127.0.0.1 (127.0.0.1) 56(84) bytes of data.
64 bytes from 127.0.0.1: icmp_seq=1 ttl=64 time=0.117 ms
64 bytes from 127.0.0.1: icmp_seq=2 ttl=64 time=0.087 ms
64 bytes from 127.0.0.1: icmp_seq=3 ttl=64 time=0.088 ms
64 bytes from 127.0.0.1: icmp_seq=4 ttl=64 time=0.093 ms
64 bytes from 127.0.0.1: icmp_seq=5 ttl=64 time=0.090 ms
64 bytes from 127.0.0.1: icmp_seq=6 ttl=64 time=0.089 ms
64 bytes from 127.0.0.1: icmp_seq=7 ttl=64 time=0.093 ms
64 bytes from 127.0.0.1: icmp_seq=8 ttl=64 time=0.093 ms
64 bytes from 127.0.0.1: icmp_seq=9 ttl=64 time=0.092 ms
64 bytes from 127.0.0.1: icmp_seq=10 ttl=64 time=0.092 ms

--- 127.0.0.1 ping statistics ---
10 packets transmitted, 10 received, 0 packets loss, time8998ms
rtt min/avg/max/mdev = 0.087/0.093/0.117/0.011 ms [/COLOR]

my ip addresses are dhcp

[COLOR="RoyalBlue"]ifconfig = 
ifconfig -a
eth1	Link encap:Ethernet  HWaddr  00:04:5A:58:9B:70
	inet6 addr:  fe80: :204:5aff:fe58:9b70/64 Scope:Link
	UP BROADCAST RUNNING MULTICAST  MTU:1500 Metric:1
	RX packets:0 errors:0 dropped:0 overruns:0 frame:0
	TX packets:0 errors:29 dropped:0 overruns:0 carrier:0
	collisions:0 txqueuelen:1000
	RX bytes:0 (0.0 b)   TX bytes:0 0.0 b)
	Interrupt:10 Base address:0xd400

lo	Link encap:Local Loopback
	Inet addr:127.0.0.1  Mask:255.0.0.0
	inet6 addr:  : :1/128 Scope Host
	UP LOOPBACK RUNNING   MTU:16436   Metric:1
	RX packets:187 errors:0 dropped:0 overruns:0 frame:0
	TX packets:187 errors:0 dropped:0 overruns:0 carrier:0
	collisions:0  txqueuelen:0
	RX bytes:11924  (11.6KiB)   TX bytes11924  (11.6KiB)

sit0	Link encap:IPv6-in-IPv4
	NOARP   MTU:1480   Metric:1
	RX packets:0 errors:0 dropped:0 overruns:0 frame:0
	TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
	collisions:0 txqueuelen:0
	Rx bytes:0 (0.0 b)   TX bytes:0  (0.0 b)[/COLOR]

[COLOR="MediumTurquoise"]/etc/network/interfaces

auto  lo
iface lo inet loopback

i face eth0 inet dhcp

i face eth1 inet dhcp

auto  eth2
i face eth2 inet dhcp

auto ath0
i face ath0 inet dhcp

auto wlan0
i face wlan0 inet dhcp [/COLOR]

---

### Post by trubblemaker on 2006-11-29
what happends when you do this:
```

sudo dhclient eth1

```

ps are you running a wirless card in that machine aswell or does it have two nics?

---

### Post by jeeptime1 on 2006-11-30
> **trubblemaker said:**
> what happends when you do this:
```

sudo dhclient eth1

```

Internet Systems Consortium DHCP Client V3.0.3
Copyright 2004-2005 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/products/DHHCP](http://www.isc.org/products/DHHCP)

Listening on LPF/eth1/00:04:5a:58:9b:70
Sending on   LPF/eth1/00:04:5a:58:9b:70
Sending on socket/fallback
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 inteval 5
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 inteval 8
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 inteval 9
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 inteval 18
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 inteval 13
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 inteval 7
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 inteval 1
No DHCPOFFERS received.
No working leases in persistant database - sleeping.


> **trubblemaker said:**
> 
ps are you running a wirless card in that machine aswell or does it have two nics?  
no wireless card installed

---

### Post by simon303 on 2006-11-30
just wondering, did you have any trouble installing the drivers for the ethernet card?

---

### Post by jeeptime1 on 2006-11-30
> **simon303 said:**
> just wondering, did you have any trouble installing the drivers for the ethernet card?

I have not manually installed any drivers.  
I'm just now setting up this computer, and new to ubuntu (and linux for that matter).  Although I feel I'm learning alot, quickly from researching thios problem on these forums.

---

### Post by j3cakes on 2006-11-30
it's not picking up an IP address. check your router and cabling to the router. or, to test, assign a static ip address (remember to give it a 'default gateway', if you want to test the internet at the same time.)

system -> network. make sure your interface is enabled and assign an ip address from the same range as your router. 

so, if your router is 192.168.0.1 (and has a subnet mask of 255.255.255.0) you'll want to use these settings:

IP add: 192.168.0.x (x = anything between 2 and 254 and can't already be in use on your LAN)
subnet mask: 255.255.255.0 (must match the entry in your router)
def gateway: 192.168.0.1

---

### Post by jeeptime1 on 2006-11-30
> **j3cakes said:**
> it's not picking up an IP address. check your router and cabling to the router. or, to test, assign a static ip address (remember to give it a 'default gateway', if you want to test the internet at the same time.)

system -> network. make sure your interface is enabled and assign an ip address from the same range as your router. 

I assigned a static ip as above.  Network settings shows the interface eth1 is active. I was still not able to connect to the router?

ping to my gatewaysdefault address = destination host uneachable

9 packets transmitted, 0 received, +6 errors, 100% packet loss, time 8008ms, pipe3

---

### Post by jeeptime1 on 2006-11-30
> **j3cakes said:**
> it's not picking up an IP address. check your router and cabling to the router. 

the router is working (the pc I'm using is connecting through it)

I have tried different cables.

---

### Post by j3cakes on 2006-11-30
> **jeeptime1 said:**
> 
I have tried different cables.

ok, but - I have to ask this - is it plugged in to the right ethernet port in your PC (I'm guessing you have two, given that it's eth1)

on your switch (or router, if it's got a built-in hub) do you have a link light for the port that this pc is plugged into?

do you have one on the pc network card as well?

---

### Post by trubblemaker on 2006-11-30
alternatively can you plug the internet straight into the computer and run:
```

sudo dhclient eth1

```

and for later

you will want to edit /etc/network/interfaces so that eth1 comes up on boot you can do that [COLOR="Red"]with:[/COLOR]

```
auto lo
iface lo inet loopback

iface eth0 inet dhcp

[COLOR="Red"]auto eth1[/COLOR]
iface eth1 inet dhcp

auto eth2
iface eth2 inet dhcp

auto ath0
iface ath0 inet dhcp

auto wlan0
iface wlan0 inet dhcp
```

as an aside, it's wierd that you can't get a wired connection. it's something linux does really well, so when it doesn't work, 9/10 times its a cabling, or hardware issue. That's why we're focusing on it not because we think that you can't setup up a computer.

---

### Post by jeeptime1 on 2006-11-30
> **trubblemaker said:**
> 
as an aside, it's wierd that you can't get a wired connection. it's something linux does really well, so when it doesn't work, 9/10 times its a cabling, or hardware issue. That's why we're focusing on it not because we think that you can't setup up a computer.

No problem - I'm for sure not beyond simple mistakes anyhow.

There is only 1 ethernet port on card - ubuntu desktop was plugged into lan3of4 port on wireless router.

I am going to try to go sraight into the card with the internet and run the code as above.

---

### Post by bxlinux on 2006-11-30
I tried to run the ifdown eth0 code but I am getting the message ifdown: failed to open statefile /var/run/network/ifstate: permission denied. Having the same issue as jeep here.

---

### Post by jeeptime1 on 2006-11-30
> **trubblemaker said:**
> alternatively can you plug the internet straight into the computer and run:
```

sudo dhclient eth1

```


[COLOR="Red"]Internet Systems Consortium DHCP Client V3.0.3
Copyright 2004-2005 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/products/DHCP](http://www.isc.org/products/DHCP)

Listening on LPF/eth1/00:04:5a:58:9b:70
Sending on  LPF/eth1/00:04:5a:58:9b:70
Sending on  Socket/fallback
DHCPDISCOVER on eth1 to 255:255:255:255: port 67 interval 6
DHCPDISCOVER on eth1 to 255:255:255:255: port 67 interval 13
DHCPDISCOVER on eth1 to 255:255:255:255: port 67 interval 15
DHCPDISCOVER on eth1 to 255:255:255:255: port 67 interval 15
DHCPDISCOVER on eth1 to 255:255:255:255: port 67 interval 11
DHCPDISCOVER on eth1 to 255:255:255:255: port 67 interval 1
No DHCPOFFERS received.
No working leases inn persistant database - sleeping.[/COLOR]



ok, but - I have to ask this - is it plugged in to the right ethernet port in your PC (I'm guessing you have two, given that it's eth1) [COLOR="red"]only 1 port on pc[/COLOR]

on your switch (or router, if it's got a built-in hub) do you have a link light for the port that this pc is plugged into?
[COLOR="red"]yes, the numbers 1 thru 4 light up when plugged in (1,2 & 3 are lit)[/COLOR]

do you have one on the pc network card as well?
[COLOR="red"]there is a green led and an amber led, [edit]both are lit[/COLOR]

[COLOR="red"]please don't hesitate to suggest that I may have overlooked or messed up something simple.  I don't know what I'm doing.  I've only done the checks that I have from searching these forums.
Thanks again for all the help.[/COLOR]

---

### Post by trubblemaker on 2006-12-01
ok lets dig deeper, can you please post the output form the following commands:

```
dmesg 
ifconfig
route
cat /etc/iftab 
ping router-address
lspci | grep controller # edit

```

please make sure to wrap the dmesg output in a "code" block it's the '#' button beside the quote.

---

### Post by jeeptime1 on 2006-12-01
Trouble,

I will run those tomorrow.

Please watch for the reply.  Thank you for your help and your patience.   I cannot copy and paste as you may have noticed, so there's a delay in my typing in the results.  

Today I don't have acces to my network.  I did not have any luck before when I tried connecting to the network at work, so I won't bother muddying the waters with that.

I should get to this in the late AM here tomorrow.

---

### Post by trubblemaker on 2006-12-02
.

---

### Post by jeeptime1 on 2006-12-02
I just got home, I'll run thaose now.

---

### Post by jeeptime1 on 2006-12-02
I'm sorry if I posted alot of irrelevant text.  I hope it's not a problem putting them all in one reply.

> ok lets dig deeper, can you please post the output form the following commands:

```
dmesg 
ifconfig
route
cat /etc/iftab 
ping router-address
lspci | grep controller # edit
```
please make sure to wrap the dmesg output in a "code" block it's the '#' button beside the quote

```
bob@ubuntu-silver1:~$ dmesg
[17179569.184000] Linux version 2.6.15-26-386 (buildd@terranova) (gcc version 4.0.3 (Ubuntu 4.0.3-1ubuntu5)) #1 PREEMPT Thu Aug 3 02:52:00 UTC 2006
[17179569.184000] BIOS-provided physical RAM map:
[17179569.184000]  BIOS-e820: 0000000000000000 - 000000000009fc00 (usable)
[17179569.184000]  BIOS-e820: 000000000009fc00 - 00000000000a0000 (reserved)
[17179569.184000]  BIOS-e820: 00000000000f0000 - 0000000000100000 (reserved)
[17179569.184000]  BIOS-e820: 0000000000100000 - 000000000c000000 (usable)
[17179569.184000]  BIOS-e820: 00000000ffff0000 - 0000000100000000 (reserved)
[17179569.184000] 0MB HIGHMEM available.
[17179569.184000] 192MB LOWMEM available.
[17179569.184000] On node 0 totalpages: 49152
[17179569.184000]   DMA zone: 4096 pages, LIFO batch:0
[17179569.184000]   DMA32 zone: 0 pages, LIFO batch:0
[17179569.184000]   Normal zone: 45056 pages, LIFO batch:15
[17179569.184000]   HighMem zone: 0 pages, LIFO batch:0
[17179569.184000] DMI 2.2 present.
[17179569.184000] ACPI: Unable to locate RSDP
[17179569.184000] Allocating PCI resources starting at 10000000 (gap: 0c000000:f3ff0000)
[17179569.184000] Built 1 zonelists
[17179569.184000] Kernel command line: root=/dev/hda1 ro quiet splash
[17179569.184000] Local APIC disabled by BIOS (or by default) -- you can enable it with "lapic"
[17179569.184000] mapped APIC to ffffd000 (01181000)
[17179569.184000] Initializing CPU#0
[17179569.184000] PID hash table entries: 1024 (order: 10, 16384 bytes)
[    0.000000] Detected 487.573 MHz processor.
[   22.930592] Using tsc for high-res timesource
[   22.932023] Console: colour VGA+ 80x25
[   22.933047] Dentry cache hash table entries: 32768 (order: 5, 131072 bytes)
[   22.934101] Inode-cache hash table entries: 16384 (order: 4, 65536 bytes)
[   22.965002] Memory: 184244k/196608k available (1976k kernel code, 11876k reserved, 606k data, 288k init, 0k highmem)
[   22.965018] Checking if this processor honours the WP bit even in supervisor mode... Ok.
[   23.041482] Calibrating delay using timer specific routine.. 976.36 BogoMIPS (lpj=1952733)
[   23.041597] Security Framework v1.0.0 initialized
[   23.041626] SELinux:  Disabled at boot.
[   23.041677] Mount-cache hash table entries: 512
[   23.042009] CPU: After generic identify, caps: 0183f9ff 00000000 00000000 00000000 00000000 00000000 00000000
[   23.042040] CPU: After vendor identify, caps: 0183f9ff 00000000 00000000 00000000 00000000 00000000 00000000
[   23.042071] CPU: L1 I cache: 16K, L1 D cache: 16K
[   23.042081] CPU: L2 cache: 128K
[   23.042091] CPU: After all inits, caps: 0183f9ff 00000000 00000000 00000040 00000000 00000000 00000000
[   23.042149] mtrr: v2.0 (20020519)
[   23.042166] CPU: Intel Celeron (Mendocino) stepping 00
[   23.042180] Enabling fast FPU save and restore... done.
[   23.042195] Checking 'hlt' instruction... OK.
[   23.058035] checking if image is initramfs... it is
[   26.336963] Freeing initrd memory: 6840k freed
[   26.400492] NET: Registered protocol family 16
[   26.400627] EISA bus registered
[   26.414538] PCI: PCI BIOS revision 2.10 entry at 0xfb3a0, last bus=1
[   26.414563] PCI: Using configuration type 1
[   26.416093] ACPI: Subsystem revision 20051216
[   26.416105] ACPI: Interpreter disabled.
[   26.416117] Linux Plug and Play Support v0.97 (c) Adam Belay
[   26.416145] pnp: PnP ACPI: disabled
[   26.416163] PnPBIOS: Scanning system for PnP BIOS support...
[   26.416645] PnPBIOS: Found PnP BIOS installation structure at 0xc00fbfc0
```

```
bob@ubuntu-silver1:~$ ifconfig
eth1      Link encap:Ethernet  HWaddr 00:04:5A:58:9B:70
          inet addr:192.168.1.10  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::204:5aff:fe58:9b70/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:10 Base address:0xd400

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:169 errors:0 dropped:0 overruns:0 frame:0
          TX packets:169 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:9456 (9.2 KiB)  TX bytes:9456 (9.2 KiB)
```


```
bob@ubuntu-silver1:~$ route
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.1.0     *               255.255.255.0   U     0      0        0 eth1
default         192.168.1.1     0.0.0.0         UG    0      0        0 eth1
```



```

bob@ubuntu-silver1:~$ cat /etc/iftab
# This file assigns persistent names to network interfaces.
# See iftab(5) for syntax.

eth0 mac 00:a0:c9:22:f3:ac arp 1
bob@ubuntu-silver1:~$
```



```
bob@ubuntu-silver1:~$ ping 192.168.0.1
PING 192.168.0.1 (192.168.0.1) 56(84) bytes of data.
From 192.168.1.10 icmp_seq=2 Destination Host Unreachable
From 192.168.1.10 icmp_seq=3 Destination Host Unreachable
From 192.168.1.10 icmp_seq=4 Destination Host Unreachable

--- 192.168.0.1 ping statistics ---
7 packets transmitted, 0 received, +3 errors, 100% packet loss, time 6003ms
, pipe 3
bob@ubuntu-silver1:~$ ping 192.168.1.1
PING 192.168.1.1 (192.168.1.1) 56(84) bytes of data.
From 192.168.1.10 icmp_seq=2 Destination Host Unreachable
From 192.168.1.10 icmp_seq=3 Destination Host Unreachable
From 192.168.1.10 icmp_seq=4 Destination Host Unreachable

--- 192.168.1.1 ping statistics ---
6 packets transmitted, 0 received, +3 errors, 100% packet loss, time 5003ms
, pipe 3
bob@ubuntu-silver1:~$
```



```

bob@ubuntu-silver1:~$ lspci | grep controller # edit
0000:00:09.0 Ethernet controller: Linksys NC100 Network Everywhere Fast Ethernet 10/100 (rev 11)
0000:00:13.0 Mass storage controller: Triones Technologies, Inc. HPT366/368/370/370A/372/372N (rev 01)
0000:00:13.1 Mass storage controller: Triones Technologies, Inc. HPT366/368/370/370A/372/372N (rev 01)
0000:01:00.0 VGA compatible controller: Silicon Integrated Systems [SiS] 86C326 5598/6326 (rev 0b)
bob@ubuntu-silver1:~$
```

---

### Post by dbott67 on 2006-12-02
Hi Jeeptime1,

I was just looking at your **/etc/network/interfaces** file.  

1. Can you please post the current output of:
```
cat /etc/network/interfaces
```

This is mine as an example:
```
dbott@edgy:~$ cat /etc/network/interfaces 
auto lo
iface lo inet loopback

auto eth0
iface eth0 inet dhcp

[B][COLOR="Red"]auto eth1
iface eth1 inet dhcp[/COLOR][/B]

auto eth2
iface eth2 inet dhcp

auto ath0
iface ath0 inet dhcp

auto wlan0
iface wlan0 inet dhcp

```

The things I noticed about yours (as trubblemaker stated in post #10) is that the 'auto eth1' is missing.  If you post your interfaces file, we can make sure it's correct.

2. What is the IP address of your router?  From your posts, it appears to be 192.168.1.1.  You can verify it by checking your IP configuration from one of your [COLOR="Red"]working[/COLOR] Windows computers using the **ipconfig /all** command.
```
Microsoft Windows XP [Version 5.1.2600]
(C) Copyright 1985-2001 Microsoft Corp.

C:\WINDOWS>ipconfig /all

Windows IP Configuration

        Host Name . . . . . . . . . . . . : omega-xp
        Primary Dns Suffix  . . . . . . . :
        Node Type . . . . . . . . . . . . : Unknown
        IP Routing Enabled. . . . . . . . : No
        WINS Proxy Enabled. . . . . . . . : No

Ethernet adapter Local Area Connection:

        Media State . . . . . . . . . . . : Media disconnected
        Description . . . . . . . . . . . : Broadcom 440x 10/100 Integrated Cont
roller
        Physical Address. . . . . . . . . : 00-15-C5-0C-AD-05

Ethernet adapter Wireless Network Connection:

        Connection-specific DNS Suffix  . :
        Description . . . . . . . . . . . : Dell Wireless 1390 WLAN Mini-Card
        Physical Address. . . . . . . . . : 00-16-CE-31-88-6F
        Dhcp Enabled. . . . . . . . . . . : Yes
        Autoconfiguration Enabled . . . . : Yes
        IP Address. . . . . . . . . . . . : 192.168.1.105
        Subnet Mask . . . . . . . . . . . : 255.255.255.0
        [B][COLOR="Red"]Default Gateway . . . . . . . . . : 192.168.1.1
        DHCP Server . . . . . . . . . . . : 192.168.1.1
        DNS Servers . . . . . . . . . . . : 192.168.1.1[/COLOR][/B]
        Lease Obtained. . . . . . . . . . : Saturday, December 02, 2006 3:25:06
PM
        Lease Expires . . . . . . . . . . : Saturday, December 09, 2006 3:25:06
PM

C:\WINDOWS>
```

3. Can you post the output of:
```
sudo lshw -C network
```

4. Lastly, can you post the output cat /etc/resolv.conf:
```
dbott@edgy:~$ cat /etc/resolv.conf 
nameserver 192.168.1.1

```

Thanks,
Dave

---

### Post by jeeptime1 on 2006-12-02
thanks Dave, here we go

> 1. Can you please post the current output of:

```

cat /etc/network/interfaces
```


```
bob@ubuntu-silver1:~$ cat /etc/network/interfaces
auto lo
iface lo inet loopback

iface eth0 inet dhcp

iface eth1 inet static
address 192.168.01.10
netmask 255.255.255.0
gateway 192.168.01.1

auto eth2
iface eth2 inet dhcp

auto ath0
iface ath0 inet dhcp

auto wlan0
iface wlan0 inet dhcp

auto eth1
```


> 2. What is the IP address of your router? From your posts, it appears to be 192.168.1.1. You can verify it by checking your IP configuration from one of your working Windows computers using the ipconfig /all command.

Yes that is my router's IP -  192.168.1.1

> 3. Can you post the output of:

```

sudo lshw -C network4. Lastly, can you post the output cat /etc/resolv.conf:
```

```
bob@ubuntu-silver1:~$ sudo lshw -C network
Password:
  *-network
       description: Ethernet interface
       product: NC100 Network Everywhere Fast Ethernet 10/100
       vendor: Linksys
       physical id: 9
       bus info: pci@00:09.0
       logical name: eth1
       version: 11
       serial: 00:04:5a:58:9b:70
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=tulip driverversion=1.1.13 ip=192.168.1.10 multicast=yes
       resources: ioport:d400-d4ff iomemory:de800000-de8003ff irq:10
```


> 
```
dbott@edgy:~$ cat /etc/resolv.conf 
nameserver 192.168.1.1
```

nothing came up for this one.

---

### Post by jeeptime1 on 2006-12-02
I did number 4 wrong - I'll try it again

---

### Post by jeeptime1 on 2006-12-02
I must be doing something wrong with your last request, because, nothing comes up.

---

### Post by dbott67 on 2006-12-02
I believe the 'resolv.conf' file is created each time the IP is 'renewed' if you use DHCP.  Due to the fact that you have a static IP (and the associated GATEWAY entry in the /etc/network/interfaces file), it's probably not an issue.

The first 2 recommendations would be:
1. Edit the /etc/network/interfaces file and change the following:
```
iface eth1 inet static
address 192.168.**0**1.10 *[COLOR="Blue"]<--- remove the zero[/COLOR]*
netmask 255.255.255.0
gateway 192.168.**0**1.1 *[COLOR="Blue"]<--- remove the zero[/COLOR]*
```

I don't see how/why the zero in front would be an issue, but you never know.

2. Disable & re-enable the network interface:
```
sudo ifdown eth1
```
```
sudo ifdup eth1
```

The other piece of info that I require is your routing table:
```
dbott@edgy:~$ **route -n**
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.1.0     0.0.0.0         255.255.255.0   U     0      0        0 eth0
0.0.0.0         192.168.1.1     0.0.0.0         UG    0      0        0 eth0

```

-Dave

---

### Post by jeeptime1 on 2006-12-02
I am having trouble with step 1

> 1. Edit the /etc/network/interfaces file and change the following:

```
iface eth1 inet static
address 192.168.01.10 <--- remove the zero
netmask 255.255.255.0
gateway 192.168.01.1 <--- remove the zero
```

> The other piece of info that I require is your routing table:
```

bob@ubuntu-silver1:~$ route -n
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.1.0     0.0.0.0         255.255.255.0   U     0      0        0 eth1
0.0.0.0         192.168.1.1     0.0.0.0         UG    0      0        0 eth1
```

---

### Post by dbott67 on 2006-12-02
To edit the interfaces file:
```
gksudo gedit /etc/network/interfaces
```
Replace this text:
```
iface eth1 inet static
address 192.168.01.10
netmask 255.255.255.0
gateway 192.168.01.1

```
With this text:
```
iface eth1 inet static
address 192.168.1.10
netmask 255.255.255.0
gateway 192.168.1.1

```

Save & close.  Then **sudo ifdown eth1** and **sudo ifup eth1**.

-Dave

---

### Post by trubblemaker on 2006-12-02
you know what bugs me is the entry in you 
/etc/iftab:

> eth0 mac 00:a0:c9:22:f3:ac arp 1

why is it there if your don't have another nic in you computer?

the mac of the card installed is:>  00:04:5a:58:9b:70
can you edit the /etc/iftab file to read
> eth1 mac 00:04:5a:58:9b:70 arp 1 
it might not fix anything but at least it will remove an incorrect statement on your computer.

---

### Post by trubblemaker on 2006-12-02
Hey on the off chance, you see this:

```

[COLOR="Red"]There is already a pid file /var/run/dhclient.pid with pid 134993416[/COLOR]
Internet systems Consortium DHCP Client V3.0.4

Listening on LPF/eth0/00:11:43:3c:6c:f8
sending on LPF/eth0/00:11:43:3c:6c:f8
sending on Socket/fallback
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 6
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 20
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 7
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 7
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 7
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 14
No DHCPOFFERS received
No working leases in persistent database - sleeping

```

I have seen some people fix the issue with deleting that file.  Just in case it's not your issue, you might want to make a backup.  

*note* the pid will surely be different

---

### Post by jeeptime1 on 2006-12-02
> Replace this text:

```

iface eth1 inet static
address 192.168.01.10
netmask 255.255.255.0
gateway 192.168.01.1With this text:

Code:
iface eth1 inet static
address 192.168.1.10
netmask 255.255.255.0
gateway 192.168.1.1
```

Save & close. Then sudo ifdown eth1 and sudo ifup eth1.

-Dave

I did this - thanks for the help with the editing.


> can you edit the /etc/iftab file to read

eth1 mac 00:04:5a:58:9b:70 arp 1  

it might not fix anything but at least it will remove an incorrect statement on your computer.

And I did that.


> Hey on the off chance, you see this:

```
There is already a pid file /var/run/dhclient.pid with pid 134993416
Internet systems Consortium DHCP Client V3.0.4

Listening on LPF/eth0/00:11:43:3c:6c:f8
sending on LPF/eth0/00:11:43:3c:6c:f8
sending on Socket/fallback
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 6
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 20
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 7
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 7
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 7
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 14
No DHCPOFFERS received
No working leases in persistent database - sleeping
```
I have seen some people fix the issue with deleting that file. Just in case it's not your issue, you might want to make a backup. 

*note* the pid will surely be different

I don't recall what I was supposed to run for this. It did not come up on it's own.

I will come back to this after some sleep - up all night at work last night.  Also I should brush up on these commands - the ubuntu book I was reading mostly dealt with the graphic interface.  I want to learn more about working with the shell.  Thanks for the help so far.  I will be reviewing everything we've done, till I get a better grasp.

I'll check back tomorrow.

---

### Post by dbott67 on 2006-12-02
> **jeeptime1 said:**
> I don't recall what I was supposed to run for this. It did not come up on it's own.

The command normally appears when you are using DHCP:
```
...
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 6
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 20
... 
```

Not sure if the *"There is already a pid file /var/run/dhclient.pid with pid 134993416"* shows up when you use static IPs (the dhclient.pid appears to be an element of DHCP).  I use DHCP and whenever I 
```
sudo ifdown eth0 && sudo ifup eth0
```
I get the dhclient.pid message which is summarily killed whenever I run it:
```
dbott@edgy:~$ sudo ifdown eth0 && sudo ifup eth0
[COLOR="Red"]There is already a pid file /var/run/dhclient.eth0.pid with pid 6838
killed old client process, removed PID file[/COLOR]
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

Listening on LPF/eth0/00:50:ba:c0:a7:55
Sending on   LPF/eth0/00:50:ba:c0:a7:55
Sending on   Socket/fallback
DHCPRELEASE on eth0 to 192.168.1.1 port 67
There is already a pid file /var/run/dhclient.eth0.pid with pid 134993416
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

Listening on LPF/eth0/00:50:ba:c0:a7:55
Sending on   LPF/eth0/00:50:ba:c0:a7:55
Sending on   Socket/fallback
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 7
DHCPOFFER from 192.168.1.1
DHCPREQUEST on eth0 to 255.255.255.255 port 67
DHCPACK from 192.168.1.1
bound to 192.168.1.106 -- renewal in 239212 seconds.
```

-Dave

---

### Post by jeeptime1 on 2006-12-03
OK, I feel better now.

I ran some of these items again this AM.

```
bob@ubuntu-silver1:~$ cat /etc/iftab
# This file assigns persistent names to network interfaces.
# See iftab(5) for syntax.

eth1 mac 00:04:5a:58:9b:70 arp 1
bob@ubuntu-silver1:~$
```
I guess i did the mac address change right?


```
bob@ubuntu-silver1:~$ ifconfig
eth1      Link encap:Ethernet  HWaddr 00:04:5A:58:9B:70
          inet6 addr: fe80::204:5aff:fe58:9b70/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:67 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:10 Base address:0xd400

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:324 errors:0 dropped:0 overruns:0 frame:0
          TX packets:324 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:20896 (20.4 KiB)  TX bytes:20896 (20.4 KiB)

bob@ubuntu-silver1:~$
```
This time I see errors:67 - I don'r remember those from before.


```

bob@ubuntu-silver1:~$ ping 192.168.1.1
connect: Network is unreachable
bob@ubuntu-silver1:~$
```


```
bob@ubuntu-silver1:~$ route
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
bob@ubuntu-silver1:~$
```

Let me know if these help or if can I can do something else.

BTW I was assuming that my network card was seen, recognized and configured. Now I'm wondering if it's configured.

---

### Post by jeeptime1 on 2006-12-03
I forgot to mention
When I try to force down eth1, I get
interface not configured

BTW  I never did change the command for the boot up

Bob

---

### Post by dbott67 on 2006-12-03
> **jeeptime1 said:**
> OK, I feel better now.

I ran some of these items again this AM.
```

bob@ubuntu-silver1:~$ ping 192.168.1.1
connect: Network is unreachable
bob@ubuntu-silver1:~$
```


```
bob@ubuntu-silver1:~$ route
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
bob@ubuntu-silver1:~$
```

Let me know if these help or if can I can do something else.

BTW I was assuming that my network card was seen, recognized and configured. Now I'm wondering if it's configured.

Your computer definitely sees the NIC (the output of **sudo lshw -C network** confirms this).

You're right in that it is not currently configured.  Under normal circumstances, either of the following commands could be used to "restart" the network:
```
dbott@edgy:~$ **sudo ifdown eth0 && sudo ifup eth0**
There is already a pid file /var/run/dhclient.eth0.pid with pid 6838
killed old client process, removed PID file
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

Listening on LPF/eth0/00:50:ba:c0:a7:55
Sending on   LPF/eth0/00:50:ba:c0:a7:55
Sending on   Socket/fallback
DHCPRELEASE on eth0 to 192.168.1.1 port 67
There is already a pid file /var/run/dhclient.eth0.pid with pid 134993416
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

Listening on LPF/eth0/00:50:ba:c0:a7:55
Sending on   LPF/eth0/00:50:ba:c0:a7:55
Sending on   Socket/fallback
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 7
DHCPOFFER from 192.168.1.1
DHCPREQUEST on eth0 to 255.255.255.255 port 67
DHCPACK from 192.168.1.1
bound to 192.168.1.106 -- renewal in 239212 seconds.
```
or
```
dbott@edgy:~$ **sudo /etc/init.d/networking restart**
Password:
 * Reconfiguring network interfaces...                                          There is already a pid file /var/run/dhclient.eth0.pid with pid 3172
killed old client process, removed PID file
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

Listening on LPF/eth0/00:50:ba:c0:a7:55
Sending on   LPF/eth0/00:50:ba:c0:a7:55
Sending on   Socket/fallback
DHCPRELEASE on eth0 to 192.168.1.1 port 67
There is already a pid file /var/run/dhclient.eth0.pid with pid 134993416
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

Listening on LPF/eth0/00:50:ba:c0:a7:55
Sending on   LPF/eth0/00:50:ba:c0:a7:55
Sending on   Socket/fallback
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 3
DHCPOFFER from 192.168.1.1
DHCPREQUEST on eth0 to 255.255.255.255 port 67
DHCPACK from 192.168.1.1
bound to 192.168.1.106 -- renewal in 242774 seconds.
There is already a pid file /var/run/dhclient.eth1.pid with pid 134993416
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

SIOCSIFADDR: No such device
eth1: ERROR while getting interface flags: No such device
eth1: ERROR while getting interface flags: No such device
Bind socket to interface: No such device
Failed to bring up eth1.
There is already a pid file /var/run/dhclient.eth2.pid with pid 134993416
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

SIOCSIFADDR: No such device
eth2: ERROR while getting interface flags: No such device
eth2: ERROR while getting interface flags: No such device
Bind socket to interface: No such device
Failed to bring up eth2.
There is already a pid file /var/run/dhclient.ath0.pid with pid 134993416
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

SIOCSIFADDR: No such device
ath0: ERROR while getting interface flags: No such device
ath0: ERROR while getting interface flags: No such device
Bind socket to interface: No such device
Failed to bring up ath0.
There is already a pid file /var/run/dhclient.wlan0.pid with pid 134993416
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

SIOCSIFADDR: No such device
wlan0: ERROR while getting interface flags: No such device
wlan0: ERROR while getting interface flags: No such device
Bind socket to interface: No such device
Failed to bring up wlan0.
                                                                         [ ok ]

```

My first step at this point would be to issue one of the above commands just to see if the interface activates.  If it does not, then your interfaces file could be corrupt.

**_Replacing a Corrupt interfaces file_**

1. Backup the existing /etc/network/interfaces file:
```
sudo mv /etc/network/interfaces /etc/network/interfaces.bak
```

2. Create a new interfaces file:
```
sudo touch /etc/network/interfaces
```

3. Edit the file:
```
gksudo gedit /etc/network/interfaces
```

4. Add the following text:
```
auto lo
iface lo inet loopback

auto eth0
iface eth0 inet dhcp

auto eth1
iface eth1 inet dhcp

auto eth2
iface eth2 inet dhcp

auto ath0
iface ath0 inet dhcp

auto wlan0
iface wlan0 inet dhcp

```

5. Restart the computer.

Check the output of **ifconfig -a**, **route -n** and ping **192.168.1.1**.

The fact that route -n does not display a default route stems from the fact that the NIC is not active.  Once it is active, you should get something like this:
```
dbott@dapper:~$ **route -n**
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.1.0     0.0.0.0         255.255.255.0   U     0      0        0 eth0
0.0.0.0         192.168.1.1     0.0.0.0         UG    0      0        0 eth0
```

-Dave

---

### Post by dbott67 on 2006-12-03
The other thing that just came to mind was firewall issues.  Are you running a software firewall of any type (iptables, firestarter, etc.)?  Can you please post the output of **sudo iptables -L**:

```
dbott@edgy:~$ sudo iptables -L
Password:
Chain INPUT (policy ACCEPT)
target     prot opt source               destination         

Chain FORWARD (policy ACCEPT)
target     prot opt source               destination         

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination       
```

---

### Post by jeeptime1 on 2006-12-03
> The other thing that just came to mind was firewall issues. Are you running a software firewall of any type (iptables, firestarter, etc.)? 
No


> Can you please post the output of sudo iptables -L:

```

dbott@edgy:~$ sudo iptables -L
Password:
Chain INPUT (policy ACCEPT)
target     prot opt source               destination         

Chain FORWARD (policy ACCEPT)
target     prot opt source               destination         

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination
```
Mine came up the exact same as yours.

---

### Post by jeeptime1 on 2006-12-04
> My first step at this point would be to issue one of the above commands just to see if the interface activates. If it does not, then your interfaces file could be corrupt.

I ran this one.
```
bob@ubuntu-silver1:~$ sudo /etc/init.d/networking restart
Password:
 * Reconfiguring network interfaces... Internet Systems Consortium DHCP Client V3.0.3
Copyright 2004-2005 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/products/DHCP

SIOCSIFADDR: No such device
eth2: ERROR while getting interface flags: No such device
eth2: ERROR while getting interface flags: No such device
Bind socket to interface: No such device
Failed to bring up eth2.
Internet Systems Consortium DHCP Client V3.0.3
Copyright 2004-2005 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/products/DHCP

SIOCSIFADDR: No such device
ath0: ERROR while getting interface flags: No such device
ath0: ERROR while getting interface flags: No such device
Bind socket to interface: No such device
Failed to bring up ath0.
Internet Systems Consortium DHCP Client V3.0.3
Copyright 2004-2005 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/products/DHCP

SIOCSIFADDR: No such device
wlan0: ERROR while getting interface flags: No such device
wlan0: ERROR while getting interface flags: No such device
Bind socket to interface: No such device
Failed to bring up wlan0.
```


> Replacing a Corrupt interfaces file

1. Backup the existing /etc/network/interfaces file:

```
sudo mv /etc/network/interfaces /etc/network/interfaces.bak2. Create a new interfaces file:
```

```
sudo touch /etc/network/interfaces3. Edit the file:
```

```
gksudo gedit /etc/network/interfaces4. Add the following text:
```

```
auto lo
iface lo inet loopback

auto eth0
iface eth0 inet dhcp

auto eth1
iface eth1 inet dhcp

auto eth2
iface eth2 inet dhcp

auto ath0
iface ath0 inet dhcp

auto wlan0
iface wlan0 inet dhcp
```
5. Restart the computer.

I did the above.



> Check the output of ```
ifconfig -a, route -n and ping 192.168.1.1
```

```
bob@ubuntu-silver1:~$ ifconfig -a
eth1      Link encap:Ethernet  HWaddr 00:04:5A:58:9B:70
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:10 Base address:0xd400

lo        Link encap:Local Loopback
          LOOPBACK  MTU:16436  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

sit0      Link encap:IPv6-in-IPv4
          NOARP  MTU:1480  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
```

```
bob@ubuntu-silver1:~$ route -n
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
bob@ubuntu-silver1:~$
```


```

bob@ubuntu-silver1:~$ ping 192.168.1.1
connect: Network is unreachable
bob@ubuntu-silver1:~$
```

---

### Post by bxlinux on 2006-12-04
Hey Jeep sorry to be in your thread bud but I am having the same issue. I issued the above commands and mine came out exactly as did Jeeps. I did load windows on my laptop and that ran fine so I know its not a hardware issue. The only difference between me and jeeps is that I am not running through a router. Directly through the modem.

---

### Post by dbott67 on 2006-12-04
Hi Bob,

I'm getting stumped as to why the eth1 'was' configured in an earlier post, but is not activating now.  Very strange....

Here's a little trick: Sometimes, when I use the Live CD of a distro, everything works fine, but after installation to hard drive, things don't always work.

So, try this: boot the Live CD and see if you can get online (ping, internet, whatever).  If so, copy the following files to a USB or floppy, boot back into your installed version and copy the files over the existing ones.

1. /etc/network/interfaces


Also, make note of the network driver being used in the "Live" version.  Your "installed" driver is 'tulip':
```
bob@ubuntu-silver1:~$ sudo lshw -C network
Password:
  *-network
       description: Ethernet interface
       product: NC100 Network Everywhere Fast Ethernet 10/100
       vendor: Linksys
       physical id: 9
       bus info: pci@00:09.0
       logical name: eth1
       version: 11
       serial: 00:04:5a:58:9b:70
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes [COLOR="Red"]driver=tulip[/COLOR] driverversion=1.1.13 ip=192.168.1.10 multicast=yes
       resources: ioport:d400-d4ff iomemory:de800000-de8003ff irq:10
```

We just want to see if there are any differences between the "Live" configuration files and the "intalled" config files.  It's also possible that one of the config files is corrupt.  Depending on how much data or customization you've done, it may be easier to do a re-install if the Live CD works.

-Dave

---

### Post by jeeptime1 on 2006-12-05
Well, I'm sorry but last night I threw in the towel and tried a re-install.  This time I tried from A version that came with a book that I bought.  During install I got the following error message:

> Network Configuration Failed
Your network is probably not using DHCP Protocol.  Alternatively, the DHCP Server may be slow or some network hardware is not working properly.

SO, I replaced the card (again), tis time with a diffeerent brand/style.  During install, this time it made it through the network setup succesfully.  I'm waiting for it to finish installing then I'll let you know if it works.

Thank for all of your help.

Bob

---

### Post by jeeptime1 on 2006-12-05
Well, I'm connected and installing updates.

I replaced the network card again as stated above.  The 2 cards that I removed were the models below (I don't know which one was the more recent/I already mixed them up) From my previous post it appears that it was number1 below that we were woprking with.  Both appear to be made by Linksys, which makes sense because they look very similar compared to the I have installed now
 
1. Network Everywhere Fast Ethernet 10/100 Network Card
   Model No. NC100
   Version 2.1

2. Linksys Etherfast 10/100 LAN Card
   Model No. LNE100TX
   Version 5.0

I don't know if the cards were bad, unsupported, or if I screwed something up by switching them and not configuring correctly.

I post this information to:
1. Thank those that tried to help (I learned alot from that help)
2. Maybe someone can tell from previous post in this thread and/or anything else I can post now, what the problem was or fix could be for someone else with same problem.

BX, I don't know if this will help you, hopefully some info here leads in the right direction, if yours isn't already solved.

---

### Post by dbott67 on 2006-12-06
Glad you solved it, Bob.

---

### Post by trubblemaker on 2006-12-06
Hey just think about this issue jeeptime1 and I think you might have a bad pci slot.  keep an eye on it.  see if the issue creeps up again. it would explain why the card started working when you added a new card....

---

### Post by jeeptime1 on 2006-12-08
Thanks.  
FWIW, I did think about that.  The first 2 cards were installed in the same slot.  The 3rd card I used a different slot.  I didn't bother trying the confirmed "good" card in the original slot.  Maybe after I get everything else working and caught up, I'll try that to make sure.

Thanks again for the help.

Bob

---

### Post by FOBioPatel on 2008-06-30
I am having the *identical* problem with the Model LNE100TX ethernet card; sadly I bought 10 of these for multiple desktops I plan on installing Ubuntu on.

This is tremendously bad for me. Time to consider Ubuntu alternatives :-(

> **jeeptime1 said:**
> Well, I'm connected and installing updates.

I replaced the network card again as stated above.  The 2 cards that I removed were the models below (I don't know which one was the more recent/I already mixed them up) From my previous post it appears that it was number1 below that we were woprking with.  Both appear to be made by Linksys, which makes sense because they look very similar compared to the I have installed now
 
1. Network Everywhere Fast Ethernet 10/100 Network Card
   Model No. NC100
   Version 2.1

2. Linksys Etherfast 10/100 LAN Card
   Model No. LNE100TX
   Version 5.0

I don't know if the cards were bad, unsupported, or if I screwed something up by switching them and not configuring correctly.

I post this information to:
1. Thank those that tried to help (I learned alot from that help)
2. Maybe someone can tell from previous post in this thread and/or anything else I can post now, what the problem was or fix could be for someone else with same problem.

BX, I don't know if this will help you, hopefully some info here leads in the right direction, if yours isn't already solved.

---

