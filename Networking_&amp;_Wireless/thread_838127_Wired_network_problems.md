---
title: "Wired network problems"
date: 2008-06-23
forum: Networking &amp; Wireless
---

### Post by elmick on 2008-06-23
Hi,

I've been searching for ages to try and fix it before posting but can't. 

When I plug in the ethernet cable, NetworkManager doesnt work. It just stays at "Requesting a network address from the wired network" and never gets any further.

It was working perfectly before I had to reformat my computer. The network currently works with XP (other OS) and my dads PC. The only difference is that before I had a dual boot with ubuntu and XP, using Grub. Whereas now I use windows boot loader first, dual booting xp MCE and ubuntu (from thread: [http://ubuntuforums.org/archive/index.php/t-632598.html](http://ubuntuforums.org/archive/index.php/t-632598.html)).

Cany anyone help? I'm dying to get back into linux, its so frustating having to use xp all the time.

/etc/network/interfaces -
```
auto lo
iface lo inet loopback

auto eth1
iface eth1 inet dhcp

auto eth2
iface eth2 inet dhcp

auto ath0
iface ath0 inet dhcp

auto wlan0
iface wlan0 inet dhcp

```
ifconfig - 
```

eth0      Link encap:Ethernet  HWaddr 00:16:D4:5C:92:6E  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:12 errors:0 dropped:0 overruns:0 frame:0
          TX packets:11 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:3418 (3.3 KiB)  TX bytes:2222 (2.1 KiB)
          Interrupt:21 

eth1      Link encap:Ethernet  HWaddr 00:18:DE:87:8A:33  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:1021 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:19 Base address:0xe000 Memory:d2100000-d2100fff 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:22 errors:0 dropped:0 overruns:0 frame:0
          TX packets:22 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:1532 (1.4 KiB)  TX bytes:1532 (1.4 KiB)

```

lspci | grep ethernet - 
```

06:01.0 Ethernet controller: Broadcom Corporation BCM4401-B0 100Base-TX (rev 02)

```

---

### Post by elmick on 2008-06-23
Also, Its working fine with the live CD. Anyone got any suggestions?

---

### Post by mips on 2008-06-23
This may or may not be related but I read something like this a long time ago. Disable the powermanagement & sleep functions for the card Windows and see what that does if you reboot into Ubuntu.

---

### Post by elmick on 2008-06-24
> **mips said:**
> This may or may not be related but I read something like this a long time ago. Disable the powermanagement & sleep functions for the card Windows and see what that does if you reboot into Ubuntu.

Thanks for the reply. I unchecked the box: "Allow the computer to turn off this device to save power" in the power management tab of the card's properties (through device manager). Is this what you meant? 
I couldnt find anything about sleep. It didn't work. 

I tried this from reading other posts: sudo /etc/init.d/networking restart.
There are errors but i dont know what they mean. Any ideas?

```

mick@laptop:~$ sudo /etc/init.d/networking restart
There is already a pid file /var/run/dhclient.eth1.pid with pid 6251
killed old client process, removed PID file
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

Listening on LPF/eth1/00:18:de:87:8a:33
Sending on   LPF/eth1/00:18:de:87:8a:33
Sending on   Socket/fallback
DHCPRELEASE on eth1 to 192.168.1.1 port 67
send_packet: Network is unreachable
send_packet: please consult README file regarding broadcast address.
execve (/lib/dhcp3-client/call-dhclient-script, ...): Exec format error
There is already a pid file /var/run/dhclient.eth1.pid with pid 134993416
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

execve (/lib/dhcp3-client/call-dhclient-script, ...): Exec format error
Listening on LPF/eth1/00:18:de:87:8a:33
Sending on   LPF/eth1/00:18:de:87:8a:33
Sending on   Socket/fallback
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 4
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 6
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 13
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 8
No DHCPOFFERS received.
No working leases in persistent database - sleeping.
execve (/lib/dhcp3-client/call-dhclient-script, ...): Exec format error
RTNETLINK answers: No such device
run-parts: /etc/network/if-up.d/avahi-autoipd exited with return code 2
ath0: ERROR while getting interface flags: No such device
There is already a pid file /var/run/dhclient.ath0.pid with pid 134993416
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

execve (/lib/dhcp3-client/call-dhclient-script, ...): Exec format error
Bind socket to interface: No such device
wlan0: ERROR while getting interface flags: No such device
There is already a pid file /var/run/dhclient.wlan0.pid with pid 134993416
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

execve (/lib/dhcp3-client/call-dhclient-script, ...): Exec format error
Bind socket to interface: No such device
Failed to bring up wlan0.


```
I also copied 'auto eth0
iface eth0 inet dhcp' into the interfaces file cos it was missing but it didnt do anything either.

---

### Post by superprash2003 on 2008-06-24
try entering static ip.. go to system->administration->network and go to your network card properties and then select static ip.. and enter accordingly.. what is your router ip?

---

### Post by elmick on 2008-06-25
Hi,
192.168.1.1
I tried that for wired and wireless. I added static addresses to my router client list then configured it system>admin..>network.

It doesnt work. When I connect to my wireless network, it looks like its connected but cant get on any websites. (the little icon is with the bars is blue.)

I tried $ping 192.168.1.1 and it repeated this:

64 bytes from 192.168.1.1: icmp_seq=1 ttl=255 time=0.446ms
...
I hit ctrl-c after icmp_seq=387 cos it didnt look like stopping. It said 0% packet loss.



If it it works when using the live CD, can I use that to reinstall something? Maybe something is corrupt

---

