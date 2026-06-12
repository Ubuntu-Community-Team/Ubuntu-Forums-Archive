---
title: "network issues"
date: 2013-10-17
forum: Networking &amp; Wireless
---

### Post by Kanefa on 2013-10-17
I've put together a small lab of salvaged computers running Lubuntu at my University.  Everything worked and I went on vacation.  When I got back I noticed none of the Lubuntu computers could connect to the internet, but were on the local network.  My personal Mac and the rest of the Windows computers were unaffected.  I'm not so sure how to begin tracking down the problem.  Could someone suggestion some commands I should run that might get to the bottom of this?

---

### Post by TheFu on 2013-10-17
[http://blog.jdpfu.com/2013/03/01/linux-troubleshooting-101-networking](http://blog.jdpfu.com/2013/03/01/linux-troubleshooting-101-networking)

---

### Post by Kanefa on 2013-10-23
I was able to run a couple tests from the article.  I ran them both on my Mac Laptop and my Lubuntu box.  Both are sitting on my desk and I am using the same ethernet cable.  The Mac is on the network and I can connect to the internet.  The Lubuntu box says it is connected, but is unable to connect to the internet.

1. Ping the router - Unsure if I used the correct router number.  For the Mac I got it from Network Preferences -> Ethernet -> Router.  For the Lubuntu box I got it from the Network icon (LXPanel) -> Information -> Default Route.
Mac - 9 packets transmitted, 9 packets received, 0.0% packet loss
Lubuntu - 10 packets transmitted, 10 packets received, 0% packet loss, time 8996ms

2. Ping commonly known internet IP (ping 8.8.8.8)
Mac - 30 packets transmitted, 6 packets received, 80.0% packet loss
Lubuntu - 248 packets transmitted, 0 received, 100% packet loss, time 248976ms

3. see if DNS is working (ping google.com)
Mac - 21 packets transmitted, 6 packets received, 71.4% packet loss
Lubuntu - ping: unknown host google.com


That's the results today.  Yesterday the Lubuntu box was working perfectly fine which is an exception to the norm.  However, when the Lubuntu box doesn't work the Mac and Windows computers still do.  The University's network along with the ISP are unreliable (I am a volunteer in a developing country), but what confuses me the most is why the Mac and Windows computers typically work when the Lubuntu doesn't.  I have no idea what that points to.  Any thoughts?

---

### Post by Bucky Ball on 2013-10-23
*Thread moved to **Networking & Wireless***

Hopefully you'll have more luck here. Quite an odd problem you have. I would take this as a given then forget about it, though: The Mac and Win boxes work regardless of what the Lubuntu box is doing, so they are not part of this equation. They only go to prove that internet is working *_all the time _*so as that's a fact, forget them. The problem is with the Lubuntu machine only so focus there. 

Considering this, you appear to be dealing with the internet dropping in and out on the Lubuntu machine, works sometimes and not others, so time to search for what might be causing that. Does the connection die when you are actually using it? If so, immediately open a terminal and check the result of:

dmesg

You also give no clue as to how the Lubuntu machine is connecting to the internet. As these are computer graveyard bits and pieces this could be a hardware issue (if not the card then perhaps the PCI slot, you could try another). What card does it use? Please provide the output of:

```
sudo lshw -C network
``` 

As the Mac and Win machines are probably using totally different cards, even more reason to pay them no attention (apart from proving you have an active internet cable coming out of whatever AP you are using).

So, give complete details of how you are connecting the Linux machine (only) to the net, and the hardware you have used to build it.

---

### Post by Kanefa on 2013-10-23
The connection does not come and go that often.  I'm starting to log the days it does work, so I have some idea of what the frequency is.  That being said the Lubuntu computers may not have connectivity for a week and then all of a sudden work for two days straight.  It's not a daily issue, so running "dmesg" at the right time would be lucky.

We do have a few Dell Dimension 2400 which are all identical, so I ran the "sudo lshw -C network" on one of these.  However, let me give you a little more background information (I'm not sure if it will be relevant).  The Dell's were all donated running a version of Windows.  We used them as is for a while and they never exhibited this problem.   In fact, we still have one I haven't switch from Windows to Lubuntu and it continues to work.  Lastly, when I put the lab together I used Clonezilla.  Every computer is an exact clone of the original, but as a post install step I make the references to hostname unique in both etc/hostname and etc/hosts.

> *-network
    description: Ethernet interface
    product: BCM4401 100Base-T
    vendor: Broadcom Corporation
    physical id: 9
    bus info: pci@0000:01:09.0
    logical name: eth0
    version: 01
    serial: 00:0d:56:51:c7:3f
    size: 10Mbit/s
    capacity: 100Mbit/s
    width: 32 bits
    clock: 33MHz
    capabilities: pm bus_master cap_list rom ethernet physical mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
    configuration: autonegotiation=on broadcast=yes driver=b44 driverversion=2.0 dublex=half latency=64 link=no multicast=yes port=twisted pair speed=10Mbit/s
    resources: irq:17 memory:fe9ee000-fe9effff memory:fea00000-fea03fff

---

### Post by steeldriver on 2013-10-23
Just a couple of observations

Unless there's a more complicated network topology that you haven't shared with us, the router IP should be the same whether you get it from the Windows boxes or the Lubuntu ones - if it's not then that would be the first thing to look in to. You might find that doing an 'ifconfig' on the *buntus and comparing to an 'ipconfig' on the Windows boxes to be helpful

The fact that you apparently get a near 9s ping time off the router from the *buntu box suggests either it's *not* the correct IP or the routing is screwed up OR driver/hardware issues

In any case, an 'ifconfig' from the *buntu box would be a useful place to start, preferably with the corresponding 'ipconfig' from Windows by way of comparison

---

### Post by TheFu on 2013-10-23
> **steeldriver said:**
>  driver/hardware issues

In any case, an 'ifconfig' from the *buntu box would be a useful place to start, preferably with the corresponding 'ipconfig' from Windows by way of comparison

Based on the data and history, I'd expect the issue is with the physical cable and/or ports either on the router or the machines.  Can you swap those around between the different machines? That would eliminate much .... or confirm it is just the Ubuntu machines.

Hope this helps.  The ideas from others above are smart too, BTW.
Thanks for doing those tests from the article. The results really did help narrow down the thousands of possibilities.

If you haven't already found the root cause, run and post the results for a few commands on OSX, Win, and Linux machines:
ifconfig - ipconfig /all
route - route print
dig google.com - nslookup google.com

Linux on the left, windows on the right.

---

### Post by Kanefa on 2013-10-23
I'm going to jump ahead for a minute.  I was looking into steeldriver's question about the topology.  I'm really not sure what the topology is (it may be fairly complex).  I wasn't sure if I got the routers IP correctly either (that's why I specified how I got them). 

 What I did was borrow a router from a friend.  This should at least simplify getting the IP address for the router.  I plugged the ethernet cable directly into the router and then my Mac and Lubuntu computers.  I open Firefox up and enter the router's IP (which I get from the "Connection Information" in Lubuntu).  On the Mac I end up at the Cable/DSL Gateway Router Setup Utility page.  On the Lubuntu computer I get "The connection has timed out."

That must mean something.  The Lubuntu computer can see the router's IP address and the rest, but than cannot access it.  Also, considering this was the first test in the "Linux Troubleshooting 101" article I figure it must mean something is going wrong quickly.

---

### Post by SeijiSensei on 2013-10-23
Please post the results of "route -n" in [noparse]```

```[/noparse] tags.  My routing table looks like this:

```

Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.100.1   0.0.0.0         UG    0      0        0 wlan0
192.168.100.0   0.0.0.0         255.255.255.0   U     9      0        0 wlan0

```

Your results should list "eth0" rather than "wlan0".  My computer's IP is 192.168.100.110, and the gateway is 192.168.100.1.  I see other computers in the 192.168.100.0/24 network via broadcasts; all other traffic goes to the gateway.

My network's topology is rather similar to yours because my gateway router is behind my Internet-facing router.  I can see the Internet from all my machines because both routers do "masquerading" and impersonate the machines behind them.  The router at 192.168.100.1 masquerades the traffic from 192.168.100.0/24 as if it is coming from its upstream-facing IP of 192.168.1.2.  The Internet facing router has local interface 192.168.1.1 that talks to 192.168.1.2 and masquerades its traffic again using the public Internet address on its "WAN" side.

Try this experiment.  Connect with the Mac and identify its IP address and the gateway's address; let's say these are 192.168.1.10 and 192.168.1.1 respectively.  Now disconnect the Mac from the network.  On the lubuntu box, use these commands

```

sudo ifconfig eth0 down
sudo ifconfig eth0 192.168.1.10 netmask 255.255.255.0 
sudo ip route add default via 192.168.1.1
ping 192.168.1.1
ping 8.8.8.8

```

How are we doing?  Can you connect to the router's configuration page now?

Oh, just one other thing, did you reset the router to its factory defaults after borrowing it?  If not, I would do that first.  There usually is a small switch behind a hole in the back of the router that you can depress with a paper clip.  Turn off the router, then turn it back while holding down the switch.  Hold it down for 30 seconds or so, then turn off the router and turn it back on again.

---

### Post by Kanefa on 2013-10-24
> Please post the results of "route -n" in ```

``` tags.

SeijiSensei, it looks like the code did not make it in.

---

### Post by Bucky Ball on 2013-10-24
> **Kanefa said:**
> SeijiSensei, it looks like the code did not make it in.

? How do you mean 'did not make it in'? You just want the command, not the ". Copy and paste the following:
```

route -n
```

You may need to use:

```

sudo route -n
```

---

### Post by Kanefa on 2013-10-25
Here are the results for steeldriver and TheFu.  To be clear I removed the router I was borrowing.  I am directly connected into the University's network.  The Windows' results are in French.  Sorry, this is just one reason we are moving to Lubuntu (I teach in the English Department).  [B]

ifconfig - Lubuntu
[/B]```

administrator@DEAA:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:0d:56:51:c7:3f  
          inet addr:192.168.2.27  Bcast:192.168.2.255  Mask:255.255.255.0
          inet6 addr: fe80::20d:56ff:fe51:c73f/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:2104 errors:0 dropped:0 overruns:0 frame:0
          TX packets:252 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:414397 (414.3 KB)  TX bytes:24555 (24.5 KB)
          Interrupt:17 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:407 errors:0 dropped:0 overruns:0 frame:0
          TX packets:407 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:29371 (29.3 KB)  TX bytes:29371 (29.3 KB)

```

  **ipconfig /all - Windows**
```

C:\Documents and Settings\Administrateur>ipconfig /all

Configuration IP de Windows

        Nom de l'hÙte . . . . . . . . . . : dell01
        Suffixe DNS principal . . . . . . :
        Type de noud . . . . . . . . . . : Inconnu
        Routage IP activÈ . . . . . . . . : Non
        Proxy WINS activÈ . . . . . . . . : Non
        Liste de recherche du suffixe DNS : local-antsiranana.mg

Carte Ethernet Connexion au rÈseau local:

        Suffixe DNS propre ‡ la connexion : local-antsiranana.mg
        Description . . . . . . . . . . . : Broadcom 440x 10/100 Integrated Cont
roller
        Adresse physique . . . . . . . . .: 00-0D-56-51-C7-8B
        DHCP activÈ. . . . . . . . . . . : Oui
        Configuration automatique activÈe . . . . : Oui
        Adresse IP. . . . . . . . .†. . . : 192.168.11.128
        Masque de sous-rÈseau . . .†. . . : 255.255.255.0
        Passerelle par dÈfaut . . .†. . . : 192.168.11.1
        Serveur DHCP. . . . . . . . . . . : 192.168.11.1
        Serveurs DNS . . . . . . . . . .  : 192.168.11.30
                                            196.192.32.5
        Bail obtenu . . . . . . . .†. . . : vendredi 25 octobre 2013 14:57:01
        Bail expirant . . . . . . .†. . . : vendredi 25 octobre 2013 16:57:01

```

[B]route - Lubuntu
[/B]```

administrator@DEAA:~$ route
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
default         192.168.2.1     0.0.0.0         UG    0      0        0 eth0
192.168.2.0     *               255.255.255.0   U     1      0        0 eth0

```

**route print - Windows**
```

C:\Documents and Settings\Administrateur>route print
===========================================================================
Liste d'Interfaces
0x1 ........................... MS TCP Loopback interface
0x2 ...00 0d 56 51 c7 8b ...... Broadcom 440x 10/100 Integrated Controller - Min
iport d'ordonnancement de paquets
===========================================================================
===========================================================================
ItinÈraires actifs†:
Destination rÈseau    Masque rÈseau  Adr. passerelle   Adr. interface MÈtrique
          0.0.0.0          0.0.0.0     192.168.11.1  192.168.11.128       20
        127.0.0.0        255.0.0.0        127.0.0.1       127.0.0.1       1
      169.254.0.0      255.255.0.0   192.168.11.128  192.168.11.128       20
     192.168.11.0    255.255.255.0   192.168.11.128  192.168.11.128       20
   192.168.11.128  255.255.255.255        127.0.0.1       127.0.0.1       20
   192.168.11.255  255.255.255.255   192.168.11.128  192.168.11.128       20
        224.0.0.0        240.0.0.0   192.168.11.128  192.168.11.128       20
  255.255.255.255  255.255.255.255   192.168.11.128  192.168.11.128       1
Passerelle par dÈfaut†:      192.168.11.1
===========================================================================
ItinÈraires persistants†:
  Aucun

```
 [B]
dig google.com - Lubuntu[/B]```

administrator@DEAA:~$ dig google.com

; <<>> DiG 9.9.2-P1 <<>> google.com
;; global options: +cmd
;; connection timed out; no servers could be reached

```[B]

nslookup google.com - Windows[/B]
```

C:\Documents and Settings\Administrateur>nslookup google.com
DNS request timed out.
    timeout was 2 seconds.
*** Impossible de trouver le nom de serveur pour l'adresse 192.168.11.30 : Timed
 out
DNS request timed out.
    timeout was 2 seconds.
*** Impossible de trouver le nom de serveur pour l'adresse 196.192.32.5 : Timed
out
*** Les serveurs par dÈfaut ne sont pas disponibles
Serveur :  UnKnown
Address:  192.168.11.30

DNS request timed out.
    timeout was 2 seconds.
DNS request timed out.
    timeout was 2 seconds.
*** Le dÈlai de la requÍte sur UnKnown est dÈpassÈ

```

---

### Post by TheFu on 2013-10-25
Thanks.  Don't have time to do more than skim today... 

Linux is being put on a different subnet than Windows. Can you explain that?

External DNS didn't work on either host - I'd guess this is due to a proxy - which is smart by your network admins. Don't let any desktop have DNS access to the outside world - only the proxy server does.
```

         Linux            Win
IP       192.168.2.27     192.168.11.128
Netmask  255.255.255.0    255.255.255.0
Gateway  192.168.2.1      192.168.11.1
DNS Srv  none             192.168.11.30
```

See the differences?  You'll need to talk with the network - AD - DHCP guys to get this fixed on their side.  Getting the internet proxy settings would be smart too.

---

### Post by Kanefa on 2013-10-26
> **Bucky Ball said:**
> ? How do you mean 'did not make it in'? You just want the command, not the ". Copy and paste the following:
```

route -n
```


I misread the instructions as run "route -n" as used in the code tags.  I tried this yesterday, but the Lubuntu computer was unable to see the network at all when using the router.  I have no explanation why.  I was going to wait a bit and try again, but I had to give back the router which was unfortunate.

---

### Post by TheFu on 2013-10-26
> **Kanefa said:**
> I misread the instructions as run "route -n" as used in the code tags.  I tried to this yesterday, but the Lubuntu computer was unable to see the network at all when using the router.  I have no explanation why.  I was going to wait a bit and try again, but I had to give back the router which was unfortunate.

You've already provided the same data above. Don't worry about it.  You need to find out why the Windows PC and the Linux PC are on 2 different subnets. Are both using DHCP or have you tried setting, unused, static IPs?

---

### Post by Kanefa on 2013-10-26
> **TheFu said:**
> Thanks.  Don't have time to do more than skim today... 

Linux is being put on a different subnet than Windows. Can you explain that?

External DNS didn't work on either host - I'd guess this is due to a proxy - which is smart by your network admins. Don't let any desktop have DNS access to the outside world - only the proxy server does.
```

         Linux            Win
IP       192.168.2.27     192.168.11.128
Netmask  255.255.255.0    255.255.255.0
Gateway  192.168.2.1      192.168.11.1
DNS Srv  none             192.168.11.30
```

See the differences?  You'll need to talk with the network - AD - DHCP guys to get this fixed on their side.  Getting the internet proxy settings would be smart too.

Thanks for the response, I really appreciate you looking over it.  I cannot explain why the two computers are being put on different subnets.  To be clear we are referring to 192.168.2 vs 192.168.11.  When you say "see the differences" I assume you are referring just to the subnet issue and nothing else.  If that is the case I do see that and will to take it to my network admin.  Looking at my Mac I notice it also has the same subnet as the Windows machine.  I'm curious as to why the Lubuntu machines would be put onto a different subnet then the Windows and Macs.  Any thoughts?

Also, why would getting the internet proxy settings be helpful in my case?

---

### Post by The Cog on 2013-10-26
The first step is to find out how the Lubuntu network is configured. 

It may be configured from a static configuration file, so let's check that. Please post the content of the file /etc/network/interfaces. 
There is probably no mention of eth0 in the file, but it helps to be sure.

Also, please post the contents of /etc/NetworkManager/NetworkManager.conf. I'm not sure what it all means, but others here will, and it may be significant.

There must be a GUI network configuration utility somewhere in Lubuntu. Sorry, I'm not familiar with Lubuntu, but I attach a screenshot of the kind of thing I'm looking for - this is from Xubuntu. Can you find anything similar and post the configuration?

Also, please try this command thich tries to ask the network for a DHCP address, and post the output. Does this command make the internet work?
```
sudo dhclient -v eth0
```

---

### Post by steeldriver on 2013-10-26
The first thing I'd do in a university / work network is talk to the network admins - these kinds of environments often use MAC address whitelists, meaning that the DHCP server only gives out IP addresses to computers it "knows". Hard to explain where it's getting the 192.168.2.xxx address - as The Cog says, it may be a static assignment.

---

### Post by Kanefa on 2013-10-26
[B][COLOR=#000000] /etc/network/interfaces
[/COLOR][/B]```

# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).


# The loopback network interface
auto lo
iface lo inet loopback


# The primary network interface
#NetworkManager#auto eth0
#NetworkManager#iface eth0 inet dhcp

```

**[COLOR=#000000]/etc/NetworkManager/NetworkManager.conf[/COLOR]**
```

[main]
plugins=ifupdown,keyfile
dns=dnsmasq


[ifupdown]
managed=false

```

**sudo dhclient -v eth0**

```

administrator@DEAA:/$ sudo dhclient -v eth0
Internet Systems Consortium DHCP Client 4.2.4
Copyright 2004-2012 Internet Systems Consortium.
All rights reserved.
For info, please visit https://www.isc.org/software/dhcp/


Listening on LPF/eth0/00:0d:56:51:c7:3f
Sending on   LPF/eth0/00:0d:56:51:c7:3f
Sending on   Socket/fallback
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 3 (xid=0x6fce155a)
DHCPREQUEST of 192.168.2.27 on eth0 to 255.255.255.255 port 67 (xid=0x6fce155a)
DHCPOFFER of 192.168.2.27 from 192.168.2.1
DHCPNAK from 192.168.11.1 (xid=0x6fce155a)
DHCPACK of 192.168.2.27 from 192.168.2.1
RTNETLINK answers: File exists
bound to 192.168.2.27 -- renewal in 563222 seconds.

```

> **steeldriver said:**
> The first thing I'd do in a university / work network is talk to the network admins - these kinds of environments often use MAC address whitelists, meaning that the DHCP server only gives out IP addresses to computers it "knows". Hard to explain where it's getting the 192.168.2.xxx address - as The Cog says, it may be a static assignment.

At some point I will have to get in touch with him, but I've been trying for over a month now.  Even when I do manage to corner him, we are going to speak two different languages.  That being said they have no knowledge of my Mac laptop or any of the other volunteers' computers and they all work (we all have Mac or Window laptops).

---

### Post by SeijiSensei on 2013-10-26
> ```

# The primary network interface
#NetworkManager#auto eth0
#NetworkManager#iface eth0 inet dhcp

```

Remove the "#NetworkManager#" comments from each line so they read

```

# The primary network interface
auto eth0
iface eth0 inet dhcp

```

That will tell the system to obtain a DHCP address just like you did manually with dhclient.  Now run "sudo service networking restart" and then "ifconfig" and see if you get back the same address, or at least some address in 192.168.2.0/24.

---

### Post by steeldriver on 2013-10-26
Isn't the issue that there are 2 DHCP servers on the network (192.168.**11**.1 and 192.168.**2**.1), and that it is the latter that is responding to the DHCPREQUEST? Not sure that simply changing from NetworkManager w/ DHCP to /etc/network/interfaces w/ DHCP will do anything about that. 

Probably what should be happening is that your box requests 192.168.2.27 (likely just because it had that lease before) and the 192.168.**11**.1 server rejects it and offers something in the 192.168.**11**.xxx pool. But either the 192.168.**2**.1 server is responding first or the 192.168.**11**.1 server is ignoring the request because your MAC is not on its whitelist.

University networks tend to be a bit of a free-for-all and it's not unusual to find someone running a DHCP server either by accident or whatever.

---

### Post by The Cog on 2013-10-26
I agree with steeldriver. It looks like the problem is that there are 2 conflicting DHCP servers running on the LAN. 192.168.2.1 is presumably the rogue one because the PCs on 192.168.11 can access the internet. This happened where I work recently because some bright spark connected a home router to act as a wireless access point and didn't think to disable its DHCP server. People at random had no connectivity to the corporate network.

Please can you try these commands and see if it helps. I am trying to release the existing lease on 192.168.2, block packets from DHCP servers on 192.168.2 and then try to get a new address lease from DHCP:
```
sudo dhclient -v -r eth0
sudo iptables -I INPUT -p udp --sport 67 -s 192.168.2.0/24 -j DROP
sudo dhclient -v eth0
```

---

### Post by Kanefa on 2013-10-26
The Cog, the current IP address was 192.168.2.27, so I changed your second command to 
[COLOR=#000000][FONT=Ubuntu Mono]
```

sudo iptables -I INPUT -p udp --sport 67 -s 192.168.2.0/27 -j DROP

```

[/FONT][/COLOR]and when I did I had internet!  

Now this leads to a couple questions.  First, the router I borrowed was another volunteers on campus.  I was never able to post the results, but if my memory serves me correctly its subnet was 192.168.2.  That would mean it's his router that is causing the problem? Besides telling him to disable the router's DHCP server how do I protect my lab from this?  It seems like it could be a very common problem.

---

### Post by steeldriver on 2013-10-26
I'm sure The Cog will clarify shortly, but AFAIK the /24 refers to the number of bits in the network portion of the drop mask - the idea being that it drops DHCP responses from any host in the range 192.168.2.**1** - 192.168.2.**255** inclusive (the host portion is 8 bits i.e. 32-8 = **24** bits for the network). By changing it to /27 you are only dropping DHCP responses from hosts below 192.168.2.32 (only 32-27 = 5 bits in the host portion) - which works in this case because the rogue DHCP server is at 192.168.2.1, but there's nothing to stop someone changing that to  192.168.2.254 for example, which would break things again.

---

### Post by SeijiSensei on 2013-10-26
[DHCP]("http://www.ietf.org/rfc/rfc2131.txt") depends on broadcasts of computers' MAC addresses.  A computer requesting a DHCP configuration sends a packet with its MAC to the "all-ones" address of 255.255.255.255 and awaits a response.  Because of this method of signalling, there can be only one authoritative DHCP server for a subnet.  With multiple servers on the network, which configuration you get probably depends on things like network latency and hop counts.  Any nearby server is more likely to respond than the school's central server which may be far away even topologically.

I would have your friend reset his router to factory defaults.  Then he should check the adminstration page to make sure that the router is not configured to answer DHCP requests on its "WAN" port, the one that would be facing the school's network.  Default configurations never permit that since it would wreak havoc in ISP's networks.  Perhaps he was playing with the settings and accidentally told the router to handle DHCP queries on both sides by mistake.

---

### Post by The Cog on 2013-10-26
For the reasons steeldriver gave, the iptables command I posted was correct. By luck, the changed command also happened to work.

The router may well not have its WAN port connected to the campus. In the case of the router where I work, one of its 4-port switch LAN ports had been connected to the local LAN - its WAN link was unused. 

Yes, your friend's router may well be the rogue one. Have him disable the DHCP service if possible. If not, get it removed from the network. It will be causing problems all over. 

If you cannot locate the rogue DHCP server, add the iptables command to the startup script /etc/rc.local. That should run it whenever Ubuntu boots which should prevent the PCs seeing responses from the rogue server.

---

### Post by Kanefa on 2013-10-27
I changed the command, because it was not having any affect.  When I changed the command it suddenly worked.  It was obviously a fluke.  Today, I went to the lab and tried to test out the commands.  Unfortunately, the commands had no affect.  I tried on four different computers.  Here are my final results from the computer next to me.  

**sudo dhclient -v -r eth0**
```

administrator@DEAA:~$ sudo dhclient -v -r eth0[sudo] password for administrator: 
Internet Systems Consortium DHCP Client 4.2.4
Copyright 2004-2012 Internet Systems Consortium.
All rights reserved.
For info, please visit https://www.isc.org/software/dhcp/


Listening on LPF/eth0/00:0d:56:51:c7:3f
Sending on   LPF/eth0/00:0d:56:51:c7:3f
Sending on   Socket/fallback
DHCPRELEASE on eth0 to 192.168.11.1 port 67 (xid=0x71411351)

```

[B]sudo iptables -I INPUT -p udp --sport 67 -s 192.168.2.0/24 -j DROP
[/B]```

administrator@DEAA:~$ sudo iptables -I INPUT -p udp --sport 67 -s 192.168.2.0/24 -j DROP

```

**sudo dhclient -v eth0**
```

administrator@DEAA:~$ sudo dhclient -v eth0
Internet Systems Consortium DHCP Client 4.2.4
Copyright 2004-2012 Internet Systems Consortium.
All rights reserved.
For info, please visit https://www.isc.org/software/dhcp/


Listening on LPF/eth0/00:0d:56:51:c7:3f
Sending on   LPF/eth0/00:0d:56:51:c7:3f
Sending on   Socket/fallback
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 3 (xid=0x5e69f626)
DHCPREQUEST of 192.168.2.27 on eth0 to 255.255.255.255 port 67 (xid=0x5e69f626)
DHCPOFFER of 192.168.2.27 from 192.168.2.1
DHCPNAK from 192.168.11.1 (xid=0x5e69f626)
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 3 (xid=0x29ec6a6f)
DHCPREQUEST of 192.168.2.27 on eth0 to 255.255.255.255 port 67 (xid=0x29ec6a6f)
DHCPOFFER of 192.168.2.27 from 192.168.2.1
DHCPNAK from 192.168.11.1 (xid=0x29ec6a6f)
DHCPACK of 192.168.2.27 from 192.168.2.1
bound to 192.168.2.27 -- renewal in 458412 seconds.

```

---

### Post by steeldriver on 2013-10-27
My understanding of DHCP is pretty hazy but I *think* your drop rule may need to specify source port 68 rather than 67 (i.e. **--sport 68**) for the replies **from** the server (67 is the DHCP server's listening port, where the client's DHCPDISCOVER requests go **to**)

---

### Post by Kanefa on 2013-10-27
> **steeldriver said:**
> My understanding of DHCP is pretty hazy but I *think* your drop rule may need to specify source port 68 ratvher than 67 (i.e. **--sport 68**) for the replies **from** the server (67 is the DHCP server's listening port, where the client's DHCPDISCOVER requests go **to**)

I tried this, but the computer still isn't getting a new IP address.

---

### Post by steeldriver on 2013-10-27
... but does it stop it from getting the **wrong** address? that's step 1. Step 2 is going to your network admin and making sure that your MAC is whitelisted - since you are seeing

```
**DHCPNAK** from 192.168.**11**.1 (xid=0x29ec6a6f)
```

---

### Post by Kanefa on 2013-10-27
I may not understand.  Before and after running the commands the IP address is "192.168.2.27" which is wrong.

I'm also not sure the issue is whether the MAC is whitelisted or not.  The Dell's all ran Windows in the lab and had no problems.  We still have one that continues to run Windows and it continues to work.  Whether or not the computers are whitelisted the problem only arises when I put Lubuntu on the computer.  Regardless, it may be a smart idea, but is that the problem?

---

### Post by The Cog on 2013-10-27
@steeldriver: I just double-checked with tcpdump, and the server does indeed reply from source port 67 to the client destination port 68. 

I also double-checked the iptables rules, and it seems that dhclient gets access to the packets before they go through iptables. dhclient -v continues to show the packets arriving from the rogue server, and the counters in iptables don't show any packets hitting the rule. As such, I guess the dhcp client is connected somewhere in the packet processing before iptables (much as tcpdump is) and we will not be able to prevent the client from seeing responses from the rogue server. Forget using iptables.

It is possible to tell the client to talk to a specific server, like this:
sudo dhclient -v -s 192.168.11.1 eth0
but when I try that here, my server does not respond, so it may not help you either.

You may get lucky by calling "dhclient -r eth0" and "dhclient -v eth0" repeatedly until you get a lease from the right server.

And as steeldriver says, the 192.168.11.1 server seems to be sending DHCPNAK which is a negative response - it is refusing you for some reason. This may be because you didn't release the 192.168.2 lease first, I don't know for sure. But you may really need to talk to the network admin to get this resolved.

---

### Post by steeldriver on 2013-10-27
@The Cog - sorry for the misdirect, thanks for clarifying

---

### Post by The Cog on 2013-10-27
Got it!
Release the bad lease with
```
sudo dhclient -r eth0
```

Then edit /etc/dhcp/dhclient.conf and add this line:
```
reject 192.168.2.1
```
and from now on, you should ignore that rogue server.
Run:
```
sudo dhclinet -v eth0
```
to (hopefully) watch it choose to ignore the rogue. Now you just have to worry about the DHCPNAK from the good server.

Edit:
It appears that you can also use the format "reject 192.168.2.0/24" which would reject any dhcp server on 192.168.2.*.

---

### Post by Kanefa on 2013-10-27
It worked!  Thanks to everyone that helped and a special thanks to The Cog.

---

### Post by steeldriver on 2013-10-27
Nice work @The Cog

---

