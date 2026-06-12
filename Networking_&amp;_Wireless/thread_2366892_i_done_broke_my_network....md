---
title: "i done broke my network..."
date: 2017-07-23
forum: Networking &amp; Wireless
---

### Post by jamroll on 2017-07-23
I have no idea where to begin.  don't really understand why it's broken.

a little background.  i'm hosting my own site.  apache2 on a ubuntu 17.04 setup.  i need an email server setup.  send/receive emails worldwide.
i have four computers in the house.  two running ubuntu, one running windows 8.1 (i think) and the other is not being used (windows xp), not even putting power to it.
anyway.  the two ubuntu boxes are nearly exactly the same installation.  the server computer took a little longer to setup cuz i only installed "Ubuntu Server", and then installed the unity desktop ontop of that.  the other ubuntu box just got the normal Ubuntu Desktop ISO installed into it...does that make sense?

it began when i tried setting up an email server on this thing...so i can setup password resets....nothing was working right.  i went through tutorial after tutorial.  constantly running into error message after error message.  the error messages are less than vague, they're downright cryptic.  search google and get little to no help.  the tutorials hammer along and say nothing about what to do when an error occurs - they don't even tell you if an error CAN occur, let alone address what to do about it if it happens.  driving me over the edge, this is.  this can't be that tough!

so, i need, firstly, my ethernet back up.  i need this wireless to go away (i cannot remove the device from the machine, as the machine is located rather inconveniently - i'd have to go through a LOT of work to get at it...)...and i need a super easy, fully working, worldwide email system.  a step by step guide (addressing any and all possible errors, or as much as possible)  preferably not chalk full of jargon - something for a guy just starting out on linux, but has much computer experience in general - i'm well versed in the technology, just linux is baffling.

i don't know if i should host both the website and email on one machine, or two.

i have a static PUBLIC IP, and the web server has a static LOCAL IP, too.  I have a [www.****.com](www.****.com) web address pointing at the public ip, and it works when my network isn't misbehaving.  speaking of which, my ethernet was named enp3s0.  i changed it to eth0.  not sure if i missed any references to enp3s0.  i made the change because i read somewhere that it's supposed to be eth0, and if not it can confuse some install/setup scripts?  not sure.

i'm beside myself on this, and i have no idea what else I can say or post, so please don't blast me if i am way off on this, or haven't included something you may need to help me.  best to start at square one (don't ask, cuz i don't know where square one is...)

i'll post whatever you need....(but i'll blur hostnames, and public web addresses).  we can refer to the host / hostname as ns-host and the web address as [www.ns.com??](www.ns.com??)  does that work?

sincerely,
jarett

PS: it's quite late now.  i'll check back in the morning...(8 or 9 hrs from now, or about 1030 or 11am PST)

---

### Post by TheFu on 2017-07-23
Ouch.  Seems you've jumped into the deep end.  I don't think I can help - don't have the time.

Please pick 1 issue at a time and open a new thread just for that single item.  Why?  People willing to help with networking might not be comfortable with email or web servers.

Blur public stuff if you like, but please do not change internal names or LAN IPs.  That will just confuse you and us.  There are only a few places where the public names are used in either email or http servers.  BTW, 'ns' usually means "name server" (i.e. DNS) - so that could be confusing to some people.

Networking.  eth0 is what the main wired interface was named in 14.04 or earlier.  The systemd guys decided that was bad, so they made an attempt to confuse everyone except the 0.00005% who needed the more complex method.  As I read it, the goal is to ensure that on systems with 5+ ethernet ports, the network device names are unique and static between reboots.  Device names were assigned in the order they were discovered at every boot.  The more devices, the more likely those names could change.  Having eth0 and eth1, 2, 3, 4 move around is a huge hassle.  For a home user, this is fairly unimportant, but in an enterprise where **every** computer has 6 network interfaces (I've worked places like that) and there are 20K computers, having just a few percent swap their NIC device names would be a support nightmare.

So --- just to clarify a few things.
Wired network?  You should use wired.  Changing en* into eth0 is completely unimportant. If done correctly, it shouldn't matter at all.  No scripts should be working at that level unless they were written by a complete noob.

Disable the wifi in the system BIOS.
The best way to configure a server network is to modify /etc/network/interfaces file.  Please post that using code tags so things line up cleanly.
Also post the output from these commands - use code tags for each and show the exact command.
* ifconfig
* route
* ping -c 3 {ip for your router}
* sudo lshw -C network

17.04 for a server is probably a mistake.  Support for it ends in Feb (probably). 16.04 would be a better choice. It is an LTS release (even years in April are). If you don't move to 16.04, you will need to move to 17.10 when it comes out to keep support until the next LTS release in April. 

IMHO, adding a desktop onto it, especially Unity, is another mistake.

That is probably enough for now.

---

### Post by jamroll on 2017-07-23
i downloaded ubuntu server 16.04 - i know this.  not sure how it got upgraded to 17.04.  meh, i have already decided to get 17.10.  i won't change internal IP's...and ok about internal names.

oh, i know i wanna use wired - wireless is so not ok.

i'll disable wfi now...after i do that, i'll come back and post the output of them commands for ya...

---

### Post by TheFu on 2017-07-23
> **jamroll said:**
> i downloaded ubuntu server 16.04 - i know this.  not sure how it got upgraded to 17.04.  meh, i have already decided to get 17.10.  i won't change internal IP's...and ok about internal names.

oh, i know i wanna use wired - wireless is so not ok.

i'll disable wfi now...after i do that, i'll come back and post the output of them commands for ya...

It is obvious and you know it already, but don't click "yes" without reading what is says AND understanding what it means. I mostly run servers, to there aren't any annoying popups making those suggestions.  I also purge the nag service for updates.  I patch weekly, period. Don't need a reminder.

17.10 isn't LTS either.  If you want stability, go back to 16.04 unless there is a clear, specific, reason, to use something else.  New is the enemy of stable.

---

### Post by jamroll on 2017-07-23
i did "sudo -i" first, just cuz

terms i don't fully understand, i just go with what you guys say, but...maybe it matters?
netmask (subnet mask), network, and gateway.

quick rundown on network hardware.  my ISP replaced my residential modem/router with a similar device in "bridge" mode.  i had to get my own router, and connect the modem from ISP to my router.  things like $ENV{REMOTE_ADDR} says my local ip is 192.168.1.1, when i thought it should be 192.168.1.81.  192.168.1.1 is my router.  .81 is my web server - so i'm a tad confused on that

anyway, the bits yer lookin for:

gedit /etc/network/interfaces

```
source /etc/network/interfaces.d/*
auto lo


iface lo inet loopback


auto eth0
iface eth0 inet static
address 192.168.1.81
netmask 255.255.255.252
network 192.168.1.0
gateway 192.168.1.1
dns-nameservers 64.59.144.16 64.59.150.132
dns-doman night-stand.ca
dns-search night-stand.ca


pre-up /sbin/ethtool -s eth0 speed 1000 duplex full
```


at this point, i'm doing "sudo -i", so i don't gotta continually use sudo on every command
ifconfig:

```
eth0: flags=4163<UP,BROADCAST,RUNNING,MULTICAST>  mtu 1500
        inet 192.168.1.81  netmask 255.255.255.252  broadcast 192.168.1.83
        inet6 fe80::12c3:7bff:fe4d:e3e5  prefixlen 64  scopeid 0x20<link>
        ether 10:c3:7b:4d:e3:e5  txqueuelen 1000  (Ethernet)
        RX packets 2242  bytes 1256400 (1.2 MB)
        RX errors 0  dropped 0  overruns 0  frame 0
        TX packets 1879  bytes 256134 (256.1 KB)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0


lo: flags=73<UP,LOOPBACK,RUNNING>  mtu 65536
        inet 127.0.0.1  netmask 255.0.0.0
        inet6 ::1  prefixlen 128  scopeid 0x10<host>
        loop  txqueuelen 1000  (Local Loopback)
        RX packets 299  bytes 71012 (71.0 KB)
        RX errors 0  dropped 0  overruns 0  frame 0
        TX packets 299  bytes 71012 (71.0 KB)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0


virbr0: flags=4099<UP,BROADCAST,MULTICAST>  mtu 1500
        inet 192.168.122.1  netmask 255.255.255.0  broadcast 192.168.122.255
        ether 52:54:00:5f:60:c3  txqueuelen 1000  (Ethernet)
        RX packets 0  bytes 0 (0.0 B)
        RX errors 0  dropped 0  overruns 0  frame 0
        TX packets 0  bytes 0 (0.0 B)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0


wlan0: flags=4163<UP,BROADCAST,RUNNING,MULTICAST>  mtu 1500
        inet 192.168.1.81  netmask 255.255.255.0  broadcast 192.168.1.255
        inet6 fe80::6e91:c956:ecf9:cc51  prefixlen 64  scopeid 0x20<link>
        ether e8:de:27:69:3e:a2  txqueuelen 1000  (Ethernet)
        RX packets 1902  bytes 306014 (306.0 KB)
        RX errors 0  dropped 0  overruns 0  frame 0
        TX packets 223  bytes 33850 (33.8 KB)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0
```
what the devil - where'd vibr0 come from...that was there a few days ago

ping -c 3 192.168.1.1

```
PING 192.168.1.1 (192.168.1.1) 56(84) bytes of data.
64 bytes from 192.168.1.1: icmp_seq=1 ttl=64 time=1.46 ms
64 bytes from 192.168.1.1: icmp_seq=2 ttl=64 time=11.9 ms
64 bytes from 192.168.1.1: icmp_seq=3 ttl=64 time=7.76 ms


--- 192.168.1.1 ping statistics ---
3 packets transmitted, 3 received, 0% packet loss, time 2002ms
rtt min/avg/max/mdev = 1.468/7.053/11.928/4.299 ms
```


and finally, lshw -C network

  ```
*-network                 
       description: Wireless interface
       product: AR9485 Wireless Network Adapter
       vendor: Qualcomm Atheros
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: wlan0
       version: 01
       serial: e8:de:27:69:3e:a2
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list rom ethernet physical wireless
       configuration: broadcast=yes driver=ath9k driverversion=4.10.0-28-generic firmware=N/A ip=192.168.1.81 latency=0 link=yes multicast=yes wireless=IEEE 802.11
       resources: irq:16 memory:fea00000-fea7ffff memory:fea80000-fea8ffff
  *-network
       description: Ethernet interface
       product: RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: eth0
       version: 11
       serial: 10:c3:7b:4d:e3:e5
       size: 100Mbit/s
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=full firmware=rtl8168g-2_0.0.1 02/06/13 ip=192.168.1.81 latency=0 link=yes multicast=yes port=MII speed=100Mbit/s
       resources: irq:35 ioport:e000(size=256) memory:fe900000-fe900fff memory:f0000000-f0003fff
  *-network:0
       description: Ethernet interface
       physical id: 1
       logical name: virbr0
       serial: 52:54:00:5f:60:c3
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A ip=192.168.122.1 link=no multicast=yes
  *-network:1 DISABLED
       description: Ethernet interface
       physical id: 2
       logical name: virbr0-nic
       serial: 52:54:00:5f:60:c3
       size: 10Mbit/s
       capabilities: ethernet physical
       configuration: autonegotiation=off broadcast=yes driver=tun driverversion=1.6 duplex=full link=no multicast=yes port=twisted pair speed=10Mbit/s
```

oh, and i could not find a way to disable my wifi - nothing in BIOS referred to wifi, or wireless....

---

### Post by deadflowr on 2017-07-23
Here's a quick code tag primer for you:
[https://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168]("https://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168")

---

### Post by jamroll on 2017-07-23
ty for fixing that for me.  lol.  some sites want square, others want the greater than, less than signs.  go figure. 

correction - vibr0 was NOT there a few days ago


lol, that's the thing.  i didn't ask to get 17.04, had no idea i had upgraded from 16.04.  I specifically recall clicking a link that had 16.04 as the text.  i do not recall seeing a 17.04 link on the page i was on.

---

### Post by TheFu on 2017-07-23
The netmasks are different - wired ethernet and wifi have different netmasks. That is bad.  Most of the time, the netmask should be 255.255.255.0 - so unless you were specifically, in writing, told use use 255.255.255.252, that is probably the issue.

virbr0 is usually added if some sort of virtual machine or bridge-utils were loaded.  It means nothing if you don't use it.

You can disable the wifi using the **rfkill** tool. Google for how to work it - I would have to myself.

I would make the interfaces file like this:
```
source /etc/network/interfaces.d/*

auto lo
iface lo inet loopback

auto eth0
iface eth0 inet static
  address 192.168.1.81
  netmask 255.255.255.0
  gateway 192.168.1.1
  dns-nameservers 64.59.144.16 64.59.150.132
  dns-doman night-stand.ca
  dns-search night-stand.ca

  pre-up /sbin/ethtool -s eth0 speed 1000 duplex full
```

On your router, the netmask should be clear. On the LAN, most people make it 255.255.255.0 to keep the network addressing easier. You can't just make up these numbers. There is a specific pattern.  Every device on the same subnet needs to have the same netmask ... that is actually how they know they are on the same subnet.  I removed the "network" line.  It isn't needed and just tends to confuse people.  IP, Netmask and gateway are the critical parts.

Having the incorrect netmask would make the network break, BTW.

route output?  Did I miss that?

BTW, only lshw needed sudo.  Over using sudo is dangerous - especially with GUI programs like gedit.  Hopefully, you haven't already screwed the config files by doing that.

---

