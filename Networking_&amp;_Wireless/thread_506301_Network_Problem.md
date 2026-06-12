---
title: "Network Problem"
date: 2007-07-21
forum: Networking &amp; Wireless
---

### Post by dr.koljan on 2007-07-21
I have recently installed Ubuntu 7.04 and the internet doesn't work at all.

Ubuntu tells me that the Network Connection is OK, but my DSL modem doesn't detect Ethernet activity and Firefox doesn't work. However, Ubuntu DOES detect the network adapter.

I am using an ASRock motherboard 775i945GZ with integrated Realtek RTL8139/810x network adapter.

I am new to Linux, but it is already beting annoying for me.

Everything works just fine on Windows.

Any help would be greatly appreciated.

---

### Post by FunkyJack on 2007-07-21
Did you configure IP address, Subnet mask and Gateway addres in System -> Administration -> Network

---

### Post by dr.koljan on 2007-07-21
I have tried to, but it doesn't help, because I get the settings by DHCP. If these settings were the problem, my modem would detect Ethernet activity anyway.

---

### Post by dr.koljan on 2007-07-23
Any help please? :(

I don't want to uninstall Ubuntu just because of the strange bug which is probably easy to fix.

---

### Post by dr.koljan on 2007-07-23
HELLO???

Is anyone there?

Is it really such a big problem that you can't even try to help me with it?

By the way, I have found that Ubuntu Network Manager tells me that Internet connection is OK even if I unplug my modem... Seems that the signal doesn't go further that the network adapter...Probably driver's fault... :confused:

---

### Post by bsfah3 on 2007-07-23
If the network card is detected and configured as you've previously stated then I would recommend a cold restart of your modem.  I've seen them get picky before.  I've frequently used realtek nics with linux and have never before had a problem so tend to think the driver is OK, (unless the driver itself is corrupted on the disk, but whatcha gonna do)

BSF

---

### Post by dr.koljan on 2007-07-23
I'm sorry, but what does cold restart mean? If it is turning the modem off and on, then it won't work - I already have tried to do so. I'm pretty sure the problem is software-related.

---

### Post by Rui Pais on 2007-07-23
hi,
do you mind to post the output:
```
lshw -C net
```
and
```
ifconfig
```
and 
```
cat /etc/network/interfaces
```
please?

Also what modem/router do you have? what model? how do you configure it?

---

### Post by bsfah3 on 2007-07-23
Cold restart means to completely unplug power from the modem for approx. 15 seconds and then power back up.

---

### Post by dr.koljan on 2007-07-23
OK, not a problem at all.

> nicholas@nicholas-desktop:~$ lshw -C net
WARNING: you should run this program as super-user.
  *-network               
       description: Ethernet interface
       product: RTL-8139/8139C/8139C+
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 7
       bus info: pci@01:07.0
       logical name: eth0
       version: 10
       serial: 00:13:8f:d9:98:fe
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=8139too driverversion=0.9.28 latency=32 maxlatency=64 mingnt=32 multicast=yes
       resources: ioport:c800-c8ff iomemory:f49ffc00-f49ffcff irq:22
nicholas@nicholas-desktop:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:13:8F:D9:98:FE  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:22 Base address:0xac00 

eth0:avah Link encap:Ethernet  HWaddr 00:13:8F:D9:98:FE  
          inet addr:169.254.11.19  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          Interrupt:22 Base address:0xac00 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:84 errors:0 dropped:0 overruns:0 frame:0
          TX packets:84 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:6300 (6.1 KiB)  TX bytes:6300 (6.1 KiB)

nicholas@nicholas-desktop:~$ cat /etc/network/interfaces
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











iface eth0 inet dhcp









auto eth0
nicholas@nicholas-desktop:~$ 

I use a SIEMENS SpeedStream 4100 Ethernet ADSL modem, I never had to configure it nor I had any problems with it on WinXP and WinVista.

---

### Post by bsfah3 on 2007-07-23
Ok... Looks like your network interfaces are correctly identified and configured for dhcp.  I'd do two things.

First do: 
```
sudo /etc/networking restart
``` 

and then:

```
ifconfig
```

and see if your interface has picked up a dhcp address.  If not, then try:

```
sudo more /var/log/messages |grep dhcp
```

and see what the message log has to say about why it's not able to get an address

---

### Post by dr.koljan on 2007-07-23
I did as you told me and here is a log which I created:

```
nicholas@nicholas-desktop:~$ sudo /etc/networking restart
Password:
sudo: /etc/networking: command not found
nicholas@nicholas-desktop:~$ sudo /etc/init.d/networking restart
 * Reconfiguring network interfaces...                                          RTNETLINK answers: No such process
There is already a pid file /var/run/dhclient.eth0.pid with pid 5278
killed old client process, removed PID file
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

Listening on LPF/eth0/00:13:8f:d9:98:fe
Sending on   LPF/eth0/00:13:8f:d9:98:fe
Sending on   Socket/fallback
There is already a pid file /var/run/dhclient.eth0.pid with pid 6847440
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

Listening on LPF/eth0/00:13:8f:d9:98:fe
Sending on   LPF/eth0/00:13:8f:d9:98:fe
Sending on   Socket/fallback
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 7
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 9
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 14
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 1
No DHCPOFFERS received.
No working leases in persistent database - sleeping.
eth1: ERROR while getting interface flags: No such device
There is already a pid file /var/run/dhclient.eth1.pid with pid 6847440
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

SIOCSIFADDR: No such device
eth1: ERROR while getting interface flags: No such device
eth1: ERROR while getting interface flags: No such device
Bind socket to interface: No such device
Failed to bring up eth1.
eth2: ERROR while getting interface flags: No such device
There is already a pid file /var/run/dhclient.eth2.pid with pid 6847440
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

SIOCSIFADDR: No such device
eth2: ERROR while getting interface flags: No such device
eth2: ERROR while getting interface flags: No such device
Bind socket to interface: No such device
Failed to bring up eth2.
ath0: ERROR while getting interface flags: No such device
There is already a pid file /var/run/dhclient.ath0.pid with pid 6847440
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

SIOCSIFADDR: No such device
ath0: ERROR while getting interface flags: No such device
ath0: ERROR while getting interface flags: No such device
Bind socket to interface: No such device
Failed to bring up ath0.
wlan0: ERROR while getting interface flags: No such device
There is already a pid file /var/run/dhclient.wlan0.pid with pid 6847440
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

SIOCSIFADDR: No such device
wlan0: ERROR while getting interface flags: No such device
wlan0: ERROR while getting interface flags: No such device
Bind socket to interface: No such device
Failed to bring up wlan0.
                                                                         [ OK ]
nicholas@nicholas-desktop:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:13:8F:D9:98:FE  
          inet6 addr: fe80::213:8fff:fed9:98fe/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:22 Base address:0xac00 

eth0:avah Link encap:Ethernet  HWaddr 00:13:8F:D9:98:FE  
          inet addr:169.254.11.19  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          Interrupt:22 Base address:0xac00 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:124 errors:0 dropped:0 overruns:0 frame:0
          TX packets:124 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:9404 (9.1 KiB)  TX bytes:9404 (9.1 KiB)

nicholas@nicholas-desktop:~$ sudo more /var/log/messages |grep dhcp
Jul 21 18:17:50 nicholas-desktop dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth0 for sub-path eth0.dbus.get.reason
Jul 21 18:17:50 nicholas-desktop dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth0 for sub-path eth0.dbus.get.reason
Jul 21 19:40:16 nicholas-desktop dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth0 for sub-path eth0.dbus.get.reason
Jul 21 19:40:16 nicholas-desktop dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth0 for sub-path eth0.dbus.get.reason
Jul 21 20:47:39 nicholas-desktop dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth0 for sub-path eth0.dbus.get.reason
Jul 21 20:47:39 nicholas-desktop dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth0 for sub-path eth0.dbus.get.reason
Jul 21 21:12:58 nicholas-desktop dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth0 for sub-path eth0.dbus.get.reason
Jul 21 21:12:58 nicholas-desktop dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth0 for sub-path eth0.dbus.get.reason
Jul 21 21:46:13 nicholas-desktop dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth0 for sub-path eth0.dbus.get.reason
Jul 21 21:46:13 nicholas-desktop dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth0 for sub-path eth0.dbus.get.reason
Jul 21 22:17:21 nicholas-desktop dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth0 for sub-path eth0.dbus.get.reason
Jul 21 22:17:21 nicholas-desktop dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth0 for sub-path eth0.dbus.get.reason
Jul 23 14:57:31 nicholas-desktop dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth0 for sub-path eth0.dbus.get.reason
Jul 23 14:57:31 nicholas-desktop dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth0 for sub-path eth0.dbus.get.reason
Jul 23 15:06:25 nicholas-desktop dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth0 for sub-path eth0.dbus.get.reason
Jul 23 15:06:25 nicholas-desktop dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth0 for sub-path eth0.dbus.get.reason
Jul 23 16:50:01 nicholas-desktop dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth0 for sub-path eth0.dbus.get.reason
Jul 23 16:50:01 nicholas-desktop dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth0 for sub-path eth0.dbus.get.reason
Jul 23 17:04:08 nicholas-desktop dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth0 for sub-path eth0.dbus.get.reason
Jul 23 17:04:08 nicholas-desktop dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth0 for sub-path eth0.dbus.get.reason
Jul 23 17:25:20 nicholas-desktop dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth0 for sub-path eth0.dbus.get.reason
Jul 23 17:25:20 nicholas-desktop dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth0 for sub-path eth0.dbus.get.reason
Jul 23 17:31:28 nicholas-desktop dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth0 for sub-path eth0.dbus.get.reason
Jul 23 17:31:28 nicholas-desktop dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth0 for sub-path eth0.dbus.get.reason
Jul 23 17:41:47 nicholas-desktop dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth0 for sub-path eth0.dbus.get.reason
Jul 23 17:41:47 nicholas-desktop dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth0 for sub-path eth0.dbus.get.reason
Jul 23 17:56:45 nicholas-desktop dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth0 for sub-path eth0.dbus.get.reason
Jul 23 17:56:45 nicholas-desktop dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth0 for sub-path eth0.dbus.get.reason
Jul 23 18:02:09 nicholas-desktop dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth0 for sub-path eth0.dbus.get.reason
Jul 23 18:02:09 nicholas-desktop dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth0 for sub-path eth0.dbus.get.reason
Jul 23 18:08:42 nicholas-desktop dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth0 for sub-path eth0.dbus.get.reason
Jul 23 18:08:42 nicholas-desktop dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth0 for sub-path eth0.dbus.get.reason
Jul 23 18:27:09 nicholas-desktop dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth0 for sub-path eth0.dbus.get.reason
Jul 23 18:27:09 nicholas-desktop dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth0 for sub-path eth0.dbus.get.reason
Jul 23 18:50:25 nicholas-desktop dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth0 for sub-path eth0.dbus.get.reason
Jul 23 18:50:25 nicholas-desktop dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth0 for sub-path eth0.dbus.get.reason
Jul 23 19:07:20 nicholas-desktop dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth0 for sub-path eth0.dbus.get.reason
Jul 23 19:07:20 nicholas-desktop dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth0 for sub-path eth0.dbus.get.reason
Jul 23 20:20:23 nicholas-desktop dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth0 for sub-path eth0.dbus.get.reason
Jul 23 20:20:23 nicholas-desktop dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth0 for sub-path eth0.dbus.get.reason
nicholas@nicholas-desktop:~$ 
```

Any ideas what should I do next? :)

---

### Post by bsfah3 on 2007-07-23
The conversation here sounds applicable:  [http://ubuntuforums.org/showthread.php?t=499361&page=4](http://ubuntuforums.org/showthread.php?t=499361&page=4)

My recommendation is to run:

```
sudo update-rc.d -f avahi-daemon remove
```

reboot and cross your fingers!

---

### Post by Pioneer5000 on 2007-07-23
I had kind of the same problem, when i ran ubuntu from the live cd the internet worked fine. but then when i properly installed it, it wouldnt detect my connection. But im new to linux so i dont know if what i did will help you but it might help someone else in the future all i did was go:
System -- > Admistration --> Network Then while on the connection page i went into properties and and enabled connection. And then ticked the box back on the connection tab. And that was it, my USB dsl connection was working. I'm guessing this wont help you but hopefully it helps someone else out in the future. Also make sure you enable the right connection and if you dont know which one is the right one just enable them all till you get the right one then disable the others. Also cold start modem before doing this.

---

### Post by dr.koljan on 2007-07-24
Problem solved :)

Internet just started working for no reason at all ^^

Seems that all I had to do was to cold-reboot my computer into Ubuntu (I used to reboot into Windows all the time) :guitar:

---

### Post by Rui Pais on 2007-07-24
> **dr.koljan said:**
> Problem solved :)

Internet just started working for no reason at all ^^

Seems that all I had to do was to cold-reboot my computer into Ubuntu (I used to reboot into Windows all the time) :guitar:

Hi, sorry yesterday i have to leave, but bsfah3 pointed correctly to the answer.

For the "reason" to start work, read my comments on [the other thread]("http://ubuntuforums.org/showthread.php?t=499361&page=4") that bsfah3 points.
It boils down to avahi daemon insist on assign an IP to your card not on the same subnet then your router/modem, ignoring dhcp (or manual settings, if you set it for static).

It's the second time i find a user with problems caused by that (redundant) daemon, both with the "inet addr:169.254.x.x"...


edit: Now reading again your post... i'm not sure if you just cold-reboot or turned off the avahi-daemon...

---

### Post by dr.koljan on 2007-07-24
> **Rui Pais said:**
> Hi, sorry yesterday i have to leave, but bsfah3 pointed correctly to the answer.

For the "reason" to start work, read my comments on [the other thread]("http://ubuntuforums.org/showthread.php?t=499361&page=4") that bsfah3 points.
It boils down to avahi daemon insist on assign an IP to your card not on the same subnet then your router/modem, ignoring dhcp (or manual settings, if you set it for static).

It's the second time i find a user with problems caused by that (redundant) daemon, both with the "inet addr:169.254.x.x"...

The weird thing is that I didn't disable anything - it just started working, that's all ;)

---

### Post by Rui Pais on 2007-07-24
> **dr.koljan said:**
> The weird thing is that I didn't disable anything - it just started working, that's all ;)

yes, i realized that after i post... 
it's weird (and boring, cause problems that magically disappear usually appear again :(...)

Can you boot from Windows and Ubuntu successively and keep connected in both systems? 
If you can then everything should be solved.

---

