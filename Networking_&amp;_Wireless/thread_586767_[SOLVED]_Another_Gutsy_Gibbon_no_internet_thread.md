---
title: "[SOLVED] Another Gutsy Gibbon no internet thread"
date: 2007-10-22
forum: Networking &amp; Wireless
---

### Post by PickPocket8686 on 2007-10-22
Hi,
I’ve just tried installing Ubuntu 64 bit (7.10) for the first time, also my first experience with Linux.  But I have one small issue…  No internet access.  It works fine in Windows but I can’t get it to work at all in Ubuntu.
From doing some reading on this forum this seems to be a repetitive problem with Gutsy Gibbon.  I also read that cold booting the system to unload the Windows drivers might help, but that’s been a no go for me so far.
Also for whatever reason the DHCP on my router stopped working a little over a month ago.  But as long as a use a static IP address I’m fine...  and yes I did enter a static IP in the network panel.

I’m not really sure what information you guys will need, but just ask and I’ll provide.
I’m on Broadband, with a Netgear Mr814v2 router, using a wired connection.

Computer Specs
AMD Opteron 165
DFI nForce4 Ultra-D
Creative Labs Sound Blaster Audigy SE
2x1GB G.Skill
XFX 8600GTS 
Western Digital Raptor 150GB Serial ATA150
Seagate Barracuda 7200.8 300GB IDE ATA100
Pioneer DVR-112L
SeaSonic S12 600W

If anyone can help I’d truly appreciate it.
Thanks,
Austin

---

### Post by KCPokes on 2007-10-22
There is that line between "internet" working and just having a working network, meaning your internal network is actually working but you cannot get outside to the actual internet.  The first step in getting some help is to provide some details and maybe someone can help determine where your issue lies.  Can you provide a "ifconfig -a" as well as a "netstat -rn".  That will provide your interface specifics as well as your routing table.  Additionally, do you have other machines on your network that you can attempt to connect?  I'd be surprised if you can connect to other private machines but not access the internet, but do need to rule out all scenarios.

---

### Post by monkeymoo on 2007-10-22
Sounds like my problem. [http://ubuntuforums.org/showthread.php?t=586578](http://ubuntuforums.org/showthread.php?t=586578) (number 2)
Solved by using OpenDNS, although there must be a better way if anyone knows one.

---

### Post by PickPocket8686 on 2007-10-22
> **KCPokes said:**
> There is that line between "internet" working and just having a working network, meaning your internal network is actually working but you cannot get outside to the actual internet.  The first step in getting some help is to provide some details and maybe someone can help determine where your issue lies.  Can you provide a "ifconfig -a" as well as a "netstat -rn".  That will provide your interface specifics as well as your routing table.  Additionally, do you have other machines on your network that you can attempt to connect?  I'd be surprised if you can connect to other private machines but not access the internet, but do need to rule out all scenarios.

```

"ifconfig -a"
eth1     Link encap:Ethernet  HWaddr 00:01:29:D3:85:F8
         UP BROADCAST MULTYCAST  MTU:1500 Metric:1
         RX packets:0 errors:0 dropped:0 overruns:0 frame:0
         TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
         collisions:0 txqueuelen:1000
         RX bytes:0 (0.0 b)   TX bytes:0 (0.0 b)
         Interrupt:18

eth2     Link encap:Ethernet  HWaddr 00:00:6C:06:55:4F
         UP BROADCAST RUNNING MULTYCAST  MTU:1500 Metric:1
         RX packets:165 errors:0 dropped:0 overruns:0 frame:0
         TX packets:150 errors:0 dropped:0 overruns:0 carrier:0
         collisions:0 txqueuelen:1000
         RX bytes:88257 (86.1 KB)   TX bytes:50316 (49.1 KB)
         Interrupt:21 Base address:0x6000

lo       Link encap:Local Loopback
         inet addr:127.0.0.1   Mask:255.0.0.0
         inet6 addr:  ::1/128 Scope:Host
         UP LOOPBACK RUNNING  MTU:16436 Metric:1
         RX packets:0 errors:0 dropped:0 overruns:0 frame:0
         TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
         collisions:0 txqueuelen:0
         RX bytes:0 (0.0 b)   TX bytes:0 (0.0 b)

```

```

"netstat -rn"
Destination     Gateway     Genmask     Flags   MSS Window  irtt Iface

```

I do have other computers on the network and when I click on "Places > Network" it shows a "Windows Network" but when I click on that there's no computers on it.

> **monkeymoo said:**
> Sounds like my problem. [http://ubuntuforums.org/showthread.php?t=586578](http://ubuntuforums.org/showthread.php?t=586578) (number 2)
Solved by using OpenDNS, although there must be a better way if anyone knows one.

I just tried OpenDNS, it doesn't make any difference for me.
BTW, I get that same black screen when I startup Ubuntu 
(in 64 bit but not 32), it still loads up fine (I just can't see anything when it's loading up or shutting down).

---

### Post by monkeymoo on 2007-10-22
> I just tried OpenDNS, it doesn't make any difference for me.
BTW, I get that same black screen when I startup Ubuntu 
(in 64 bit but not 32), it still loads up fine (I just can't see anything when it's loading up or shutting down).

Sorry that OpenDNS didn't work. 
I think you may have to do "sudo /etc/init.d/networking restart" to get it going to begin with. But maybe it isn't that. 

Have you tried disabling ipv6?
Do a “sudo gedit /etc/modprobe.d/aliases”
from a terminal window.
Add the following lines:
> alias net-pf-10 ipv6 off
alias net-pf-10 off
alias ipv6 off
and comment out
> #alias net-pf-10 ipv6
See [http://faler.wordpress.com/2007/10/14/ubuntu-linux-710-gutsy-gibbon-on-a-sony-vaio-sz4-xwn/](http://faler.wordpress.com/2007/10/14/ubuntu-linux-710-gutsy-gibbon-on-a-sony-vaio-sz4-xwn/)
for the details. 

On the black screen issue, it lasts a very long time, I don't think it is doing anything. I get the black screen briefly when using the kernel that does work. I think it's different.

---

### Post by PickPocket8686 on 2007-10-22
> **monkeymoo said:**
> Sorry that OpenDNS didn't work. 
I think you may have to do "sudo /etc/init.d/networking restart" to get it going to begin with. But maybe it isn't that. 

Have you tried disabling ipv6?
Do a “sudo gedit /etc/modprobe.d/aliases”
from a terminal window.
Add the following lines:

and comment out

See [http://faler.wordpress.com/2007/10/14/ubuntu-linux-710-gutsy-gibbon-on-a-sony-vaio-sz4-xwn/](http://faler.wordpress.com/2007/10/14/ubuntu-linux-710-gutsy-gibbon-on-a-sony-vaio-sz4-xwn/)
for the details. 

On the black screen issue, it lasts a very long time, I don't think it is doing anything. I get the black screen briefly when using the kernel that does work. I think it's different.

I just tried all that but I still can't connect.
Something interesting did happen though.  Now when I click on the network icon it shows the "Wired Network" tab with a dot in it.  Before it was grayed out and empty.

Also, when I did "sudo /etc/init.d/networking restart" it said.

```
 * Reconfiguring network interfaces...
eth0: ERROR while getting interface flags: No such device
SIOCSIFADDR: No such device
eth0: ERROR while getting interface flags: No such device
SIOCSIFNETMASK: No such device
eth0: ERROR while getting interface flags: No such device
Failed to bring up eth0.
```

Anyone have anymore ideas?
Austin

---

### Post by monkeymoo on 2007-10-22
Could you post the content of your "/etc/network/interfaces" file? That might help. 
Also the output of "lshw -C network" may shed some light.

---

### Post by PickPocket8686 on 2007-10-22
> **monkeymoo said:**
> Could you post the content of your "/etc/network/interfaces" file? That might help.

```
/etc/network/interfaces
auto lo
iface lo inet loopback


iface eth0 inet static
address 192.168.0.99
netmask 255.255.255.0
gateway 192.168.0.1

auto eth0


iface eth1 inet static
address 192.168.0.99
netmask 255.255.255.0
gateway 192.168.0.1

auto eth1
```

> **monkeymoo said:**
> Also the output of "lshw -C network" may shed some light.

```
sudo lshw -C network 
  *-network               
       description: Ethernet interface 
       product: 88E8001 Gigabit Ethernet Controller 
       vendor: Marvell Technology Group Ltd. 
       physical id: a 
       bus info: pci@0000:01:0a.0 
       logical name: eth1 
       version: 13 
       serial: 00:01:29:d3:85:f8 
       capacity: 1GB/s 
       width: 32 bits 
       clock: 66MHz 
       capabilities: pm vpd bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation 
       configuration: autonegotiation=on broadcast=yes driver=skge driverversion=1.11 firmware=N/A latency=32 link=no maxlatency=31 mingnt=23 module=skge multicast=yes port=twisted pairS 
```

---

### Post by monkeymoo on 2007-10-22
I'm no expert so hopefully somebody else will have a better idea from what you've posted but I'd try commenting out the references to eth0 in the /etc/network/interfaces as it's eth1 that is the "logical name" of your ethernet device (from sudo lshw -C network), and "sudo /etc/init.d/networking restart" is complaining there is no eth0 device.

---

### Post by PickPocket8686 on 2007-10-23
Turns out if I switch Ethernet plugs on the motherboard and turn off ipv6 I get Internet again.

Thanks everyone.
Austin

---

