---
title: "No Wired Network [Please help!]"
date: 2007-05-09
forum: Networking &amp; Wireless
---

### Post by DWRZ on 2007-05-09
**This post could be related to an Ubuntu bug filed at**: network wired no connection internet [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				I had this problem in Edgy Eft 6.10, but I never really took care of it (bad, busy/lazy me) since I could always fall back on my wireless connection.

I did a clean install of Feisty Fawn today, and now I'm stuck with no network connection and I've had to fall back on Windows XP SP2. :( 

Basically, my Ethernet is plugged in and it works fine in Windows XP. In Ubuntu 7.04, it detects the wired card and is able to "connect" to the network, but loading up Firefox and trying to connect to anything results in an endless, uhm, "loading of page".

I've looked at other threads here on the board and using google as well, but I can't seem to find any solutions... most threads are dead ends. :( Any ideas on how to fix this?

Here's the ifconfig info:
```
eth0      Link encap:Ethernet  HWaddr 00:C0:9F:81:C7:CB  
          inet addr:129.133.158.250  Bcast:255.255.255.255  Mask:255.255.224.0
          inet6 addr: fe80::2c0:9fff:fe81:c7cb/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:8474 errors:0 dropped:0 overruns:0 frame:0
          TX packets:54 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:2910908 (2.7 MiB)  TX bytes:6438 (6.2 KiB)
          Interrupt:22 Base address:0xe400 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:2 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:100 (100.0 b)  TX bytes:100
```

lspci info:
```

(100.0 b)
00:00.0 Host bridge: Intel Corporation 82915G/P/GV/GL/PL/910GL Memory Controller Hub (rev 04)
00:01.0 PCI bridge: Intel Corporation 82915G/P/GV/GL/PL/910GL PCI Express Root Port (rev 04)
00:1c.0 PCI bridge: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 1 (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #3 (rev 03)
00:1d.3 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #4 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB2 EHCI Controller (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev d3)
00:1e.2 Multimedia audio controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) AC'97 Audio Controller (rev 03)
00:1e.3 Modem: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) AC'97 Modem Controller (rev 03)
00:1f.0 ISA bridge: Intel Corporation 82801FB/FR (ICH6/ICH6R) LPC Interface Bridge (rev 03)
00:1f.1 IDE interface: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) IDE Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) SMBus Controller (rev 03)
01:00.0 VGA compatible controller: ATI Technologies Inc M24 1P [Radeon Mobility X600]
0b:00.0 CardBus bridge: Texas Instruments PCIxx21/x515 Cardbus Controller
0b:00.2 FireWire (IEEE 1394): Texas Instruments OHCI Compliant IEEE 1394 Host Controller
0b:00.3 Mass storage controller: Texas Instruments PCIxx21 Integrated FlashMedia Controller
0b:00.4 Generic system peripheral [0805]: Texas Instruments PCI6411/6421/6611/6621/7411/7421/7611/7621 Secure Digital Controller
0b:02.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
0b:03.0 Network controller: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller (rev 02)
```

---

### Post by joft on 2007-05-09
> **DWRZ said:**
> Basically, my Ethernet is plugged in and it works fine in Windows XP. In Ubuntu 7.04, it detects the wired card and is able to "connect" to the network, but loading up Firefox and trying to connect to anything results in an endless, uhm, "loading of page".

Do you use DHCP or static configuration? What does
```
sudo route -n
```
say? Perhaps a routing issue (e.g. default route)? What does
```
cat /etc/resolv.conf
```
say? Perhaps a DNS resolver issue?

> **DWRZ said:**
> 
```
eth0      Link encap:Ethernet  HWaddr 00:C0:9F:81:C7:CB  
          inet addr:129.133.158.250  Bcast:255.255.255.255  Mask:255.255.224.0

```

Are you sure that this (129.133.158.250) is the right IP your PC is supposed to use? This seems to be "public" IP .... BTW: The subnet mask is bit unusual, however, this does not mean that it is incorrect.

What does your Windows XP tell you about configuration (IP ("ipconfig /all"), routing table ("route print"), DNS server)?

---

### Post by DWRZ on 2007-05-09
Ok, before I try to answer the questions, here's some more info I just dug up

Contents of resolve.conf
```
search wesleyan.edu
nameserver 129.133.6.11
nameserver 129.133.6.10
```

If I try to ping [www.google.com](www.google.com)
```
ping www.google.com
ping: unknown host www.google.com 
```

If I ping 129.133.6.10 or ping 129.133.6.11
```
ping 129.133.6.10
PING 129.133.6.10 (129.133.6.10) 56(84) bytes of data.
[nothing happens]
```

If I ping localhost:
```
PING localhost (127.0.0.1) 56(84) bytes of data.
64 bytes from localhost (127.0.0.1): icmp_seq=1 ttl=64 time=0.032 ms
64 bytes from localhost (127.0.0.1): icmp_seq=2 ttl=64 time=0.023 ms
64 bytes from localhost (127.0.0.1): icmp_seq=3 ttl=64 time=0.023 ms
64 bytes from localhost (127.0.0.1): icmp_seq=4 ttl=64 time=0.024 ms
64 bytes from localhost (127.0.0.1): icmp_seq=5 ttl=64 time=0.025 ms
Etc.
```

If I try to go to [www.google.com](www.google.com) with Firefox:
```
Server not found.
```

Interestingly enough, selecting the "Network" option in "Places" brought up a prompt for username and password to access MSHOME or something like that. Inputting my Ubuntu (and WinXP) username and password, I got guest access to what appeared to be various computers and servers on my university's network. *shrug* Not sure if this is of any use...

---

### Post by DWRZ on 2007-05-09
I'm pretty sure I've always used DHCP without problems. When I did use the wired network before I had issues I don't recall having to do anything except plug in my cable to the Ethernet jack here.

This is what WinXP gives me:

ipconfig /all:
```

Windows IP Configuration

        Host Name . . . . . . . . . . . . : dwrz-ulysses
        Primary Dns Suffix  . . . . . . . :
        Node Type . . . . . . . . . . . . : Hybrid
        IP Routing Enabled. . . . . . . . : No
        WINS Proxy Enabled. . . . . . . . : No
        DNS Suffix Search List. . . . . . : wesleyan.edu

Ethernet adapter Local Area Connection:

        Connection-specific DNS Suffix  . : wesleyan.edu
        Description . . . . . . . . . . . : Realtek RTL8139 Family PCI Fast Ethe
rnet NIC
        Physical Address. . . . . . . . . : 00-C0-9F-81-C7-CB
        Dhcp Enabled. . . . . . . . . . . : Yes
        Autoconfiguration Enabled . . . . : Yes
        IP Address. . . . . . . . . . . . : 129.133.143.171
        Subnet Mask . . . . . . . . . . . : 255.255.224.0
        Default Gateway . . . . . . . . . : 129.133.128.1
        DHCP Server . . . . . . . . . . . : 129.133.1.5
        DNS Servers . . . . . . . . . . . : 129.133.6.11
                                            129.133.6.10
        Primary WINS Server . . . . . . . : 129.133.1.115
        Secondary WINS Server . . . . . . : 129.133.1.113
        Lease Obtained. . . . . . . . . . : 2007.05.09. Wednesday 03.14.45
        Lease Expires . . . . . . . . . . : 2007.05.11. Friday 17.32.22

Ethernet adapter Wireless Network Connection:

        Connection-specific DNS Suffix  . : wesleyan.edu
        Description . . . . . . . . . . . : Broadcom 802.11b/g WLAN
        Physical Address. . . . . . . . . : 00-90-4B-F7-AF-F7
        Dhcp Enabled. . . . . . . . . . . : Yes
        Autoconfiguration Enabled . . . . : Yes
        IP Address. . . . . . . . . . . . : 129.133.184.110
        Subnet Mask . . . . . . . . . . . : 255.255.240.0
        Default Gateway . . . . . . . . . : 129.133.176.1
        DHCP Server . . . . . . . . . . . : 1.1.1.1
        DNS Servers . . . . . . . . . . . : 129.133.168.1
        Primary WINS Server . . . . . . . : 129.133.1.113
        Secondary WINS Server . . . . . . : 129.133.1.115
        Lease Obtained. . . . . . . . . . : 2007.05.09. Wednesday 03.14.55
        Lease Expires . . . . . . . . . . : 2007.05.13. Sunday 14.18.33

```
Route Print:
```

===========================================================================
Interface List
0x1 ........................... MS TCP Loopback interface
0x2 ...00 c0 9f 81 c7 cb ...... Realtek RTL8139 Family PCI Fast Ethernet NIC - P
acket Scheduler Miniport
0x3 ...00 90 4b f7 af f7 ...... Broadcom 802.11b/g WLAN - Packet Scheduler Minip
ort
===========================================================================
===========================================================================
Active Routes:
Network Destination        Netmask          Gateway       Interface  Metric
          0.0.0.0          0.0.0.0    129.133.128.1  129.133.143.171      20
          0.0.0.0          0.0.0.0    129.133.176.1  129.133.184.110      25
        127.0.0.0        255.0.0.0        127.0.0.1       127.0.0.1       1
    129.133.128.0    255.255.224.0  129.133.143.171  129.133.143.171      20
  129.133.143.171  255.255.255.255        127.0.0.1       127.0.0.1       20
    129.133.176.0    255.255.240.0  129.133.184.110  129.133.184.110      25
  129.133.184.110  255.255.255.255        127.0.0.1       127.0.0.1       25
  129.133.255.255  255.255.255.255  129.133.143.171  129.133.143.171      20
  129.133.255.255  255.255.255.255  129.133.184.110  129.133.184.110      25
      169.254.0.0      255.255.0.0  129.133.143.171  129.133.143.171      30
        224.0.0.0        240.0.0.0  129.133.143.171  129.133.143.171      20
        224.0.0.0        240.0.0.0  129.133.184.110  129.133.184.110      25
  255.255.255.255  255.255.255.255  129.133.143.171  129.133.143.171      1
  255.255.255.255  255.255.255.255  129.133.184.110  129.133.184.110      1
Default Gateway:     129.133.128.1
===========================================================================
Persistent Routes:
  None


```

Any ideas? :(

---

### Post by joft on 2007-05-09
As I said in my last last post: Could you please post the output of
```
sudo route -n
```
from within Ubuntu?

You should see a default route which is pointing ("Gateway") to 129.133.128.1 or 129.133.176.1 like in Windows.

---

### Post by .rdg on 2007-05-09
DWRZ,

there are two things I would consider strange.

The first one is here:
```

eth0      Link encap:Ethernet  HWaddr 00:C0:9F:81:C7:CB  
          inet addr:129.133.158.250  Bcast:**255.255.255.255**  Mask:255.255.224.0
          inet6 addr: fe80::2c0:9fff:fe81:c7cb/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:8474 errors:0 dropped:0 overruns:0 frame:0
          TX packets:54 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:2910908 (2.7 MiB)  TX bytes:6438 (6.2 KiB)
          Interrupt:22 Base address:0xe400 

```

Your broadcast IP address is completely wrong - it should be 129.133.159.255 with the IP/mask you were assigned.

The second strange thing is:
Ubuntu IP - 129.133.158.250
Windows IP - 129.133.143.171

on the same NIC. There is nothing completely wrong with that (both are in the same subnet), but seems strange to have a different IP with the same MAC address. It might just be a coincidence, that when you released your IP address (on Windows shutdown) the DHCP server just gave it to someone else and you got a different one in Ubuntu (could you try booting to Windows and Ubuntu couple of times and confirm the IP addresses are the same all the time?). Still - it does seem pretty unusual as for my taste.

Also - please post the route table joft asked for. If it's not a bother - I would prefer it the way it is printed out by netstat:

netstat -rn

(above are r - for route, n - for numbers, no resolving).

DNS is ok set ok in Ubuntu - so only the broadcast and probably routes are set wrong.
Regards,
.rdg

---

### Post by DWRZ on 2007-05-09
Ok: the Ubuntu IP was the same just now that I went to check the sudo route -n info. Which, by the way, gives this:

```
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
129.133.128.0   0.0.0.0         255.255.224.0   U     0      0        0 eth0
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 eth0
0.0.0.0         129.133.128.1   0.0.0.0         UG    0      0        0 eth0
```

Here's the current Windows ipconfig info:
```

        Connection-specific DNS Suffix  . : wesleyan.edu
        IP Address. . . . . . . . . . . . : 129.133.143.171
        Subnet Mask . . . . . . . . . . . : 255.255.224.0
        Default Gateway . . . . . . . . . : 129.133.128.1

```

@.rdg do you want the netstat -rn from Ubuntu?

Really appreciate the help so far!

---

### Post by .rdg on 2007-05-09
As for your routing table - it's definitely ok, as you have the route to default gateway set up which is enough to get networking.

The DNS servers are also fine. The strange broadcast IP is not used all the time (to be honest Linux uses much less broadcasts than Windows), so the networking should work most of the time.

Could you also do the following two tests. First - check if you are able to ping [www.google.com](www.google.com) (I just checked - they're not dropping ICMP). Post results.

Also, while still in Ubuntu, edit the /etc/network/interfaces file so you have:

```

auto eth0
iface eth0 inet static
    address 129.133.143.171
    netmask 255.255.224.0
    broadcast 129.133.159.255
    gateway 129.133.128.1

```

instead of the default:

```

auto eth0
iface eth0 inet dhcp

```

Then in terminal issue 2 commands:

sudo ifdown eth0
sudo ifup eth0

Try networking then - if it's OK (well it should be) then the problem is solely in DHCP settings you are receiving.

One other thing there might be wrong is Network Manager - it also tries to get your connection working. It might (just might) be doing something wrong - I had my share of pain with it (although not Ubuntu supplied packages and in Edgy). We could always test, so revert the /etc/network/interfaces to the way it was (dhcp). Then:

ps aux | grep nm-applet | grep -v grep

The second column is showing the PID (process ID), so we would have to kill it:

sudo kill PID

naturally change PID to the number you get from the previous command.

Then issue:

sudo ifdown eth0
sudo ifup eth0

And check your network settings again (ifconfig eth0) as well as if your networking is working.
Please post the relevant info on each test you made.

.rdg

---

### Post by DWRZ on 2007-05-09
I'll get right to those tests. Here's the info (netstat -rn) I just got:

```
Kernel IP routing table
Destination     Gateway         Genmask         Flags   MSS Window  irtt Iface
129.133.128.0   0.0.0.0         255.255.224.0   U         0 0          0 eth0
169.254.0.0     0.0.0.0         255.255.0.0     U         0 0          0 eth0
0.0.0.0         129.133.128.1   0.0.0.0         UG        0 0          0 eth0
```

Ubuntu and WinXP IPs still the same...

Going to test...

---

### Post by DWRZ on 2007-05-09
**Ping Google:**
```
ping www.google.com
ping: unknown host www.google.com

```

**Default setting:**
```
auto lo
iface lo inet loopback

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
```

Modified Settings:```

auto lo
iface lo inet loopback

auto eth0
iface eth0 inet static
    address 129.133.143.171
    netmask 255.255.224.0
    broadcast 129.133.159.255
    gateway 129.133.128.1

auto eth1
iface eth1 inet dhcp

auto eth2
iface eth2 inet dhcp

auto ath0
iface ath0 inet dhcp

auto wlan0
iface wlan0 inet dhcp

```

**Result:**
Nothing. Neither with Firefox or with pinging [www.google.com](www.google.com)... same old stuff.

**Next:**
```
dwrz@dwrz-Ulysses:~$ ps aux|grep nm-applet|grep -v grep
dwrz      5678  0.0  2.5  35256 13020 ?        S    04:53   0:00 nm-applet --sm-disable
dwrz@dwrz-Ulysses:~$ sudo kill 5678
dwrz@dwrz-Ulysses:~$ sudo ifdown eth0
ifdown: interface eth0 not configured
dwrz@dwrz-Ulysses:~$ sudo ifup eth0
There is already a pid file /var/run/dhclient.eth0.pid with pid 134993416
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

Listening on LPF/eth0/00:c0:9f:81:c7:cb
Sending on   LPF/eth0/00:c0:9f:81:c7:cb
Sending on   Socket/fallback
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 3
DHCPOFFER from 129.133.128.2
DHCPREQUEST on eth0 to 255.255.255.255 port 67
DHCPACK from 129.133.128.2
bound to 129.133.158.250 -- renewal in 116545 seconds.
```

:(

```
dwrz@dwrz-Ulysses:~$ ifconfig eth0
eth0      Link encap:Ethernet  HWaddr 00:C0:9F:81:C7:CB  
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:14416 errors:0 dropped:0 overruns:0 frame:0
          TX packets:478 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:3809560 (3.6 MiB)  TX bytes:61442 (60.0 KiB)
          Interrupt:22 Base address:0x6400 
```

Nothing. :( :confused: :( 
Did I mess up the tests or is there something else at work?

[Note: Been up all night trying to figure this out... going to hit the sack soon, but will try to dedicate the rest of today to fixing this... All help so far really appreciated and I hope this can be resolved... Thanks again.]

---

### Post by joft on 2007-05-09
Hmmm, very strange. There has to be "something else at work" ... Perhaps one new try would be to logout of X and at the login screen switch to a text console by the usual Ctrl-Alt-F2 for example. Then login with your usual name and password and "sudo ifdown eth0" followed by "sudo ifup eth0".
Then look at ifconfig, route -n and try to ping the default gateway, then the DNS servers and then whatever, e.g. [www.google.com](www.google.com) .

By not using X, we avoid all the apps/tools/daemons which get started as soon as you login "graphically". But I'm afraid that does solve the problem ....... hmmmm.

---

### Post by DWRZ on 2007-05-09
Ok, I will try that right now. 

Would there be any way of getting wireless to work? Download drivers to a USB stick from XP, then go through the motions on Ubuntu?

Otherwise, what else can I do in the meantime? Contact my Admin here, or report a bug?

Update:
Just tried all of that nothing, nothing works, everything is the same.

So what should I do? Contact my Administrator? Install Edgy again? Install Fedora Core 6 (see if it's a Linux or distro specific problem)?

I mean, is the problem in my network or in the distro?

---

### Post by .rdg on 2007-05-09
Installing other distro, such as Fedora, should at least show if it's Ubuntu specific or Linux generally. I haven't really ran into trouble such as you have, so it really seems strange - dhcp should have been easy for users.

What's really strange is that your manually entered network settings didn't work - they should be working out of the box. Perhaps you could try to try that again, but also check whether your DNS settings are correctly set up in /etc/resolv.conf file. If there's nothing (empty file or nothing relevant) you could hand-enter the DNS settings as well and it definitely should be working.

As for wireless - that's a really different story. Didn't have anything to do with that - so can't really give you a good tip. Start reading the forums / other sources for directions how to set up ndiswrapper (or perhaps your wifi NIC is supported by Linux already).

---

### Post by DWRZ on 2007-05-09
*sigh*

Well, I just finished installing Fedora Core 6, and... the internet doesn't work. Same exact problem. :mad:

I guess I should contact my network admin now? :(

---

### Post by EnderTheThird on 2007-05-10
I'm having the same problem!  I think the root of this is that 

```
Interrupt:22 Base address:0xe400"
```

at the end of "ifconfig" for your network interface.  This line shows up on my entries every time this happens to me.  It happens both with the onboard ethernet on my MSI P6N SLI Platinum and on a PCI NIC I installed.  I think it's something specific with the hardware in that it doesn't "refresh" itself and retry making a connection after it encounters an error or boots from Windows into Ubuntu.

I had it working shortly last night (with my onboard ethernet) but then got another "Interrupt" when I told my router to assign *.201 to my onboard MAC address instead of my NIC's MAC address.  After that, when the Router rebooted, I had Interrupts listed for both NICs and I was hosed again.

One thing you might try is turning off your computer and unplugging it for about 5 minutes.  This worked for me at one point last night because it reset my BIOS after it was without power for so long, and therefore reset my network connection/settings on the hardware.  I thought I broke my computer until I finally checked the BIOS after it kept sitting there idle after POST; my boot order had changed and it wasn't looking at the right HDD.

Anyway, give that a try and let us know what happens.  I can't get my BIOS to consistently reset, so it's not quite working for me.  I've even tried popping out the motherboard's battery while the computer is unplugged but it didn't reset the BIOS again.  If anyone has any ideas as to how to "reset" or "clear" the network connection/settings, please let me know.  Also, I am NOT dual booting Windows on here; it's just Feisty.  So whatever is causing this, it's not JUST limited to dual booters.

---

### Post by .rdg on 2007-05-11
DWRZ: did you try static IP configuration in Ubuntu with the suggested DNS settings I gave you? 

You might also contact the admin of your network - this is really strange, as it happens on more than one distro (which actually says it's Linux specific to me - I might be wrong though).

One other thing is to just get a new Ethernet NIC - just for a short test. Then you probably would have to do some tweaking (like changing the MAC for the tests) if your network admin requires to have a MAC registered. Pick some Realtek 8139 (I know you already have one) or 3Com - perhaps the network admin has a spare one to borrow for tests.

Really strange situation.

EnderTheThird: perhaps there's more of a irq/hardware issue in your case than others.

---

### Post by DWRZ on 2007-05-11
@.rdg-- yep, I tried the static IP and/with  the info you gave me (three times), even tried using some OpenDNS nameservers... nothing.

I was just wondering: when I originally came on campus in the Fall semester I had to register my PC with "Resnet". I had this done with XP. When I returned in January with Linux, all I did was plug it in and it worked. Could it be possible that I must now register my Linux OS even though XP is already registered on the network? I also heard that the university removed guest access recently-- I thought it was for wireless only, but perhaps it has an effect (or was also implemented) for wired access as well?

Here's a few University FAQs I dug up, maybe they help explain something:
[http://helpdesk.wesleyan.edu/tipsheets/resnet/general.shtml](http://helpdesk.wesleyan.edu/tipsheets/resnet/general.shtml)
[http://helpdesk.wesleyan.edu/tipsheets/resnet/winxp.shtml](http://helpdesk.wesleyan.edu/tipsheets/resnet/winxp.shtml)
[http://helpdesk.wesleyan.edu/tipsheets/resnet/consoles.shtml](http://helpdesk.wesleyan.edu/tipsheets/resnet/consoles.shtml)

I'm still stuck with XP in the meantime. :(

---

### Post by bukwirm on 2007-05-11
You shouldn't need to register again - it appears that your university tracks tour MAC address, which shouldn't change.

You might try [disabling IPv6]("http://ubuntuforums.org/showthread.php?t=6841&highlight=disable+ipv6").

---

### Post by DWRZ on 2007-05-11
[https://answers.launchpad.net/ubuntu/+question/6342](https://answers.launchpad.net/ubuntu/+question/6342)

I posted the question up, was told to test some stuff out, responded with some more output there...

I tried disabling ipv6 and it didn't work. :(

](*,)

Would switching back to edgy provide some interesting information? ](*,) ](*,) ](*,)

---

### Post by bukwirm on 2007-05-11
Make sure you restart after disabling it.

---

### Post by DWRZ on 2007-05-11
Yeah, I made sure, I took my time. I tried both combinations as well (off and off ipv6)... did the Firefox thing... nothing. :(

---

### Post by PHuN on 2007-08-29
@DWRZ, did you ever get the situation resolved? I know that you probably returned to classes but was wondering if you got it.

@Everyone, I am running into the same issue, similar setting.

I will be honest up-front and say that I am hardly an expert but I am learning fast.

I am running 7.04 server, acting as gateway/router/firewall/dhcp-server and thinking about bringing web into it, for a small network.

Then I added Ubuntu-desktop.

Everything is fine w/o desktop installed (as far as I know) yet when I have gdm up and alter anything dealing with network settings both eth0 (internet side), and eth1 (network side) somehow go down.

As posted before, if I disconnect server cat5 for a few minutes problem "goes away".
And the normal #/etc/init.d/networking restart or ifconfig eth* dowm/up do not change a thing.
Not even logout or restart fix it.

The way I found this thread (was at the bug post first then came here) was an error message that I plopped into google:

 
```
#/etc/init.d/networking restart
[...]
DHCPACK from 192.168.1.254
bound to 76.202.224.154 -- renewal in 265 seconds.
RTNETLINK answers: File exists
**run-parts: /etc/network/if-up.d/avahi-autopd exited with return code 2 **
#
```

This does **not** show up when all is well!?

I do not believe it to be a hardware/irq problem as i have tested that theory many times, both changing NIC cards (different brands and models for both "eth's" though I like to stick with intel [never knew I had so many laying around :oops:]) and played around with bios IRQ settings.

One thing is for sure that manually disconnecting server cable is not acceptable.

I guess I will not use gui anymore with server, don't get me wrong CLI and I are friends, just nice to have a splash of color while doing "admin stuff".

I hope this may offer some more information to digest.

If you would like any more information let me know.


**EDIT**: Well I found my mistake, When the server would update from dhclient3 it was conflicting with my networks sub-net, adjusted network side and it seems that all is well. I don't know how i missed that. Live and learn and don't do again.**/EDIT**

---

### Post by LinuxMonk on 2007-08-29
@DWRZ - this may sound like a dumb question, but is your Ubuntu firewall running?  That's what had me scratching my head.  Look in "System" for "Firestarter".

---

