---
title: "IP keeps changing"
date: 2007-08-06
forum: Networking &amp; Wireless
---

### Post by stealth17 on 2007-08-06
I have firestarter going so I can share internet off of my extra ethernet card. I have set that NIC to use 192.168.0.1... but it likes to change to 192.168.0.253 for no apparent reason. I set the IP in /etc/network/interfaces but it didn't help. I figured it is getting that IP from it's own DHCP server, so I made the IP static and restarted networking. Still didn't help.

Any idea why it keep changing? Every time it changes I loose internet so it is really annoying.

Thanks.

---

### Post by noob12 on 2007-08-06
Can you post the output of each of these **cat /etc/network/interfaces**,  **ifconfig -a**, and **ps -ef | grep dhclient** ?

---

### Post by stealth17 on 2007-08-07
```
stealth17@stealth17-desktop:~$ cat /etc/network/interfaces
auto lo
iface lo inet loopback

auto eth0
iface eth0 inet dhcp
address 192.168.1.103
netmask 255.255.255.0
gateway 192.168.1.1

##auto eth1
##iface eth1 inet dhcp

##auto eth2
##iface eth2 inet dhcp

##auto ath0
##iface ath0 inet dhcp

##auto wlan0
##iface wlan0 inet dhcp


iface eth1 inet static
address 192.168.0.1
netmask 255.255.255.0

```

```
stealth17@stealth17-desktop:~$ ifconfig -a
eth0      Link encap:Ethernet  HWaddr 00:01:29:D4:E9:2B  
          inet addr:192.168.1.103  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::201:29ff:fed4:e92b/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:189625 errors:0 dropped:0 overruns:0 frame:0
          TX packets:191351 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:123367957 (117.6 MiB)  TX bytes:91164272 (86.9 MiB)
          Interrupt:21 

eth1      Link encap:Ethernet  HWaddr 00:01:29:D4:E9:5D  
          inet addr:192.168.0.1  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::201:29ff:fed4:e95d/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1535248 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1076528 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1234752835 (1.1 GiB)  TX bytes:133625354 (127.4 MiB)
          Interrupt:16 Base address:0x8000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:17163 errors:0 dropped:0 overruns:0 frame:0
          TX packets:17163 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:11191943 (10.6 MiB)  TX bytes:11191943 (10.6 MiB)

vmnet1    Link encap:Ethernet  HWaddr 00:50:56:C0:00:01  
          inet addr:172.16.18.1  Bcast:172.16.18.255  Mask:255.255.255.0
          inet6 addr: fe80::250:56ff:fec0:1/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:6 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

vmnet8    Link encap:Ethernet  HWaddr 00:50:56:C0:00:08  
          inet addr:172.16.167.1  Bcast:172.16.167.255  Mask:255.255.255.0
          inet6 addr: fe80::250:56ff:fec0:8/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:6 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

```

```
stealth17@stealth17-desktop:~$ ps -ef | grep dhclient 
dhcp     15142     1  0 Aug06 ?        00:00:00 dhclient3 -pf /var/run/dhclient.eth0.pid -lf /var/lib/dhcp3/dhclient.eth0.leases eth0
1000     22307 22229  0 00:04 pts/4    00:00:00 grep dhclient
dhcp     25096  4633  0 Aug05 ?        00:00:00 /sbin/dhclient -1 -lf /var/lib/dhcp3/dhclient.eth1.leases -pf /var/run/dhclient.eth1.pid -q -e dhc_dbus=31 -d eth1

```


That is with it working correctly. Do you need the output of when it switches to 192.168.0.253 too?

---

### Post by noob12 on 2007-08-07
The eth0 one is odd because you have dhcp and a static config.  These aren't going to mix well.
I would recommend that you change the word **dhcp** to **static** here.
> 
auto eth0
iface eth0 inet [COLOR="Red"]dhcp[/COLOR] (should say [COLOR="Green"]static[/COLOR])
address 192.168.1.103
netmask 255.255.255.0
gateway 192.168.1.1


The eth1 one is ok but the interface won't come up automatically that way.  You should have
the following if you want the interface to come up automatically at boot.
> 
[COLOR="Green"]auto eth1[/COLOR]
iface eth1 inet static
address 192.168.0.1
netmask 255.255.255.0


Your ps shows that you have a dhclient running for eth1 since Aug 5.  That is what is screwing with the address.  If you fix the two problems above and reboot, you shouldn't have this issue when things come back up.

I'm going to assume for now that you'll follow these suggestions; that will kill both birds.  If you do want eth0 under dhcp, then we'll need to deal with the eth1 dhclient lease state issue.  Let me know how it works.

---

### Post by stealth17 on 2007-08-07
k made the changes and will see how it goes.

btw it went out again and I grabbed the outputs just cause I could, here they are:

```
stealth17@stealth17-desktop:~$ ps -ef | grep dhclient 
dhcp     15142     1  0 Aug06 ?        00:00:00 dhclient3 -pf /var/run/dhclient.eth0.pid -lf /var/lib/dhcp3/dhclient.eth0.leases eth0
dhcp     25096  4633  0 Aug05 ?        00:00:00 /sbin/dhclient -1 -lf /var/lib/dhcp3/dhclient.eth1.leases -pf /var/run/dhclient.eth1.pid -q -e dhc_dbus=31 -d eth1
1000     26095 26058  0 01:26 pts/4    00:00:00 grep dhclient

```

```
stealth17@stealth17-desktop:~$ ifconfig -a
eth0      Link encap:Ethernet  HWaddr 00:01:29:D4:E9:2B  
          inet addr:192.168.1.103  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::201:29ff:fed4:e92b/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:399753 errors:0 dropped:0 overruns:0 frame:0
          TX packets:405892 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:258012000 (246.0 MiB)  TX bytes:152008458 (144.9 MiB)
          Interrupt:21 

eth1      Link encap:Ethernet  HWaddr 00:01:29:D4:E9:5D  
          inet addr:192.168.0.253  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::201:29ff:fed4:e95d/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1537017 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1079750 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1235625421 (1.1 GiB)  TX bytes:133967435 (127.7 MiB)
          Interrupt:16 Base address:0x8000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:21245 errors:0 dropped:0 overruns:0 frame:0
          TX packets:21245 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:14765165 (14.0 MiB)  TX bytes:14765165 (14.0 MiB)

vmnet1    Link encap:Ethernet  HWaddr 00:50:56:C0:00:01  
          inet addr:172.16.18.1  Bcast:172.16.18.255  Mask:255.255.255.0
          inet6 addr: fe80::250:56ff:fec0:1/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:6 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

vmnet8    Link encap:Ethernet  HWaddr 00:50:56:C0:00:08  
          inet addr:172.16.167.1  Bcast:172.16.167.255  Mask:255.255.255.0
          inet6 addr: fe80::250:56ff:fec0:8/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:6 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
```

and of course the /etc/network/interfaces was the same at that time.... here is my new config though just for shits:

```
auto lo
iface lo inet loopback

auto eth0
iface eth0 inet static
address 192.168.1.103
netmask 255.255.255.0
gateway 192.168.1.1

##auto eth1
##iface eth1 inet dhcp

##auto eth2
##iface eth2 inet dhcp

##auto ath0
##iface ath0 inet dhcp

##auto wlan0
##iface wlan0 inet dhcp

auto eth1
iface eth1 inet static
address 192.168.0.1
netmask 255.255.255.0
```

thanks for the help :)

---

### Post by noob12 on 2007-08-07
It went out before the changes, right?  That's ok.  When you reboot you should see no dhclient for either eth0 or eth1 in your **ps -ef | grep dhclient**.  If you do, we need to do some cleanup of dhclient lease state.

---

### Post by stealth17 on 2007-08-07
> **noob12 said:**
> It went out before the changes, right?  That's ok.  When you reboot you should see no dhclient for either eth0 or eth1 in your **ps -ef | grep dhclient**.  If you do, we need to do some cleanup of dhclient lease state.

Yeah that was before the changes/reboot.

Once I reboot I'll give you the new output :popcorn:

---

### Post by stealth17 on 2007-08-09
> **noob12 said:**
> It went out before the changes, right?  That's ok.  When you reboot you should see no dhclient for either eth0 or eth1 in your **ps -ef | grep dhclient**.  If you do, we need to do some cleanup of dhclient lease state.

Looks like it worked:

```
stealth17@stealth17-desktop:~/.wine/drive_c$ ps -ef | grep dhclient
1000      6321  6194  0 01:33 pts/0    00:00:00 grep dhclient
```

Thanks!

---

