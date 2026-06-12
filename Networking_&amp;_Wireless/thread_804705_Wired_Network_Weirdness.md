---
title: "Wired Network Weirdness"
date: 2008-05-23
forum: Networking &amp; Wireless
---

### Post by mcdougrs on 2008-05-23
Hi everyone,

After spending hours trying to figure out my network issue in google and browsing MANY forums, I thought maybe I should come here and ask you guys. 

First I have a Broadcom Netxtreme 5751 Wired Card in a Dell Optiplex GX620 and FRESH install of Ubuntu 8.04.

The weirdness is that I get an IP, and I can ping IPs in my subnet (10.11.4.x) however when I try go to the web or anyplace other than 10.11.4.x I can't get out. And I have already disabled IPv6 via the blacklist AND in the aliases parts in modprobe.d

Any help would be GREAT,
Ryan

PS
I'm not a complete linux n00b but I am definately an Ubuntu newbie.

---

### Post by mapes12 on 2008-05-23
Hi

The output to these would be helpful:

```
sudu lshw -C network
```
```
ifconfig
```
```
sudo dhclient
```
```
cat /etc/resolv.conf
```

---

### Post by mcdougrs on 2008-05-23
I didn't want you to think I wasn't checking this thread, but this is on a work machine and I won't be back to work until Wednesday (may 28th) and I will post those results ASAP.

Thanx for the reply

---

### Post by mcdougrs on 2008-05-28
Here is the output from the commands you asked about. Thanx again for at least looking at this. PS I did a brand new install again so IPv6 stuff is on at the time of this post and for the commands below. If you want me to turn them off again just let me kow.

```
sudu lshw -C network
*-network
       description: Ethernet interface
       product: NetXtreme BCM5751 Gigabit Ethernet PCI Express
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:01:00.0
       logical name: eth0
       version: 01
       serial: 00:18:8b:5c:28:60
       size: 100MB/s
       capacity: 1GB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm vpd msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=tg3 driverversion=3.86 duplex=full firmware=5751-v3.44a ip=10.11.4.40 latency=0 link=yes module=tg3 multicast=yes port=twisted pair speed=100MB/s

```
```
ifconfig
eth0      Link encap:Ethernet  HWaddr 00:18:8b:5c:28:60  
          inet addr:10.11.4.40  Bcast:10.11.7.255  Mask:255.255.252.0
          inet6 addr: fe80::218:8bff:fe5c:2860/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:2466 errors:0 dropped:0 overruns:0 frame:0
          TX packets:42 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1067145 (1.0 MB)  TX bytes:6570 (6.4 KB)
          Interrupt:16 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:986 errors:0 dropped:0 overruns:0 frame:0
          TX packets:986 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:49300 (48.1 KB)  TX bytes:49300 (48.1 KB)
```
```
sudo dhclient
Internet Systems Consortium DHCP Client V3.0.6
Copyright 2004-2007 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

Listening on LPF/eth0/00:18:8b:5c:28:60
Sending on   LPF/eth0/00:18:8b:5c:28:60
Sending on   Socket/fallback
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 4
DHCPOFFER of 10.11.4.40 from 10.11.0.2
DHCPREQUEST of 10.11.4.40 on eth0 to 255.255.255.255 port 67
DHCPACK of 10.11.4.40 from 10.11.0.2
SIOCADDRT: No such process
bound to 10.11.4.40 -- renewal in 39561 seconds.

```
```
cat /etc/resolv.conf
search fulton.cnyric.org
nameserver 10.11.0.2
nameserver 10.10.0.3
nameserver 10.10.0.27

```

---

### Post by mapes12 on 2008-05-28
I can't see anything wrong with those outputs.
> but this is on a work machineAre you positive that the network administrator (I'm making a big assumption it isn't you. Forgive me if I'm wrong) has the network configured for internet access?

Can you ping your DHCP router service?

```
ping -c4 10.11.0.2
```

Can you ping Google?

```
ping -c4 www.google.com
```

---

### Post by mapes12 on 2008-05-28
I've just realised something:

> Mask:255.255.252.0

Your IP address is a class A private address. The subnetmask to which should be 255.0.0.0

Class B would be mask 255.255.0.0

Class C would be mask 255.255.255.0

So, your subnetmask is none standard. It might not be the problem but it's the only irregularity I can see.

EDIT:..............on the other hand, based on the analogy of your subnetmask being like an area code on a telephone exchange, it could be that packet header handlers somewhere are seeing  a class A prefix and assuming a standard subnetmask of 255.0.0.0  If this were the case you may be able to "see" the internet but the internet would be returning your traffic to an incorrect address?? Just a thought.

---

### Post by mcdougrs on 2008-05-28
Hello,

You were correct in your assumption that I am not the network administrator. The network is configured for internet access though. The same machine with windows XP on it can get out to the internet ok with those settings configured the same via dhcp. As far as the subnet mask goes, the only answer I can offer for that is... We split the class A in to serveral seperate subnets so that we can use different subnets for different purposes (i.e. servers on one subet, printers on another, dhcp clients on anther one etc etc). That of which I did not set up.

Yeah with the first ping command gives me "connect: Network is unreachable" and the second gives me a "ping: unknown host www.google.com" Which seems logical seeing as how it can't get out to the DNS server. But why is that WindowsXP can handle the DHCP settings fine but linux can't (retorical question, I don't know if there is an answer for that). Should I try and set my IP config up manually and give it a different subnet mask? If so would I use the 255.0.0.0 that you mention above?

The one REALLY confusing part is that if  I use a live CD distro of SLAX (not sure which version right now) I can access the internet and the rest of the network just fine.

Thanx again for your help.

---

### Post by mapes12 on 2008-05-28
> "connect: Network is unreachable"So are we saying the ping to the router failed?

---

### Post by mcdougrs on 2008-05-28
Well... I cannot ping the DNS server. I can however ping any other active PC in my subnet. I can get to 0.2 because that is also the DHCP server. So needless to say I'm quite confused.

---

### Post by mapes12 on 2008-05-28
> I cannot ping the DNS serverI appreciate your comments about the network being configured for internet access but as you know, no DNS service = no internet service.> I can however ping any other active PC in my subnetThis is expected since these machines are on the same "dialing code/local telephone exchange". Please excuse my analogy but it's the only way I get this stuff straight.

I am still of the opinion that the network subnetmask none standard configuration is screwing something up. Per previous posts, your client machine does not exhibit any configuration issues.

Are there any other Linux machines in your LAN that work in this network configuration?

---

### Post by Iowan on 2008-05-28
I confuse easily, so forgive me if I type something stupid...
The 10.11.4.40 address in a different subnet than the 10.11.0.2 DHCP server or any of the nameservers.  CIDR addressing shouldn't care about nonstandard subnet mask, but does it cause problems having nameservers in different subnet?  Is there a gateway address specified somewhere?  If the other machines on your net are using that subnet mask, you'd lose contact with them if you changed it.  Do the machines that work with these settings use those nameservers?

---

### Post by mcdougrs on 2008-05-29
> Are there any other Linux machines in your LAN that work in this network configuration?

I can get a live CD version of SLAX to be able to access the internet on this same machine. Would you like me to see about running those same commands on that version of Linux?

---

### Post by mcdougrs on 2008-05-29
> **Iowan said:**
> Is there a gateway address specified somewhere?  If the other machines on your net are using that subnet mask, you'd lose contact with them if you changed it.  Do the machines that work with these settings use those nameservers?

I don't know the answers to the beginning part of your post but let me try to answer this quoted part.

The one thing that I NEVER did see configured anywhere, was a default gateway. Which is configured on Windows boxes via DHCP. I kinda thought that was odd but have no idea on how to configure that manually.

As far as the machines that work using those name servers I would assume they do but don't really kow how I would go about checking which name server they use. Unless I am misunderstanding your question... The only other way I can answer that is that yes the other machines (that do get internet service, also windwos XP) are configured to use those same DNS IPs.

---

### Post by mcdougrs on 2008-05-29
Something else wierd I noticed... when I go to System -> Administration -> Network Tools when I select eth0 it shows me all the info that it has on the device. However, when I click on the Configure button it says 
> 
The interface does not exist

Check that it is correctly typed and that it is correctly supported by your system

Seems odd to me seeing as how all the other commands have shown that it is getting an address at least. Just thought I'd mention it.

---

### Post by mcdougrs on 2008-05-30
Ok so it seems as though theres an issue with the new tg3 driver and my card... I just downloaded the new version of slax (the other one was just a disc a co-worker had laying around and happened to work I think it was slax version 2.something)

If that is the case, I wouldn't even be able to snag that old driver from that CD would I? It most likely would have been compiled for an older kernal?? I guess I can see what else I can find. 

I appreciated you guys' help on this!!!

---

### Post by mcdougrs on 2008-05-30
Ok so I just did a make of the driver available for DL at broadcom's site and it still doesn't work. just an fyi

---

