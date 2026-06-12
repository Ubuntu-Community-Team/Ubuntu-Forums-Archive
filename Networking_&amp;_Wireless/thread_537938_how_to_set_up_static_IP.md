---
title: "how to set up static IP"
date: 2007-08-29
forum: Networking &amp; Wireless
---

### Post by uputer on 2007-08-29
I know the concepts  (or at least, I claim to) and how to set up a static IP in Windows.

Can someone outline the steps?   I am actually using Kubuntu (I prefer KDE over Gnome) but perhaps, the steps are similar and just under a different GUI system?  

My computer has the dual ethernet eth0 and eth1 and I'm not sure which is assigned what (in other words, which port gets eth0 and  eth1 respectively.).   I have Windows 2K on another partition already setup in static IP configuration.  I use a Linksys WRT54G router.   I have a P2P client (Azureus) to configure as well and I like to think I know how to forward ports.  It was working in Windows. 

I would appreciate if anyone could explain or provide links here where this is discussed and explained in detail.   Perhaps, there are even examples?   I think I can configure the P2P program on my own but I'm rather perplexed why I cannot get Kubuntu (Ubuntu) to setup the static IP properly.  Part of it is the ethernet ports designation confusion and the other is the unfamiliar territory of Ubuntu/Kubuntu in general.   I utilized the Network interfaces and configured the Internet Protocol for manual but I couldn't maintain my internet connection after the ip settings change.  

Hopefully, someone will try to assist and/or recognizes this problem.   

Thanks in advance (for any attempts at assisting).

---

### Post by uputer on 2007-08-30
Nobody?

---

### Post by bapoumba on 2007-08-30
Can you please post the output to:
```
cat /etc/network/interfaces
cat /etc/resolv.conf
ifconfig
```

---

### Post by uputer on 2007-08-31
First of all, sorry for the delay.   Hmmm...It's a very lengthy output.  Note:   This is on Kubuntu.   

user@computername:~$ cat /etc/network/interfaces
auto lo
iface lo inet loopback
address 127.0.0.1
netmask 255.0.0.0

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

~$ cat /etc/resolv.conf
nameserver 206.248.154.22
nameserver 69.28.199.126

~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:13:D4:D9:2E:45
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:16 Base address:0x4000

eth1      Link encap:Ethernet  HWaddr 00:13:D4:D9:2D:7D
          inet addr:192.168.1.101  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::213:d4ff:fed9:2d7d/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:233983 errors:0 dropped:0 overruns:0 frame:0
          TX packets:218338 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:69240458 (66.0 MiB)  TX bytes:23011827 (21.9 MiB)
          Interrupt:20

eth0:avah Link encap:Ethernet  HWaddr 00:13:D4:D9:2E:45
          inet addr:169.254.6.88  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          Interrupt:16 Base address:0x4000

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

I have disabled eth0 now and set eth1:
Network Interfaces
Available Network Interfaces
eth0  protocol:  dhcp    (manually) disabled
eth1 ip address set (manually) enabled 
Routes
Default Gateway
IP address:
0.0.0.0

I might want to set the Default Gateway?   Anything I need to do (now)?   I hope the output helps...

---

### Post by bapoumba on 2007-08-31
Okay, assuming you want eth1 on static IP, you need to change the /etc/network/interfaces to make it look like this, with appropriate IPs (sorry, I'm short on time right now, maybe someone else can provide details):
```
auto lo
iface lo inet loopback

# <insert_a_comment_here_if_you_want>
auto eth1
iface eth1 inet static
       address xxx.xxx.xxx.xxx
       netmask xxx.xxx.xxx.xxx
       network xxx.xxx.xxx.xxx
       broadcast xxx.xxx.xxx.xxx
       gateway xxx.xxx.xxx.xxx

```
Do you have a firewall, or a firewall GUI configuration application such as Firestarter running?

---

### Post by uputer on 2007-08-31
> **bapoumba said:**
> Okay, assuming you want eth1 on static IP, you need to change the /etc/network/interfaces to make it look like this, with appropriate IPs...

Do you have a firewall, or a firewall GUI configuration application such as Firestarter running?
No, no firewall running.  I just use the router.

How do I change the /etc/network/interfaces to "make it look like...?"   

Just asking but I will look into it.

---

### Post by bapoumba on 2007-08-31
You can edit the file with nano, a small test editor that runs in a terminal:
```
sudo nano -B /etc/network/interfaces
```
The -B option will create a backup copy of the file.

Change the sections according to the previous post (leave the other ones).
address 192.168.1.101
netmask 255.255.255.0
broadcast 192.168.1.255

I'm not sure about the other IPs, did not find them in your post. Do you have the gateway IP?

To save the file: CTRL-O (same name, hit enter)
To exit nano: CTRL-X

Restart the network
```
sudo /etc/init.d/networking restart
```

---

