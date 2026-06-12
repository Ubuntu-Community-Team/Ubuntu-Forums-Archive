---
title: "eth0 active, but no internet!"
date: 2006-09-07
forum: Networking &amp; Wireless
---

### Post by hollym on 2006-09-07
Have been trying on and off for a couple of days but still no joy with internet. eth0 is active and there is some activity in the system Monitor screen. I was asked a couple of times to find out the contents of $route and $ifconfig, so here they are. Yesterday someone commented that I had no gateway defined and no IP address for that gateway or something. Anyway, here is the text dump of the files. Any ideas? cheers in advance ...

$route 
Kernel IP routing table
Destination Gateway Genmask Flags Metric Ref
(no information - this the problem i assume, but exactly what information should be here?)

$ifconfig
Link encap:Ethernet HWaddr 00:0C:6E:11:1B:3B
inet6 addr: fe80::20c:6eff:fe11:1b3b/64 Scope:Link
UP BROADCAST MULTICAST MTU:1500 Metric:1
RX packets:1633 errors:0 dropped:0 overruns:0 frame:0
TX packets:17 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:1000
RX bytes:97980 (95.6 KiB) TX bytes:4230 (4.1 KiB)
Interrupt:201 Base address:0x9800lo

Link encap:Local Loopback
inet addr:127.0.0.1 Mask:255.0.0.0
inet6 addr: ::1/128 Scope:Host
UP LOOPBACK RUNNING MTU:16436 Metric:1
RX packets:135 errors:0 dropped:0 overruns:0 frame:0
TX packets:135 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:0
RX bytes:10196 (9.9 KiB) TX bytes:10196 (9.9 KiB)

setup is that i plug my internet directly into a wall socket (i.e. my building is hardwired) and they have a central server box in the basement. No modems, no router, just a sraight plug into the wall.
I am using DHCP, though it seems as though it is not configured properly. I have run the sudo invoke-rc.d networking restart command a few times and constantly get a DHCP no offers received response. havent tried the sudo dhcpclient command but I'm guessing the result will probably be the same.

/etc/network/interfaces file

not the full file but the part that relates to eth0 just says

auto eth0
iface eth0 inet dhcp

If the problem is with DHCP, what is the next step ... cheers

---

### Post by Uluen on 2006-09-07
Don't start multiple threads about the same issue please.

What happens if you do a ```
$ sudo ifup eth0
```

The output of *route* should be something like this:
```
$ route
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.1.0     *               255.255.255.0   U     0      0        0 eth0
default         your.domain     0.0.0.0          UG    0      0        0 eth0
```

---

### Post by hollym on 2006-09-07
sorry about the multiple threads, point taken.
I have pieced together the following information 

$ route
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
**(so, something should be here? - how do I configure or find out these numbers?)**


$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:0C:6E:11:1B:3B
          **(there should be an IP address, and Mask value here?)** 
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:457 errors:0 dropped:0 overruns:0 frame:0
          TX packets:7 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:27420 (26.7 KiB)  TX bytes:1082 (1.0 KiB)
          Interrupt:217 Base address:0x9800

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:155 errors:0 dropped:0 overruns:0 frame:0
          TX packets:155 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:11881 (11.6 KiB)  TX bytes:11881 (11.6 KiB)



$ etc/network/interfaces
auto lo
iface lo inet loopback

auto eth0
iface eth0 inet dhcp
dns-nameservers 168.126.63.1, 168.126.63.2

auto eth1
iface eth1 inet dhcp

auto eth2
iface eth2 inet dhcp

auto ath0
iface ath0 inet dhcp

auto wlan0
iface wlan0 inet dhcp


$ etc/resolv.conf
nameserver 168.126.63.1
nameserver 168.126.63.2

sudo dhclient is ok

when I open System -> Administration -> Networking
the tab that says "Default gateway device is" is empty. ie. does not select eth0 as the default. Is this important?

finally, when i run sudo invoke-rc.d networking restart get this
No DHCPOFFERS received.
No working leases in persistent database.


does everything else look ok? 
what should i do next?
is the IP of the DHCP Server at all useful?
I have also tried using a static IP address as my address is more or less static, but no joy with that either.

i know this must feel like talking to children somethimes, so thanks a lot for your help

---

### Post by Uluen on 2006-09-07
[QUOTE=hollym]
$ route
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
**(so, something should be here? - how do I configure or find out these numbers?)**[/QUOTE]You could use *route add* but you should get this info from DHCP.


> $ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:0C:6E:11:1B:3B
          **(there should be an IP address, and Mask value here?)** Yes.



> auto eth0
iface eth0 inet dhcp
dns-nameservers 168.126.63.1, 168.126.63.2Where is this DNS info from, did you manually add it to *interfaces*?
> 
auto eth1
iface eth1 inet dhcpLooks fine.
You *are* using the same interface (eth) in all places, right?



> $ etc/resolv.conf
nameserver 168.126.63.1
nameserver 168.126.63.2Ditto.


> when I open System -> Administration -> Networking
the tab that says "Default gateway device is" is empty. ie. does not select eth0 as the default. Is this important?Yes but you should get this info from the DHCP server.

And *$ sudo ifup eth*X (your interface) does what?


> is the IP of the DHCP Server at all useful?Not really, if the DHCP server is reachable, it should give you an IP.

What ethernet card do you have, is it detected at all?
```
$ lspci
```

---

### Post by BLTicklemonster on 2006-09-07
I had this problem once, and I just went to admin and disabled it and then enabled it and it workd. Probly won't this time, but it's worth a looksee.

---

### Post by hollym on 2006-09-07
> **Uluen said:**
> You could use *route add* but you should get this info from DHCP.

ok, i see.

Where is this DNS info from, did you manually add it to *interfaces*?

yes, i manually entered these values into System -> Administration -> Networking -> DNS 
Got these numbers from my windows installation (at the moment just swapping the cable over when playing with linux) by running ipconfig /all

You *are* using the same interface (eth) in all places, right?

Question: when you say "You are using the same interface (eth) in all places, right?" what places are you referring to? As far as I know I am only using eth0.


And *$ sudo ifup eth*X (your interface) does what?

eth0: ifup: interface is already configured
eth1: Failed to bring up eth1


What ethernet card do you have, is it detected at all?
```
$ lspci
```

0000:00:00.0 Host bridge: Silicon Integrated Systems [SiS] 651 Host (rev 02)
0000:00:01.0 PCI bridge: Silicon Integrated Systems [SiS] Virtual PCI-to-PCI bridge (AGP)
0000:00:02.0 ISA bridge: Silicon Integrated Systems [SiS] SiS962 [MuTIOL Media IO] (rev 25)
0000:00:02.1 SMBus: Silicon Integrated Systems [SiS] SiS961/2 SMBus Controller
0000:00:02.5 IDE interface: Silicon Integrated Systems [SiS] 5513 [IDE]
0000:00:02.7 Multimedia audio controller: Silicon Integrated Systems [SiS] Sound Controller (rev a0)
0000:00:03.0 USB Controller: Silicon Integrated Systems [SiS] USB 1.0 Controller (rev 0f)
0000:00:03.1 USB Controller: Silicon Integrated Systems [SiS] USB 1.0 Controller (rev 0f)
0000:00:03.3 USB Controller: Silicon Integrated Systems [SiS] USB 2.0 Controller0000:00:04.0 Ethernet controller: Silicon Integrated Systems [SiS] SiS900 PCI Fast Ethernet (rev 91)
0000:00:0e.0 Multimedia audio controller: C-Media Electronics Inc CM8738 (rev 10)
0000:01:00.0 VGA compatible controller: nVidia Corporation NV34 [GeForce FX 5200] (rev a1)

Please note: I also tried to install Mandriva Linux and also had the same problem. So, I thought it may be at the hardware level. But when running windows, internet works fine.

---

### Post by hollym on 2006-09-08
got internet working but only using a static IP address. I guess for some reason the server in my building is not dishing me up an IP automatically.
The IP I am assigned is different from when I simply unplug the cable and plug it into my Windows box. It seems that the server is giving me a new number for my second box. Interestingly though, it is basically a static IP (my IP address has only changed 3 times in the last year). Seems as though I can have as many IP addresses as I want in my apartment!!
Anyway, thanks for all the effort and if you have any ideas about how I might get DHCP working, please let me know.
Cheers

---

