---
title: "Simple network related problem"
date: 2007-02-05
forum: Networking &amp; Wireless
---

### Post by Sidster on 2007-02-05
Hi All

I have a simple yet confounding problem. I'm running Ubuntu 6.10 with latest updates on my desktop and laptop. I've tried to network the two in several different ways without any success. When I say "without any success" I mean I can't ping either machine from the other. I have XP on another disk of my desktop that I dual boot into.

Before I start let me say this. I've checked the cables and hardware on other networks. They work fine. The hardware I have is:
2 x 5m CAT5 straight network cables
1 x 3m CAT5 crossover cable
1 x Dlink 5 port network switch
1 x Compaq Evo n610c laptop
1 x AMD Athlon 3500 Desktop: Asus A8N sli deluxe MoBo, Dual gigabit lan (Marvel & Nvidia lan controllers)

The final bit of info I have to add is that I connect to the internet using my 3G enabled phone via bluetooth. I connect on ppp0 and would eventually like to share this connection through eth0.

Here's what I've tried:

1.) Simply connecting the two together with the crossover cable. Gave the desktop an ip of 192.168.0.1 and the laptop an ip of 192.168.0.2. Rebooted, tried to ping either one, no luck. (When I do this in Windows it works) By that I mean the Windows on my desktop has an ip of 1.92.168.0.1 and the Ubuntu laptop an ip of 192.168.0.2 and I can ping both ways.

2.) Tried connecting the two with a straight cable, since this also works in Windows (The desktop's NIC automagically handles the crossover). However I'm not sure this is meant to work in Ubuntu. I think the NIC's Windows driver is what allows this bit of magic to exist. No luck.

3.) Tried involving the switch, (It also handles crossover and straight cables automagically) even though my common sense tells me If I can't connect directly between the two, the switch isn't gonna change anything. I tried the switch in a few different ways too. Using just straight cables as well as a crossover between the desktop and switch and a straight between the laptop and switch. Trust me I've tried almost every conceivable configuration. No luck.

After trying all that with static ip's I decided I'd try the dhcp route which is strictly not necessary since I'm only networking two machines. Anyhow, here's what I did:

1.) Installed firestarter on laptop, read up on [how to get dhcp working with firestarter]("http://www.fs-security.com/docs/dhcp.php"). Installed dhcp and tried to start up dhcp = Failed. After that went to [http://ubuntuguide.org/](http://ubuntuguide.org/) and followed their how-to. Basically they tell you to install dhcp3-server and edit the config file to include your networks info. I replaced their examples with what I think to be correct in my case and when I restart I get the error "config file incorrect please fix" or something to that effect. If you want me to elaborate on this let me know, cause this post is getting a bit long plus I'm not sure dhcp is the way to go for my situation.

2.) Tried getting the dhcp to run independantly of firestarter on desktop machine (doesn't have firestarter installed), I get the same errors.

3.) Tried to use Webmin, discovered it's only a front end for existing functionality. Tried setting up my network using [this how-to]("http://ubuntulinuxhowto.blogspot.com/2006/06/setup-your-computer-to-be-router.html") no luck.

Phew! That's a lot of messing about.

Anyway. I don't see why this should be so difficult. All I want to do is be able to share files between the two and maybe share the internet connection. I have read how-tos on doing all this and they don't seem too difficult. None of it matters though if I can't establish a physical connection between the two machines! I'm sure it's something tiny that I've overlooked. Any help would be greatly appreciated! :-)

---

### Post by zgornel on 2007-02-05
Please post /etc/network/interfaces and results from "ifconfig"

---

### Post by Sidster on 2007-02-05
Thanks for the quick reply! :-) I'll post the results tonight. I'm at work at the moment. :(

---

### Post by Sidster on 2007-02-05
Hi I'm back

Here is "/etc/networking/interfaces" for the *desktop*

```
auto lo
iface lo inet loopback

iface eth0 inet static
	address 196.168.0.1
	netmask 255.255.255.0
	pre-up iptables-restore < /etc/iptables.up.rules

iface eth1 inet dhcp
address 192.168.0.2
netmask 255.255.255.0
gateway 192.168.0.1

auto eth2
iface eth2 inet dhcp

auto ath0
iface ath0 inet dhcp

auto wlan0
iface wlan0 inet dhcp

auto eth0

```

and here is the result of "ifconfig" for the *desktop*

```
eth0      Link encap:Ethernet  HWaddr 00:11:D8:CA:E2:F1  
          inet addr:196.168.0.1  Bcast:196.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::211:d8ff:feca:e2f1/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:12 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:936 (936.0 b)
          Interrupt:217 Base address:0x4000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:8 errors:0 dropped:0 overruns:0 frame:0
          TX packets:8 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:400 (400.0 b)  TX bytes:400 (400.0 b)

ppp0      Link encap:Point-to-Point Protocol  
          inet addr:xx.xx.xx.xxx  P-t-P:10.6.6.6  Mask:255.255.255.255
          UP POINTOPOINT RUNNING NOARP MULTICAST  MTU:1500  Metric:1
          RX packets:633 errors:0 dropped:0 overruns:0 frame:0
          TX packets:522 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:3 
          RX bytes:537128 (524.5 KiB)  TX bytes:113886 (111.2 KiB)

```

Just "xxx'ed"  my ppp0's ip. Maybe I'm bein a n00b. Feel free to correct me if I'm being paranoid :-)

---

### Post by Sidster on 2007-02-05
Sorry forgot to mention that my previous post was for my desktop machine ](*,) 

Here are the results for my laptop:

"/etc/network/interfaces" for the *laptop*

```
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

iface eth0 inet static
address 192.168.0.2
netmask 255.255.255.0
```

The results of "ifconfig" for the *laptop*

```
eth0      Link encap:Ethernet  HWaddr 00:08:02:94:DF:EE  
          inet addr:192.168.0.2  Bcast:192.168.0.255  Mask:255.255.255.0
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:58 errors:0 dropped:0 overruns:0 frame:0
          TX packets:58 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:4792 (4.6 KiB)  TX bytes:4792 (4.6 KiB)

ppp0      Link encap:Point-to-Point Protocol  
          inet addr:xx.xx.xxx.xx  P-t-P:10.6.6.6  Mask:255.255.255.255
          UP POINTOPOINT RUNNING NOARP MULTICAST  MTU:1500  Metric:1
          RX packets:902 errors:0 dropped:0 overruns:0 frame:0
          TX packets:865 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:3 
          RX bytes:796317 (777.6 KiB)  TX bytes:173648 (169.5 KiB)
```

Any help would be much appreciated ;-)

---

### Post by zgornel on 2007-02-05
From what I see, your desktop has only **one** NIC but in the *interfaces* file there are two (eth0 and eth1). Try commenting these lines:
```

iface eth1 inet dhcp
address 192.168.0.2
netmask 255.255.255.0
gateway 192.168.0.1
```
Theoretically, the desktop and laptop /etc/network/interfaces files should be the same. The gateway part you may add on the laptop machine if you intend to use it as a router (for the laptop)

---

### Post by Sidster on 2007-02-05
Thanks for the help but it doesn't solve my problem.

My desktop machine has two ethernet ports. eth0 and eth1. After scouring the forums I discovered that firestarters default setting is to deny all packet requests (pings). I really thought that was the problem and I was just about to kick myself for being such a noob but I enabled the setting in firestarter and still no luck.

I'm running out of google results for my problem. All of them have been dead ends so far :confused:

---

### Post by koenn on 2007-02-05
> pre-up iptables-restore < /etc/iptables.up.rules
Looks like you're running a firewall
you might try again after removing that line from /etc/network/interfaces and /or disabling it completly by running
```
iptables --flush
iptables -P OUTPUT ACCEPT
iptables -P INPUT ACCEPT
iptables -P FORWARD ACCEPT

```

If it works then, it's (still) the firewall that's causing the trouble and you'll have to work at the rules to get things going.

---

### Post by zgornel on 2007-02-05
Change the ip of one of the desktop NIC so you won't have 2 NICs with the same address (192.168.0.2). Why is eth1 not shown by ifconfig results on the desktop ?

---

### Post by koenn on 2007-02-06
> **zgornel said:**
> Change the ip of one of the desktop NIC so you won't have 2 NICs with the same address (192.168.0.2). Why is eth1 not shown by ifconfig results on the desktop ?
hmm, missed that one. good point. both et0 of the laptop and eth1 of the desktop have the
same address (192.168.0.2) - that has to be wrong

---

### Post by mips on 2007-02-06
Post the output from both machines for **lspci -v | grep Eth**  just incase you have one of those funnies.

---

### Post by Sidster on 2007-02-06
Sorry for messing you guys around. I had posted too quickly. I was still messing around with the settings :oops:  I know that the machines need to have unique ip's I was just experimenting at the time. Sorry.

Just to clear things up:

My desktop has two NIC's. I've disabled eth0 and given eth1 an ip of 192.168.0.1 (connected to switch with straight CAT5 cable)

My laptop has the ppp0 connection via 3G to the internet and eth0 with an ip of 192.168.0.2 (connected to switch with straight CAT5 cable)

I've checked that the switch has power. lol

Other than that everything is pretty much default. The only complication could be:

1.) I've had firestarter installed on the laptop - I've since uninstalled it (not sure if it leaves behind some residual config)

2.) I've tried and failed to get dhcp3-server running on both machines. Unfortunately dhcp3-server doesn't have very descriptive error messages :???: just "Failed". I realise I'll have to tweak the config file but I'm not sure which addresses to put where :confused: 

I'll post the results of ifconfig tonight with the setup the way it's *supposed* to be along with /etc/network/interfaces and "lspci -v | grep Eth"

---

### Post by Sidster on 2007-02-06
It's working! I can ping other machine's on my LAN!!! Oh my greatness this is awesome! :-)

Here's what did it for me:

> Originally Posted by **koenn**[QUOTE]pre-up iptables-restore < /etc/iptables.up.rules
Looks like you're running a firewall
you might try again after removing that line from /etc/network/interfaces and /or disabling it completely by running

```
iptables --flush
iptables -P OUTPUT ACCEPT
iptables -P INPUT ACCEPT
iptables -P FORWARD ACCEPT
```

If it works then, it's (still) the firewall that's causing the trouble and you'll have to work at the rules to get things going.[/QUOTE]

Thanks koenn!

Webmin was the culprit!  I had webmin installed on the desktop and it comes with iptables. I uninstalled it cause I won't be needing it for now.  The only reason I used webmin was cause I thought it would help configure my dhcp. Firestarter should be fine for my needs.

Phew! I was just getting a little freaked out there for a minute cause I couldn't ping machine's on my LAN. I thought the hardware was faulty.

Now that I've confirmed that the hardware works I can start doing all sorts of cool stuff like ICS and samba file sharing.

I'll just take it slow. One how-to at a time :) 

Thanks you guy's You rock!!! :guitar:

---

