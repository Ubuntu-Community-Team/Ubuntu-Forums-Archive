---
title: "Network Bridge Problem"
date: 2006-09-15
forum: Networking &amp; Wireless
---

### Post by xboxrob on 2006-09-15
I am strying to get ubuntu to act as a network bridge for two network interfaces. I am using bridge-utils to do this.
So far i have set up a bridge br0 and added the two interfaces to it. The ubuntu comp can now access both networks eg any computer. The problem is that any other computer cannot go through the bridge both sides are cut off from one another. Both sides though do have access to the ubuntu computer.
Many thanks for any help

---

### Post by kidders on 2006-09-15
Hi there,

I hope these aren't really obvious questions ...

1. Have you enabled packet forwarding?
2. Is your firewall blocking forwarded packets?

---

### Post by xboxrob on 2006-09-17
I hadnt enabled packet forwarding and have now done so but still the same problem. I have restarted the box and checked the forwarding was on. 

As for firewall i havent installed one and havent changed anything in that sense so unless it automatically was set i guess that wouldnt be the cause?

Thanks for your help

---

### Post by kidders on 2006-09-17
Hmm. I wonder if you could post some detail... IP addresses, routing tables, etc. It would help give a clearer picture of how far you've gotten so far.

---

### Post by bait on 2006-09-17
What do you get when you use the following command?

brctl showmacs br0

 Are both NICs set to promisc mode?

---

### Post by xboxrob on 2006-09-18
right cheers for trying to solve this heres some info hope this will help.

This is from route (and i feel could be the problem)

> Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.1.0     *               255.255.255.0   U     0      0        0 br0
default         api.home        0.0.0.0         UG    0      0        0 br0



Then this is from ifconfig

> 
br0       Link encap:Ethernet  HWaddr 00:60:B3:69:48:67
          inet addr:192.168.1.73  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::200:ff:fe00:0/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:40785 errors:0 dropped:0 overruns:0 frame:0
          TX packets:18015 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:21215766 (20.2 MiB)  TX bytes:2258980 (2.1 MiB)

eth0      Link encap:Ethernet  HWaddr 00:E0:18:7E:1E:EF
          inet6 addr: fe80::2e0:18ff:fe7e:1eef/64 Scope:Link
          UP BROADCAST RUNNING PROMISC MULTICAST  MTU:1500  Metric:1
          RX packets:10977 errors:0 dropped:0 overruns:0 frame:0
          TX packets:84747 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:1907815 (1.8 MiB)  TX bytes:11967980 (11.4 MiB)
          Interrupt:185 Base address:0x2000

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:1373329 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1373329 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:112146985 (106.9 MiB)  TX bytes:112146985 (106.9 MiB)

wlan0     Link encap:Ethernet  HWaddr 00:60:B3:69:48:67
          inet6 addr: fe80::260:b3ff:fe69:4867/64 Scope:Link
          UP BROADCAST RUNNING PROMISC  MTU:1500  Metric:1
          RX packets:102648 errors:0 dropped:0 overruns:0 frame:0
          TX packets:46168 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:37484656 (35.7 MiB)  TX bytes:6012523 (5.7 MiB)

Then finally brctl show

> br0
 bridge id               8000.0060b3694867
 designated root         8000.0060b3694867
 root port               0                path cost                  0
 max age                 20.00            bridge max age            50.00
 hello time              2.00             bridge hello time          5.00
 forward delay           37.50            bridge forward delay      15.00
 ageing time             300.01
 hello timer             1.22             tcn timer                  0.00
 topology change timer   0.00             gc timer                   0.02
 flags


wlan0 (1)
 port id            8001                   state                forwarding
 designated root    8000.0060b3694867      path cost                100
 designated bridge  8000.0060b3694867      message age timer          0.00
 designated port    8001                   forward delay timer        0.00
 designated cost    0                      hold timer                 0.22
 flags

eth0 (2)
 port id             8002                   state                forwarding
 designated root     8000.0060b3694867      path cost                  100
 designated bridge   8000.0060b3694867      message age timer          0.00
 designated port     8002                   forward delay timer        0.00
 designated cost     0                      hold timer                 0.22
 flags


also here is brctl showmacs

> port no mac addr                is local?       ageing timer
  2     00:09:5b:b8:43:a8       no               202.57
  1     00:0d:56:6e:ac:ae       no                65.56
  1     00:0d:93:ae:69:70       no                 5.34
  2     00:11:50:6e:73:ae       no                 2.72
  1     00:14:7f:55:92:42       no                15.74
  1     00:60:b3:69:48:67       yes                0.00
  2     00:e0:18:7e:1e:ef       yes                0.00
  1     02:14:7f:55:92:42       no               251.81


hope this is useful

---

### Post by kidders on 2006-09-20
Yeah, I think you might be right ... it seems odd that there isn't more in your bridge's routing table, not to mention the fact that your default route might not be right. All the rest seems pretty good though :-)

This may be a dumb question, but do all your machines have 192.168.1.73 as their default route?

My understanding of bridging is a little limited, but it strikes me that you seem to be using a loop detection algorithm. These are quite complicated and can sometimes flood your bridge with lots of garbage. Since yours is so straightforward (relatively speaking!!), a routing loop is probably extremely unlikely ... so you could switch the protection off. I know there is an easy way to do this ... I just don't know what it is :-( :-(

Maybe bait can be of some help? I can't see the problem in what you've posted! Dammit!

---

### Post by xboxrob on 2006-09-20
Well cheers very much for all your help! I think there are some Hardware products i can get a hold of that will do what i need i just thought that it would be nice if the ubuntu computer i was already using could do it and it was annoying me because everywhere i looked seemed to suggest it was so easy to do just a couple of simple comands! 
Anyway thanks again

---

### Post by ambrosa on 2006-09-24
I've the SAME IDENTICAL PROBLEM.

For fun I've tried yesterday to make a simple "bridge box eth+wlan" with a VIA EPIA-M mobo (CPU C3 Ezra 933 Mhz), embedded ethernet VIA Rhine-II and external usb WiFi 54g adapter (LinkSys WUSB54G v4 (RT2570 chipset)).
With Windows XP the setup works very fine and bridge works great. But I want use Linux (I need ebtables).
I use since many years RedHat products so yesterday after formatting I've installed a minimal Fedora Core 5 with ndiswrapper 1.18 to use LinkSys Windows driver.
Wlan works very very well and ethernet too.
Then I've create the bridge br0 and I've the same your problem.
PC_Bridge can ping (and telnet and ....) any hosts at the two side of bridge (eth or wlan).
But host in eth side can't reach hosts in wlan side.
Bridge seems not working.
The output of "brctl show" and "brctl showmacs br0" seems ok.
Forward is enable (/proc/sys/net ... /ip_forward = 1)
I've search in many forums but I've found no solution.
So I want to try with another different distro (Ubuntu) but I've read now your message so I supppose that is not a distro problem.

My opinion is that the wifi card driver don't support correctly promiscous mode. Perhaps....

---

### Post by dixon on 2007-08-09
I was trying to do this some time ago, but with no success. I got answers that it's impossible to bridge wireless and ethernet interfaces :\ Bridging two ethernet intefaces worked just fine, but wireless and ethernet impossible :\ I hope somebody will soon find some soulution.

---

### Post by ambrosa on 2007-08-12
> **dixon said:**
> I was trying to do this some time ago, but with no success. I got answers that it's impossible to bridge wireless and ethernet interfaces :\ Bridging two ethernet intefaces worked just fine, but wireless and ethernet impossible :\ I hope somebody will soon find some soulution.

I'm not agree.
Every linux-based adsl router do this !
I've an USR 9106 and USR 9108 : adsl router with 4 ethernet and wifi 54G
These routers are Linux based and I can do telnet in to them.
They use brctl and they setup bridge in a very simple manner and they do the bridge without any problem.

I suppose that the problem is the type of hardware of wifi.
The wifi component MUST enter correctly in promiscous mode.

---

### Post by dsmoot on 2007-11-12
I just joined the forum to get basically the same question answered but after skimming the responses maybe I need to read some more.
**What I want to do**
I want my dual NIC Kubuntu box to be my dhcp / gateway between my private network and my cable modem.  I want to be able to set up ssh, apache, openvpn, etc on the public IP and I want it also to serve as a gateway to the internet for all my other gadgets.  I **don't** care about making wireless work on this box, I've got two wired gigabit NIC's.

**Setup**
AMD64 X2 on an ABIT AN-M2 mobo, two 160GB sata drives set up as software raids.  Mobo NIC is connected to cable modem with 78.xx.xx.xx address.  Second NIC is set up as DHCP server with the static IP of 10.10.0.1.  

**what works so far**
DHCP works, I can get an IP on my clients.  I can ping the 10.10.0.1 address.

**what doesn't work**
Lots!.  I got bridge-utils installed and I can make a bridge but I can't get to the outside world.  Plus when ever I turn on the bridging I seem to screw up local browsing on my Kubuntu box.

I'm a pretty smart geek, I can google up my answers, I'm just not sure how to phrase my searches.  Can someone point me in the right direction?
David

---

### Post by paphko on 2008-04-09
> **ambrosa said:**
> I suppose that the problem is the type of hardware of wifi.
The wifi component MUST enter correctly in promiscous mode.

Same problem here, but when I do [FONT="Courier New"]ifconfig[/FONT], both adapters (wlan0 and eth0) seem to be in promisc mode. For example:
```
eth0      Link encap:Ethernet  HWaddr 00:81:BB:F8:4E:71
          UP BROADCAST RUNNING **PROMISC **MULTICAST  MTU:1500  Metric:1
          ...
```

Any other suggestions?

---

### Post by Schroedinger on 2008-06-02
brctl addbr br0
> ifconfig eth0 0.0.0.0 promisc up
ifconfig eth1 0.0.0.0 promisc up
brctl addif br0 eth0
brctl addif br0 eth1
ip link set br0 up
ip addr add 192.168.1.2/24 brd + dev br0
route add default gw 192.168.1.1 dev br0

I think you need to whack those into your RC.local. They'll set up the bridge and give you a local IP as well on your eth0. I've got that working on my ethernet bridge at the moment, so unless it's a problem with your wireless driver [haven't read the whole thread, just trying to help out people who might have a problem] configuring your bridge correctly should be as easy as doing that.

---

