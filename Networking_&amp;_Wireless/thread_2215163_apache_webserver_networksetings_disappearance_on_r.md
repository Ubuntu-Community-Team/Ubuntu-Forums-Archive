---
title: "apache webserver networksetings disappearance on reboot"
date: 2014-04-05
forum: Networking &amp; Wireless
---

### Post by burge38 on 2014-04-05
Hi I recently moved house before I moved my web server was running flawlessly. On unpacking and setting up desk top and servers in the attic and finally running cat5e cables all through house. On completion of the cables I used RJ45 jacks attached to both ends of the 3 cables. I used my Linksys router 4 port switch model BEFVP41 to check the connections. All working full connectivity the router reports. 
On reboot of the ubuntu apache server only eth1 was showing up I used ifconfig this confirmed it the lights on lan port switch and server were on so working
I used this forums ubuntu networking configuration help files 
```
Sudo iplink set dev eth0 down
Sudo dhclient eth0
Sudo ip addr add 192.168.1.14/24 dev eth0
Sudo ip link set dev eth0 up
Sudo ip route add defualt via 192.168.1.1
```
Now the above steps did indeed fix my problem I had full control of server again inside the network and out on eth0 like it was before I moved. So I followed the above procedures replacing eth0 with eth1 sure enough this fixed eth1 problems full connectivity inside and out the network .
The above changes are not saved to a file but rather in real memory so they need to be saved to network config file
So I used
```
Sudo nano /ect/network/interfaces 
```
I added 
```
Auto eth0
Iface eth0 inet dhcp
Auto eth1
Iface eth1 inet dhcp
```
And used ttrl O to save over write file
Now it was very late and I was quite happy with myself so hit the sack not before I powered down desktop and servers got up this morning server has no eth0 or eth1 ifconfig -a shows they are their no ip configured what gives guys tried my dam hardest what have I done wrong 
Regards coolvibes

After again entering the above I got full connectivity on eth0 and eth1 now
but on opening
```
Sudo nano /ect/network/interfaces
```

it changes were
```

auto lo
iface lo inet loopback

the primary network interface
auto eth1
iface eth1 inet dhcp
address 192.168.1.35
netmask 255,255,255,0
gateweay 192.168.1.255

```
also

procedure 4 Sudo ip route add defualt via 192.168.1.1
came back with this error last night and today although up and working here is error


rtnetlink answers: file exists


thanks for looking

---

### Post by burge38 on 2014-04-05
as I thought unexplainable cheers for looking

---

### Post by burge38 on 2014-04-06
wow 121 Linux savvy forum users looked but no explanations strange that be. But not as strange as four of the brightest Linux gurus have LOOKED but none of them has an explanation either I made a mistake and posted it in wrong section, Or my Linux terminology is not up to scratch or may be I missed a post with the answer. at this point a no go away be appreciated kind regards.

---

### Post by lisati on 2014-04-06
I've added [noparse]```
 and 
``` to your first post to aid readability. 

Were your router settings (e.g. reserving IP addresses) changed during your move?


(BTW, the usual rule for bumping unanswered threads on this forum is not to do it more than once every 24 hours)

---

### Post by burge38 on 2014-04-06
funny you should mention that because on first boot at new address only eth1 was active I could communicate through internal network via putty but no web connectivity so this is when I tried to emulate conditions at old address but my problems got worse I started editing the config file got both eth0 and eth1 working flawlessly saved config file reboot now I stuck in this cycle. Every morning manually configure eth0 come out loft log on through putty get eth1 working retype settings in config file ctr o overwrite  restart network.
I used the same dhcp protocol allowing the Linux server to assign ip address in the range of 192.168.1.4 to 192.168.1.104 for my Linux side and just let windows do its normal (bollocks) excuse language , Also can not reach site outside network put in web ip and takes me to router page. yes I port forwarded 80 but have a Linksys befvap router connected to my talk talk router I use as a switch my server connects eth0 to my Linksys that's connected to windows pc and eth1 connects directly to talk talk router

---

### Post by burge38 on 2014-04-06
Sorry Thanks for sorting post out and answering me top user thanks!

---

### Post by burge38 on 2014-04-06
Page 9 getting very interesting

CISCO NETWORKIN ACADEMY PROGRAM
SECOND-YEAR
COMPANION GUIDE
SECOND EDITION

heavy reading 800 odd pages left please someone save me from this

---

### Post by steeldriver on 2014-04-06
It's hard to understand what you're asking - have you fixed ALL the obvious typos in your /etc/network/interfaces file?

Aside from the original incorrect capitalization:

```

netmask 255[COLOR=#ff0000]**,**[/COLOR]255[COLOR=#ff0000]**,**[/COLOR]255[COLOR=#ff0000]**,**[/COLOR]0
gatew[COLOR=#ff0000]**e**[/COLOR]ay 192.168.1.255

```

Why are you even trying to specify address / netmask / gateway after declaring the interface to use **dhcp**? AFAIK it needs to be type **static** if you wat to do that.

---

### Post by burge38 on 2014-04-06
my apologies for the typo but it as all from memory had no script to copy and paste

I did not that's what the file comes back at after reboot

---

### Post by burge38 on 2014-04-06
auto lo
iface lo inet loopback

Auto eth0
Iface eth0 inet dhcp
Auto eth1
Iface eth1 inet dhcp


is what I save file as on reboot changes to one you asked about

---

### Post by burge38 on 2014-04-06
> **steeldriver said:**
> It's hard to understand what you're asking - have you fixed ALL the obvious typos in your /etc/network/interfaces file?

Aside from the original incorrect capitalization:

```

netmask 255[COLOR=#ff0000]**,**[/COLOR]255[COLOR=#ff0000]**,**[/COLOR]255[COLOR=#ff0000]**,**[/COLOR]0
gatew[COLOR=#ff0000]**e**[/COLOR]ay 192.168.1.255

```

Why are you even trying to specify address / netmask / gateway after declaring the interface to use **dhcp**? AFAIK it needs to be type **static** if you wat to do that.

the network is running how I want flawlessly but the config file changes on reboot manually system up all day no downtime connecting inside and out network on reboot back to no network connection and that config file changed again

---

### Post by burge38 on 2014-04-06
this happens on reboot to that file 

sudo nano /etc/network/interfaces# This file describes the network interfaces a$
# and how to activate them. For more information, see interfaces(5).
# The loopback network interface
auto lo
iface lo inet loopback
# The primary network interface
auto eth1
iface eth1 inet dhcp
address 192.168.1.35
netmask 255.255.255.0
gateway 192.168.1.255

---

### Post by burge38 on 2014-04-06
I never typed any of it

could it be loading that file from a saved temp file or something like that

---

### Post by burge38 on 2014-04-06
Last login: Sun Apr  6 09:58:31 2014 from 192.168.1.107
[EMAIL="coolvibes@linuxserver:~$"]coolvibes@linuxserver:~$[/EMAIL] sudo ip link set dev eth1 down
[sudo] password for coolvibes:
[EMAIL="coolvibes@linuxserver:~$"]coolvibes@linuxserver:~$[/EMAIL] sudo dhclient eth1
[EMAIL="coolvibes@linuxserver:~$"]coolvibes@linuxserver:~$[/EMAIL] sudo ip addr add 192.168.1.14/24 dev eth1
[EMAIL="coolvibes@linuxserver:~$"]coolvibes@linuxserver:~$[/EMAIL] sudo ip link set dev eth1 up
[EMAIL="coolvibes@linuxserver:~$"]coolvibes@linuxserver:~$[/EMAIL] sudo ip route add default via 192.168.1.1
RTNETLINK answers: File exists

this is pasted from putty what I use to get the eth0 and eth1 up and runnig

---

### Post by burge38 on 2014-04-06
Last login: Sun Apr  6 12:15:44 2014 from 192.168.1.107
[EMAIL="coolvibes@linuxserver:~$"]coolvibes@linuxserver:~$[/EMAIL] ifconfig
eth0      Link encap:Ethernet  HWaddr 00:04:23:b0:da:f1
          inet addr:192.168.1.6  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::204:23ff:feb0:daf1/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:17483 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2558 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:1856915 (1.8 MB)  TX bytes:733828 (733.8 KB)
eth1      Link encap:Ethernet  HWaddr 00:04:23:b0:da:f0
          inet addr:192.168.1.104  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::204:23ff:feb0:daf0/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:445 errors:0 dropped:0 overruns:0 frame:0
          TX packets:6 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:43003 (43.0 KB)  TX bytes:1012 (1.0 KB)
lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:354 errors:0 dropped:0 overruns:0 frame:0
          TX packets:354 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:31328 (31.3 KB)  TX bytes:31328 (31.3 KB)
 
what network saying now

---

### Post by burge38 on 2014-04-06
changed file /etc/network/interfaces

sudo nano /etc/network/interfaces# This file describes the network interfaces a$
# and how to activate them. For more information, see interfaces(5).
# The loopback network interface
auto lo
iface lo inet loopback
# The primary network interface
auto eth1
iface eth1 inet dhcp
address 192.168.1.35
netmask 255.255.255.0
gateway 192.168.1.255


to

sudo nano /etc/network/interfaces# This file describes the network interfaces a$
# and how to activate them. For more information, see interfaces(5).
# The loopback network interface
auto lo
iface lo inet loopback
# The primary network interface eth0
auto eth0
iface eth0 inet dhcp
# The secondary network interface eth1
auto eth1
iface eth1 inet dhcp


ctrl o save wrote 16 lines

---

### Post by burge38 on 2014-04-06
now want to press enter on this command

[FONT=Courier New]sudo /etc/init.d/networking restart[/FONT] 

but I have to d it all over again any suggestions

---

### Post by burge38 on 2014-04-06
[FONT=Courier New]sudo /etc/init.d/networking restart[/FONT]

results

Last login: Sun Apr  6 12:29:53 2014 from 192.168.1.107
[EMAIL="coolvibes@linuxserver:~$"]coolvibes@linuxserver:~$[/EMAIL] sudo /etc/init.d/networking restart
[sudo] password for coolvibes:
 * Running /etc/init.d/networking restart is deprecated because it may not enable again some interfaces
 * Reconfiguring network interfaces...                                          /etc/network/interfaces:1: misplaced option
ifdown: couldn't read interfaces file "/etc/network/interfaces"
/etc/network/interfaces:1: misplaced option
ifup: couldn't read interfaces file "/etc/network/interfaces"
                                                                         [fail]

---

### Post by burge38 on 2014-04-06
[EMAIL="coolvibes@linuxserver:~$"]coolvibes@linuxserver:~$[/EMAIL] sudo invoke-rc.d networking stop
[sudo] password for coolvibes:
 * Deconfiguring network interfaces...                                                                 /etc/network/interfaces:1: misplaced option
ifdown: couldn't read interfaces file "/etc/network/interfaces"

---

### Post by burge38 on 2014-04-06
[EMAIL="coolvibes@linuxserver:~$"]coolvibes@linuxserver:~$[/EMAIL]  ls -l /etc/network/interfaces
-rw-r--r-- 1 root root 379 Apr  6 12:29 /etc/network/interfaces
[EMAIL="coolvibes@linuxserver:~$"]coolvibes@linuxserver:~$[/EMAIL] cat -e /etc/network/interfaces
sudo nano /etc/network/interfaces# This file describes the network interfaces available on your system$
# and how to activate them. For more information, see interfaces(5).$
$
# The loopback network interface$
auto lo$
iface lo inet loopback$
$
# The primary network interface eth0$
auto eth0$
iface eth0 inet dhcp$
$
# The secondary network interface eth1$
auto eth1$
iface eth1 inet dhcp$
$
$

---

### Post by burge38 on 2014-04-06
# The loopback network interface
auto lo
iface lo inet loopback
 
# The primary network interface
auto eth0
iface eth0 inet static
        address 192.168.2.35
        network 192.168.2.0
        netmask 255.255.255.0        
        broadcast 192.168.2.255
        gateway 192.168.2.1

worked

---

### Post by burge38 on 2014-04-06
epic fail have to clime in loft re enter eth0 and eth 1 to get network back ball ake

---

### Post by burge38 on 2014-04-06
My mistake had wrong ip for putty now it saved eth0 as 192.168.1.2 now web activity now and missing eth1 any ideas

---

### Post by Iowan on 2014-04-06
Punctuation would be a good idea...
Your */etc/network/interfaces* file shows no definition for eth1.

---

### Post by burge38 on 2014-04-07
yes I tried to add eth1 in the config file but my syntax is bad Punctuation is Perfect as I get network back on reboot now ,also the auto dhcp on eth0 gives no web activity its not until I manual add eth1 that I regain outside network activity

# The loopback network interface
 auto lo
 iface lo inet loopback

 # The primary network interface
 auto eth0
 iface eth0 inet dhcp

now every command after the iface eth0 inet dhcp is seen by Linux as a layer for eth0 and reads as an extra set of parameters that Linux dose not except returning error what command do I use to separate it from eht0

---

### Post by steeldriver on 2014-04-07
What additional commands are you trying to add, specifically?

---

### Post by burge38 on 2014-04-07
# The loopback network interface
 auto lo
 iface lo inet loopback


# The primary Secondary interface
 auto eth1
 iface eth1 inet dhcp

---

### Post by Iowan on 2014-04-07
Maybe something like this?:
```
# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto eth0
iface eth0 inet static
address 192.168.2.35
network 192.168.2.0
netmask 255.255.255.0
broadcast 192.168.2.255
gateway 192.168.2.1

# The primary Secondary interface

auto eth1
iface eth1 inet dhcp 
```

---

### Post by burge38 on 2014-04-07
thank you I try now
Perfect case scenario  would be eth0 and static IP ADDRESS 192.168.1.2 (with web connectivity)
And eth1 DHCP (With web connectivity )
And my external ip address to point to my web server not my router, and yes IP Service provided allows port forwarding And I am Port forwarding port 80

---

### Post by burge38 on 2014-04-07
155 packages can be updated.
85 updates are security updates.
Last login: Mon Apr  7 09:14:50 2014 from 192.168.1.109
[EMAIL="coolvibes@linuxserver:~$"]coolvibes@linuxserver:~$[/EMAIL] sudo nano /etc/network/interfaces
[sudo] password for coolvibes:
Sorry, try again.
[sudo] password for coolvibes:
[EMAIL="coolvibes@linuxserver:~$"]coolvibes@linuxserver:~$[/EMAIL] sudo /etc/init.d/networking restart
 * Running /etc/init.d/networking restart is deprecated because it may not enable again some interfaces
 * Reconfiguring network interfaces...                                          RTNETLINK answers: No such process
ssh stop/waiting
ssh start/running, process 5459
ssh stop/waiting
ssh start/running, process 5519

---

### Post by burge38 on 2014-04-07
```
coolvibes@linuxserver:~$ ifconfig -a
eth0      Link encap:Ethernet  HWaddr 00:04:23:b0:da:f1
          inet addr:192.168.2.35  Bcast:192.168.2.255  Mask:255.255.255.0
          inet6 addr: fe80::204:23ff:feb0:daf1/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:35914 errors:0 dropped:0 overruns:0 frame:0
          TX packets:11053 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:4936301 (4.9 MB)  TX bytes:10509722 (10.5 MB)
eth1      Link encap:Ethernet  HWaddr 00:04:23:b0:da:f0
          inet addr:192.168.1.104  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::204:23ff:feb0:daf0/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:28174 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1592 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:2635952 (2.6 MB)  TX bytes:269052 (269.0 KB)
lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:315 errors:0 dropped:0 overruns:0 frame:0
          TX packets:315 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:24500 (24.5 KB)  TX bytes:24500 (24.5 KB)
```

right have web connectivity but eth1 ip stayed the same on reboot of network I try a full system reboot in one sec looking good so far though

---

### Post by burge38 on 2014-04-07
Well Done full reboot getting know activity through static ip via putty so I give it five try again failing that crawl in loft time to check network status

---

### Post by burge38 on 2014-04-07
both eth0 and eth1 are working except I can not reach 192.168.2.35 going to try changing to 192.168.1.4

---

### Post by burge38 on 2014-04-07
This got back network bet lost web connectivity

---

### Post by burge38 on 2014-04-07
[EMAIL="coolvibes@linuxserver:~$"]coolvibes@linuxserver:~$[/EMAIL] ping 8.8.8.8
PING 8.8.8.8 (8.8.8.8) 56(84) bytes of data.
64 bytes from 8.8.8.8: icmp_req=7 ttl=47 time=38.2 ms
64 bytes from 8.8.8.8: icmp_req=8 ttl=47 time=38.6 ms
64 bytes from 8.8.8.8: icmp_req=9 ttl=47 time=38.1 ms
64 bytes from 8.8.8.8: icmp_req=10 ttl=47 time=38.1 ms
64 bytes from 8.8.8.8: icmp_req=11 ttl=47 time=37.9 ms
64 bytes from 8.8.8.8: icmp_req=12 ttl=47 time=38.8 ms
64 bytes from 8.8.8.8: icmp_req=13 ttl=47 time=39.8 ms
64 bytes from 8.8.8.8: icmp_req=14 ttl=47 time=38.6 ms
^X^C
--- 8.8.8.8 ping statistics ---
19 packets transmitted, 8 received, 57% packet loss, time 18091ms
rtt min/avg/max/mdev = 37.995/38.573/39.891/0.583 ms

---

### Post by burge38 on 2014-04-07
[EMAIL="coolvibes@linuxserver:~$"]coolvibes@linuxserver:~$[/EMAIL] sudo apt-get update
[sudo] password for coolvibes:
0% [Connecting to gb.archive.ubuntu.com (194.169.254.10)] [Connecting to [EMAIL="securi^Ccoolvibes@linuxserver:~$"]securi^Ccoolvibes@linuxserver:~$[/EMAIL]

it just hangs

---

### Post by burge38 on 2014-04-07
# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto eth0
iface eth0 inet static
address 192.168.1.2
network 192.168.2.0
netmask 255.255.255.0
broadcast 192.168.2.255
gateway 192.168.1.1


auto eth1#
 The primary Secondary interface
this gave me full network control both ways inside and out the network just doing full reboot to see if its fixed cheers brother well on right track anyway thank you so much for your help top user I post a fixed on top post when I confirm it cheers again in advance .

---

