---
title: "Wired Connection / No Internet"
date: 2007-10-23
forum: Networking &amp; Wireless
---

### Post by NcA on 2007-10-23
I'm in the process of setting up a friends' PC at the workplace using Gutsy 7.10. Installed fine etc. Once booted however, there was no connection to the internet...  Common story, I know. First of all the PC is a (semi) old Dell 'Dimension' 4600, built in ethernet etc. It's connected to a D-Link DSL-504T ADSL Router, on which all the XP machines in the rest of the office run fine one. Where it gets strange, is that if I plug my laptop (running Ubuntu Studio 7.04) into the same ethernet cable, it works fine.

I can ping the router from the problem PC, everything in the internal network seems to be running fine, I've made sure the address is allocated by DHCP, but to no avail. So, can anyone give me any suggestions or advice?

Cheers, NcA

p.s. I won't be able to run ifconfig or anything until tomorrow, but any preliminary advice would help ;)

---

### Post by noob12 on 2007-10-24
If you can post the output of these extracted from the box, it would be helpful:

```

lspci -nn

sudo lshw -C network

```

---

### Post by NcA on 2007-10-25
This took a little longer than expected to get around to, but I've played around with the DNS settings on the router, and trying to manually configure everything, but none of that worked. SO here's some readouts for anyone to look at and see what you can make of this problem;

[quote=ifconfig]eth0      Link encap:Ethernet  HWaddr 00:11:11:1F:A3:23  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:601 errors:0 dropped:0 overruns:0 frame:0
          TX packets:433 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:825422 (806.0 KB)  TX bytes:34900 (34.0 KB)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)[/quote]

[quote=lshw -C network]  *-network               
       description: Ethernet interface
       product: 82562EZ 10/100 Ethernet Controller
       vendor: Intel Corporation
       physical id: 8
       bus info: pci@0000:01:08.0
       logical name: eth0
       version: 02
       serial: 00:11:11:1f:a3:23
       size: 10MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=e100 driverversion=3.5.17-k4-NAPI duplex=half firmware=N/A latency=64 link=no maxlatency=56 mingnt=8 module=e100 multicast=yes port=MII speed=10MB/s[/quote]

[quote=lspci -nn]efaranghi@efaranghi-office:~$ lspci -nn
00:00.0 Host bridge [0600]: Intel Corporation 82865G/PE/P DRAM Controller/Host-Hub Interface [8086:2570] (rev 02)
00:02.0 VGA compatible controller [0300]: Intel Corporation 82865G Integrated Graphics Controller [8086:2572] (rev 02)
00:1d.0 USB Controller [0c03]: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #1 [8086:24d2] (rev 02)
00:1d.1 USB Controller [0c03]: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #2 [8086:24d4] (rev 02)
00:1d.2 USB Controller [0c03]: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #3 [8086:24d7] (rev 02)
00:1d.3 USB Controller [0c03]: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #4 [8086:24de] (rev 02)
00:1d.7 USB Controller [0c03]: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB2 EHCI Controller [8086:24dd] (rev 02)
00:1e.0 PCI bridge [0604]: Intel Corporation 82801 PCI Bridge [8086:244e] (rev c2)
00:1f.0 ISA bridge [0601]: Intel Corporation 82801EB/ER (ICH5/ICH5R) LPC Interface Bridge [8086:24d0] (rev 02)
00:1f.1 IDE interface [0101]: Intel Corporation 82801EB/ER (ICH5/ICH5R) IDE Controller [8086:24db] (rev 02)
00:1f.2 IDE interface [0101]: Intel Corporation 82801EB (ICH5) SATA Controller [8086:24d1] (rev 02)
00:1f.3 SMBus [0c05]: Intel Corporation 82801EB/ER (ICH5/ICH5R) SMBus Controller [8086:24d3] (rev 02)
01:00.0 Multimedia audio controller [0401]: Creative Labs SB Audigy LS [1102:0007]
01:01.0 Modem [0703]: Intel Corporation FA82537EP 56K V.92 Data/Fax Modem PCI [8086:1080] (rev 04)
01:08.0 Ethernet controller [0200]: Intel Corporation 82562EZ 10/100 Ethernet Controller [8086:1050] (rev 02)[/quote]

Any suggestions will be greatly appreciated. Thanks,

NcA

---

### Post by ezphilosophy on 2007-10-25
I installed Gutsy on a friend's computer and had the exact same problem.  It's hooked up to a router and I can access the router (wired connection) but cannot connect to the internet.  
Hope to solve this [strange] problem!

---

### Post by NcA on 2007-10-25
Out of curiosity, was your friends' computer a Dell also?

I tried installing Ubuntu Studio 7.10 on the same PC a litte later, and it has the same problem. So I'm assuming it's something to do with 7.10. I'll try 7.04 out, and with a little bit of luck that might work, if not, Ubuntu will have failed me, and it'll be back to windows :(

---

### Post by froy02 on 2007-10-25
Try this Ububtu website.  It may help you.

[https://help.ubuntu.com/7.04/internet/C/connect-to-internet.html#modems](https://help.ubuntu.com/7.04/internet/C/connect-to-internet.html#modems)

---

### Post by lordbelgar on 2007-10-25
Ditto.

I have just installed Kubuntu 7.10 Gutsy, after fixing a video driver issue (apparently X11's nv driver does not work on Geforce 8 cards even though it says it does) I came upon no internet. I however do not have a Dell, my system is built from scratch and has an ABIT NF-M2 nView mobo with built-in nVidia Ethernet. The driver for this card loads with no problem I can see it on ifconfig and lspci. When I launch the Network Manager from the desktop I see eth0 listed and when I "manually" configure it throught this interface to use DHCP it gleefully restarts my networking and shows back up with an ip assigned to eth0, but still no internet. After all of this I go back to ifconfig and now I have a fake card listed as eth0:avah. This card has the ip that I just saw assigned to eth0 in the gui and eth0 is still listed as UP but with no ip and I still can't access the internet or anything past my Linksys VoIP router. So, anyone got a clue? I should mention that I dual boot Gentoo and this new install of Kubuntu, Gentoo works fine. I simply use DHCPCD in Gentoo and I am unfamiliar with the DHCLIENT and the other networking apps that came with Kubuntu.

---

### Post by handy on 2007-10-26
IPv6 can cause some strange problems on the buntoos, have look here? Hopefully it may help someone, the how-to covers a few issues:

***_[http://ubuntuforums.org/showthread.php?t=282034](http://ubuntuforums.org/showthread.php?t=282034)_***

---

### Post by lordbelgar on 2007-10-26
Thank you Handy! I can't try it out yet but just reading through your write-up I think this may be the thing I needed. On my Gentoo, I had never configured IPv6, it just didn't occur to me that on Kubuntu it was there by default.

---

### Post by ezphilosophy on 2007-10-27
> **NcA said:**
> Out of curiosity, was your friends' computer a Dell also?
Yeah, actually it is.

> **handy said:**
> IPv6 can cause some strange problems on the buntoos, have look here? Hopefully it may help someone, the how-to covers a few issues:
***_[http://ubuntuforums.org/showthread.php?t=282034](http://ubuntuforums.org/showthread.php?t=282034)_***

I'll check this out.

> **froy02 said:**
> Try this Ububtu website.  It may help you.

[https://help.ubuntu.com/7.04/internet/C/connect-to-internet.html#modems](https://help.ubuntu.com/7.04/internet/C/connect-to-internet.html#modems)

My friend is using a router and everything works fine in other OS's.  Don't think the problem lies here.

---

### Post by kevdog on 2007-10-27
Can you ping external IP addresses beyond the router?

Do you have the router configured as the gateway? (route -n)

---

### Post by Ghost Pirate on 2007-10-27
I'm having the same problem . . . no internet.  The odd thing is, I can download programs and updates at my full download speed, I just can't access any web pages.  It started after I upgraded to Gutsy, so I'm going to try going back to Feisty.

---

### Post by handy on 2007-10-27
> **Ghost Pirate said:**
> I'm having the same problem . . . no internet.  The odd thing is, I can download programs and updates at my full download speed, I just can't access any web pages.  It started after I upgraded to Gutsy, so I'm going to try going back to Feisty.

First thing I would do in your situation is disable ipv6 in Firefox, & see if you can browse then.

I have had that situation myself, & it is so easy to fix.

Scroll down to the Quick IPv6 fix for Firefox part of [***_this how-to_***]("http://ubuntuforums.org/showthread.php?t=282034")?

---

### Post by rudasn on 2007-10-27
> **kevdog said:**
> Can you ping external IP addresses beyond the router?

Do you have the router configured as the gateway? (route -n)

I am having a similar problem, The output I get from this command is:

```
Kernel IP routeing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.1.0     0.0.0.0         255.255.255.0   U     0      0        0 eth0
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 eth0
0.0.0.0         192.168.1.1     0.0.0.0         UG    100    0        0 eth0

```

192.168.1.1 is my router's address. However, both the router and my pc are connected to airport extreme whose IP address is 192.168.1.6. When I have the router's ip as my gateway address I can connect to the internet but not to airport's base station. When I have airport's IP as a gateway I can't connect anywhere.

Any suggestions?

---

### Post by ezphilosophy on 2007-10-30
Ok.  I've tried disabling the ipv6 (with the quick fix) and the internet still didn't work, nor can I update the computer.  I still can access the router (wired connection) and windows can get on the internet.  Strange problem!
I then did the command: sudo lshw -C network
and got this:

```
ubuntu@ubuntu:~$ sudo lshw -C network
  *-network               
       description: Ethernet interface
       product: RTL8111/8168B PCI Express Gigabit Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:04:00.0
       logical name: eth0
       version: 01
       serial: 00:1a:4d:4a:57:9a
       size: 100MB/s
       capacity: 1GB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm vpd msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.2LK duplex=full ip=192.168.1.101 latency=0 link=yes module=r8169 multicast=yes port=twisted pair speed=100MB/s

```

Before, I said my friend's computer is a dell.  It is not.  I was getting the problem confused with another problem with another friend.  The computer with this current wired connection/internet problem is a built computer and is running pretty much top of the line everything.  (Intel Quad core, 8800 GTX, 4 Gig Ram...)

---

### Post by ezphilosophy on 2007-10-30
Although I'm not a big fan of doing it, I'm just gonna give this thread a little *bump*.

---

### Post by ross350 on 2007-10-30
don't usualy do&BUMP it  cause i'm lazy and BUMPonly occured to me that signing in and doing it was actualy worth wile,BUMP
bump ,
someone who knows whats going on here find a computer and solve it.
thats how we&r going to get anywhere here
if anyone wants a dell user besides the guy the the blog about his amazing 1501 that is working out of the box *thats so strange)

bump 
I wanted BUMP gutsy Bump 
on my BUMP DELL 1501 
soooo Bump bad
ahhhh
 silly internet will not connect for me 
i will use the boot cd for feist for one more hour 
but i doubt anyone will fix it 
people offer codes but i have not heard one user report back and say yes it is working thank you and that be the end of the story. its something wrong with this upgrade i have tried fresh install and upgrade from feisty and neither give me internet out of the box like feisty does.
 how can they make such a stuff up
can we get every thing else for gutsy without upgrading?
like can i get someone to make a pack with all the good stuff and leav out this anoying problem  a special upgrade that works would be so great

---

### Post by ross350 on 2007-10-30
simply must bump

---

### Post by ross350 on 2007-10-30
gonna bump on through to the other side

---

### Post by ross350 on 2007-10-30
T.N.T Bump! bump bump

---

### Post by ross350 on 2007-10-30
getting up to make a coffee to achieve much more Bumps when i return
Bumps toe on table !***
spills hot *** coffee over my *BUMP((***
and slips in the puddle before going don the steps head first 
BUMP(
          Bump *
                     Bump*
                               bu
                                    mp!!!!!!

                                           pants when i think its all over only to see a shaking vase tilt in my direction.  
                       \
                         \
                          l
                          l
                          . 
                          l



      Bump((((

---

### Post by Ghost Pirate on 2007-11-07
> **handy said:**
> First thing I would do in your situation is disable ipv6 in Firefox, & see if you can browse then.

I have had that situation myself, & it is so easy to fix.

Scroll down to the Quick IPv6 fix for Firefox part of [***_this how-to_***]("http://ubuntuforums.org/showthread.php?t=282034")?

Sorry I didn't reply back to this right away.  Yes, this did work for me.  As soon as I disabled ipv6, my internet was working beautifully once again, and has continued to do so without a hitch.  Thanks.

---

### Post by handy on 2007-11-21
***@ross350:*** Sorry for not replying sooner, I have not been looking at my previous posts until now as there were so few of them, (except in the Backyard ;-)).

I have edited [***_my how-to_***]("http://ubuntuforums.org/showthread.php?t=282034") to include globally disabling ipv6, it that doesn't help, I'm sorry the problem is beyond my meager linux knowledge.

---

