---
title: "Feisty Networking (DNS Issues) :("
date: 2007-04-19
forum: Networking &amp; Wireless
---

### Post by obz on 2007-04-19
Hello. 

I'm having issues getting anywhere on the Internet. I'm using the new Ubuntu 7.04 Feisty Fawn on a home network behind a Cable Modem Router. I have other computers using the same Router (Windows XP) and they have no issues at all. 

I had the previous version of Ubuntu working without any issues. So whatever is the cause of this is likely due to a recent update. 

I've read several posts related to this problem and I have disabled IPV6. I also added the dyndns DNS server ips to my DNS server list.  I can't ping any computer on the LAN. Attempts to do so result in : Destination Host Unreachable 100% packet loss.

I've tried both static and dhcp ip addresses neither worked.

Any suggestions or direction would be great. 

:(

---

### Post by keith11 on 2007-04-20
I am not sure if this would help but I was going through many threads regarding an issue with my wireless in Feisty and I came across the following through a solved bug at launchpad:

1. You may want to change the channel number which is automatically looked for when you connect through a network manager. You can find out the channel number of your wireless connection by typing "sudo iwlist scan". After you know the channel number and if it is not 6 (6 is the channel number the network manager will usually look for), then try changing the channel number by typing "sudo iwconfig eth1 freq channel number". Replace the term "channel number" by your channel number without any quotes. This might tell your network manager to find that particular channel instead of the default channel number.

2. You can use wicd (I am going to try that myself) from [http://adam.blackhole.cx/wicd/wb/](http://adam.blackhole.cx/wicd/wb/)  and you can also add it to the tray by following the instructions provided in the FAQ section of the same website.

Hope this helps. Good Luck!

Keith.

---

### Post by obz on 2007-04-20
Hmm. I connect directly to the router. I'm not wireless. (but I'll remember this in case one day I do go Feisty Wireless. :) )

---

### Post by j0sh0 on 2007-04-20
go to a terminal and type:

sudo ifconfig

put in your password and let us know what interfaces it lists there. there should be "lo", which is the loopback interface, and presuming you're connecting thru ethernet, "eth0" or something similar. get back to us and we can start from there.

---

### Post by nautilus on 2007-04-20
'ifconfig' does not require superuser priveleges to view interfaces.

---

### Post by obz on 2007-04-20
eth0   Link encap:Ethernet  HWaddr 00:48:54:1E:4E:16
          inet addr:192.168.200.2  Bcast:192.168.255.255  Mask:255.255.0.0
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:19 Base address:0x8000

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:1202 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1202 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:115302 (112.5 KiB)  TX bytes:115302 (112.5 KiB)


Also...
updated the Subnet Mask (which matches other computers on the LAN with functional 'Net) : 
255.255.255.0

DNS:
208.67.222.222 <- dyndns public DNS server IP
208.67.220.220 <-dyndns public DNS server IP
192.168.200.1 <-router

---

### Post by dominicd on 2007-04-20
> **obz said:**
> Hello. 

I'm having issues getting anywhere on the Internet. I'm using the new Ubuntu 7.04 Feisty Fawn on a home network behind a Cable Modem Router. I have other computers using the same Router (Windows XP) and they have no issues at all. 

I had the previous version of Ubuntu working without any issues. So whatever is the cause of this is likely due to a recent update. 

I've read several posts related to this problem and I have disabled IPV6. I also added the dyndns DNS server ips to my DNS server list.  I can't ping any computer on the LAN. Attempts to do so result in : Destination Host Unreachable 100% packet loss.

I've tried both static and dhcp ip addresses neither worked.

Any suggestions or direction would be great. 

:(


What do you mean by adding the dyndns DNS server ips? I'm also having some issues and maybe that will sort things out.

---

### Post by obz on 2007-04-20
Well normally I would just set the DNS to my router (it is still one of the ip addresses listed 192.168.200.1) and everything is usually fine... I read in another post that this *may* cause a problem and to try using dyndyns' public DNS servers (which are the other two DNS ips that I have listed)...

I've tried combos of all (just router IP, just dyndns DNS ips) of them with no results.

I think a more fundamental networking setting has been altered...I've used linux with this router with the same settings for well over a year without issues until the current Ubuntu upgrade.

I'm using the following in my DNS settings:

208.67.222.222 <- dyndns public DNS server IP
208.67.220.220 <-dyndns public DNS server IP
192.168.200.1 <-router

---

### Post by dominicd on 2007-04-20
> **obz said:**
> Well normally I would just set the DNS to my router (it is still one of the ip addresses listed 192.168.200.1) and everything is usually fine... I read in another post that this *may* cause a problem and to try using dyndyns' public DNS servers (which are the other two DNS ips that I have listed)...

I've tried combos of all (just router IP, just dyndns DNS ips) of them with no results.

I think a more fundamental networking setting has been altered...I've used linux with this router with the same settings for well over a year without issues until the current Ubuntu upgrade.

I'm using the following in my DNS settings:

208.67.222.222 <- dyndns public DNS server IP
208.67.220.220 <-dyndns public DNS server IP
192.168.200.1 <-router

THANK YOU!! That fixed my issues! I knew it was something with the DNS settings but just couldn't work it out, I'm still on Edgy btw. I'm really glad it's sorted out now, you made my day friend.

I wish I could help you with your problem as well but I'm afraid the only support I am able to give you at this point is bumping your question with this post. Good luck!

---

### Post by obz on 2007-04-20
Awesome! Glad it helped someone! :) 

Hopefully someone will great wisdom can help me. (yes I'm resorting to blatant flattery... ;)

---

### Post by Detonate on 2007-04-20
Are you sure you have the correct DNS for your router?  don't know what router you have, but most of the ones I have dealt with default to a DNS of 192.168.0.1 or 192.168.0.2.  

Can you ping the other computers on the network using their IP address?

---

### Post by dbott67 on 2007-04-20
Can you post the output of:
```
dbott@feisty:~$ route -n
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.1.0     0.0.0.0         255.255.255.0   U     0      0        0 eth0
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 eth0
0.0.0.0         192.168.1.1     0.0.0.0         UG    0      0        0 eth0

```and
```
dbott@feisty:~$ ifconfig -a
eth0      Link encap:Ethernet  HWaddr 00:50:BA:C0:A7:55
          inet addr:192.168.1.106  Bcast:192.168.1.255  Mask:255.255.255.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1857684 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1414950 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:1786176347 (1.6 GiB)  TX bytes:828098517 (789.7 MiB)
          Interrupt:17 Base address:0x4000

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:42241 errors:0 dropped:0 overruns:0 frame:0
          TX packets:42241 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:56162939 (53.5 MiB)  TX bytes:56162939 (53.5 MiB)


```
and
```

dbott@feisty:~$ cat /etc/network/interfaces
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto eth0
iface eth0 inet dhcp

```
Thanks,
Dave

---

### Post by dbott67 on 2007-04-20
Hi Obz,

I also see that you (like me) have resorted to cheering for the Sabres.  Of course, it pains me to do so as a Leaf fan, but I just can't root for the Sens.

Let's hope the Sabres can knock out the Islanders tonight (and that you can get online, too).

-Dave

---

### Post by obz on 2007-04-20
> **dbott67 said:**
> Hi Obz,

I also see that you (like me) have resorted to cheering for the Sabres.  Of course, it pains me to do so as a Leaf fan, but I just can't root for the Sens.

Let's hope the Sabres can knock out the Islanders tonight (and that you can get online, too).

-Dave

whooooa there Cowboy. I'm NOT a Leafs fan. I'm a full time Sabres fan. 

Should be a good game tonight! GO SABRES...

---

### Post by obz on 2007-04-20
> **Detonate said:**
> Are you sure you have the correct DNS for your router?  don't know what router you have, but most of the ones I have dealt with default to a DNS of 192.168.0.1 or 192.168.0.2.  

Can you ping the other computers on the network using their IP address?

This is true - i had to set it to 192.168.200 because it was conflicting with a VPN my gf uses for work. 

I'll post the information requests when I get home this evening.

Thanks!

---

### Post by dbott67 on 2007-04-20
> **obz said:**
> whooooa there Cowboy. I'm NOT a Leafs fan. I'm a full time Sabres fan. 

Should be a good game tonight! GO SABRES...

Oops... sorry.  I'm still a Leaf fan, but you gotta love the way those Sabres play.  Glad to see Tim Connolly back in the line-up --- that guy is a human highlight reel (and he'd look real good in a Leaf jersey... and Miller, Briere, Drury, Afinogenov, Numminem, Campbell.... uhhh, you wanna trade for Razor? :)

But nonetheless: GO SABRES (all the way in the east)... and Canucks, Flames or Sharks (in that order) in the West!

---

### Post by obz on 2007-04-20
Here are my numbers....

route -n:
--------------------------
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.200.0   0.0.0.0         255.255.255.0   U     0      0        0 eth0
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 eth0
0.0.0.0         192.168.200.1   0.0.0.0         UG    0      0        0 eth0

ifconfig -a:
-------------------------
eth0      Link encap:Ethernet  HWaddr 00:48:54:1E:4E:16
          inet addr:192.168.200.2  Bcast:192.168.200.255  Mask:255.255.255.0
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:19 Base address:0x8000

eth2      Link encap:Ethernet  HWaddr 00:0C:6E:A8:4C:27
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:614 errors:0 dropped:0 overruns:0 frame:0
          TX packets:336 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:37633 (36.7 KiB)  TX bytes:34238 (33.4 KiB)
          Interrupt:16 Base address:0x6000

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:1238 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1238 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:118398 (115.6 KiB)  TX bytes:118398 (115.6 KiB)


dag@warwick:~$ cat /etc/network/interfaces
----------------------------------------------------------------
auto lo
iface lo inet loopback
address 127.0.0.1
netmask 255.0.0.0

auto eth0
iface eth0 inet static
address 192.168.200.2
netmask 255.255.255.0
gateway 192.168.200.1

auto eth1
iface eth1 inet dhcp

auto eth2
iface eth2 inet static
address 192.168.200.212
netmask 255.255.0.0
gateway 192.168.200.1

auto ath0
iface ath0 inet dhcp

auto wlan0
iface wlan0 inet dhcp

---

### Post by obz on 2007-04-20
> **dbott67 said:**
> Oops... sorry.  I'm still a Leaf fan, but you gotta love the way those Sabres play.  Glad to see Tim Connolly back in the line-up --- that guy is a human highlight reel (and he'd look real good in a Leaf jersey... and Miller, Briere, Drury, Afinogenov, Numminem, Campbell.... uhhh, you wanna trade for Razor? :)

But nonetheless: GO SABRES (all the way in the east)... and Canucks, Flames or Sharks (in that order) in the West!

Ya great to see Timmah back even if he isn't 100%. He knows how to dangle! Heh. I'm sure the Leafs will pick of some talent in the offseason. If only they would drop Sundin and McCabe they could really improve the team with free agents. Big win tonight! Advance to round 2! 

Miller isn't that much better than Raycroft... he lets in his share of garbage... ;)

---

### Post by dbott67 on 2007-04-20
Yes, big win tonight... although they had my heart racing when the Isles made it 4-3. Unbelievable stop by Miller at the end (remind you of the Dominator?)  Hopefully they can keep it up.

Anyhow, you mention that you can't ping anything on the LAN.

What do get when you ping 127.0.0.1 (loopback), 192.168.200.2 (eth0) and 192.168.200.1 (gateway)?

Also, what kind of network hardware & driver (there's been some issues with RealTek cards in various posts):
```
dbott@feisty:~$ sudo lshw -C network
Password:
  *-network               
       description: Ethernet interface
       product: [COLOR=Red]**RTL8139 Ethernet**[/COLOR]
       vendor: D-Link System Inc
       physical id: b
       bus info: pci@02:0b.0
       logical name: eth0
       version: 10
       serial: 00:50:ba:c0:a7:55
       size: 100MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes [COLOR=Red]driver=8139too driverversion=0.9.28[/COLOR] duplex=full ip=192.168.1.106 latency=32 link=yes maxlatency=64 mingnt=32 multicast=yes port=MII speed=100MB/s
       resources: ioport:b000-b0ff iomemory:be800000-be8000ff irq:17

```

You might also want to try loading an older kernel in grub.  Press 'esc' right after post to view the grub menu list and try picking one of the older kernels.

-Dave

---

### Post by bronyraur777 on 2007-04-20
Well hopefully someone has an answer, I'm in the same boat and at a loss as what to do...

---

### Post by obz on 2007-04-20
More info...it is the exact Realtec listed.... I'll try the ESC after POST....

dag@warwick:~$ ping 127.0.0.1
PING 127.0.0.1 (127.0.0.1) 56(84) bytes of data.
64 bytes from 127.0.0.1: icmp_seq=1 ttl=64 time=0.034 ms
64 bytes from 127.0.0.1: icmp_seq=2 ttl=64 time=0.027 ms
64 bytes from 127.0.0.1: icmp_seq=3 ttl=64 time=0.027 ms
64 bytes from 127.0.0.1: icmp_seq=4 ttl=64 time=0.028 ms
^X64 bytes from 127.0.0.1: icmp_seq=5 ttl=64 time=0.026 ms
64 bytes from 127.0.0.1: icmp_seq=6 ttl=64 time=0.026 ms
64 bytes from 127.0.0.1: icmp_seq=7 ttl=64 time=0.026 ms

dag@warwick:~$ ping 192.168.200.2
PING 192.168.200.2 (192.168.200.2) 56(84) bytes of data.
64 bytes from 192.168.200.2: icmp_seq=1 ttl=64 time=0.027 ms
64 bytes from 192.168.200.2: icmp_seq=2 ttl=64 time=0.024 ms
64 bytes from 192.168.200.2: icmp_seq=3 ttl=64 time=0.027 ms
64 bytes from 192.168.200.2: icmp_seq=4 ttl=64 time=0.027 ms
64 bytes from 192.168.200.2: icmp_seq=5 ttl=64 time=0.027 ms

dag@warwick:~$ ping 192.168.200.1
PING 192.168.200.1 (192.168.200.1) 56(84) bytes of data.
From 192.168.200.2 icmp_seq=2 Destination Host Unreachable
From 192.168.200.2 icmp_seq=3 Destination Host Unreachable
From 192.168.200.2 icmp_seq=4 Destination Host Unreachable
From 192.168.200.2 icmp_seq=6 Destination Host Unreachable
From 192.168.200.2 icmp_seq=7 Destination Host Unreachable
From 192.168.200.2 icmp_seq=8 Destination Host Unreachable

dag@warwick:~$ sudo lshw -C network
Password:
  *-network DISABLED
       description: Ethernet interface
       product: nForce2 Ethernet Controller
       vendor: nVidia Corporation
       physical id: 4
       bus info: pci@00:04.0
       logical name: eth2
       version: a1
       serial: 00:0c:6e:a8:4c:27
       size: 100MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 66MHz
       capabilities: bus_master cap_list ethernet physical mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=forcedeth driverversion=0.59 duplex=full latency=0 link=yes maxlatency=20 mingnt=1 multicast=yes port=MII speed=100MB/s
       resources: iomemory:e1000000-e1000fff ioport:e000-e007 irq:16
 
 *-network
       description: Ethernet interface
       product: RTL-8139/8139C/8139C+
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 9
       bus info: pci@01:09.0
       logical name: eth0
       version: 10
       serial: 00:48:54:1e:4e:16
       size: 10MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=8139too driverversion=0.9.28 duplex=half ip=192.168.200.2 latency=32 link=no maxlatency=64 mingnt=32 multicast=yes port=MII speed=10MB/s
       resources: ioport:d000-d0ff iomemory:e0000000-e00000ff irq:19

---

### Post by obz on 2007-04-20
> **dbott67 said:**
> 
You might also want to try loading an older kernel in grub.  Press 'esc' right after post to view the grub menu list and try picking one of the older kernels.
-Dave

Since it is a fresh install there is only one Kernel version listed... :( (Nice tip to hold down ESC though... didn't know I could do that...)

---

### Post by dbott67 on 2007-04-21
You (and quite a few others) seem to be suffering with the same card.  I did find in one thread that someone had success by disabling acpi (acpi=off):

**1. You can try disabling some options at boot time by editing grub:**
[https://help.ubuntu.com/community/DebuggingIRQProblems](https://help.ubuntu.com/community/DebuggingIRQProblems)

> **How do I know there is a problem?**

The following are some symptoms which may indicate an IRQ-related problem:

    * [COLOR=Blue]Hardware devices being detected, but not functional[/COLOR] (sound, [COLOR=Blue]network[/COLOR], etc.)
    * Problems using two hardware devices at the same time, or only when devices are connected at the same time.
    * System hangs (lockup).

**What do I do?**

If you think you may be experiencing such a problem, [COLOR=Blue]try these steps in order[/COLOR]:

    * Boot the system with the [COLOR=Red]acpi=off[/COLOR] boot parameter [COLOR=Blue]*<--- this was originally the last step to try, but someone posted success using it.*[/COLOR]
* Boot the system with the [COLOR=Red]noapic[/COLOR] boot parameter
    * Boot the system with the [COLOR=Red]pci=routeirq[/COLOR]
    * Boot the system with the [COLOR=Red]pci=noacpi[/COLOR] boot parameter


To add these options to the boot command line, use the [COLOR=Red]edit[/COLOR] option in the [COLOR=Red]grub boot menu[/COLOR]. Full instructions on how to use grub:
[https://help.ubuntu.com/community/GrubHowto](https://help.ubuntu.com/community/GrubHowto)


I hope this helps, otherwise you may have to buy a cheap NIC.

-Dave

---

### Post by obz on 2007-04-21
hmm. of all the things... I'll try another NIC. I'll let you know. :)

---

### Post by obz on 2007-04-21
> **obz said:**
> hmm. of all the things... I'll try another NIC. I'll let you know. :)

Tried a new D-Link DGE-530T NIC... and it is the same. :( :( :confused: :confused: :mad: 

The lshw -C network now shows: driver=skge driverversion=1.9...

This is really starting to suck.

---

### Post by obz on 2007-04-21
Any further ideas? I tried the IRC #ubuntu but no one even acknowledged me. So that is pretty pointless as a help resource. :(

---

### Post by TakisX on 2007-04-21
The same here .I have an asus p5b mobo and ubuntu does not detect the ethernet card , so no internet. Older versions worked fine .Something they meshed with 7.04 .And here no help at all

---

### Post by dbott67 on 2007-04-22
Hi Obz,

The other thread that I'm helping in with the same card had some success:
[http://ubuntuforums.org/showthread.php?p=2504407#post2504407](http://ubuntuforums.org/showthread.php?p=2504407#post2504407)
[quote=Bob3 (from Ajax, ON)]So I tried removing Firestarter (firewall app) and*[COLOR=Blue] while I was at it I took out the [COLOR=Red]noacpi [/COLOR]kernel parameter[/COLOR]*. And suddenly there was joy - a wonderful internet connection.
So it must have been the firewall, right. Well I put the noacpi parm back in and rebooted.
And you guessed it not internet. So [COLOR=Red]*the issue is the noacpi parm*[/COLOR]...[/quote]

Anyhow, he's going to try a bunch of the options to see what else he can find out.  You may want to subscribe to that thread.

-Dave

---

### Post by obz on 2007-04-22
> **dbott67 said:**
> Hi Obz,

The other thread that I'm helping in with the same card had some success:
[http://ubuntuforums.org/showthread.php?p=2504407#post2504407](http://ubuntuforums.org/showthread.php?p=2504407#post2504407)


Anyhow, he's going to try a bunch of the options to see what else he can find out.  You may want to subscribe to that thread.

-Dave

I tried to locate the firewall in add/remove programs and it doesn't appear to be there. Still searching for a solution. Thanks for your help dbott67.

---

### Post by sdide on 2007-04-22
Hey, 

can you open 2 terminals and do first in number 1 (root user):

~# tcpdump -nli eth0

end then in the second terminal do (root or not)
 
~$ ping 192.168.200.1

and post output from tcpdump? (just a few seconds after the ping has started, will do)

---

### Post by obz on 2007-04-22
> **sdide said:**
> Hey, 

can you open 2 terminals and do first in number 1 (root user):

~# tcpdump -nli eth0

end then in the second terminal do (root or not)
 
~$ ping 192.168.200.1

and post output from tcpdump? (just a few seconds after the ping has started, will do)

Sure. Hope this helps. Thanks for your assistance.

root@warwick:/boot/grub# tcpdump -nli eth1
tcpdump: verbose output suppressed, use -v or -vv for full protocol decode
listening on eth1, link-type EN10MB (Ethernet), capture size 96 bytes
20:18:52.813212 arp who-has 192.168.200.45 (ff:ff:ff:ff:ff:ff) tell 192.168.200.1
20:18:53.395326 IP 192.168.200.1.520 > 255.255.255.255.520: RIPv1, Response, length: 24
20:19:08.541719 IP 192.168.200.34 > 192.168.200.1: ICMP echo request, id 32537, seq 1, length 64
20:19:09.542878 IP 192.168.200.34 > 192.168.200.1: ICMP echo request, id 32537, seq 2, length 64
20:19:10.542932 IP 192.168.200.34 > 192.168.200.1: ICMP echo request, id 32537, seq 3, length 64
20:19:11.542984 IP 192.168.200.34 > 192.168.200.1: ICMP echo request, id 32537, seq 4, length 64
20:19:12.543036 IP 192.168.200.34 > 192.168.200.1: ICMP echo request, id 32537, seq 5, length 64
20:19:13.543070 arp who-has 192.168.200.1 tell 192.168.200.34
20:19:13.543124 IP 192.168.200.34 > 192.168.200.1: ICMP echo request, id 32537, seq 6, length 64
20:19:14.543122 arp who-has 192.168.200.1 tell 192.168.200.34
20:19:14.543194 IP 192.168.200.34 > 192.168.200.1: ICMP echo request, id 32537, seq 7, length 64
20:19:15.543174 arp who-has 192.168.200.1 tell 192.168.200.34
20:19:15.543248 IP 192.168.200.34 > 192.168.200.1: ICMP echo request, id 32537, seq 8, length 64
20:19:16.547228 arp who-has 192.168.200.1 tell 192.168.200.34
20:19:17.547282 arp who-has 192.168.200.1 tell 192.168.200.34
20:19:18.547334 arp who-has 192.168.200.1 tell 192.168.200.34
20:19:20.547436 arp who-has 192.168.200.1 tell 192.168.200.34
20:19:21.547484 arp who-has 192.168.200.1 tell 192.168.200.34
20:19:22.547530 arp who-has 192.168.200.1 tell 192.168.200.34
20:19:23.392983 IP 192.168.200.1.520 > 255.255.255.255.520: RIPv1, Response, length: 24
20:19:24.299235 arp who-has 192.168.200.27 (ff:ff:ff:ff:ff:ff) tell 192.168.200.1
20:19:24.543646 IP 192.168.200.34 > 192.168.200.1: ICMP echo request, id 32537, seq 17, length 64
20:19:25.543693 IP 192.168.200.34 > 192.168.200.1: ICMP echo request, id 32537, seq 18, length 64
20:19:26.543741 IP 192.168.200.34 > 192.168.200.1: ICMP echo request, id 32537, seq 19, length 64
20:19:27.543788 IP 192.168.200.34 > 192.168.200.1: ICMP echo request, id 32537, seq 20, length 64
20:19:28.543845 IP 192.168.200.34 > 192.168.200.1: ICMP echo request, id 32537, seq 21, length 64
20:19:29.543875 arp who-has 192.168.200.1 tell 192.168.200.34
20:19:29.543908 IP 192.168.200.34 > 192.168.200.1: ICMP echo request, id 32537, seq 22, length 64
20:19:30.543928 arp who-has 192.168.200.1 tell 192.168.200.34
20:19:30.544022 IP 192.168.200.34 > 192.168.200.1: ICMP echo request, id 32537, seq 23, length 64
20:19:31.543982 arp who-has 192.168.200.1 tell 192.168.200.34
20:19:31.544076 IP 192.168.200.34 > 192.168.200.1: ICMP echo request, id 32537, seq 24, length 64
20:19:32.548036 arp who-has 192.168.200.1 tell 192.168.200.34
20:19:33.548091 arp who-has 192.168.200.1 tell 192.168.200.34

---

### Post by dbott67 on 2007-04-22
I'm starting to run out of ideas... I ran the same tcpdump -nli eth0 / ping gateway commands as you & got this:

```
root@feisty:/home/dbott# tcpdump -nli eth0
tcpdump: verbose output suppressed, use -v or -vv for full protocol decode
listening on eth0, link-type EN10MB (Ethernet), capture size 96 bytes
21:57:01.974835 IP [COLOR=Blue]192.168.1.106[/COLOR] > [COLOR=Red]192.168.1.1[/COLOR]: ICMP echo [COLOR=Blue]request[/COLOR], id 15900, seq 1, length 64
21:57:01.975384 IP [COLOR=Red]192.168.1.1[/COLOR] > [COLOR=Blue]192.168.1.106[/COLOR]: ICMP echo [COLOR=Red]reply[/COLOR], id 15900, seq 1, length 64
21:57:02.974134 IP 192.168.1.106 > 192.168.1.1: ICMP echo request, id 15900, seq 2, length 64
21:57:02.974676 IP 192.168.1.1 > 192.168.1.106: ICMP echo reply, id 15900, seq 2, length 64
21:57:03.974010 IP 192.168.1.106 > 192.168.1.1: ICMP echo request, id 15900, seq 3, length 64
21:57:03.974564 IP 192.168.1.1 > 192.168.1.106: ICMP echo reply, id 15900, seq 3, length 64
21:57:04.973984 IP 192.168.1.106 > 192.168.1.1: ICMP echo request, id 15900, seq 4, length 64
21:57:04.974542 IP 192.168.1.1 > 192.168.1.106: ICMP echo reply, id 15900, seq 4, length 64
21:57:05.973895 IP 192.168.1.106 > 192.168.1.1: ICMP echo request, id 15900, seq 5, length 64
21:57:05.974445 IP 192.168.1.1 > 192.168.1.106: ICMP echo reply, id 15900, seq 5, length 64

[1]+  Stopped                 tcpdump -nli eth0

```

I'm guessing your output *should* look like this, but it keeps returning this:
```
 20:19:12.543036 IP 192.168.200.34 > 192.168.200.1: ICMP echo request, id 32537, seq 5, length 64
 20:19:13.543070 arp who-has 192.168.200.1 tell 192.168.200.34
 20:19:13.543124 IP 192.168.200.34 > 192.168.200.1: ICMP echo request, id 32537, seq 6, length 64
 20:19:14.543122 arp who-has 192.168.200.1 tell 192.168.200.34
 20:19:14.543194 IP 192.168.200.34 > 192.168.200.1: ICMP echo request, id 32537, seq 7, length 64
 20:19:15.543174 arp who-has 192.168.200.1 tell 192.168.200.34
```

The one thing that I'm now confused about is your setup.  The above output is for eth1, which is not the problem card (I think).  

The output of lshw -C network reveals 2 nics: **eth0** (the RealTek card) and **eth2** (the nForce2 card - DISABLED)

In your interfaces file, you have static IPs set for eth0 (192.168.200.2) and eth2 (192.168.200.212).  eth1 is DHCP, but there does not appear to be a physical device.

So I have a few questions/requests:

1. How many ethernet cards do you have and what is their purpose?  
2. Can you re-post using **tcpdump -nli eth[COLOR=Blue]0[/COLOR]**[COLOR=Blue][COLOR=Black] (or eth2, as the case may be)?
3. Can you post the output of:
```
dbott@feisty:~$ cat /etc/iftab 
# This file assigns persistent names to network interfaces.
# See iftab(5) for syntax.

eth0 mac 00:50:ba:c0:a7:55 arp 1

```

-Dave
[/COLOR][/COLOR][COLOR=Blue][COLOR=Black][/COLOR][/COLOR]

---

### Post by obz on 2007-04-22
Before any of this started I was using a PCI Realtek NIC... I disabled it and tried the OnBoard NIC... that didn't work either so I disabled it... I bought a new NIC and that is the only one currently enabled. (as eth1)

the above dump was from eth1 the only enabled NIC.

Let me know if those requests are still relevant.

---

### Post by obz on 2007-04-24
still offline. does anyone have any ideas?

I don't want to have to revert to an older version... :(

---

### Post by keith11 on 2007-04-24
> **obz said:**
> Hello. 

I'm having issues getting anywhere on the Internet. I'm using the new Ubuntu 7.04 Feisty Fawn on a home network behind a Cable Modem Router. I have other computers using the same Router (Windows XP) and they have no issues at all. 

I had the previous version of Ubuntu working without any issues. So whatever is the cause of this is likely due to a recent update. 

I've read several posts related to this problem and I have disabled IPV6. I also added the dyndns DNS server ips to my DNS server list.  I can't ping any computer on the LAN. Attempts to do so result in : Destination Host Unreachable 100% packet loss.

I've tried both static and dhcp ip addresses neither worked.

Any suggestions or direction would be great. 

:(


Do you know if your wireless card module is listed in the list of modules? Are you sure your MD5 sums matched with the downloaded iso image?

---

### Post by Detonate on 2007-04-24
Another thought, have you opened Firestarter to see if it is recording anything as being blocked?  Try disabling your firewall and see what happens.

---

### Post by obz on 2007-04-24
> **keith11 said:**
> Do you know if your wireless card module is listed in the list of modules? Are you sure your MD5 sums matched with the downloaded iso image?

It ISN'T a wireless card. It is a normal nothing special PCI D-Link NIC.

---

### Post by obz on 2007-04-24
> **Detonate said:**
> Another thought, have you opened Firestarter to see if it is recording anything as being blocked?  Try disabling your firewall and see what happens.

I ran a test before to see if Firestarter was running. It isn't.

---

### Post by Detonate on 2007-04-24
But Firestarter is just a front end GUI for your iptables, which is your firewall, which is worth checking to see if that's blocking anything, and Firestarter is a easy way to check that for someone who is not an expert on iptables.  so the fact that firestarter itself is not running means nothing, the firewall could still be the problem.

---

### Post by obz on 2007-04-24
> **Detonate said:**
> But Firestarter is just a front end GUI for your iptables, which is your firewall, which is worth checking to see if that's blocking anything, and Firestarter is a easy way to check that for someone who is not an expert on iptables.  so the fact that firestarter itself is not running means nothing, the firewall could still be the problem.

So how do I check if my iptables settings are correct?

---

### Post by Detonate on 2007-04-24
With Firestarter.

---

### Post by obz on 2007-04-24
> **Detonate said:**
> With Firestarter.

Great thanks for that. I already stated Firestarter isn't running... :-k

---

### Post by dbott67 on 2007-04-24
> **obz said:**
> So how do I check if my iptables settings are correct?

You did that already... a couple of pages back! :)  

It was **sudo iptables -L**:```
dbott@feisty:~$ sudo iptables -L
Chain INPUT (policy ACCEPT)
target     prot opt source               destination         

Chain FORWARD (policy ACCEPT)
target     prot opt source               destination         

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination      
```

-Dave

---

### Post by obz on 2007-04-24
> **dbott67 said:**
> You did that already... a couple of pages back! :)  

It was **sudo iptables -L**:```
dbott@feisty:~$ sudo iptables -L
Chain INPUT (policy ACCEPT)
target     prot opt source               destination         

Chain FORWARD (policy ACCEPT)
target     prot opt source               destination         

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination      
```

-Dave

This is starting to blur into one big mess. I'm likely just going to give up and go back 6.10; clearly 7.04 isn't ready for prime time and it is seems the problem is elusive. sigh... :(

---

### Post by Detonate on 2007-04-24
Sorry, I missed that one.  My point about Firestarter is to run it.  It will give you a GUI that you can look at the "Events" and see if anything is being blocked, and a means to easily clear those up if needed.  But you've already checked that from the CLI, so that is probably not your problem.  So I don't have any other ideas.

---

### Post by obz on 2007-04-24
> **Detonate said:**
> Sorry, I missed that one.  My point about Firestarter is to run it.  It will give you a GUI that you can look at the "Events" and see if anything is being blocked, and a means to easily clear those up if needed.  But you've already checked that from the CLI, so that is probably not your problem.  So I don't have any other ideas.

No worries. I'm going to drop back to 6.10. Thanks for your help.

---

### Post by Detonate on 2007-04-24
When you drop back to Edgy, save a copy of your config files from Feisty so we can compare them to see where the problem was.  You hosts, and hosts.conf file and you IPtables and your modprobe files and anything else you can think of.  Heck, just copy your whole darn etc directory to a CD or something.  Hope everything works in edgy.  If it does, we may be able to compare the files and find out what the problem is.

---

### Post by obz on 2007-04-30
Not sure why this worked... but after having tried several ubuntu distros that *i knew worked* on my computer from previous installs ... I figured somehow it *had* to be a hardware problem. I ruled out the NICs, cablesm router. It seems like I was right...

I reset my mobo bios back to original state and tried it. And Voila! I got interweb. What setting was messing up my installs I don't know. I find it really odd. Hopefully this will help someone in some way.

I'm Feisty again. Phew. :)

---

### Post by Detonate on 2007-04-30
That is very interesting.  A BIOS update broke your network.  Hmmm, I have to think about that one.  I belong to the "if it ain't broke, don't fix it" school when it comes to BIOS updates.  I only update if I know there is a new supported feature that I need.

---

