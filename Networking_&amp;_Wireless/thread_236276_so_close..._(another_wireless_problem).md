---
title: "so close... (another wireless problem)"
date: 2006-08-14
forum: Networking &amp; Wireless
---

### Post by ImplicitProcrastination on 2006-08-14
Hey ubuntu! I missed you guys.

After having taken a month long hiatus from using linux I have returned and am spending the morning working on a familiar problem. If somebody could help me out that would be awesome.

Here's the deal: I am connecting to the internet through my uncle's wireless router (it's a Blitzz Netgear BWA711 I think) with my Atheros 808.2 (or some such number for a model) wireless card which is built into my computer.  In the past I've had terrible luck trying to do this, but this morning everything except for my repositories seem to work (thus I can make this post).  I'm glad everything works except that but I'm really itching to update and run automatix.

I gathered from reading other threads that my problem may have something to do with the wireless router blocking specific ports, though I'm not sure how to test this hypothesis.  Also I've gathered that my problem might have something to do with DNS settings which I've toyed with before trying to get my internet to work, but never understood where those numbers come from.

Anyway here's some random stuff that I hope may be relevant:

Me trying to run an update:

```
rockstar@rockstar-laptop:~$ sudo apt-get update
Password:
Err http://security.ubuntu.com dapper-security Release.gpg
  Cannot initiate the connection to security.ubuntu.com:80 (0.0.32.144). - connect (22 Invalid argument)
Ign http://security.ubuntu.com dapper-security Release
Ign http://security.ubuntu.com dapper-security/main Packages
Ign http://security.ubuntu.com dapper-security/main Sources
Ign http://security.ubuntu.com dapper-security/universe Packages
Ign http://security.ubuntu.com dapper-security/universe Sources
Err http://security.ubuntu.com dapper-security/main Packages
  Cannot initiate the connection to security.ubuntu.com:80 (0.0.32.144). - connect (22 Invalid argument)
Err http://security.ubuntu.com dapper-security/main Sources
  Cannot initiate the connection to security.ubuntu.com:80 (0.0.32.144). - connect (22 Invalid argument)
Err http://security.ubuntu.com dapper-security/universe Packages
  Cannot initiate the connection to security.ubuntu.com:80 (0.0.32.144). - connect (22 Invalid argument)
Err http://security.ubuntu.com dapper-security/universe Sources
  Cannot initiate the connection to security.ubuntu.com:80 (0.0.32.144). - connect (22 Invalid argument)
Get:1 http://www.getautomatix.com kubuntu Release.gpg [189B]
Hit http://www.getautomatix.com kubuntu Release
Ign http://us.archive.ubuntu.com dapper Release.gpg
Ign http://us.archive.ubuntu.com dapper-updates Release.gpg
Hit http://www.getautomatix.com kubuntu/main Packages
Ign http://us.archive.ubuntu.com dapper-backports Release.gpg
Ign http://us.archive.ubuntu.com dapper Release
Ign http://us.archive.ubuntu.com dapper-updates Release
Ign http://us.archive.ubuntu.com dapper-backports Release
Ign http://us.archive.ubuntu.com dapper/main Packages
Ign http://us.archive.ubuntu.com dapper/restricted Packages
Ign http://us.archive.ubuntu.com dapper/main Sources
Ign http://us.archive.ubuntu.com dapper/restricted Sources
Ign http://us.archive.ubuntu.com dapper/universe Packages
Ign http://us.archive.ubuntu.com dapper/universe Sources
Ign http://us.archive.ubuntu.com dapper-updates/main Packages
Ign http://us.archive.ubuntu.com dapper-updates/restricted Packages
Ign http://us.archive.ubuntu.com dapper-updates/main Sources
Ign http://us.archive.ubuntu.com dapper-updates/restricted Sources
Ign http://us.archive.ubuntu.com dapper-backports/main Packages
Ign http://us.archive.ubuntu.com dapper-backports/restricted Packages
Ign http://us.archive.ubuntu.com dapper-backports/universe Packages
Ign http://us.archive.ubuntu.com dapper-backports/multiverse Packages
Ign http://us.archive.ubuntu.com dapper-backports/main Sources
Ign http://us.archive.ubuntu.com dapper-backports/restricted Sources
Ign http://us.archive.ubuntu.com dapper-backports/universe Sources
Ign http://us.archive.ubuntu.com dapper-backports/multiverse Sources
Err http://us.archive.ubuntu.com dapper/main Packages
  404 Not Found
Err http://us.archive.ubuntu.com dapper/restricted Packages
  404 Not Found
Err http://us.archive.ubuntu.com dapper/main Sources
  404 Not Found
Err http://us.archive.ubuntu.com dapper/restricted Sources
  404 Not Found
Err http://us.archive.ubuntu.com dapper/universe Packages
  404 Not Found
Err http://us.archive.ubuntu.com dapper/universe Sources
  404 Not Found
Err http://us.archive.ubuntu.com dapper-updates/main Packages
  404 Not Found
Err http://us.archive.ubuntu.com dapper-updates/restricted Packages
  404 Not Found
Err http://us.archive.ubuntu.com dapper-updates/main Sources
  404 Not Found
Err http://us.archive.ubuntu.com dapper-updates/restricted Sources
  404 Not Found
Err http://us.archive.ubuntu.com dapper-backports/main Packages
  404 Not Found
Err http://us.archive.ubuntu.com dapper-backports/restricted Packages
  404 Not Found
Err http://us.archive.ubuntu.com dapper-backports/universe Packages
  404 Not Found
Err http://us.archive.ubuntu.com dapper-backports/multiverse Packages
  404 Not Found
Err http://us.archive.ubuntu.com dapper-backports/main Sources
  404 Not Found
Err http://us.archive.ubuntu.com dapper-backports/restricted Sources
  404 Not Found
Err http://us.archive.ubuntu.com dapper-backports/universe Sources
  404 Not Found
Err http://us.archive.ubuntu.com dapper-backports/multiverse Sources
  404 Not Found
Fetched 1B in 1s (1B/s)
Failed to fetch http://security.ubuntu.com/ubuntu/dists/dapper-security/Release.gpg  Cannot initiate the connection to security.ubuntu.com:80 (0.0.32.144). - connect (22 Invalid argument)
Failed to fetch http://security.ubuntu.com/ubuntu/dists/dapper-security/main/binary-i386/Packages.gz  Cannot initiate the connection to security.ubuntu.com:80 (0.0.32.144). - connect (22 Invalid argument)
Failed to fetch http://security.ubuntu.com/ubuntu/dists/dapper-security/main/source/Sources.gz  Cannot initiate the connection to security.ubuntu.com:80 (0.0.32.144). - connect (22 Invalid argument)
Failed to fetch http://security.ubuntu.com/ubuntu/dists/dapper-security/universe/binary-i386/Packages.gz  Cannot initiate the connection to security.ubuntu.com:80 (0.0.32.144). - connect (22 Invalid argument)
Failed to fetch http://security.ubuntu.com/ubuntu/dists/dapper-security/universe/source/Sources.gz  Cannot initiate the connection to security.ubuntu.com:80 (0.0.32.144). - connect (22 Invalid argument)
Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/dapper/main/binary-i386/Packages.gz  404 Not Found
Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/dapper/restricted/binary-i386/Packages.gz  404 Not Found
Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/dapper/main/source/Sources.gz  404 Not Found
Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/dapper/restricted/source/Sources.gz  404 Not Found
Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/dapper/universe/binary-i386/Packages.gz  404 Not Found
Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/dapper/universe/source/Sources.gz  404 Not Found
Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/dapper-updates/main/binary-i386/Packages.gz  404 Not Found
Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/dapper-updates/restricted/binary-i386/Packages.gz  404 Not Found
Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/dapper-updates/main/source/Sources.gz  404 Not Found
Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/dapper-updates/restricted/source/Sources.gz  404 Not Found
Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/dapper-backports/main/binary-i386/Packages.gz  404 Not Found
Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/dapper-backports/restricted/binary-i386/Packages.gz  404 Not Found
Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/dapper-backports/universe/binary-i386/Packages.gz  404 Not Found
Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/dapper-backports/multiverse/binary-i386/Packages.gz  404 Not Found
Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/dapper-backports/main/source/Sources.gz  404 Not Found
Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/dapper-backports/restricted/source/Sources.gz  404 Not Found
Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/dapper-backports/universe/source/Sources.gz  404 Not Found
Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/dapper-backports/multiverse/source/Sources.gz  404 Not Found
Reading package lists... Done
E: Some index files failed to download, they have been ignored, or old ones used instead.

```

my sources.list:

```
rockstar@rockstar-laptop:~$ cat /etc/apt/sources.list

# Line commented out by installer because it failed to verify:
deb http://us.archive.ubuntu.com/ubuntu/ dapper main restricted
# Line commented out by installer because it failed to verify:
deb-src http://us.archive.ubuntu.com/ubuntu/ dapper main restricted

## Major bug fix updates produced after the final release of the
## distribution.
# Line commented out by installer because it failed to verify:
deb http://us.archive.ubuntu.com/ubuntu/ dapper-updates main restricted
# Line commented out by installer because it failed to verify:
deb-src http://us.archive.ubuntu.com/ubuntu/ dapper-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://us.archive.ubuntu.com/ubuntu/ dapper universe
deb-src http://us.archive.ubuntu.com/ubuntu/ dapper universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb http://us.archive.ubuntu.com/ubuntu/ dapper-backports main restricted universe multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ dapper-backports main restricted universe multiverse

# Line commented out by installer because it failed to verify:
deb http://security.ubuntu.com/ubuntu dapper-security main
# Line commented out by installer because it failed to verify:
deb-src http://security.ubuntu.com/ubuntu dapper-security main
deb http://security.ubuntu.com/ubuntu dapper-security universe
deb-src http://security.ubuntu.com/ubuntu dapper-security universe

deb http://www.getautomatix.com/apt kubuntu main

```

ifconfig:

```
rockstar@rockstar-laptop:~$ ifconfig
ath0      Link encap:Ethernet  HWaddr 00:90:96:C5:B1:9C
          inet addr:192.168.1.4  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::290:96ff:fec5:b19c/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:14084 errors:735 dropped:0 overruns:0 frame:735
          TX packets:12664 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:200
          RX bytes:13363537 (12.7 MiB)  TX bytes:1486999 (1.4 MiB)
          Interrupt:209 Memory:dcb80000-dcb90000

eth0      Link encap:Ethernet  HWaddr 00:02:3F:D6:7E:D3
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:201 Base address:0xe800

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:3 errors:0 dropped:0 overruns:0 frame:0
          TX packets:3 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:172 (172.0 b)  TX bytes:172 (172.0 b)

```

iwconfig:

```
rockstar@rockstar-laptop:~$ iwconfig
lo        no wireless extensions.

ath0      IEEE 802.11g  ESSID:"BWA711"
          Mode:Managed  Frequency:2.462 GHz  Access Point: 00:20:ED:08:FA:A1
          Bit Rate:54 Mb/s   Tx-Power:18 dBm   Sensitivity=0/3
          Retry:off   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=32/94  Signal level=-63 dBm  Noise level=-95 dBm
          Rx invalid nwid:11  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

eth0      no wireless extensions.

sit0      no wireless extensions.


```

lspci:

```
rockstar@rockstar-laptop:~$ lspci
0000:00:00.0 Host bridge: ATI Technologies Inc RS300 Host Bridge (rev 02)
0000:00:01.0 PCI bridge: ATI Technologies Inc Radeon 9100 IGP AGP Bridge
0000:00:13.0 USB Controller: ATI Technologies Inc OHCI USB Controller #1 (rev 01)
0000:00:13.1 USB Controller: ATI Technologies Inc OHCI USB Controller #2 (rev 01)
0000:00:13.2 USB Controller: ATI Technologies Inc EHCI USB Controller (rev 01)
0000:00:14.0 SMBus: ATI Technologies Inc ATI SMBus (rev 18)
0000:00:14.1 IDE interface: ATI Technologies Inc ATI Dual Channel Bus Master PCI IDE Controller
0000:00:14.3 ISA bridge: ATI Technologies Inc: Unknown device 434c
0000:00:14.4 PCI bridge: ATI Technologies Inc: Unknown device 4342
0000:00:14.5 Multimedia audio controller: ATI Technologies Inc IXP150 AC'97 Audio Controller
0000:00:14.6 Modem: ATI Technologies Inc IXP AC'97 Modem (rev 01)
0000:01:05.0 VGA compatible controller: ATI Technologies Inc RS300M AGP [Radeon Mobility 9100IGP]
0000:02:00.0 FireWire (IEEE 1394): Texas Instruments TSB43AB21 IEEE-1394a-2000 Controller (PHY/Link)
0000:02:02.0 Ethernet controller: Atheros Communications, Inc. AR5212 802.11abg NIC (rev 01)
0000:02:03.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
0000:02:04.0 CardBus bridge: ENE Technology Inc CB-710/2/4 Cardbus Controller
0000:02:04.1 FLASH memory: ENE Technology Inc ENE PCI Memory Stick Card Reader Controller
0000:02:04.2 0805: ENE Technology Inc ENE PCI Secure Digital Card Reader Controller
0000:02:04.3 FLASH memory: ENE Technology Inc: Unknown device 0520

```

/etc/apt/apt.conf:

```

Acquire::http::Proxy "false";

```

finally /etc/network/interfaces:

```

rockstar@rockstar-laptop:/etc/network$ cat interfaces
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


That's all I can think of to offer you, I hate to have to ask for personalized assistance but I've put in ample time searching the forums/documentation/etc. about this subject and I don't want to go trying to fix it in random ways I'm not sure about when the solution doesn't seem that far away.

So if anybody would be willing to help by pointing me in the right direction I'd greatly appreciate it. I'll be checking this post often this morning (August 14 2006).

Thanks alot,
y'all are the rockinest.

---

### Post by bensexson on 2006-08-14
The problem is not your wireless.  That is working.  Post the output from cat /etc/resolve.conf and ping security.ubuntu.com.

---

### Post by ImplicitProcrastination on 2006-08-14
cat /etc/resolve.conf produced:

```

nameserver 192.168.1.1

```

ping security.ubuntu.com produced nothing (strange) but archive came through:

```

rockstar@rockstar-laptop:/etc$ ping -c 5 security.ubuntu.com
connect: Invalid argument
rockstar@rockstar-laptop:/etc$ ping -c 5 archive.ubuntu.com
PING archive.ubuntu.com (82.211.81.182) 56(84) bytes of data.
64 bytes from archive.ubuntu.com (82.211.81.182): icmp_seq=1 ttl=45 time=114 ms
64 bytes from archive.ubuntu.com (82.211.81.182): icmp_seq=2 ttl=45 time=114 ms
64 bytes from archive.ubuntu.com (82.211.81.182): icmp_seq=3 ttl=45 time=119 ms
64 bytes from archive.ubuntu.com (82.211.81.182): icmp_seq=4 ttl=45 time=114 ms
64 bytes from archive.ubuntu.com (82.211.81.182): icmp_seq=5 ttl=45 time=119 ms

--- archive.ubuntu.com ping statistics ---
5 packets transmitted, 5 received, 0% packet loss, time 4015ms
rtt min/avg/max/mdev = 114.271/116.600/119.944/2.557 ms

```

Very strange that one of the servers will connect but the other won't (invald argument?).  

If I were to guess at a solution to this problem I'd say it has to do with altering resolve.conf...

but that's why I'm asking you guys for help.

Thanks for the prompt response.

---

### Post by bensexson on 2006-08-15
I am assuming that 192.168.1.1 is the IP address of your router.  I would check the DNS servers your router is using and add them to your resolv.conf before 192.168.1.1

---

### Post by ImplicitProcrastination on 2006-08-15
interesting...

how do i go about checking the DNS settings? this isn't the first time i've been given that piece of advice before but i've been told they come from my ISP (which is not helpful).

I just tried connecting through the router wired, I still get enough internet to type this message but have yet to successfully get an update.

I'm looking into the services of [www.opendns.com](www.opendns.com), do you think that will help me?

---

### Post by ImplicitProcrastination on 2006-08-15
I configured my router to use the Static IP addresses that are opendns.com and added them as nameservers to resolv.conf.

no luck with that.

---

### Post by bensexson on 2006-08-16
You will need to check in your router for the DNS entries.  It seems like the issue is a slow DNS resolution.

---

### Post by ImplicitProcrastination on 2006-08-18
By in your router do you mean typing the ip address in a browser windows and editing the settings? That's what I did.
Slow DNS resolution? How would that cause my apt-get not to work?


Although I disabled the the opendns servers because I think it was slowing down my bittorrents on a windows box in the house.

Which leads me to another unrelated consideration, my uncle always plays online poker but when I download bittorrents this seems to cause him lag, even though I know I'm not approaching the 3 mbps download capabilities that I tested last night. I'd really love to leave my downloads on always. Any ideas?

---

### Post by lupine_nickt on 2006-08-18
Bittorrents will saturate your upload, causing TCP connections (in which, for every packet you receive, you must send a response) to be slowed down.

You have two possible solutions - if your router supports QoS, then you can tell it to prioritise "ACK" packets, so they don't get delayed. Alternatively, you can tell your bittorrent client to behave itself, and restrict it's upload to (say) 50-80% of your line's upload capacity. 

As for your apt-get problem... if you look at the error message:-
```

Err http://security.ubuntu.com dapper-security/main Packages
  Cannot initiate the connection to security.ubuntu.com:80 (**0.0.32.144**). - connect (22 Invalid argument)

```

The bit in bold is the IP address that your DNS server (or rather, your ISP's DNS server) is reporting for 'security.ubuntu.com'. It's **wrong** - that address doesn't exist, and never will (it's invalid). Hence the error. This could be a rather poorly done attempt at DNS cache poisoning, but is more likely to just be incompetence at your ISP. Contact them and tell them to flush their cache. 

As a temporary solution, you can add an entry in your /etc/hosts file with the *correct* IP address of 'security.ubuntu.com' - for me, that's 195.248.90.23, so the line to add would be:-
```
195.248.90.23 security.ubuntu.com
``` but that's only a quick 'n dirty hack.

In case you don't trust the IP address I've given you (which would be wise!), here's how to find it for yourself:-

1. run 'whois ubuntu.com', and look for this section:-
```

 Domain servers in listed order:
    NS0.BLACKCATNETWORKS.CO.UK
    NS1.BLACKCATNETWORKS.CO.UK
    NS.UBUNTU.COM   82.211.81.173

```

Next, 'apt-get install dig', and run 'dig @<nameserver> security.ubuntu.com A |grep security'

Et voila, your problem is solved :)

xF,

...Nick

---

### Post by ImplicitProcrastination on 2006-08-19
That's interesting, I thank your for your response.

I can see no reason why anybody would want into my computer, the installation is fresh. The only thing I could think of would be the that somebody is using it for kiddie porn or something.

This should fix the error with security.ubuntu.com but what about all the other servers it's failing to connect to? My ISP is roadrunner, is it possible that a corporation like Time Warner would fail to take care of its cache?

I'll tinker with your suggestion and let you guys know what's up.

I need to buy a mac...

---

### Post by lupine_nickt on 2006-08-19
The large companies are generally the worst for support/technical stuff, as it's all too easy to assume someone else is taking care of x, y or z. Get on at them and give 'em Hel ;)

As for the DNS cache poisoning... it's an ISP-level thing and would affect all customers of that ISP, so not directed towards a specific person.

xF,

...Nick

---

### Post by ImplicitProcrastination on 2006-08-21
I don't seem to have whois on my computer, is there another way to figure out the ip addresses to use? by pinging i was able to figure out us.archive.ubuntu.com but security.ubuntu.com remains an enigma.

Not that I don't trust you, well yea, that's exactly it. (Although the only reason is because you pointed that out, I'd like to think I have enough sense to have known that alone) :)

Also what does dig do?

Suppose I move and connect from somewhere else or the cache finally gets cleared, will that mess with me and will it be important to undo what I've done?

Thanks alot, I realize at this point I'm merely indulging my curiosity.

---

### Post by lupine_nickt on 2006-08-21
Just 'sudo apt-get install whois' and 'sudo apt-get install dig', and you're set to go.

WHOIS gets details about the domain name in question from the registrar (e.g. Nominet, ARIN, RIPE, etc). Dig queries a *specific* DNS server for a specific record - in the example, that output is then piped (using the "|" operator) to grep (search for lines containing) the important data. 

If you need ammo against your ISP, one thing you could do is to compare the output of 'dig' for your ISP nameserver (just your router address normally works for this), against the 'authoritative' nameserver (the one given in the whois record). If they differ, then your ISP is definitely doing something wrong.

Anyway, because your computer will always check your /etc/hosts file before it checks DNS (history lesson alert! - back before DNS was created, name resolution was done in exactly this manner - everyone had a hosts file that they kept updated from a central server. Time-consuming and wasteful), if Ubuntu change their IP addresses (for whatever reason - it happens more often than you might think), then you'll be unable to reach the server, so you'll need to update your hosts file. For the same reason, once you've got the DNS problem sorted with your ISP, you'd be wise to remove the entries.

HTH...

xF,

...Nick

---

### Post by ImplicitProcrastination on 2006-08-21
SUCCESS!

Thanks very much dude.

---

