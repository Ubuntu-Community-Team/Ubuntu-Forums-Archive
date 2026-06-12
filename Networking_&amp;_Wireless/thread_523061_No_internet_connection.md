---
title: "No internet connection"
date: 2007-08-11
forum: Networking &amp; Wireless
---

### Post by CraigWally on 2007-08-11
I'm pulling my hair out - and ready to throw Ubuntu (7.04) through the window and never darken it's doors again.
I'm a linux newbie so by gentle with me.

It seems to be a problem related to network devices

It lists 3 devices
loopback interface (lo)                  IP address - 127.0...
Ethernet Interface (eth0)            IP info not available
Ethernet Interface (eth0:avahi)  IP address - 169.254....

now the configure button is greyed out on the first two but is available on the avahi one - however when clicked the error message says "Interface does not exist"

Now - its exactly the same if I run the LiveCD, but I'm sure I could browse the web from the LiveCD prior to installation yesterday

HELP
Craig

---

### Post by moore.bryan on 2007-08-11
*let's start simple; what's the output of ```
lspci
```*

---

### Post by CraigWally on 2007-08-11
Sorry - I'm a complete newbie - please explain
how do I find the output of lspci?

---

### Post by moore.bryan on 2007-08-11
*no problem... open a terminal, aka cli (command-line interface), and type "lspci" (without the quotes).*

---

### Post by CraigWally on 2007-08-11
thanks

00:00.0 Host bridge: ALi Corporation M1689 K8 Northbridge [Super K8 Single Chip]
00:01.0 PCI bridge: ALi Corporation AGP8X Controller
00:02.0 PCI bridge: ALi Corporation M5249 HTT to PCI Bridge
00:03.0 ISA bridge: ALi Corporation M1563 HyperTransport South Bridge (rev 70)
00:03.1 Bridge: ALi Corporation M7101 Power Management Controller [PMU]
00:04.0 Multimedia audio controller: ALi Corporation M5455 PCI AC-Link Controller Audio Device (rev 20)
00:0e.0 IDE interface: ALi Corporation M5229 IDE (rev c7)
00:0e.1 Mass storage controller: ALi Corporation ULi 5289 SATA (rev 10)
00:0f.0 USB Controller: ALi Corporation USB 1.1 Controller (rev 03)
00:0f.1 USB Controller: ALi Corporation USB 1.1 Controller (rev 03)
00:0f.2 USB Controller: ALi Corporation USB 1.1 Controller (rev 03)
00:0f.3 USB Controller: ALi Corporation USB 2.0 Controller (rev 01)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:00.0 VGA compatible controller: nVidia Corporation NV44A [GeForce 6200] (rev a1)
02:0a.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)

---

### Post by moore.bryan on 2007-08-11
> **CraigWally said:**
> thanks*no problem... this is the line which gives us the info we need:*
> ```
02:0a.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
```*it tells us your internet controller is realtek.  now, are you attempting wireless or a hard-line connection (via ethernet cable)?*

---

### Post by CraigWally on 2007-08-11
wired ethernet cable into a router
yes the router works - other pc running XP and Vista is fine
Ubuntu is being dual-booted with Vista - Vista connects fine

---

### Post by moore.bryan on 2007-08-11
*that's a little strange... usually, ubuntu just "connects."  have you tried going online after you login to ubuntu?*

---

### Post by CraigWally on 2007-08-11
just says server not found
tried refresh etc
nothing

---

### Post by moore.bryan on 2007-08-11
*hmm... and you said vista connects fine?  what does ```
ping -c 3 www.google.com
``` give you from a terminal?*

---

### Post by CraigWally on 2007-08-11
unknown host

---

### Post by moore.bryan on 2007-08-11
*okay... under the System --> Administration --> Networking menu, what shows-up?*

---

### Post by sisco311 on 2007-08-11
it's a bug: [https://bugs.launchpad.net/ubuntu/+source/avahi/+bug/82287](https://bugs.launchpad.net/ubuntu/+source/avahi/+bug/82287)

---

### Post by CraigWally on 2007-08-11
under system admin network I have
Connections
Wired Connection - this is ticked
             Address dhcp

Modem Connection
            not configured

---

### Post by moore.bryan on 2007-08-11
> **sisco311 said:**
> it's a bug: [https://bugs.launchpad.net/ubuntu/+source/avahi/+bug/82287](https://bugs.launchpad.net/ubuntu/+source/avahi/+bug/82287)
*thanks sisco... do you know if wicd is a work-around?*
> **CraigWally said:**
> under system admin network I have
Connections
Wired Connection - this is ticked
             Address dhcp

Modem Connection
            not configured
*as you can see from sisco's post, it seems to be a known-bug... let's think on a work-around...*

---

### Post by CraigWally on 2007-08-11
Ok I've read the link from Sisco
I've edited /etc/network/interfaces
enabled roaming mode
I've edited /etc/nsswitch.conf

still no joy

---

### Post by moore.bryan on 2007-08-11
[I]yeah, i figured--at best--it would offer enlightenment, but just reading the post didn't seem to give hope.  
if you're up to it, i'd like for you to try wicd to manage your network interfaces.  go to Administration > Synaptic Package Manager.  when synaptic launches, go to Settings > Repositories > Third Party Software > Add... and type-in ```
deb http://wicd.longren.org feisty extras
```  click reload and then look for wicd; select install and we might be up and running.  post if you run into any issues...[/I]

---

### Post by sisco311 on 2007-08-11
ok. you can try this
remove the network-manager
```
sudo aptitude remove network-manager network-manager-gnome
```backup your old settings
```
sudo cp /etc/network/interfaces /etc/network/interfaces_backup
```make sure you have the correct settings
```
sudo gedit /etc/network/interfaces
```replace with this:
> auto lo
iface lo inet loopback

auto eth0
iface eth0 inet dhcp

#auto eth1
#iface eth1 inet dhcp

#auto eth2
#iface eth2 inet dhcp

#auto ath0
#iface ath0 inet dhcp

#auto wlan0
#iface wlan0 inet dhcprestart your network
```
sudo /etc/init.d/networking restart
```maybe you need to reboot

---

### Post by sisco311 on 2007-08-11
> [I]yeah, i figured--at best--it would offer enlightenment, but just reading the post didn't seem to give hope.  
if you're up to it, i'd like for you to try wicd to manage your network interfaces. go to Administration > Synaptic Package Manager. when synaptic launches, go to Settings > Repositories > Third Party Software > Add... and type-in      Code:
     deb [http://wicd.longren.org](http://wicd.longren.org) feisty extras 
  click reload and then look for wicd; select install and we might be up and running.  post if you run into any issues...[/I]

without internet?

---

### Post by moore.bryan on 2007-08-11
> **sisco311 said:**
> without internet?
[i]doh, i'm an idiot... :-)

go with sisco's suggestion...[/i]

---

### Post by CraigWally on 2007-08-11
still no joy

does this help

~$ sudo /etc/init.d/networking restart
 * Reconfiguring network interfaces...                                          RTNETLINK answers: No such process
There is already a pid file /var/run/dhclient.eth0.pid with pid 5184
killed old client process, removed PID file
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006
 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)
Listening on LPF/eth0/00:0f:ea:2d:e7:66
Sending on   LPF/eth0/00:0f:ea:2d:e7:66
Sending on   Socket/fallback
There is already a pid file /var/run/dhclient.eth0.pid with pid 134993416
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 
Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)
Listening on LPF/eth0/00:0f:ea:2d:e7:66
Sending on   LPF/eth0/00:0f:ea:2d:e7:66
Sending on   Socket/fallback
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 8
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 11
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 12
No DHCPOFFERS received.
No working leases in persistent database - sleeping.

---

### Post by sisco311 on 2007-08-11
go to the System-->Administration-->Network DNS tab and add your routers ip address to DNS Servers

---

### Post by CraigWally on 2007-08-11
still no joy
it is now taking a while before deciding it won't connect
it does seem to be thinking about it though

---

### Post by moore.bryan on 2007-08-11
*could it be a router issue?*

---

### Post by kevdog on 2007-08-11
Could you post :
lshw -C network

This will tell us at the most basic level if a driver is being associated with your card.  After rebooting, type dmesg | more at command line and look for any error message discussing your network card.  I dont know whats wrong with your connection, I need more information right now!

---

### Post by sisco311 on 2007-08-11
what's the output of ```
ifconfig
```

---

### Post by CraigWally on 2007-08-11
@kevdog

lshw -C network
  *-network               
       description: Ethernet interface
       product: RTL-8139/8139C/8139C+
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: a
       bus info: pci@02:0a.0
       logical name: eth0
       version: 10
       serial: 00:0f:ea:2d:e7:66
       size: 100MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=8139too driverversion=0.9.28 duplex=full latency=64 link=yes maxlatency=64 mingnt=32 multicast=yes port=MII speed=100MB/s
       resources: ioport:c000-c0ff iomemory:fb000000-fb0000ff irq:16

---

### Post by CraigWally on 2007-08-11
@sisco

ifconfig
eth0      Link encap:Ethernet  HWaddr 00:0F:EA:2D:E7:66  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:16 Base address:0x6000 

eth0:avah Link encap:Ethernet  HWaddr 00:0F:EA:2D:E7:66  
          inet addr:169.254.8.5  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          Interrupt:16 Base address:0x6000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:312 errors:0 dropped:0 overruns:0 frame:0
          TX packets:312 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:29106 (28.4 KiB)  TX bytes:29106 (28.4 KiB)



I'm off to bed now
see you all tomorrow
and thanks everybody for your time and help so far

---

### Post by drbombay on 2007-08-12
Setting a static IP address seemed to solve the problem for me.

Good luck.

---

### Post by CraigWally on 2007-08-12
> **drbombay said:**
> Setting a static IP address seemed to solve the problem for me.

Good luck.

how do I do that?
and what IP address do I use?

---

### Post by drbombay on 2007-08-13
System > Administration > Network

Click on the wired connection properties and select static IP address. You can boot into Vista and check the addresses that are given to you by the router.

---

### Post by kevdog on 2007-08-13
Can you post dmesg.  Might take two posts!

---

### Post by master_kernel on 2007-08-13
This is very odd. I have the same exact problem with my internet. It works through XP, but not through Ubuntu. I am also running an Athlon 64 machine like Craig. Could it be an x64 issue?
I have done some googling and found many bugs that relate to the avahi-daemon and nss-mdsn or something, but none of those solutions worked for me. I removed network-monitor-gnome as suggested earlier but no cookie. I cannot update the MK thread if Ubuntu does not connect! When I first received my computer a few days ago, the networking worked fine on the Live CD. A few days ago, when I installed Feisty, the networking failed. I figured it was time to upgrade to Gutsy anyway. I installed Gutsy and voila! no internet. Any suggestions?

---

### Post by CraigWally on 2007-08-13
> **kevdog said:**
> Can you post dmesg.  Might take two posts!

I cant do that its 2,300 lines!

---

### Post by master_kernel on 2007-08-13
I found a solution that worked for me! One minute for me to post it.

---

### Post by master_kernel on 2007-08-13
One of the threads I read here on Ubuntu Forums said something about Windows putting the NIC to sleep when it shuts down. Someone suggested unplugging my computer for about 10 minutes to reset it. I booted into Ubuntu and amazingly, my internet connection worked! I am now searching for a way to stop Windows from putting my NIC to sleep. I'll post instructions here if I find a way. Hope this works for you!

~ Master Kernel

---

### Post by upthelum on 2007-08-13
Rule out the amd64  as a problem i use the same and have had no networking problems after numerous installs, Ubuntu has always picked up the wired nic for me but the only problems i ever had were related to wireless cards, you dont use wireless or have a wireless card in the machine do you? If so i would take it out and reboot.

---

### Post by s00pcan on 2007-08-13
I'm having problems with my internet connection on ubuntu also. I got a laptop with vista then installed ubuntu (dual boot). I started getting really stupid errors with mysql and hibernating wasn't working, so I reinstalled ubuntu. Now my internet connection doesn't work at home, though it has been a problem anytime I try linux here. It works fine at work, it works fine anywhere in windows. The farthest ubuntu can get on my home network is my router, and it goes no further. I can log into the router from ubuntu and do stuff, so I don't think it's a driver issue.

---

### Post by CraigWally on 2007-08-14
> **master_kernel said:**
> One of the threads I read here on Ubuntu Forums said something about Windows putting the NIC to sleep when it shuts down. Someone suggested unplugging my computer for about 10 minutes to reset it. I booted into Ubuntu and amazingly, my internet connection worked! I am now searching for a way to stop Windows from putting my NIC to sleep. I'll post instructions here if I find a way. Hope this works for you!

~ Master Kernel

HOORAY :)
Problem solved
As soon as I read that response I just knew that it was going to work - I remember the same solution to a windows pc a few years ago.

I declare master_kernel to be a true master

thanks to everybody else aswell for your time and trouble.

Wally

---

