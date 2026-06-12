---
title: "WG511v2 issues"
date: 2006-11-23
forum: Networking &amp; Wireless
---

### Post by kausbose on 2006-11-23
Hi all,

I would like to thank you in advance for your help. I guess that I have the worst wireless card to use under linux. I have the WG511v2](*,) . Anyways I have been reading in the forums and I have managed to get **ndiswrapper** ver 1.29 to get to work for me. I used the Windows 2000/XP .inf and .sys files for my card. When I run 'ndiswrapper -l' I get the following output

kbose@kbose-laptop:~$ ndiswrapper -l
Installed drivers:
wg511v2         driver installed, hardware present 

But this is what I get when I run ifconfig

kbose@kbose-laptop:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:0D:56:AE:C0:CF  
          inet addr:192.168.2.3  Bcast:192.168.2.255  Mask:255.255.255.0
          inet6 addr: fe80::20d:56ff:feae:c0cf/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:2141 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2313 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1660805 (1.5 MiB)  TX bytes:360904 (352.4 KiB)
          Interrupt:7 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:2 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:100 (100.0 b)  TX bytes:100 (100.0 b)

sit0      Link encap:IPv6-in-IPv4  
          inet6 addr: ::127.0.0.1/96 Scope:Unknown
          inet6 addr: ::192.168.2.3/96 Scope:Compat
          UP RUNNING NOARP  MTU:1480  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

and iwconfig

kbose@kbose-laptop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

sit0      no wireless extensions.

but I know that ndiswrapper is in running

kbose@kbose-laptop:~$ ndiswrapper -m
modprobe config already contains alias directive

Could someone please shed some light on this issue?:confused: 

Thanks in advance.

Kaustav

System config
Ubuntu Edgy Efy 6.10
Dell Inspiron 5100

---

### Post by FrodoB on 2006-11-23
Have you tried:

sudo depmod -a

sudo modprobe ndiswrapper

then

iwconfig

---

### Post by kausbose on 2006-11-23
> **FrodoB said:**
> Have you tried:

sudo depmod -a

sudo modprobe ndiswrapper

then

iwconfig
Yes I did use sudo! No avail!

---

### Post by FrodoB on 2006-11-23
I don't know this device. 

Have you looked carefully at each of these in the hardware list on the ndiswrapper site for clues:

[LIST=1]
[*]Card: Netgear WG511 v2 54Mbps Cardbus adapter (Made in China) [LIST]
[*]Chipset: Marvell Technology Group Ltd.: Unknown device 1faa (rev 03)
[*]pciid: 11ab:1faa
[*]Driver: Windows 2000 driver available on the Netgear CD: WG511v2.INF
[*]Other:Tested with ndiswrapper 1.1 source compile. Also works with ndiswrapper 1.2 release, using Fedora Core 3, with 16k kernel from [www.Linuxant.com](www.Linuxant.com) (2.6.9-1.667), using Windows driver. Possible hang on 'modprobe ndiswrapper', but works on reboot, once ndiswrapper is in /etc/modprobe.conf via 'ndwrapper -m'. Note: have not tried any encryption settings. Note: Previous info here was wrong, win XP driver does not work[/LIST][/LIST] Encryption settings work.  Problem at startup on Ubuntu Dapper. Clashes with mrv8k driver at system startup. Blacklist mrv8k by adding 'blacklist mrv8k'(without quotes) in /etc/modprobe.d/blacklist. This solves the problem at startup. 
 [LIST=1]
[*]Card: Netgear WG511 V2 (Made in Taiwan)[LIST]
[*]Chipset: Marvell Technology Group Ltd.: Unknown device lfaa (rev 03)
[*]Driver: Windows XP driver available on the Netgear CD: WG511v2.INF
[*]Other: I'm using Ubuntu Breezy with Kernel 2.6.12-8-386. Ndiswrapper is provided by Ubuntu Breezy Colony 3 CD and version is 1.1-4. I also tried with Ubuntu Horay and its ndiswrapper seems to be broken. Once I upgrade to Breezy and it all works fine.[/LIST] 
[*]Card: Netgear WG511 v2 (Made in China)[LIST]
[*]Chipset: Marvell Technology Group Ltd.: Unknown device 1faa (rev 03)
[*]Driver: Any marvell chipset driver, either from the CD, from Netgear website or from Marvell website
[*]Other: You cannot have preemtive kernel. It hangs either on modprobe, or randomly later. Tried with 2.6.8, 2.6.12, 2.6.13.4 and ndiswrapper1.1 and 1.4.[/LIST][/LIST]Usually it is a matter of getting the "right" NDIS files to work with. If there are differing versions for XP, 2000, etc, you need to systematically work your way through them, removing the ones that did not work before putting the new ones in.

Best of Luck.

---

### Post by FrodoB on 2006-11-23
Also note the NDIS drivers recommended in this blog page. He got it working and you will too eventually:

[http://verens.com/archives/2005/02/21/installing-a-netgear-wg511-v2-marvell-chipset-in-linux/](http://verens.com/archives/2005/02/21/installing-a-netgear-wg511-v2-marvell-chipset-in-linux/)

---

