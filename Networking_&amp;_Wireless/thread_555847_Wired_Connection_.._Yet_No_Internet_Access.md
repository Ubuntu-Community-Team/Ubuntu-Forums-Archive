---
title: "Wired Connection .. Yet No Internet Access"
date: 2007-09-20
forum: Networking &amp; Wireless
---

### Post by rave23 on 2007-09-20
hello,

i had some problem with NIC (REALTEK 8129  / SILAN SC92031 ) ... so did everything given in this link ...

[http://ubuntu-os.blogspot.com/2007/04/installing-ethernet-card-having-silan.html](http://ubuntu-os.blogspot.com/2007/04/installing-ethernet-card-having-silan.html)

BUT now im lost at this place ..
it specifies of

" Open /etc/modeprobe.conf and add following line:
alias wlan0 ndiswrapper "

BUT I DIDNT FIND ANY MODEPROBE.CONF file in ubuntu 7.04 ..
so i opened the modules file in etc ... and pasted
alias wlan0 ndiswrapper

was it right ??

also im completely lost at " Configure Network " stage ..


HOWEVER MY CARD IS DETECTED BUT UNABLE TO CONNECT TO NET ..
i get the wired connection message at top right corner ......

---

### Post by noob12 on 2007-09-20
No that wasn't right for ndiswrapper, but more fundamentally, it's not clear you should be using ndiswrapper at all.

Can you please post some information about your device so people can make a recommendation?

Run these and post the output:
```

lspci -nn

sudo lshw -C network

```

---

### Post by rave23 on 2007-09-22
thanks for the reply ..
will do it and get back ...


ubuntu@ubuntu:~/Desktop/winXP$ lspci -nn

00:00.0 Host bridge [0600]: nVidia Corporation nForce CPU bridge [10de:01a4] (rev b2)
00:00.1 RAM memory [0500]: nVidia Corporation nForce 220/420 Memory Controller [10de:01ac] (rev b2)
00:00.2 RAM memory [0500]: nVidia Corporation nForce 220/420 Memory Controller [10de:01ad] (rev b2)
00:00.3 RAM memory [0500]: nVidia Corporation Unknown device [10de:01aa] (rev b2)
00:01.0 ISA bridge [0601]: nVidia Corporation nForce ISA Bridge [10de:01b2] (rev c3)
00:01.1 SMBus [0c05]: nVidia Corporation nForce PCI System Management [10de:01b4] (rev c1)
00:02.0 USB Controller [0c03]: nVidia Corporation nForce USB Controller [10de:01c2] (rev c3)
00:03.0 USB Controller [0c03]: nVidia Corporation nForce USB Controller [10de:01c2] (rev c3)
00:05.0 Multimedia audio controller [0401]: nVidia Corporation nForce Audio [10de:01b0] (rev c2)
00:06.0 Multimedia audio controller [0401]: nVidia Corporation nForce Audio [10de:01b1] (rev c2)
00:08.0 PCI bridge [0604]: nVidia Corporation nForce PCI-to-PCI bridge [10de:01b8] (rev c2)
00:09.0 IDE interface [0101]: nVidia Corporation nForce IDE [10de:01bc] (rev c3)
00:1e.0 PCI bridge [0604]: nVidia Corporation nForce AGP to PCI Bridge [10de:01b7] (rev b2)
01:07.0 Ethernet controller [0200]: Hangzhou Silan Microelectronics Co., Ltd. Unknown device [1904:2031] (rev 01)
02:00.0 VGA compatible controller [0300]: nVidia Corporation NV44A [GeForce 6200] [10de:0221] (rev a1)


ubuntu@ubuntu:~/Desktop/winXP$ sudo lshw -C network

  *-network               
       description: Ethernet interface
       product: Hangzhou Silan Microelectronics Co., Ltd.
       vendor: Hangzhou Silan Microelectronics Co., Ltd.
       physical id: 7
       bus info: pci@01:07.0
       logical name: wlan0
       version: 01
       serial: 00:e0:20:b9:1f:f5
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=ndiswrapper+netslnt driverversion=1.47+Realtek Inc.,04/05/2002, 1. ip=192.168.1.2 latency=64 link=yes maxlatency=40 mingnt=20 multicast=yes
       resources: iomemory:e4800000-e48000ff ioport:b800-b8ff irq:18


some additional info if needed ..

ubuntu@ubuntu:~/Desktop/winXP$ ifconfig -a

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:20 errors:0 dropped:0 overruns:0 frame:0
          TX packets:20 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:1396 (1.3 KiB)  TX bytes:1396 (1.3 KiB)

wlan0     Link encap:Ethernet  HWaddr 00:E0:20:B9:1F:F5  
          inet addr:192.168.1.2  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::2e0:20ff:feb9:1ff5/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:29 errors:0 dropped:0 overruns:0 frame:0
          TX packets:97 errors:0 dropped:2 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:4096 (4.0 KiB)  TX bytes:11625 (11.3 KiB)
          Interrupt:18 Memory:e4800000-e4800100 


ubuntu@ubuntu:~/Desktop/winXP$ sudo ifup wlan0

ifup: interface wlan0 already configured

ONE MORE QUESTTION .. whats my ip address  and gateway supposed to be ???

---

### Post by noob12 on 2007-09-22
OK.  So that's an unusual solution but it will probably work.  The 8139too driver supports some 8129 cards but that device id doesn't seem to be among the ones it has listed.  I'm not sure whether there's any way to get it to claim it.

Normally ndiswrapper expects to be used for wireless devices; it can be used with wired NDIS drivers, and you do seem to have got it setup for that.  

You can get it to have a normal name like **eth0** by loading it using the option **ifname=eth%d**.  You can put this option right on the ndiswrapper line you probably already have  in **/etc/modules**.

Take out the alias definition from **/etc/modules**.  You can create an alias in a new file called **/etc/modprobe.d/ndiswrapper**.  If you do use the above to make it eth0, use the same alias, and make sure any entry you have in **/etc/iftab** for that mac address (00:E0:20:B9:1F:F5) agrees with both.

You seem to have gotten an address assigned by DHCP: 192.168.1.2.  You probably have a gateway too.   The command **route -n** will show you.  Look in the Gateway column where the Flags column says UG.

---

### Post by deroldj on 2007-09-22
get back to the basics with all settings then do this
As of 27 May 2007, in kernel 2.6.21.3, you may experience the issues with the r8169 driver if you dual boot Windows on some systems. Windows by defaults disables the NIC at Windows shutdown time in order to disable Wake-On-Lan, and this NIC will remain disabled until the next time Windows turns it on. The r8169 driver in the kernel does not know how to turn the NIC on from this disabled state; therefore, the device will not respond, even if the driver loads and reports that the device is up. To work around this problem, simply enable the feature "Wake-on-lan after shutdown." You can set this option through Windows' device manager.

---

### Post by rave23 on 2007-09-23
> **deroldj said:**
> get back to the basics with all settings then do this
As of 27 May 2007, in kernel 2.6.21.3, you may experience the issues with the r8169 driver if you dual boot Windows on some systems. Windows by defaults disables the NIC at Windows shutdown time in order to disable Wake-On-Lan, and this NIC will remain disabled until the next time Windows turns it on. The r8169 driver in the kernel does not know how to turn the NIC on from this disabled state; therefore, the device will not respond, even if the driver loads and reports that the device is up. To work around this problem, simply enable the feature "Wake-on-lan after shutdown." You can set this option through Windows' device manager.

i did that ..  by didnt provide any help ....

---

### Post by rave23 on 2007-09-23
i dont want to bother much about converting to eth0 ... so here is some info ..

asdf@asdf-desktop:/lib/modules/2.6.20-15-generic/kernel/drivers/net$ cat  /etc/modules
# /etc/modules: kernel modules to load at boot time.
#
# This file contains the names of kernel modules that should be loaded
# at boot time, one per line. Lines beginning with "#" are ignored.

fuse
lp


asdf@asdf-desktop:/etc/modprobe.d$ cat /etc/iftab
# This file assigns persistent names to network interfaces.
# See iftab(5) for syntax.


asdf@asdf-desktop:/etc/modprobe.d$ route -n
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.1.0     0.0.0.0         255.255.255.0   U     0      0        0 wlan0
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 wlan0
0.0.0.0         192.168.1.1     0.0.0.0         UG    0      0        0 wlan0

asdf@asdf-desktop:/etc/modprobe.d$ lsmod 
Module                  Size  Used by
ndiswrapper           188252  0 


asdf@asdf-desktop:/lib/modules/2.6.20-15-generic/kernel/drivers/net$ ifconfig wlan0
wlan0     Link encap:Ethernet  HWaddr 00:E0:20:B9:1F:F5  
          inet addr:192.168.1.2  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::2e0:20ff:feb9:1ff5/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:29 errors:0 dropped:0 overruns:0 frame:0
          TX packets:270 errors:0 dropped:2 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:4270 (4.1 KiB)  TX bytes:28194 (27.5 KiB)
          Interrupt:18 Memory:e4800000-e4800100 

asdf@asdf-desktop:/etc/modprobe.d$ cat /etc/network/interfaces
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


asdf@asdf-desktop:/lib/modules/2.6.20-15-generic/kernel/drivers/net$ cat /etc/resolv.conf
nameserver 192.168.1.1


asdf@asdf-desktop:/lib/modules/2.6.20-15-generic/kernel/drivers/net$ cat /etc/resolv.conf
nameserver 192.168.1.1
asdf@asdf-desktop:/lib/modules/2.6.20-15-generic/kernel/drivers/net$ grep dhclient /var/log/syslog | tail -50
Sep 23 19:44:36 asdf-desktop dhclient: There is already a pid file /var/run/dhclient.wlan0.pid with pid 134993416
Sep 23 19:44:36 asdf-desktop dhclient: Internet Systems Consortium DHCP Client V3.0.4
Sep 23 19:44:36 asdf-desktop dhclient: Copyright 2004-2006 Internet Systems Consortium.
Sep 23 19:44:36 asdf-desktop dhclient: All rights reserved.
Sep 23 19:44:36 asdf-desktop dhclient: For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)
Sep 23 19:44:36 asdf-desktop dhclient: 
Sep 23 19:44:37 asdf-desktop dhclient: Listening on LPF/wlan0/00:e0:20:b9:1f:f5
Sep 23 19:44:37 asdf-desktop dhclient: Sending on   LPF/wlan0/00:e0:20:b9:1f:f5
Sep 23 19:44:37 asdf-desktop dhclient: Sending on   Socket/fallback
Sep 23 19:44:37 asdf-desktop dhclient: There is already a pid file /var/run/dhclient.wlan0.pid with pid 134993440
Sep 23 19:44:38 asdf-desktop dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 8
Sep 23 19:44:39 asdf-desktop dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 8
Sep 23 19:44:39 asdf-desktop dhclient: DHCPOFFER from 192.168.1.1
Sep 23 19:44:39 asdf-desktop dhclient: DHCPREQUEST on wlan0 to 255.255.255.255 port 67
Sep 23 19:44:39 asdf-desktop dhclient: DHCPACK from 192.168.1.1
Sep 23 19:44:39 asdf-desktop dhclient: bound to 192.168.1.2 -- renewal in 1413 seconds.
Sep 23 19:44:46 asdf-desktop dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 21
Sep 23 19:44:46 asdf-desktop dhclient: DHCPOFFER from 192.168.1.1
Sep 23 19:44:46 asdf-desktop dhclient: DHCPREQUEST on wlan0 to 255.255.255.255 port 67
Sep 23 19:44:46 asdf-desktop dhclient: DHCPACK from 192.168.1.1
Sep 23 19:44:46 asdf-desktop dhclient: bound to 192.168.1.2 -- renewal in 1743 seconds.


asdf@asdf-desktop:/etc/modprobe.d$ sudo iptables -nL
Chain INPUT (policy ACCEPT)
target     prot opt source               destination         

Chain FORWARD (policy ACCEPT)
target     prot opt source               destination         

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination   


hope it helps ... 
i connect in windows XP usin bridge mode .. but use dialer for username and password ....

i used pppoeconf ... heres some outputs ...

asdf@asdf-desktop:/dev$ sudo pon dsl-provider
Plugin rp-pppoe.so loaded.

asdf@asdf-desktop:/dev$ plog
Sep 23 20:49:20 asdf-desktop pppd[19261]: Exit.
Sep 23 20:49:29 asdf-desktop pppd[19285]: Plugin rp-pppoe.so loaded.
Sep 23 20:49:29 asdf-desktop pppd[19287]: pppd 2.4.4 started by root, uid 0
Sep 23 20:49:29 asdf-desktop pppd[19287]: PPP session is 1932
Sep 23 20:49:29 asdf-desktop pppd[19287]: Using interface ppp0
Sep 23 20:49:29 asdf-desktop pppd[19287]: Connect: ppp0 <--> wlan0
Sep 23 20:49:30 asdf-desktop pppd[19287]: Remote message: permission denied
Sep 23 20:49:30 asdf-desktop pppd[19287]: PAP authentication failed
Sep 23 20:49:36 asdf-desktop pppd[19287]: Connection terminated.
Sep 23 20:49:36 asdf-desktop pppd[19287]: Modem hangup

asdf@asdf-desktop:/dev$ ifconfig pppoe
pppoe: error fetching interface information: Device not found

asdf@asdf-desktop:/dev$ sudo poff dsl-provider

asdf@asdf-desktop:/dev$ plog
Sep 23 20:50:06 asdf-desktop pppd[19287]: Connection terminated.
Sep 23 20:50:36 asdf-desktop pppd[19287]: write: Bad file descriptor (9)
Sep 23 20:50:37 asdf-desktop pppd[19287]: PPP session is 2242
Sep 23 20:50:37 asdf-desktop pppd[19287]: Using interface ppp0
Sep 23 20:50:37 asdf-desktop pppd[19287]: Connect: ppp0 <--> wlan0
Sep 23 20:50:40 asdf-desktop pppd[19287]: Remote message: permission denied
Sep 23 20:50:40 asdf-desktop pppd[19287]: PAP authentication failed
Sep 23 20:50:40 asdf-desktop pppd[19287]: Connection terminated.
Sep 23 20:50:52 asdf-desktop pppd[19287]: Terminating on signal 15
Sep 23 20:50:52 asdf-desktop pppd[19287]: Exit.

---

### Post by noob12 on 2007-09-23
OK.  Two suggestions:

To load ndiswrapper automatically at boot add a line that just says **ndiswrapper** to the file **/etc/modules**.  This will do that for you:

```

echo "ndiswrapper" | sudo tee -a /etc/modules

```

Run **ifconfig -a** to see which interfaces you actually have.  Remove the entries for all of the interfaces you don't have from **/etc/network/interfaces**.  They're benign but will somewhat slow your boot time.

You seem to be getting a private LAN IP address by DHCP already from your router/modem, and you have a default route from the same.  It doesn't look like your connection is a PPPOE connection.  It looks like straight ethernet to your router/modem.

You mention some kind of authentication you do in Windows to get to the internet.  I'm not sure what you are using to do that and what the equivalent would be.  Maybe if you mention your ISP someone will know.

Can you ping your router  and have you tried pinging an external site?
```

# your router
ping -c 4 192.168.1.1

# One of the google IPs
ping -c 4 74.125.19.99

```

---

### Post by rave23 on 2007-09-23
ubuntu@ubuntu:~/Desktop/winXP$ ifconfig -a

lo Link encap:Local Loopback
inet addr:127.0.0.1 Mask:255.0.0.0
inet6 addr: ::1/128 Scope:Host
UP LOOPBACK RUNNING MTU:16436 Metric:1
RX packets:20 errors:0 dropped:0 overruns:0 frame:0
TX packets:20 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:0
RX bytes:1396 (1.3 KiB) TX bytes:1396 (1.3 KiB)

wlan0 Link encap:Ethernet HWaddr 00:E0:20:B9:1F:F5
inet addr:192.168.1.2 Bcast:192.168.1.255 Mask:255.255.255.0
inet6 addr: fe80::2e0:20ff:feb9:1ff5/64 Scope:Link
UP BROADCAST RUNNING MULTICAST MTU:1500 Metric:1
RX packets:29 errors:0 dropped:0 overruns:0 frame:0
TX packets:97 errors:0 dropped:2 overruns:0 carrier:0
collisions:0 txqueuelen:1000
RX bytes:4096 (4.0 KiB) TX bytes:11625 (11.3 KiB)
Interrupt:18 Memory:e4800000-e4800100 

i typed 192.168.1.1 in browser in firefox ( WINDOWS XP )
then went to bridge  mode ... VPI 1and VCI 32...
for authentication im usind the usual windows DIALER... ( which i got by following the windows new internet connection wizard )

so u suggest there is no use of pppoeconf ??

---

### Post by noob12 on 2007-09-23
Yes, pppoeconf would be used if the ethernet connection out of your box has to use PPPOE to talk via the modem.  It doesn't.  You don't need that.

You have real IP over ethernet to your modem/router.  Try following the directions posted in my previous posting and  tell us what you get.

---

### Post by rave23 on 2007-09-23
asdf@asdf-desktop:~$ ping -c 4 192.168.1.1
PING 192.168.1.1 (192.168.1.1) 56(84) bytes of data.
64 bytes from 192.168.1.1: icmp_seq=1 ttl=255 time=6.77 ms
64 bytes from 192.168.1.1: icmp_seq=2 ttl=255 time=0.630 ms
64 bytes from 192.168.1.1: icmp_seq=3 ttl=255 time=0.631 ms
64 bytes from 192.168.1.1: icmp_seq=4 ttl=255 time=0.621 ms

--- 192.168.1.1 ping statistics ---
4 packets transmitted, 4 received, 0% packet loss, time 3013ms
rtt min/avg/max/mdev = 0.621/2.163/6.770/2.659 ms
asdf@asdf-desktop:~$ ping -c 4 74.125.19.99
PING 74.125.19.99 (74.125.19.99) 56(84) bytes of data.

--- 74.125.19.99 ping statistics ---
4 packets transmitted, 0 received, 100% packet loss, time 2999ms


this time i also added the dns address 125.22.47.125
202.56.250.5 

and /etc/resolv.conf shows
nameserver 125.22.47.125
nameserver  202.56.250.5

and my ISP is AIRTEL

---

### Post by noob12 on 2007-09-23
You're getting to your modem/router fine but not beyond.   So those DNS servers aren't reachable yet.

Are you saying you have to use PPPOE in windows to connect?   Normally when that is the case your modem/router doesn't assign you an address itself by DHCP.  Yours is assigning you an address, so it suggests you have to setup something in the modem to authenticate with the ISP.   

If you post who your ISP is and the type of modem that you have maybe someone will be familiar with the required setup.

---

### Post by rave23 on 2007-09-23
> **noob12 said:**
> You're getting to your modem/router fine but not beyond.   So those DNS servers aren't reachable yet.

Are you saying you have to use PPPOE in windows to connect?   Normally when that is the case your modem/router doesn't assign you an address itself by DHCP.  Yours is assigning you an address, so it suggests you have to setup something in the modem to authenticate with the ISP.   

If you post who your ISP is and the type of modem that you have maybe someone will be familiar with the required setup.

ISP ---- AIRTEL 
MODEM /ROUTER ---- DLINK 502T 

yes .. i think i use pppoe ... 
u gave me an idea ...
i will store userid and password on the modem itself ( will get rid of dialer .... by modifying modem settings )

hey .. pppoe stores id and password on modem ...... did that now .. hopefully will work in ubuntu ......

---

### Post by rave23 on 2007-09-23
**[SIZE="5"]guess what ????????? IT WORKS .......... IM POSTING THIS REPLY FROM UBUNTU .......[/SIZE]**:guitar:


[SIZE="7"]THANKS A LOT FOR YOUR SUPPORT  NOOB12  ;)[/SIZE]

the problem as i said   my previous post  is that 
THE USER ID AND PASSWORD WAS IN A DIALER .. 
NOW I USED PPPOE MODE IN WINDOWS ... HENCE STORED THEN PERMANENTLY ONTO THE MODEM ....

NOW UBUNTU WORKS FINE ........ BYE BYE WINDOWS ...........

and a tip for others ...never forget to store DNS address ........get em frm ur ISP ( in my case  airtel )

if u need em .....

dns (nameserver )
125.22.47.125
202.56.250.5            (it must be in ur /etc/resolv.conf file)

gateway address 192.168.1.1
ip address 192.168.1.2  (or any number between 2 to 255 as my isp guy said ) 
subnet 255.255.255.0


thanks again to the ubuntu community and noob12 .......):P

---

