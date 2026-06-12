---
title: "Problem connecting to internet"
date: 2006-10-18
forum: Networking &amp; Wireless
---

### Post by mangoHead84 on 2006-10-18
I recently installed Ubuntu 6.06 on my computer. I connected it to my ADSL modem through my ethernet jack. I know that the modem is working and that it is plugged in properly because its a dual boot system and the windows XP recognises the modem/connection without any problems. 

My problem is that when i try to use Firefox it doesn't go anywhere, just displays the 'page cannot be found' message. The synaptic package manager doesn't work either. I tried diabling the IPv6 in Firefox, but still no help. 

Any ideas as to what this problem might be? Im using a Asus M2N-E motherboard with the nForce 570 chipset. The adsl modem Im using is the Dynalink RTA1025W. 

The results when I run ifconfig are:

eth0      Link encap:Ethernet  HWaddr 00:17:31:7F:D1:E5
          inet6 addr: fe80::217:31ff:fe7f:d1e5/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:50 Base address:0x8000

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:21 errors:0 dropped:0 overruns:0 frame:0
          TX packets:21 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:1456 (1.4 KiB)  TX bytes:1456 (1.4 KiB)


When I go to System->Administration->Networking it shows that the interface eth0 is active. I tried de-activating it and then activating it again, it took a long time but it activated again, but still no internet. 
When I click on the Hosts tab, I get the following:

Network Settings

Ip Address	Aliases
ff00::0		ip6-mcastprefix
127.0.0.1	localhost srdan-desktop
fe00::0		ip6-localnet
ff02::2		ip6-allrouters
ff02::1		ip6-allnodes
::1		ip6-localhost ip6-loopback
127.0.1.1	srdan-desktop
ff02::3		ip6-allhosts

---

### Post by cakmin on 2006-10-18
Hi,
Are you using Static IP Address?
Have you tried this?

System-Preference-Network Tools

Choose eth0 and configure
Then type your Gateway IP, DNS, netmask etc.

Find all those information from your WinXP setting.
Give it a go if you haven't done that.

---

### Post by carontis on 2006-10-18
From what I can see cakmin is right. You haven't done (not yet) a net so you need to do it now, using as he told. After you'll try again with ifconfig and you'll see something different: your IP and other parts in relation to the net you did. Remember also that many modems (ADSL interfaces) have their own ID in the eeprom, so it's probable you'll need to go in it and check if it's positioned on dial-up or lease, this simply to have the connection-up when the pc is booted or have the connection with a command (dialing). Check your modem instructions for exact ip and how to set parameters in it.

---

### Post by mangoHead84 on 2006-10-19
Im not using a static Ip. My WinXP connection uses DHCP and obtains IP adresses and DNS adresses automatically. 

Despite that I tried setting it to static IP and setting the gateway etc... still no result.

I also noticed that when I tried to connect to my modem directly (by typing in 192.168.1.1 in the address bar) it couldn't connect. So I figure this must be some communication problem at the device level. But it shows that my NIC is recognised and active?

---

### Post by handy on 2006-10-20
Sorry, invalid. :rolleyes:

---

### Post by lloyd_b on 2006-10-20
Just for a test, try the following:

In a console, type "ifconfig eth0 192.168.1.25 netmask 255.255.255.0"
Then "ping 192.168.1.1"

If this comes back with a response, then there is most likely a problem with your "/etc/network/interfaces" file.  In that case, I would suggest posting a copy of that file here.

Lloyd B.

---

### Post by mangoHead84 on 2006-10-20
Ok, I tried what you said, it came back with this response:

dave@dave-desktop:~$ sudo ifconfig eth0 192.168.1.25 netmask 255.255.255.0
Password:
dave@dave-desktop:~$ ping 192.168.1.1
PING 192.168.1.1 (192.168.1.1) 56(84) bytes of data.
From 192.168.1.25 icmp_seq=2 Destination Host Unreachable
From 192.168.1.25 icmp_seq=3 Destination Host Unreachable
From 192.168.1.25 icmp_seq=4 Destination Host Unreachable
From 192.168.1.25 icmp_seq=5 Destination Host Unreachable
From 192.168.1.25 icmp_seq=6 Destination Host Unreachable
From 192.168.1.25 icmp_seq=7 Destination Host Unreachable
From 192.168.1.25 icmp_seq=9 Destination Host Unreachable
From 192.168.1.25 icmp_seq=10 Destination Host Unreachable
From 192.168.1.25 icmp_seq=11 Destination Host Unreachable
From 192.168.1.25 icmp_seq=13 Destination Host Unreachable
From 192.168.1.25 icmp_seq=14 Destination Host Unreachable
From 192.168.1.25 icmp_seq=15 Destination Host Unreachable
From 192.168.1.25 icmp_seq=16 Destination Host Unreachable
From 192.168.1.25 icmp_seq=17 Destination Host Unreachable
From 192.168.1.25 icmp_seq=18 Destination Host Unreachable

--- 192.168.1.1 ping statistics ---
20 packets transmitted, 0 received, +15 errors, 100% packet loss, time 19003ms
, pipe 4


Here are the contents of my /etc/network/interfaces file (after running the commands above):

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

---

### Post by lloyd_b on 2006-10-20
> Ok, I tried what you said, it came back with this response:

dave@dave-desktop:~$ sudo ifconfig eth0 192.168.1.25 netmask 255.255.255.0
Password:
dave@dave-desktop:~$ ping 192.168.1.1
PING 192.168.1.1 (192.168.1.1) 56(84) bytes of data.
From 192.168.1.25 icmp_seq=2 Destination Host Unreachable
From 192.168.1.25 icmp_seq=3 Destination Host Unreachable
From 192.168.1.25 icmp_seq=4 Destination Host Unreachable
From 192.168.1.25 icmp_seq=5 Destination Host Unreachable
From 192.168.1.25 icmp_seq=6 Destination Host Unreachable
From 192.168.1.25 icmp_seq=7 Destination Host Unreachable
From 192.168.1.25 icmp_seq=9 Destination Host Unreachable
From 192.168.1.25 icmp_seq=10 Destination Host Unreachable
From 192.168.1.25 icmp_seq=11 Destination Host Unreachable
From 192.168.1.25 icmp_seq=13 Destination Host Unreachable
From 192.168.1.25 icmp_seq=14 Destination Host Unreachable
From 192.168.1.25 icmp_seq=15 Destination Host Unreachable
From 192.168.1.25 icmp_seq=16 Destination Host Unreachable
From 192.168.1.25 icmp_seq=17 Destination Host Unreachable
From 192.168.1.25 icmp_seq=18 Destination Host Unreachable

--- 192.168.1.1 ping statistics ---
20 packets transmitted, 0 received, +15 errors, 100% packet loss, time 19003ms
, pipe 4

Now that is interesting.  The "Destination Host Unreachable" is a sign of a routing problem...

Okay, another test:

"sudo ifconfig eth0 192.168.1.25 netmask 255.255.255.0"
"route"

The route command will display a list of active routes.  I'm curious as to what the default route is being set to (if anything).  What you *should* see is something like this:

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.1.0     *               255.255.255.0   U     0      0        0 eth0

Lloyd B

---

### Post by mangoHead84 on 2006-10-20
Tried that. The results came out exactly as you said they would:

dave@dave-desktop:~$ sudo ifconfig eth0 192.168.1.25 netmask 255.255.255.0
Password:
dave@dave-desktop:~$ route
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.1.0     *               255.255.255.0   U     0      0        0 eth0
dave@dave-desktop:~$

---

### Post by lloyd_b on 2006-10-21
Oops....

That "Destination Host Unreachable" was NOT an indicator of a routing problem - I was confusing it with something else.

If my machine were giving those results, I would suspect a bad ethernet cable.  But you say that it works fine from XP, so that can't be the issue...

What kind of ethernet card are you using (if you know).  I noticed in one of your earlier posts a references to "eth1" "eth2" "ath0" and "wlan0", and was wondering where they were coming from.

Another experiment:

"sudo ifconfig eth0 192.168.1.25 netmask 255.255.255.0"
"sudo route add default gw 192.168.1.1."
"cat /proc/net/route"

I'm curious to see if anything besides eth0 shows up in that file.  From the results of the previous experiments, it acts like the ping packets are going *somewhere*, but not to eth0.

Also try this:
"ping -I eth0 192.168.1.1"

(that "ping dash capital-letter-i" - when I previewed this post, it looked more like an lowercase L)

That will force the ping packets to use that interface.

Lloyd B

---

### Post by mangoHead84 on 2006-10-22
Im using a built in ethernet card. The motherboard is an ASUS M2N-E motherboard with the nForce 570 chipset. I only have one ethernet jack at the back of the machine so I don't know where the references to "eth1" "eth2" and "ath0" and "wlan0" are coming from either. The cable is in fact working fine, i tried it with another computer running Ubuntu with the same modem and it worked. 

The results of the experiment:

dave@dave-desktop:~$ sudo ifconfig eth0 192.168.1.25 netmask 255.255.255.0
Password:
dave@dave-desktop:~$ sudo route add default gw 192.168.1.1
dave@dave-desktop:~$ cat /proc/net/route

Iface   Destination     Gateway         Flags   RefCnt  Use     Metric  Mask   MTU      Window  IRTT
eth0    0001A8C0        00000000        0001    0       0       0       00FFFFF0
eth0    00000000        0101A8C0        0003    0       0       0       00000000

dave@dave-desktop:~$ ping -I eth0 192.168.1.1
PING 192.168.1.1 (192.168.1.1) from 192.168.1.25 eth0: 56(84) bytes of data.
From 192.168.1.25 icmp_seq=2 Destination Host Unreachable
From 192.168.1.25 icmp_seq=3 Destination Host Unreachable
From 192.168.1.25 icmp_seq=4 Destination Host Unreachable
From 192.168.1.25 icmp_seq=6 Destination Host Unreachable
From 192.168.1.25 icmp_seq=7 Destination Host Unreachable
From 192.168.1.25 icmp_seq=8 Destination Host Unreachable

--- 192.168.1.1 ping statistics ---
8 packets transmitted, 0 received, +6 errors, 100% packet loss, time 6999ms
, pipe 3

---

### Post by lloyd_b on 2006-10-22
I hate to say it, but I'm fresh out of ideas on this one.

1.  The ethernet card is recognized by the system.
2.  The system can load an IP address on it.
3.  A default route is being set.

But when you actually send packets, it acts like a there's a bad/missing ethernet cable.

My only thought is that there's a problem with the device driver.  So we need to find out what kind of ethernet device you've got, and then what driver is being loaded for it.

In a terminal window, type:

```
[B]lshw
lspci[/B]

```
With any luck, this will tell us exactly what ethernet controller you have.  

Lloyd B.

---

### Post by louistan3 on 2006-10-23
dd u try entering ur DNS addresses manually? go to system > administration > networking > DNS tab.. or as a test before u enter ur DNS manually.. you could try and ping yahoo's ip.. im not sure what yahoo's ip is.. someone else might be able to help you with that.. or you could copy it by pinging from xp.. hope this helps :D

---

### Post by mangoHead84 on 2006-10-23
ok, here's the result of the lshw command: 

e02bfff irq:58
     *-pci:0
          description: PCI bridge
          product: nVidia Corporation
          vendor: nVidia Corporation
          physical id: 6
          bus info: pci@00:06.0
          version: a2
          width: 32 bits
          clock: 66MHz
          capabilities: pci subtractive_decode bus_master cap_list
     *-multimedia
          description: Multimedia controller
          product: nVidia Corporation
          vendor: nVidia Corporation
          physical id: 6.1
          bus info: pci@00:06.1
          version: a2
          width: 32 bits
          clock: 66MHz
          capabilities: bus_master cap_list
          configuration: driver=HDA Intel
          resources: iomemory:fe024000-fe027fff irq:58

--------->

     *-bridge
          description: Ethernet interface
          product: MCP55 Ethernet
          vendor: nVidia Corporation
          physical id: 8
          bus info: pci@00:08.0
          logical name: eth0
          version: a2
          serial: 00:17:31:7f:d1:e5
          size: 100000000
          capacity: 1000000000
          width: 32 bits
          clock: 66MHz
          capabilities: bridge bus_master cap_list ethernet physical mii 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegociation
          configuration: autonegociation=on broadcast=yes driver=forcedeth driverversion=0.48 duplex=full link=yes multicast=yes port=MII speed=100MB/s
          resources: iomemory:fe02a000-fe02afff ioport:b400-b407 iomemory:fe029000-fe0290ff iomemory:fe028000-fe02800f irq:50     


and here is the result of the lspci command:

dave@dave-desktop:~$ sudo lspci
0000:00:00.0 RAM memory: nVidia Corporation MCP55 Memory Controller (rev a1)
0000:00:01.0 ISA bridge: nVidia Corporation MCP55 LPC Bridge (rev a2)
0000:00:01.1 SMBus: nVidia Corporation MCP55 SMBus (rev a2)
0000:00:01.2 RAM memory: nVidia Corporation MCP55 Memory Controller (rev a2)
0000:00:02.0 USB Controller: nVidia Corporation MCP55 USB Controller (rev a1)
0000:00:02.1 USB Controller: nVidia Corporation MCP55 USB Controller (rev a2)
0000:00:04.0 IDE interface: nVidia Corporation MCP55 IDE (rev a1)
0000:00:05.0 IDE interface: nVidia Corporation MCP55 SATA Controller (rev a2)
0000:00:05.1 IDE interface: nVidia Corporation MCP55 SATA Controller (rev a2)
0000:00:05.2 IDE interface: nVidia Corporation MCP55 SATA Controller (rev a2)
0000:00:06.0 PCI bridge: nVidia Corporation: Unknown device 0370 (rev a2)
0000:00:06.1 0403: nVidia Corporation: Unknown device 0371 (rev a2)

--------------->
0000:00:08.0 Bridge: nVidia Corporation MCP55 Ethernet (rev a2)

0000:00:0a.0 PCI bridge: nVidia Corporation: Unknown device 0376 (rev a2)
0000:00:0b.0 PCI bridge: nVidia Corporation: Unknown device 0374 (rev a2)
0000:00:0c.0 PCI bridge: nVidia Corporation: Unknown device 0374 (rev a2)
0000:00:0d.0 PCI bridge: nVidia Corporation: Unknown device 0378 (rev a2)
0000:00:0e.0 PCI bridge: nVidia Corporation: Unknown device 0375 (rev a2)
0000:00:0f.0 PCI bridge: nVidia Corporation: Unknown device 0377 (rev a2)
0000:00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
0000:00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
0000:00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
0000:00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
0000:07:00.0 VGA compatible controller: nVidia Corporation: Unknown device 0392 (rev a1)

I appreciate you taking the time to help me out with this, at least I'm getting a better idea of what the problem might be.

---

### Post by lloyd_b on 2006-10-23
Okay - device is an MPC55 Ethernet 
Driver is "forcedeth", version "0.48"

The driver shows it's set for 100mb (megabit) ethernet.  Do you know whether or not that's actually what you've got? (if you were connecting to a 10mb or 1000mb network, we'd see EXACTLY the results we're getting).

Idea: disconnect the cable, boot the machine up, reconnect the cable, and then try the "ipconfig" and "route" tests.  I looked at the driver code, and whenever the ethernet link pulse is detected, it forces parts of the driver to reintialize themselves.  This might make a difference.

I don't see anything else in there that would explain this problem.

Lloyd B.

---

### Post by mangoHead84 on 2006-10-27
I ended up just installing Ubuntu 6.10 and it worked like a charm. Still not sure what the original problem was. Oh well, at least it works now.

---

