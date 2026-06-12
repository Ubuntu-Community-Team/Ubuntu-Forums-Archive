---
title: "wired connection problem help needed"
date: 2008-04-09
forum: Networking &amp; Wireless
---

### Post by jeretraca on 2008-04-09
Dear Friends
Iam new to ubuntu and having tried to connect my network it gave the following errors 
please help me find the cause of the problem
I have even tried some commands to no avail

00:00.0 Host bridge: VIA Technologies, Inc. CN700/VN800/P4M800CE/Pro Host Bridge
        Subsystem: ASRock Incorporation Unknown device 0314
        Flags: bus master, 66MHz, medium devsel, latency 8
        Memory at f8000000 (32-bit, prefetchable) [size=64M]
        Capabilities: <access denied>

00:00.1 Host bridge: VIA Technologies, Inc. CN700/VN800/P4M800CE/Pro Host Bridge
        Subsystem: ASRock Incorporation Unknown device 1314
        Flags: bus master, medium devsel, latency 0

00:00.2 Host bridge: VIA Technologies, Inc. CN700/VN800/P4M800CE/Pro Host Bridge
        Subsystem: ASRock Incorporation Unknown device 2314
        Flags: bus master, medium devsel, latency 0

00:00.3 Host bridge: VIA Technologies, Inc. PT890 Host Bridge
        Flags: bus master, medium devsel, latency 0

00:00.4 Host bridge: VIA Technologies, Inc. CN700/VN800/P4M800CE/Pro Host Bridge
        Subsystem: ASRock Incorporation Unknown device 4314
        Flags: bus master, medium devsel, latency 0

00:00.7 Host bridge: VIA Technologies, Inc. CN700/VN800/P4M800CE/Pro Host Bridge
        Subsystem: ASRock Incorporation Unknown device 7314
        Flags: bus master, medium devsel, latency 0

00:01.0 PCI bridge: VIA Technologies, Inc. VT8237 PCI Bridge (prog-if 00 [Normal decode])
        Flags: bus master, 66MHz, medium devsel, latency 0
        Bus: primary=00, secondary=01, subordinate=01, sec-latency=0
        Memory behind bridge: fca00000-feafffff
        Prefetchable memory behind bridge: eff00000-f7efffff
        Capabilities: <access denied>

00:0f.0 RAID bus controller: VIA Technologies, Inc. VIA VT6420 SATA RAID Controller (rev 80)
        Subsystem: ASRock Incorporation K7VT6 motherboard
        Flags: bus master, medium devsel, latency 32, IRQ 16
        I/O ports at ec00 [size=8]
        I/O ports at e800 [size=4]
        I/O ports at e400 [size=8]
        I/O ports at e000 [size=4]
        I/O ports at dc00 [size=16]
        I/O ports at d800 [size=256]
        Capabilities: <access denied>

00:0f.1 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE (rev 06) (prog-if 8a [Master SecP PriP])
        Subsystem: ASRock Incorporation K7VT2/K7VT6 motherboard
        Flags: bus master, medium devsel, latency 32, IRQ 16
        [virtual] Memory at 000001f0 (32-bit, non-prefetchable) [size=8]
        [virtual] Memory at 000003f0 (type 3, non-prefetchable) [size=1]
        [virtual] Memory at 00000170 (32-bit, non-prefetchable) [size=8]
        [virtual] Memory at 00000370 (type 3, non-prefetchable) [size=1]
        I/O ports at fc00 [size=16]
        Capabilities: <access denied>

00:10.0 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81) (prog-if 00 [UHCI])
        Subsystem: ASRock Incorporation K7VT6
        Flags: bus master, medium devsel, latency 32, IRQ 17
        I/O ports at c000 [size=32]
        Capabilities: <access denied>

00:10.1 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81) (prog-if 00 [UHCI])
        Subsystem: ASRock Incorporation K7VT6
        Flags: bus master, medium devsel, latency 32, IRQ 17
        I/O ports at c400 [size=32]
        Capabilities: <access denied>

00:10.2 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81) (prog-if 00 [UHCI])
        Subsystem: ASRock Incorporation K7VT6
        Flags: bus master, medium devsel, latency 32, IRQ 17
        I/O ports at c800 [size=32]
        Capabilities: <access denied>

00:10.3 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81) (prog-if 00 [UHCI])
        Subsystem: ASRock Incorporation K7VT6
        Flags: bus master, medium devsel, latency 32, IRQ 17
        I/O ports at cc00 [size=32]
        Capabilities: <access denied>

00:10.4 USB Controller: VIA Technologies, Inc. USB 2.0 (rev 86) (prog-if 20 [EHCI])
        Subsystem: ASRock Incorporation K7VT6 motherboard
        Flags: bus master, medium devsel, latency 32, IRQ 17
        Memory at febff800 (32-bit, non-prefetchable) [size=256]
        Capabilities: <access denied>

00:11.0 ISA bridge: VIA Technologies, Inc. VT8237 ISA bridge [KT600/K8T800/K8T890 South]
        Subsystem: ASRock Incorporation K7VT4 motherboard
        Flags: bus master, stepping, medium devsel, latency 0
        Capabilities: <access denied>

00:11.5 Multimedia audio controller: VIA Technologies, Inc. VT8233/A/8235/8237 AC97 Audio Controller (rev 60)
        Subsystem: ASRock Incorporation K7VT6 motherboard
        Flags: medium devsel, IRQ 19
        I/O ports at d000 [size=256]
        Capabilities: <access denied>

00:12.0 Ethernet controller: VIA Technologies, Inc. VT6102 [Rhine-II] (rev 78)
        Subsystem: ASRock Incorporation K7VT6 motherboard
        Flags: bus master, medium devsel, latency 32, IRQ 18
        I/O ports at d400 [size=256]
        Memory at febffc00 (32-bit, non-prefetchable) [size=256]
        Capabilities: <access denied>

01:00.0 VGA compatible controller: VIA Technologies, Inc. UniChrome Pro IGP (rev 01) (prog-if 00 [VGA])
        Subsystem: ASRock Incorporation Unknown device 3344
        Flags: bus master, 66MHz, medium devsel, latency 32, IRQ 10
        Memory at f0000000 (32-bit, prefetchable) [size=64M]
        Memory at fd000000 (32-bit, non-prefetchable) [size=16M]
        Expansion ROM at feaf0000 [disabled] [size=64K]
        Capabilities: <access denied>

jeremy@jeremy-desktop:~$ 

jeremy@jeremy-desktop:~$ ifconfig eth0
eth0      Link encap:Ethernet  HWaddr 00:13:8F:92:6E:39  
          inet addr:195.202.83.69  Bcast:195.202.83.95  Mask:255.255.255.224
          inet6 addr: fe80::213:8fff:fe92:6e39/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:2 errors:0 dropped:0 overruns:0 frame:1
          TX packets:10 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:184 (184.0 b)  TX bytes:1342 (1.3 KB)
          Interrupt:18 Base address:0xd400 

jeremy@jeremy-desktop:~$ 
jeremy@jeremy-desktop:~$ ifup eth0
ifup: failed to open statefile /var/run/network/ifstate: Permission denied
jeremy@jeremy-desktop:~$ ifdown etho
ifdown: failed to open statefile /var/run/network/ifstate: Permission denied
jeremy@jeremy-desktop:~$
PING 195.202.83.94 (195.202.83.94) 56(84) bytes of data.
64 bytes from 195.202.83.94: icmp_seq=4 ttl=255 time=0.523 ms
64 bytes from 195.202.83.94: icmp_seq=5 ttl=255 time=0.595 ms
64 bytes from 195.202.83.94: icmp_seq=7 ttl=255 time=0.579 ms
64 bytes from 195.202.83.94: icmp_seq=11 ttl=255 time=0.574 ms
64 bytes from 195.202.83.94: icmp_seq=14 ttl=255 time=0.624 ms
64 bytes from 195.202.83.94: icmp_seq=16 ttl=255 time=0.632 ms

[1]+  Stopped                 ping 195.202.83.94 

jeremy@jeremy-desktop:~$ ping 195.202.64.1
PING 195.202.64.1 (195.202.64.1) 56(84) bytes of data.
64 bytes from 195.202.64.1: icmp_seq=1 ttl=61 time=16.2 ms
64 bytes from 195.202.64.1: icmp_seq=2 ttl=61 time=14.4 ms
64 bytes from 195.202.64.1: icmp_seq=5 ttl=61 time=9.94 ms
64 bytes from 195.202.64.1: icmp_seq=11 ttl=61 time=9.58 ms

[2]+  Stopped                 ping 195.202.64.1
jeremy@jeremy-desktop:~$ 
jeremy@jeremy-desktop:~$ ping 195.202.64.1
PING 195.202.64.1 (195.202.64.1) 56(84) bytes of data.
64 bytes from 195.202.64.1: icmp_seq=1 ttl=61 time=16.2 ms
64 bytes from 195.202.64.1: icmp_seq=2 ttl=61 time=14.4 ms
64 bytes from 195.202.64.1: icmp_seq=5 ttl=61 time=9.94 ms
64 bytes from 195.202.64.1: icmp_seq=11 ttl=61 time=9.58 ms

[2]+  Stopped                 ping 195.202.64.1
jeremy@jeremy-desktop:~$ ping ubuntu.com
PING ubuntu.com (91.189.94.158) 56(84) bytes of data.

[3]+  Stopped                 ping ubuntu.com
jeremy@jeremy-desktop:~$ ping 91.189.94.158
PING 91.189.94.158 (91.189.94.158) 56(84) bytes of data.
64 bytes from 91.189.94.158: icmp_seq=5 ttl=49 time=558 ms
64 bytes from 91.189.94.158: icmp_seq=6 ttl=49 time=547 ms
64 bytes from 91.189.94.158: icmp_seq=8 ttl=49 time=544 ms
64 bytes from 91.189.94.158: icmp_seq=10 ttl=49 time=546 ms

[4]+  Stopped                 ping 91.189.94.158
jeremy@jeremy-desktop:~$ ping 64.233.167.104
PING 64.233.167.104 (64.233.167.104) 56(84) bytes of data.
64 bytes from 64.233.167.104: icmp_seq=3 ttl=243 time=587 ms
64 bytes from 64.233.167.104: icmp_seq=7 ttl=243 time=616 ms
64 bytes from 64.233.167.104: icmp_seq=10 ttl=243 time=594 ms
64 bytes from 64.233.167.104: icmp_seq=14 ttl=243 time=589 ms
64 bytes from 64.233.167.104: icmp_seq=18 ttl=243 time=584 ms

[5]+  Stopped                 ping 64.233.167.104
jeremy@jeremy-desktop:~$ 
jeremy@jeremy-desktop:~$ cat /etc/network/interfaces
auto lo
iface lo inet loopback


iface eth0 inet static
address 195.202.83.69
netmask 255.255.255.224
gateway 195.202.83.94

auto eth0

---

### Post by ibutho on 2008-04-09
Whats the actual problem? Your ifup and ifdown commands won't work unless you prefix them with sudo e.g. "sudo ifup eth0".

---

### Post by jeretraca on 2008-04-11
Okay I have tried the command sudo ifup eth0 and the responce  was
interface eth0 already configured but to no avail when I connect the ethernet network cable it doesnt work

---

### Post by jeretraca on 2008-04-11
When I try to open mozilla firefox and go online Mozilla informs me its connecting to google ie [www.google.co.ke](www.google.co.ke) it then says downloading from google yet doesnt do any thing else it doesnt even show the webpage  

But when i ping the domain address of [www.google.co.ke](www.google.co.ke) in numbers  eg ping 64.233.167.99 in the terminal it shows me its connected as indicated above

another thing I have noticed is the gateway address I put into the the was  195.202.83.94

Yet the broadcast adress is indicated as 195.202.83.95 is there a problem there

One more thing The local area network I use is configured to run at 10mbps full  and that has caused problems in Mackintosh and windows machines before untill we changed to 10mbps full instead of Auto or 100mbps lan settings of the network card

 Okay

---

### Post by superprash2003 on 2008-04-11
try changing your DNS server to opendns
go to the terminal and type

sudo gedit /etc/dhcp3/dhclient.conf

then add the following line to it

prepend domain-name-servers 208.67.222.222,208.67.220.220;

save the file and close.this should work

---

