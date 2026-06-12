---
title: "Can't connect to the internet"
date: 2006-10-28
forum: Networking &amp; Wireless
---

### Post by piratenaapje on 2006-10-28
After unmounting my hard disk with ubuntu on it(well, removing it manually), installing windows on another hard disk and then mounting the hard disk back I've had a problem with connecting to the internet: I can connect with windows, but no longer with ubuntu.
I was able to connect before I installed windows and never had a problem
```
 
kristof@piratenaapje:~$ ifconfig -a
eth0      Link encap:Ethernet  HWaddr 00:10:DC:0F:7C:A9
          inet6 addr: fe80::210:dcff:fe0f:7ca9/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:24 errors:0 dropped:0 overruns:0 frame:0
          TX packets:12 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:1880 (1.8 KiB)  TX bytes:2520 (2.4 KiB)
          Interrupt:201

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:2 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:100 (100.0 b)  TX bytes:100 (100.0 b)

sit0      Link encap:IPv6-in-IPv4
          NOARP  MTU:1480  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

kristof@piratenaapje:~$ cat /etc/resolv.conf
search telenet.be
nameserver 195.130.130.163
nameserver 195.130.130.3
kristof@piratenaapje:~$ netstat -rn
Kernel IP routing table
Destination     Gateway         Genmask         Flags   MSS Window  irtt Iface
kristof@piratenaapje:~$
```
The code might make my problem more clear to some of you: I don't know what's wrong,... any ideas?

---

### Post by DaveBorealis on 2006-10-28
Are you able to ping out via IP number rather than domain name?  If your /etc/resolv.conf is messed up, you'll get something like this
```

$ ping -c1 google.com
ping: unknown host google.com

$ ping -c1 72.14.207.99
PING 72.14.207.99 (72.14.207.99) 56(84) bytes of data.
64 bytes from 72.14.207.99: icmp_seq=1 ttl=241 time=64.4 ms

--- 72.14.207.99 ping statistics ---
1 packets transmitted, 1 received, 0% packet loss, time 0ms
rtt min/avg/max/mdev = 64.478/64.478/64.478/0.000 ms
```

---

### Post by piratenaapje on 2006-10-28
You're probably right: I guess my resolv.conf is messed up:
```

kristof@piratenaapje:~$ ping -c1 google.com
ping: unknown host google.com
kristof@piratenaapje:~$ ping -c1 72.14.207.99
connect: Network is unreachable
kristof@piratenaapje:~$

```
Any idea on what to do next?

---

### Post by hortimech on 2006-10-28
You do not seem to have an IP address on eth0
Here is an the relevant bit if I do the same as you did

    inet addr:192.168.1.126  Bcast:192.168.1.255  Mask:255.255.255.0
    inet6 addr: fe80::20f:b0ff:fe73:c8c7/64 Scope:Link
You will have to enter your ip address manually (unless you use DHCP from your router, in which case you should probably look at that)
enter 'ifconfig <whatever your ip address is> broadcast <Again what ever> netmask <again what ever>'
 
if in doubt see the sample above.

---

### Post by piratenaapje on 2006-10-28
```
kristof@piratenaapje:~$ ifconfig 213.118.71.103 broadcast 213.118.70.1 netmask 255.255.254.0
SIOCSIFBRDADDR: Permission denied
213.118.71.103: ERROR while getting interface flags: No such device
SIOCSIFNETMASK: Permission denied
kristof@piratenaapje:~$ ifconfig eth0 213.118.71.103 broadcast 213.118.70.1 netmask 255.255.254.0
SIOCSIFADDR: Permission denied
SIOCSIFFLAGS: Permission denied
SIOCSIFBRDADDR: Permission denied
SIOCSIFFLAGS: Permission denied
SIOCSIFNETMASK: Permission denied
kristof@piratenaapje:~$
```

That didn't work... maybe I need to do this as root?
Also, a friend of mine with the same provider says there's nothing wrong with my etc/resolv.conf file, he thinks something may be wrong with my zeroconf file.
Edit: by the way, i'm not behind a router.

---

### Post by DaveBorealis on 2006-10-28
Yeah, your resolv.conf file is probably okay because neither of the pings worked.  To bring up your eth0 you need a sudo.  Why don't you try
```

sudo /sbin/ifconfig eth0 213.118.71.103 up
sudo /sbin/route add default gw 213.118.70.1
ping -c1 google.com

```

---

### Post by piratenaapje on 2006-10-28
```
kristof@piratenaapje:~$ sudo ifconfig eth0 213.118.71.103 up
Password:
kristof@piratenaapje:~$ ping google.com
ping: unknown host google.com
kristof@piratenaapje:~$ sudo /sbin/route add default gw 213.118.70.1
SIOCADDRT: Network is unreachable
kristof@piratenaapje:~$ ping -c1 google.com
ping: unknown host google.com
kristof@piratenaapje:~$

```
This didn't seem to work..

---

### Post by piratenaapje on 2006-10-28
Bring
Up
My
Post
Does anyone know what I should do next?

---

### Post by mips on 2006-10-28
Edit your /etc/network/interfaces file manually with sudo

Here is an example of what goes into it:
```
# The primary network interface
auto eth0
iface eth0 inet static
        network 10.0.0.0
        address 10.0.0.11
        netmask 255.0.0.0
        gateway 10.0.0.2
        broadcast 10.0.0.255
```

---

### Post by DaveBorealis on 2006-10-28
> **mips said:**
> Edit your /etc/network/interfaces file manually with sudo

Here is an example of what goes into it:
```
# The primary network interface
auto eth0
iface eth0 inet static
        network 10.0.0.0
        address 10.0.0.11
        netmask 255.0.0.0
        gateway 10.0.0.2
        broadcast 10.0.0.255
```
Hello mips,

Once he changes interfaces, would he then do this?
```
sudo /etc/init.d/networking start (or restart)
```

Otherwise, myself, I would have done the 'ifconfig up/route add' thing.

Thanks....

---

### Post by mips on 2006-10-28
> **DaveBorealis said:**
> Hello mips,

Once he changes interfaces, would he then do this?
```
sudo /etc/init.d/networking start (or restart)
```

Otherwise, myself, I would have done the 'ifconfig up/route add' thing.

Thanks....

I believe you would have to restart but I could be wrong. One way to find out is to try it ;)

---

### Post by piratenaapje on 2006-10-29
Thanks for your help everybody, but it's still not working, after doing what Dave said, it still says this:
kristof@piratenaapje:~$ ping -c1 google.com
ping: unknown host google.com
I tried if internet worked from a live cd: it didn't either

---

### Post by hortimech on 2006-10-29
I should have said that you have to be root to run ifconfig if you want to change things, so unless like me you have turned root on, use sudo before everything if you are denied permission. You also need to set up your gateway with route.

---

### Post by piratenaapje on 2006-10-29
> **hortimech said:**
> I should have said that you have to be root to run ifconfig if you want to change things, so unless like me you have turned root on, use sudo before everything if you are denied permission. You also need to set up your gateway with route.

I don't think this would work, because I'm not behind a router, and my host doesn't allow static ip adresses...
```
kristof@piratenaapje:~$ ifconfig -a
eth0      Link encap:Ethernet  HWaddr 00:10:DC:0F:7C:A9
          inet6 addr: fe80::210:dcff:fe0f:7ca9/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:20 errors:0 dropped:0 overruns:0 frame:0
          TX packets:13 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:2877 (2.8 KiB)  TX bytes:2862 (2.7 KiB)
          Interrupt:193 Base address:0xc000

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:2 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:100 (100.0 b)  TX bytes:100 (100.0 b)

sit0      Link encap:IPv6-in-IPv4
          NOARP  MTU:1480  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

kristof@piratenaapje:~$     
kristof@piratenaapje:~$ sudo /etc/init.d/networking restart
 * Reconfiguring network interfaces...                                                                                                                       There is already a pid file /var/run/dhclient.eth0.pid with pid 4736
killed old client process, removed PID file
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

Listening on LPF/eth0/00:10:dc:0f:7c:a9
Sending on   LPF/eth0/00:10:dc:0f:7c:a9
Sending on   Socket/fallback
DHCPRELEASE on eth0 to 195.130.137.7 port 67
send_packet: Network is unreachable
send_packet: please consult README file regarding broadcast address.
There is already a pid file /var/run/dhclient.eth0.pid with pid 134993416
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

Listening on LPF/eth0/00:10:dc:0f:7c:a9
Sending on   LPF/eth0/00:10:dc:0f:7c:a9
Sending on   Socket/fallback
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 8
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 18
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 14
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 20
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 1
No DHCPOFFERS received.
No working leases in persistent database - sleeping.
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
kristof@piratenaapje:~$                             

```
This might make my problem easier to solve for someone, perhaps..

---

### Post by mips on 2006-10-29
> **piratenaapje said:**
> I don't think this would work, because I'm not behind a router, and my host doesn't allow static ip adresses...


Now why did you not mention that earlier ?

Maybe you should tell us your exact setup before we go any further. Stuff like ISP and a link to their site etc how this was done in windows, hardware brand/models use for the networking etc

---

### Post by piratenaapje on 2006-10-29
> **mips said:**
> Now why did you not mention that earlier ?

Maybe you should tell us your exact setup before we go any further. Stuff like ISP and a link to their site etc how this was done in windows, hardware brand/models use for the networking etc
Actually, I did say that.
My provider is telenet: [http://www.telenet.be/en/home/index.page](http://www.telenet.be/en/home/index.page)
I get to the internet using dhcp without a problem in windows, but it doesn't work in ubuntu

---

### Post by piratenaapje on 2006-10-29
Does anyone know what I should try next?

---

### Post by mips on 2006-10-29
Disable IPv6 system wide and also post output of lspci -v here.

---

### Post by piratenaapje on 2006-10-31
```

kristof@piratenaapje:~$ sudo lspci -v
00:00.0 Host bridge: Intel Corporation 82845 845 (Brookdale) Chipset Host Bridge (rev 03)
        Subsystem: Intel Corporation 82845 845 (Brookdale) Chipset Host Bridge
        Flags: bus master, fast devsel, latency 0
        Memory at d0000000 (32-bit, prefetchable) [size=128M]
        Capabilities: [e4] Vendor Specific Information
        Capabilities: [a0] AGP version 2.0

00:01.0 PCI bridge: Intel Corporation 82845 845 (Brookdale) Chipset AGP Bridge (rev 03) (prog-if 00 [Normal decode])
        Flags: bus master, 66MHz, fast devsel, latency 64
        Bus: primary=00, secondary=01, subordinate=01, sec-latency=32
        Memory behind bridge: e0000000-e1ffffff
        Prefetchable memory behind bridge: d8000000-dfffffff

00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev 12) (prog-if 00 [Normal decode])
        Flags: bus master, fast devsel, latency 0
        Bus: primary=00, secondary=02, subordinate=02, sec-latency=32
        I/O behind bridge: 0000c000-0000cfff
        Memory behind bridge: e2000000-e3ffffff
        Prefetchable memory behind bridge: 20000000-200fffff

00:1f.0 ISA bridge: Intel Corporation 82801BA ISA Bridge (LPC) (rev 12)
        Flags: bus master, medium devsel, latency 0

00:1f.1 IDE interface: Intel Corporation 82801BA IDE U100 (rev 12) (prog-if 80 [Master])
        Subsystem: Micro-Star International Co., Ltd. Unknown device 3990
        Flags: bus master, medium devsel, latency 0
        I/O ports at f000 [size=16]

00:1f.2 USB Controller: Intel Corporation 82801BA/BAM USB (Hub #1) (rev 12) (prog-if 00 [UHCI])
        Subsystem: Micro-Star International Co., Ltd. Unknown device 3990
        Flags: bus master, medium devsel, latency 0, IRQ 177
        I/O ports at d000 [size=32]

00:1f.3 SMBus: Intel Corporation 82801BA/BAM SMBus (rev 12)
        Subsystem: Micro-Star International Co., Ltd. Unknown device 3990
        Flags: medium devsel, IRQ 11
        I/O ports at 5000 [size=16]

00:1f.4 USB Controller: Intel Corporation 82801BA/BAM USB (Hub #2) (rev 12) (prog-if 00 [UHCI])
        Subsystem: Micro-Star International Co., Ltd. Unknown device 3990
        Flags: bus master, medium devsel, latency 0, IRQ 185
        I/O ports at d800 [size=32]

01:00.0 VGA compatible controller: nVidia Corporation NV20 [GeForce3 Ti 200] (rev a3) (prog-if 00 [VGA])
        Subsystem: Micro-Star International Co., Ltd. Unknown device 8838
        Flags: bus master, 66MHz, medium devsel, latency 248, IRQ 193
        Memory at e0000000 (32-bit, non-prefetchable) [size=16M]
        Memory at d8000000 (32-bit, prefetchable) [size=64M]
        Memory at dc000000 (32-bit, prefetchable) [size=512K]
        [virtual] Expansion ROM at dc080000 [disabled] [size=64K]
        Capabilities: [60] Power Management version 2
        Capabilities: [44] AGP version 2.0

02:02.0 FireWire (IEEE 1394): VIA Technologies, Inc. IEEE 1394 Host Controller (rev 43) (prog-if 10 [OHCI])
        Subsystem: VIA Technologies, Inc. IEEE 1394 Host Controller
        Flags: bus master, medium devsel, latency 32, IRQ 169
        Memory at e3002000 (32-bit, non-prefetchable) [size=2K]
        I/O ports at c000 [size=128]
        Capabilities: [50] Power Management version 2

02:03.0 Communication controller: Ambient Technologies Inc HaM controllerless modem (rev 02)
        Subsystem: Creatix Polymedia GmbH Unknown device 0002
        Flags: medium devsel, IRQ 5
        Memory at e3000000 (32-bit, non-prefetchable) [size=4K]
        I/O ports at c400 [size=256]
        Capabilities: [60] Power Management version 2

02:06.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
        Subsystem: Realtek Semiconductor Co., Ltd. RT8139
        Flags: bus master, medium devsel, latency 32, IRQ 201
        I/O ports at c800 [size=256]
        Memory at e3001000 (32-bit, non-prefetchable) [size=256]
        [virtual] Expansion ROM at 20000000 [disabled] [size=64K]
        Capabilities: [50] Power Management version 2

02:07.0 Multimedia audio controller: C-Media Electronics Inc CM8738 (rev 10)
        Subsystem: Micro-Star International Co., Ltd. Unknown device 3990
        Flags: bus master, medium devsel, latency 32, IRQ 209
        I/O ports at cc00 [size=256]
        Capabilities: [c0] Power Management version 2

kristof@piratenaapje:~$      

```
I disabled IPv6 and rebooted before doing lspci -v

---

### Post by mips on 2006-10-31
Do a search for **8139** here and see if you pick anything up regarding the Realtek 8139 lan chipset.

---

### Post by piratenaapje on 2006-10-31
Hmm, problem has been (kind of) fixed: I can connect to the internet again: I had to do ipconfig /release in the windows command prompt. Problem is: I'll have to do this command every time windows shuts down, so is there any way to run this command every time I shut down windows, or any way to render this command unnecesary?

---

### Post by piratenaapje on 2006-10-31
Anyone got any ideas on how to do this?

---

### Post by DaveBorealis on 2006-10-31
> **piratenaapje said:**
> I had to do ipconfig /release in the windows command prompt. Problem is: I'll have to do this command every time windows shuts down

I'm guessing that your ISP won't assign you another IP address, even though you're requesting with the same ethernet card's MAC that matches the current one, because they view it as still in use.  Maybe it's some kind of anti-spoofing thing they've set up with their DHCP.

So...something to try:

Under Windows do the 'ipconfig /all', get that IP address, and assign it to your Ubuntu statically.  As long as you don't change ethernet cards, there's a chance you have the same address for months.  (With MediaCom I've had my current IP for about a year!)

Best regards,
Dave

---

### Post by skisky on 2007-07-29
you could make a .bat file with the ipconfig renew_all within it....then put the .bat file in the startup folder.

---

