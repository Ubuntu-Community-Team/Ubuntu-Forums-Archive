---
title: "unable to ping my router? arooo?"
date: 2005-04-23
forum: Networking &amp; Wireless
---

### Post by superwesman on 2005-04-23
hi...

I just installed this ubuntu dealie and all seemed to be going well until it got to the network configuration - it claimed inability to communicate with the dhcp server ...

my setup:
dsl modem -> linksys router (wired + wireless G) 

from that I've got this windows PC and the linux machine that had gentoo on it yesterday and worked fine (except that mozilla kept crashing) .... my goal is to have a static ip address (so I can port forward into it for ftp and ssh) but I've also tried dynamic 

when I try to ping my router or modem (192.168.1.1 and 192.168.0.1, respectively) I get a 
```

connect: Network is unreachable
```

ifconfig reveals something mysterious (just a snippet because I'm typing this by hand - bla)

```
eth0        Link encap:Ethernet   HWaddr  13:01:13:01:13:01
               inet6 addr: fe80::1101:13ff:fe01:1301/64 Scope:Link
               UP BROADCAST RUNNING MULTICAST  MTU:1500 Metric:1
         


```

why is there no ip address? I'm not getting my dhcp on .... hmmm....

my /etc/network/interfaces is 

```
auto lo
iface lo inet loopback

mapping hotplug
     script grep
     map eth0

auto eth0

iface eth0 inet dhcp

```

---------------

I also tried using this (after the "auto eth0" above)

```
iface eth0 inet static
address 192.168.1.6                              # i picked this one
netmask 255.255.255.0                         # my router told me this one
network 192.168.0.1                              # i read this one on the internet
broadcast 192.168.255.255                   # my modem told me this one
gateway 192.168.1.1                              # my router told me this one too

```

and still no dice

here are my assumptions and thoughts so far...

the card works - it worked in both windows and gentoo yesterday
the router and modem work - i'm posting this message - pud<proof>ding
because I can't ping even my router, I think this is a hardware config thing, which is my weak point in all of this (well, one of them)

when I use the Interweb y Network-o > Network Settings in the Control Center, I can't enable the device eth0 if I have it set to dhcp, if I set it to static (in the /etc/networks/interfaces)  it will enable, but I still can't do anything...

a 'sudo ifup eth0' reveals 
ifup: interface eth0 already configured

'sudo ifdown eth0' hits me with a ...

<copyright bla bla>V3.01,2004,blabla

sit0: unkown hardware address type 776
sit0: unkown hardware address type 776
Listening on LPF/eth0/13:01:13:01:13:01
Sending on LPF/eth0/13:01:13:01:13:01
Sending on Socket/fallback

(this is when I'm set to a dhcp thing-a-majigger)

now, I switch to the static IP I mentioned above and 'sudo ifup eth0' then ping the router ....

PING 192.168.1.1 (192.168.1.1) 56(84) bytes of data
From 192.168.1.6 icmp_seq=2 Destination Host Unreachable

etc...

'sudo /etc/init.d/networking restart' will typically take some time (maybe a minute or 2 or 3) and tell me OK (this particularly time - I'm running through this as I type - it was very quick ..hmmmmm) but still my inability to ping is stopping me dead in the proverbial tracks...

if I ifconfig up eth0 it things for a while then...

eth0: Host name lookup failure...

so, as you may have guessed, I'm desperate here - I feel like I've tried everything that would have even the remotest possibility of being related to the issue and I'm still stuck - can anybody out there help out? if you do, it will be christmas for you and festivus for the rest of us - thanks
-w

---

### Post by mudra on 2005-04-23
I have set up a similar system here at my place. To start of with I avoided using DHCP so I could understand the process.

When you have booted up, go to a konsole and try the following:-

su
<password>
ifconfig eth0 192.168.0.101 (or any address on the correct subnet mask that is not already being used)
route add default gw 192.168.0.1 (or address of gateway to internet)

then try pinging your router / modem.

They appear to be on different sub-nets, so I don't know if that might be an issue

eg. 192.168.0.1. and 192,168.1.1 perhaps your subnet should be 255.255.0.0 ?

Hope some of this ramble has helped you out.

Mudra.

---

### Post by alastair on 2005-04-23
[QUOTE=superwesman]
```
iface eth0 inet static
address 192.168.1.6                              # i picked this one
netmask 255.255.255.0                         # my router told me this one
network 192.168.0.1                              # i read this one on the internet
broadcast 192.168.255.255                   # my modem told me this one
gateway 192.168.1.1                              # my router told me this one too

```
[/QUOTE]

You can't have the "network" being a different subnet like the above (to your IP).

Your network should be 192.168.1.0 above.

The broadcast should also be 192.168.1.255.

---

