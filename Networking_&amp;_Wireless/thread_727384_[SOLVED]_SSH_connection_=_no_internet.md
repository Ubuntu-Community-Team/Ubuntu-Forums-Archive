---
title: "[SOLVED] SSH connection = no internet"
date: 2008-03-17
forum: Networking &amp; Wireless
---

### Post by secondstage on 2008-03-17
When I connect to my SSH server, the wireless internet stops working. I have to reboot to get the wireless to work.

**ifconfig before the SSH connection:**
```
john@john:~$ ifconfig
eth1      Link encap:Ethernet  HWaddr 00:17:3F:1D:7A:38  
          inet addr:192.168.1.67  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::217:3fff:fe1d:7a38/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:952 errors:5517 dropped:18 overruns:0 frame:5507
          TX packets:567 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:645819 (630.6 KB)  TX bytes:61885 (60.4 KB)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
```

**ifconfig after the SSH connection:**
```
john@john:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:1A:4D:55:C9:9B  
          inet addr:192.168.0.3  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::21a:4dff:fe55:c99b/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:102 errors:0 dropped:0 overruns:0 frame:0
          TX packets:119 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:19854 (19.3 KB)  TX bytes:15109 (14.7 KB)
          Interrupt:16 Base address:0xc000 

eth1      Link encap:Ethernet  HWaddr 00:17:3F:1D:7A:38  
          inet addr:192.168.1.67  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::217:3fff:fe1d:7a38/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1423 errors:8866 dropped:24 overruns:0 frame:8850
          TX packets:802 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:896690 (875.6 KB)  TX bytes:84607 (82.6 KB)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:4 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:200 (200.0 b)  TX bytes:200 (200.0 b) 
```

---

### Post by Eiríkr on 2008-03-17
I assume that eth0 is a wired connection; I'm baffled as to why this would activate, and even then, confused as to why that would kill the wireless.  All you're doing is ssh-ing in?  Very strange...

---

### Post by secondstage on 2008-03-17
Yes eth0 is the wired and eth1 is the wireless usb. What is thew purpose of a loopback?

If ssh-ing is having two computers connected via Ethernet cable through a 4-port switch, and having the ability to transfer files between them, then yes. If not then please explain.

---

### Post by Eiríkr on 2008-03-17
Loopback is required for a machine to contact itself via the networking stack.  Unixy systems make use of this in various ways, and disabling the lo interface usually makes the system unusable.  

I must admit I don't quite understand your comment here:
> If ssh-ing is having two computers connected via Ethernet cable through a 4-port switch, and having the ability to transfer files between them, then yes. If not then please explain.

If you're asking what I mean by "ssh-ing in", I simply mean accessing the machine via ssh.

---

### Post by secondstage on 2008-03-17
Sorry for the bad wording. I was just asking what ssh-ing meant. It was just one of those things that only the writer gets, I guess.

Back on subject. Got any ideas?

---

### Post by loudnlownoma on 2008-03-17
I ran into a similar problem with my home network a while back.  At home, I am limited to a dial-up(using my cell phone, but registered as a modem so dial-up is close enough), but have a wireless router for sharing files between the home PC's.  Anyway, the dial-up connection would disconnect when enabling the Ethernet card to connect through the router, and I would have to restart or disable all the connections and re-connect on the dial-up.  I found through some trial and error and advice from a friend that it likele gives the Ethernet connection priority when it's enabled or connected, and this may be true over the wireless as well.

The solution I found was o give the Ethernet connection a static IP, and leaving the default gateway blank.  Doing so allows the Ethernet to connect, but does not over-ride the gateway used for your Internet connection by the other hardware.  This seemed to solve my problem there, so it might be worth a try.

---

### Post by Eiríkr on 2008-03-17
Well, there's a thought.  Secondstage, is there any difference in your /etc/network/interfaces file from before and after a ssh session?

---

### Post by secondstage on 2008-03-18
**loudnlownoma**: let me just check what your saying
1. Give the wireless connection a static ip,
2. Leave the box where the gateway goes empty

**Eiríkr**: heres the /etc/network/interfaces file
_Before SSH connection_
```
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

iface eth1 inet dhcp
wireless-key **********
wireless-essid Bristol

auto eth1

iface eth0 inet dhcp


```

_After the SSH connection_
```

# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

iface eth1 inet dhcp
wireless-key **********
wireless-essid Bristol

auto eth1

iface eth0 inet dhcp

auto eth0

```
I took out some spaces and starred the key for my network. Just assume that the key would be there.

---

### Post by Eiríkr on 2008-03-18
I read recently in a [thread=723053]different thread[/thread] that Network Manager runs on login.  I had initially assumed that meant a full Gnome / KDE / XFCE / other GUI login, since NM seems to be a GUI program, but then in [thread=726894]another thread[/thread] it was clear that NM was running even on a machine that had X removed.  NM seems to be a very troublesome app from what I've seen on the boards; it apparently has a tendency to overwrite the interfaces file, and change a few other things as well.  If you don't need it, try removing it, and I rather expect your wierd network troubles will go away.  

HTH,

Eiríkr

---

### Post by secondstage on 2008-03-18
Are they all based on the same sketchy code,or could I find a good replacement?

---

### Post by Eiríkr on 2008-03-18
If you need something like it, I've heard good things about [wicd]("http://wicd.sourceforge.net/") as a replacement, but it's not in the Ubuntu repositories.  

Cheers,

Eiríkr

---

### Post by secondstage on 2008-03-18
Finally! Thanks

---

### Post by loudnlownoma on 2008-03-18
> **secondstage said:**
> **loudnlownoma**: let me just check what your saying
1. Give the wireless connection a static ip,
2. Leave the box where the gateway goes empty


That was what I meant, and sorry for the delay.  Glad you got it straightened out tho!

---

