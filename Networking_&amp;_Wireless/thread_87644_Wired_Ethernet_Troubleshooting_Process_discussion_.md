---
title: "Wired Ethernet Troubleshooting Process discussion thread"
date: 2005-11-08
forum: Networking &amp; Wireless
---

### Post by mlomker on 2005-11-08
This is the discussion thread for the wired ethernet troubleshooting sticky.  The sticky will be updated and refined based upon your input.

Please only post questions about the post itself to this thread.  Start another thread to troubleshoot your particular problem.

Thanks!

---

### Post by ssam on 2005-12-03
can someone copy this to the wiki? it might be quite useful there aswell.

---

### Post by mlomker on 2005-12-03
[QUOTE=ssam]can someone copy this to the wiki? it might be quite useful there aswell.[/QUOTE]

Absolutely. I've received no feedback on it so I wasn't sure if it was useful to people or not.

I was thinking about writing another one for wireless but wireless is more complicated.

---

### Post by teaker1s on 2005-12-03
I had problems with login account reseting static ip and ip address nothing solved it until I created a new account and bizarely it stopped reseting

many people don't turn on upnp in their routers which causes problems

a lot of dns issues are because ubuntu has dns auto discover issues this is solved by both specifying manually dns address in router and puting ubunto on a 
static ip in router and ubuntu

---

### Post by Mathboy on 2005-12-05
Commenting out ipv6 in aliases and rebooting didn't stop it loading for me :confused: 

lsmod still has this:

> 
ipv6                  217408  10


and I can't remove it:
> 
root@server:/etc# rmmod ipv6
ERROR: Module ipv6 is in use


I've been trying to figure out a [networking issue]("http://www.ubuntuforums.org/showthread.php?p=545366"), and am turning off things like ipv6 in the hopes of resolving it.

---

### Post by mlomker on 2005-12-05
[QUOTE=Mathboy]Commenting out ipv6 in aliases and rebooting didn't stop it loading for me :confused: [/QUOTE]

So am I because it worked with the 2.6.12-9 kernel but now that I'm on -10 it doesn't.

You could rename the file, but you may get some errors on bootup that way.  

```

mlomker@mlomkernote:/$ cd /lib/modules/$(uname -r)/kernel/net/ipv6
mlomker@mlomkernote:/lib/modules/2.6.12-10-k7/kernel/net/ipv6$ ls
ah6.ko   ip6_tunnel.ko  ipv6.ko  xfrm6_tunnel.ko
esp6.ko  ipcomp6.ko     netfilter

```

---

### Post by parthipan on 2005-12-07
hai  guys i have signed in i dont know how to post my questions
iam in a bpo industry for internet suppot

in a ethernet powerd internet
alway make sure the nic is working fine
and unplug and replug the cables from the modem
this is a basic and good step

guys inform me how to bridge the modem with the router and configuer the router

---

### Post by licaonr on 2005-12-09
Could you please help me and explain why isn't this working, i've added all the corect informations, but it doesn't want to connect to the internet:


[COLOR="DarkRed"]none@ubuntu:~$ sudo mii-tool eth0[/COLOR]
eth0: autonegotiation failed, link ok

[COLOR="DarkRed"]none@ubuntu:~$ ifconfig eth0[/COLOR]
eth0      Link encap:Ethernet  HWaddr 00:02:44:99:35: D1
          inet addr:80.97.152.20  Bcast:80.255.255.255  Mask:255.255.255.128
          inet6 addr: fe80::202:44ff:fe99:35d1/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:4325 errors:0 dropped:0 overruns:0 frame:0
          TX packets:5 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:375283 (366.4 KiB)  TX bytes:378 (378.0 b)
          Interrupt:12 Base address:0xd800

[COLOR="DarkRed"]none@ubuntu:~$ lspci | grep Eth[/COLOR]
0000:00:0f.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)

[COLOR="DarkRed"]none@ubuntu:~$ lsmod | grep mii[/COLOR]
mii                     5248  2 8139too,8139cp

[COLOR="DarkRed"]none@ubuntu:~$ route -n[/COLOR]
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
80.97.152.0    0.0.0.0         255.255.255.0   U     0      0        0 eth0

[COLOR="DarkRed"]none@ubuntu:~$ ping 62.231.124.129[/COLOR]
connect: Network is unreachable

[COLOR="DarkRed"]none@ubuntu:~$ cat /etc/resolv.conf[/COLOR]
domain workgroup
nameserver 194.153.227.82

[COLOR="DarkRed"]none@ubuntu:~$ cat /etc/network/interfaces[/COLOR]
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# This is a list of hotpluggable network interfaces.
# They will be activated automatically by the hotplug subsystem.
mapping hotplug
        script grep
        map eth0







iface eth0 inet static
address 80.97.152.20
netmask 255.255.255.128
gateway 62.231.124.129



auto eth0

[COLOR="DarkRed"]none@ubuntu:~$ ifconfig -a[/COLOR]
eth0      Link encap:Ethernet  HWaddr 00:02:44:99:35: D1
          inet addr:80.97.152.20  Bcast:80.255.255.255  Mask:255.255.255.128
          inet6 addr: fe80::202:44ff:fe99:35d1/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:6034 errors:0 dropped:0 overruns:0 frame:0
          TX packets:5 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:591154 (577.2 KiB)  TX bytes:378 (378.0 b)
          Interrupt:12 Base address:0xd800

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:2884 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2884 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:259594 (253.5 KiB)  TX bytes:259594 (253.5 KiB)

sit0      Link encap:IPv6-in-IPv4
          NOARP  MTU:1480  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

---

### Post by Mathboy on 2005-12-09
I've typed out some potentially useful info in this thread for gigabit networking: 

[http://ubuntuforums.org/showthread.php?t=101117]("http://ubuntuforums.org/showthread.php?t=101117")

Hope it's OK I link it here - I suspect people might read through this thread trying to find gigabit help. :)

---

### Post by Mathboy on 2005-12-09
[QUOTE=licaonr]
[COLOR="DarkRed"]none@ubuntu:~$ sudo mii-tool eth0[/COLOR]
eth0: autonegotiation failed, link ok
[/QUOTE]

That doesn't look promising - have you tried another ethernet cable and another port on your hub/switch?

---

### Post by licaonr on 2005-12-09
Yes i did, i've also tried set it manual with "mii-tool -F 100baseTx-FD eth0", but still nothing:(

---

### Post by mlomker on 2005-12-09
[QUOTE=licaonr]
[COLOR="DarkRed"]none@ubuntu:~$ lsmod | grep mii[/COLOR]
mii                     5248  2 8139too,8139cp
[/QUOTE]

I think your problem is here.  It is loading two ethernet drivers for one card.  That seems to be a common problem with the Realtek cards.  Try removing them both using **sudo rmmod *drivername*** and then try them one at a time using **sudo modprobe *drivername***.  

Once you figure out which one to use I'd simply delete the wrong one.  You'll find them under /lib/modules/*yourkernelversion*/kernel/drivers/net/

---

### Post by licaonr on 2005-12-09
Thank you for your response, i did what you told me, and still nothing:

[COLOR="DarkRed"]none@ubuntu:~$ lsmod | grep mii[/COLOR]
mii                     5248  2 8139too,8139cp
[COLOR="DarkRed"]none@ubuntu:~$ sudo rmmod 8139too[/COLOR]
[COLOR="DarkRed"]none@ubuntu:~$ sudo rmmod 8139cp[/COLOR]
[COLOR="DarkRed"]none@ubuntu:~$ lsmod | grep mii[/COLOR]
mii                     5248  0
[COLOR="DarkRed"]none@ubuntu:~$ sudo modprobe 8139too
none@ubuntu:~$ lsmod | grep mii[/COLOR]
mii                     5248  1 8139too
[COLOR="DarkRed"]none@ubuntu:~$ ifconfig -a[/COLOR]
eth0      Link encap:Ethernet  HWaddr 00:02:44:99:35: D1
          inet addr:80.97.152.20 Bcast:80.255.255.255  Mask:255.255.255.128
          inet6 addr: fe80::202:44ff:fe99:35d1/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:43 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:9150 (8.9 KiB)  TX bytes:308 (308.0 b)
          Interrupt:12 Base address:0xd800

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:8862 errors:0 dropped:0 overruns:0 frame:0
          TX packets:8862 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:807147 (788.2 KiB)  TX bytes:807147 (788.2 KiB)

sit0      Link encap:IPv6-in-IPv4
          NOARP  MTU:1480  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

[COLOR="DarkRed"]none@ubuntu:~$ cat /etc/resolv.conf[/COLOR]
domain workgroup
nameserver 194.153.227.82

[COLOR="DarkRed"]none@ubuntu:~$ cat /etc/network/interfaces[/COLOR]
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# This is a list of hotpluggable network interfaces.
# They will be activated automatically by the hotplug subsystem.
mapping hotplug
        script grep
        map eth0







iface eth0 inet static
address 80.97.152.20
netmask 255.255.255.128
gateway 62.231.124.129



auto eth0
[COLOR="DarkRed"]none@ubuntu:~$ ping 62.231.124.129[/COLOR]
connect: Network is unreachable
[COLOR="DarkRed"]none@ubuntu:~$ sudo rmmod 8139too
none@ubuntu:~$ lsmod | grep mii[/COLOR]
mii                     5248  0
[COLOR="DarkRed"]none@ubuntu:~$ sudo modprobe 8139cp
none@ubuntu:~$ lsmod | grep mii[/COLOR]
mii                     5248  1 8139cp
none@ubuntu:~$ ifconfig -a
lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:9414 errors:0 dropped:0 overruns:0 frame:0
          TX packets:9414 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:857595 (837.4 KiB)  TX bytes:857595 (837.4 KiB)

sit0      Link encap:IPv6-in-IPv4
          NOARP  MTU:1480  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
[COLOR="DarkRed"]
none@ubuntu:~$ cat /etc/network/interfaces[/COLOR]
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# This is a list of hotpluggable network interfaces.
# They will be activated automatically by the hotplug subsystem.
mapping hotplug
        script grep
        map eth0







iface eth0 inet static
address 80.97.152.20
netmask 255.255.255.128
gateway 62.231.124.129



auto eth0

---

### Post by jnoreiko on 2005-12-31
I need to set my ethernet's MTU to 1400 to work correctly with my ISP.
I know how to do that in Terminal, but how do I set it permanently?

---

### Post by mlomker on 2006-01-01
[I found this.]("http://glasnost.beeznest.org/articles/290")

---

### Post by projecteternity on 2006-01-03
I am getting a strange error at the first step.

benoit@beach1:~$ sudo mii-tool eth0
SIOCGMIIPHY on 'eth0' failed: Operation not supported

Could anyone point me in the right direction?

---

### Post by mlomker on 2006-01-04
[QUOTE=projecteternity]SIOCGMIIPHY on 'eth0' failed: Operation not supported
[/QUOTE]

What kind of card is it?

---

### Post by projecteternity on 2006-01-04
It is an onboard ICS 1883 chip 10/100mbs (this is very surprising concidering on their site ICS makes no mension of ever making ethernet chips). My motherboard also has a marvell 8001 chip that supports 10/100/1000 and tells me the same thing but my computer has problems comunicating with it (when I try to set the speed (with ethtool) it gives me an error).

I am using the ICS right now with windows and the Marvell dosen't seem to work with windows either.

---

### Post by mlomker on 2006-01-04
[QUOTE=projecteternity]I am using the ICS right now with windows and the Marvell dosen't seem to work with windows either.[/QUOTE]

I'd recommend disabling the unused interface in your motherboard's BIOS.  I'm not sure what driver your card would use.  You could try **dmesg | grep eth0** after booting up.

---

### Post by projecteternity on 2006-01-04
Here is what I got with dmesg | grep eth0

[4294675.555000] eth0: forcedeth.c: subsystem: 01458:e000 bound to 0000:00:05.0
[4294701.151000] eth0:no link during initialization.
[4341997.623000] eth0: forcedeth.c: subsystem: 01458:e000 bound to 0000:00:05.0
[4341999.227000] eth0:no link during initialization.

Also just to see what would happen (seeing as it apeared to br less than successful the first time) I tried it on eth1 and I got:

[4294675.631000] skge eth1: addr 00:14:85:03:53:75
[4341997.787000] skge eth1: addr 00:14:85:03:53:75

Also I have disabled the ethernet chip i don't use, in the process I have found that the chip that works is a part of the nvidea nforce 3 chipset (it said in the bios).

---

### Post by mips on 2006-01-04
Might want to have a look at:
[http://ubuntuforums.org/showthread.php?t=47615](http://ubuntuforums.org/showthread.php?t=47615)
[http://ubuntuforums.org/showthread.php?t=101117](http://ubuntuforums.org/showthread.php?t=101117)
[http://ubuntuforums.org/showthread.php?t=98322](http://ubuntuforums.org/showthread.php?t=98322)

---

### Post by jnoreiko on 2006-01-10
[QUOTE=mlomker][I found this.]("http://glasnost.beeznest.org/articles/290")[/QUOTE]

Thanks.
That's worked.

For reference, this is what I now have in my /etc/network/interfaces file for the eth0 interface:

```
iface eth0 inet dhcp
        pre-up /sbin/ifconfig $IFACE mtu 1400

```

the other lines mentioned on that page don't seem to be needed.

---

### Post by joecr on 2006-01-14
From what I'm seeing here & from my troubleshooting earlier I think I have the problem with the IPv6 causing problems with my router.  The only problem is I'm using the Live CD, & I plan on using it to try to get my mom to switch at least one of her computers over to Linux.  I just don't think she would go for an OS that doesn't work on the Internet.

Basicly what I'm asking is there a way to disable IPv6 on the live CD?

---

### Post by Upuntu on 2006-01-14
I have done everything but my network does not work. It says like this:
**cat /etc/network/interfaces**
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback
address 127.0.0.1
netmask 255.0.0.0

# This is a list of hotpluggable network interfaces.
# They will be activated automatically by the hotplug subsystem.
mapping hotplug
        script grep
        map eth0


iface eth0 inet dhcp

auto eth0
**ifconfig eth0**
eth0      Link encap:Ethernet  HWaddr 00:13:D3:B7:27:10
          inet addr:84.253.206.248  Bcast:84.253.207.255  Mask:255.255.240.0
          inet6 addr: fe80::213:d3ff:feb7:2710/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1208 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1085 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:151700 (148.1 KiB)  TX bytes:131815 (128.7 KiB)
          Interrupt:23 Base address:0xec00

**route -n**
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
84.253.192.0    0.0.0.0         255.255.240.0   U     0      0        0 eth0
0.0.0.0         84.253.192.1    0.0.0.0         UG    0      0        0 eth0
**ping 84.253.194.154**
PING 84.253.194.154 (84.253.194.154) 56(84) bytes of data.

--- 84.253.194.154 ping statistics ---
13 packets transmitted, 0 received, 100% packet loss, time 11998ms

---

### Post by mlomker on 2006-01-15
[QUOTE=joecr]Basicly what I'm asking is there a way to disable IPv6 on the live CD?[/QUOTE]

I'm not that knowledgable about it, but I doubt it.

---

### Post by mlomker on 2006-01-15
```

Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
84.253.192.0    0.0.0.0         255.255.240.0   U     0      0        0 eth0
0.0.0.0         84.253.192.1    0.0.0.0         UG    0      0        0 eth0
**ping 84.253.194.154**
PING 84.253.194.154 (84.253.194.154) 56(84) bytes of data.

```

I don't know what that address is.  Can you ping your router at the 192.1 address?

---

### Post by Mr_Grieves on 2006-01-15
I've written a little guide on how to troubleshoot the diffrent errors counters that are being displayed with 'ifconfig'. I hope you find it useful. No text has been copied off any websites. I work as a network engineer on a ISP/Carrier.

The diffrent error types are pretty general for diffrent fysical-level protocols. So this mostly applies to wireless connections aswell, though, I had wired connections in mind when writing this. If you like I guess I could re-write it to fit both wireless and wired connections, or write another guide for wireless..

Please check for spelling misstakes, I'm not native English :)

----
**_Troubleshooting error counters**_

Look at the error section in output from 'ifconfig eth0'.
Error counters should read 0. In case there are registrered errors this *may* indicate diffrent network problems.
Have in mind that a few errors could appear when for example connecting the network cable to a network interface card/port. What we are most interested in here are larger amounts of errors in relation to the total amount of packets that's been send or received.

> 
RX Packets:56891 errors:0 dropped:0 overruns:0 frame:0
TX Packets:45 errors:0 dropped:0 overruns:0 frame:0
collisions:0 txqueuelen:1000


If you happen to have errors registered, take a note and check back 5 minuters later. If there has counted up more errors you might be experiencing diffrent problems, read more below. If the error counters are unchanged and you still suspect something might show, repeat the procedure and check back in 15 minutes, then 30, then 60, then 6 hours, then 12 hours and so on.

**RX/TX**
RX means inbound towards your network interface card.
TX means outbound towards the network.
It is difficult to diagnose where a problem come from, by just looking at if errors are registrered as inbound or outbound on your computer. If possible, also check error counters on the device that you connect to.

**Error types**

**Errors**
Registrered errors often indicate that you have sending or receiving corrupted packets. Most often the result of either a faulty cabling or faulty network interfaces. Try and change your cabling, network interface card (NIC) in your computer or port/NIC that you are connected to.

**Frame**
Like above with "Errors" this indicate that your system are detecting corrupted information. Frames being send or recieved seems to be faulty. Most often the result of either a faulty cabling or faulty network interfaces. Try and change your cabling, network interface card (NIC) in your computer or port/NIC that you are connected to.

**Dropped**
Dropped packets. This is not due to your firewall. Dropped packets indicate that either your computers or connecting systems packet buffers are overflowing. When there is to much packets to process, packets get dropped. Check for bottle necks in the network and traffic abnormalities. Your system or your network are receiving or sending too much traffic.

**Overruns**
Overruns occurs when the buffers of the network interface card is full, but is still trying to handle incoming traffic. Again, check for bottle necks in the network and traffic abnormalities. Your system or your network are receiving or sending too much traffic.

**Collisions**
Collisions typically indicate that you are running half duplex in your network, if this is not normal you may have a duplex missmatch on the Network. Check duplex settings for you're system and for connecting systems.

---

### Post by mips on 2006-01-15
> RX/TX
RX means outbound towards the network.
TX means inbound towards your network interface card.

That should be the other way round.
RX=Receive
TX=Transmit

---

### Post by Mr_Grieves on 2006-01-15
[QUOTE=mips]That should be the other way round.
RX=Receive
TX=Transmit[/QUOTE]
Yea, I saw that when reading thru the text, allready fixed :)

Maybe one should also make a note above what kind of cable one should use, depending on what device you are connecting to. I know this does not apply in fully due to that most router/switch ports today can adept thier selfs, but..

This is a good page: [http://cabletype.hacka.net](http://cabletype.hacka.net)

*Edit* I spelled Received wrong - Fixed

*Edit* Changed: "You are receiving/sending too much traffic." -> "Your system or your network are receiving or sending too much traffic." As the overflow in traffic could be caused by other sources inside/outside the local network.

---

### Post by Mr_Grieves on 2006-01-15
*Edit* duplicate.

---

### Post by Seventh-Monkey on 2006-01-20
I'm trying to run a static-IP Ubuntu box as 192.168.2.128 on my LAN, and am failing. When I tried switching to DCHP, the network adapter's MAC address was listed on my router's DCHP client webpage, but I have yet to be able to ping/do anything useful in either direction. Here's some of what I've tried. Help much appreciated.

> $mii-tool eth0

eth0: negotiated 100baseTx-FD, link ok


$ifconfig eth0

eth0      Link encap:Ethernet  HWaddr 00:10:A7:12:D4:F6  
          inet addr:192.168.2.128  Bcast:192.168.2.255  Mask:255.255.255.0
          inet6 addr: fe80::210:a7ff:fe12:d4f6/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:5 Base address:0xe400 


$route -n

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.2.0     0.0.0.0         255.255.255.0   U     0      0        0 eth0
0.0.0.0         192.168.2.1     0.0.0.0         UG    0      0        0 eth0


$ip ad

1: lo: <LOOPBACK,UP> mtu 16436 qdisc noqueue 
    link/loopback 00:00:00:00:00:00 brd 00:00:00:00:00:00
    inet 127.0.0.1/8 scope host lo
    inet6 ::1/128 scope host 
       valid_lft forever preferred_lft forever
2: wlan0: <BROADCAST,MULTICAST> mtu 1500 qdisc noop qlen 1000
    link/ether 00:11:50:3e:4a:47 brd ff:ff:ff:ff:ff:ff
3: eth0: <BROADCAST,MULTICAST,UP> mtu 1500 qdisc pfifo_fast qlen 1000
    link/ether 00:10:a7:12:d4:f6 brd ff:ff:ff:ff:ff:ff
    inet 192.168.2.128/24 brd 192.168.2.255 scope global eth0
    inet6 fe80::210:a7ff:fe12:d4f6/64 scope link 
       valid_lft forever preferred_lft forever
4: sit0: <NOARP> mtu 1480 qdisc noop 
    link/sit 0.0.0.0 brd 0.0.0.0


$ip ro

192.168.2.0/24 dev eth0  proto kernel  scope link  src 192.168.2.128 
default via 192.168.2.1 dev eth0 


$ping 192.168.2.128 -c 4

PING 192.168.2.128 (192.168.2.128) 56(84) bytes of data.
64 bytes from 192.168.2.128: icmp_seq=1 ttl=64 time=0.094 ms
64 bytes from 192.168.2.128: icmp_seq=2 ttl=64 time=0.086 ms
64 bytes from 192.168.2.128: icmp_seq=3 ttl=64 time=0.086 ms
64 bytes from 192.168.2.128: icmp_seq=4 ttl=64 time=0.086 ms

--- 192.168.2.128 ping statistics ---
4 packets transmitted, 4 received, 0% packet loss, time 2999ms
rtt min/avg/max/mdev = 0.086/0.088/0.094/0.003 ms


$ping 192.168.2.1 -c 4

PING 192.168.2.1 (192.168.2.1) 56(84) bytes of data.
From 192.168.2.128 icmp_seq=2 Destination Host Unreachable
From 192.168.2.128 icmp_seq=3 Destination Host Unreachable
From 192.168.2.128 icmp_seq=4 Destination Host Unreachable

--- 192.168.2.1 ping statistics ---
4 packets transmitted, 0 received, +3 errors, 100% packet loss, time 2999ms
, pipe 3

---

### Post by ThirdGenLS1 on 2006-01-20
alright I just booted up ubuntu last night and i can't get it to connect to the internet if my life depended on it. I have a wireless card but for right now i'm just trying to get it working with my etho cord. When i plug the cord in it reads that i'm connnected but i just can't get any internet. Its in DHCP mode right now and when i enter in the ifconfig eth0 in the terminal i get

Link encap:Ethernet HWaddr 00:08:02: DO:35:58
inet6 addr: fe80::208:3558/64 Scope:Link
UP BROADCAST MULTICAST MTU:1500 Metric:1
RX packets:1355 errors:0 drpped:0 overruns:0 frame:0
TX packets:7 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txpuenelen:100
RX bytes:62999 (61.5 KiB) TX bytes:2394 (2.3 KiB)
interrupt:11 Base adress:0xa800

and when i enter lspci | Eth
ethernet controller: Realtek Semiconductor Co., Ltd. Rtl-8139/8139c/8139C+ (rev 20)

When intering route -n it shows nothing in the gateway, genmask, ETC.

Any help would be greatly appreciated, cause i'm pretty excited to get this up and running.

---

### Post by mips on 2006-01-21
Well you are not getting an IP address from your DHCP server. Maybe try and use a static address for now.

---

### Post by mips on 2006-01-21
[QUOTE=Seventh-Monkey]I'm trying to run a static-IP Ubuntu box as 192.168.2.128 on my LAN, and am failing. When I tried switching to DCHP, the network adapter's MAC address was listed on my router's DCHP client webpage, but I have yet to be able to ping/do anything useful in either direction. Here's some of what I've tried. Help much appreciated.[/QUOTE]

Look at IPv6 & DNS. This is not really the thread to reply to as it only concerns the actual howto, you should start your own thread.

---

### Post by Luk8 on 2006-02-01
Hello everyone :) .

I'm having problems with my network connection... when I try to activate (enable) the connection,it deactivates itself imeadiatly.
I attached a .txt with data that might be usefull (the "ifconfig eth0" are taken in an interval of an hour in total,from first one to last one ).

Any ideas or adviced ? I tryied anything I saw on this topic , and still nothing .The network is fine , as now I'm writing from WindowsXP (I have a dual boot machine) .

Thx,and sorry for my poor english.

PS: I should be recieving the network settings (IP,subnet mask,etc)  from a DHCP server ,but that might not be the problem if I can't even enable the connection properly.

Edit: I'm using Kubuntu 5.10

---

### Post by mlomker on 2006-02-01
That's a common problem with that model of card--it's trying to load two Ethernet drivers for one card:

```

george@Geo88:~$ lsmod | grep mii
mii                     5248  2 8139too,8139cp

```

You could try renaming them one at a time and then rebooting.  One of the two will be the correct driver for your card.

You'll find them in a directory similar to the following:

/lib/modules/2.6.12-10-k7/kernel/drivers/net/8139too.ko

---

### Post by Luk8 on 2006-02-01
Thanks for your reply :) ,however I'm still having some issues :( .

> You could try renaming them one at a time and then rebooting. One of the two will be the correct driver for your card.

You'll find them in a directory similar to the following:

/lib/modules/2.6.12-10-k7/kernel/drivers/net/8139too.ko


I renamed them,however renaming them doesn't prevent them from loading after a reboot.


I renamed ```
8139cp.ko
``` to ```
x8139cp.ko
``` (from the folder you told me) and the result of > george@Geo88:~$ lsmod | grep miiafter a reboot (actually 2-3 reboots) is still> 
mii                     5248  2 8139too,8139cp

PS: I found somwhere in    \sys\     2 folders named 8139cp (I was planing to rename this driver first ) , but I can't rename them even with sudo provileges, it seems they can only be modified by root,and root login is forbiden as far as I've seen.

](*,) #-o

---

### Post by mlomker on 2006-02-02
I should have been more specific...you need to change the extension and not the first part.  Rename it to 8139too.old or similar...

---

### Post by jamesr on 2006-02-23
I thought that this tread was to be about suggestions with reference to ethernet  troubleshooting  sticky.

> This is the discussion thread for the wired ethernet troubleshooting sticky. The sticky will be updated and refined based upon your input.

Please only post questions about the post itself to this thread. Start another thread to troubleshoot your particular problem.

Thanks!


You have not mentioned the problem of the card not being recognised and needing a 
sudo modprobe nicname
to find it. There are many people still using ISA cards and the common ones are not recognised by Ubuntu automatically. The same problem occurs with Debian. 
If you do an expert installation Ubuntu or with Debian leave out the card  and then pick from the list, you can get round the problem, but new users do not usually wish to try that route.
I would think that the section allocated to the physical layer ie the NIC itself , should include the ways of identifying the card including ISA cards.

I personally always  suggest starting  with 
sudo ifconfig -a 
then depending on the result work backwards ie 
dmesg |grep eth0
or forwards
sudo dhclient
then 
ifconfig -a
again

Always getting it to work before changing any files and then always making copies before changing the files.

Doesn't the miitool route depend on  having a working router and that can in itself could be a problem. Equally I have certainly seen problems where the link LED is green but the link does not work. I was taught never to assume anything and that was the way that I taught users and engineers to fault find on scientific equipment.

---

### Post by adam.mech09 on 2006-02-26
Hi

having the exact same problem as ThirdGenLS1, but mine seems to have happened for no reason.  I have been having some hardware difficulties lately, nothing to do with ubuntu, and booting into either ubuntu or xp has been problematic.  I swapped around some memory sticks and now it boots properly, but it takes a long time to "configure network devices" on bootup.

When I log in, I cannot connect to my network at all.  I do have a small issue that is different, and that is that I'm using a switch instead of a router.

I have tried assigning it an ip, 192.168.0.4, but that didnt work.

Any other suggestions?

---

### Post by mlomker on 2006-02-27
[QUOTE=jamesr]You have not mentioned the problem of the card not being recognised and needing a
[/quote]

Yup, that is worth adding.

> Doesn't the miitool route depend on  having a working router and that can in itself could be a problem. 

No.

> Equally I have certainly seen problems where the link LED is green but the link does not work. 

I have seen duplex negotiation problems and EMI/RMI issues can show that symptom, but it is exceedingly rare in business settings and even more unlikely for a home user.  

---
If I start running into questions in this thread about a particular issue then I add a section about that, based upon the frequency of the questions.  

This how-to is intended as a starting point and not a one-stop solution to avoid asking any questions or using other resources.

---

### Post by CameronCalver on 2006-04-20
Hey this is a mad how to but can you help me with my problem i have 2 ubuntu computer each have a network cable going to a 8 port ethonet switcher and it says that they are both connected what will i run to find out the other computer ip and what do i have to  do to share a folder and share internet and share printer do u no what i have to do i need a very easy to understand post becuase i am a noob

---

### Post by TiZeta on 2006-04-24
Hope this can help someone: :D 

I have an Acer1600 with a realtek network adapter, connected to a router (Dlink dsl-504t).
I have Dapper installed, kernel is 2.6.15-21-286.
My problem whas that the adapter was recognised, network was configured ok,  two drivers were loaded, 8139cp and 8139too  (but double drivers are not the problem, now it works fine and they are still there).
Well, when i tried to ping my router it gave me "host unreachable".
I couldn't connect the internet too, of course.

I've found the solution in dmesg: kernel disabled my nic irq, and suggested to boot with irqpoll option. That's the solution!

Just add irqpoll to your kernel parameters.

With Grub just edit /boot/grub/menu.lst, search for your kernel line and add 
[COLOR="Red"] irqpoll  [/COLOR]
toghether with the all the other options.
This worked for me, after rebooting the message has disappeared and now nerwork works fine.

---

### Post by daniel83 on 2006-04-26
Hello, I am a complete noob hoping never to use Windows again for anything other than games. 

I want as less hassle in my transition, but I understand things aren't going to be as easy as Windows.

I just installed ubuntu 5.10, I've tried to follow instructions to get my internet connection to work, but no luck.

Seems I am having a problem with my Physical Layer; no lights on the Ethernet card (or should say mother board Ethernet socket)! I have no idea how to resolve.

I've tried:

sudo mii-tool eth0
..and get...
eth0: link ok

ifconfig eth0
...looks okay, but there are 0 packets sent & received.

lspci | grep Eth
...looks okay, it returns the name of my card (Realtek RTL8139 Family PCI Fast Ethernet NIC).

Of course, I have never had such problems in Windows ?!?

Any help would be great, thanks,
Daniel.

---

### Post by Batouttahell on 2006-04-26
I can't help you, but I am having trouble making my Ubuntu machine pick up my schools wireless network, and I can't login as root in order to change it. Can someone tell me how to do this, as I am trying to host an FTP server from the box

---

### Post by daniel83 on 2006-04-26
[QUOTE=daniel83]
...looks okay, it returns the name of my card (Realtek RTL8139 Family PCI 
[/QUOTE]

I think there might be something simular happening to as in TiZeta's post ... except I have no idea how to edit the menu.ls file in GRUB! I can manage to open it in GNOME, but its read-only.

Thanks for any guidence,
  Daniel.

---

### Post by Jussi Kukkonen on 2006-04-27
[QUOTE=daniel83]I think there might be something simular happening to as in TiZeta's post ... except I have no idea how to edit the menu.ls file in GRUB! I can manage to open it in GNOME, but its read-only.

Thanks for any guidence,
  Daniel.[/QUOTE]
Please start new threads for questions, this thread is for discussion about the how-to and hijacking it is rude.


ps. you'll need to have super-user rights for editing grub files. Try *sudo gedit* in a terminal.
ps2. do not edit menu.lst if you do not understand what you're doing (unless you're willing to take risks, of course. Personally, I like risk ;)).

---

### Post by daniel83 on 2006-04-27
Sorry Jussi Kukkonen, I had no idea that I was hijacking ... just a noob in need :-|

---

### Post by nightwolf2k5 on 2006-12-03
hey everyone.. ah.. ikinda have a strange problem with my net.. i have to always disable and enable my eth0 connection everytime i restart my comp in order to surf the net.. otherwise.. the net does not work.. :(

---

