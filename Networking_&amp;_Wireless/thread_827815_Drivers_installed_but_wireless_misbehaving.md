---
title: "Drivers installed but wireless misbehaving"
date: 2008-06-13
forum: Networking &amp; Wireless
---

### Post by HazeUK on 2008-06-13
I've "correctly" installed my rt61 driver for my belkin wireless card, I can connect to my router on "roaming" mode, but if i switch to DHCP the gui goes really slow and it won't let me connect.. or even look up routers in range.

I'm not sure what info you'll need, so please ask away.

Thanks, Haze.

---

### Post by nickdbliss on 2008-06-13
It happens with me as well. Some drivers don't support WEP or WPA

---

### Post by HazeUK on 2008-06-13
This card does work on windows btw, perfectly fine.

Just want to get on the internet on linux :(

---

### Post by dnairb on 2008-06-13
It depends on the chip. Some chips don't support encryption in Ubuntu.
There are USB wireless adapters as well - I have seen versions 3, 4 and 5 - version 4 works perfectly.

---

### Post by HazeUK on 2008-06-13
My chip had 6000 on the back of it.

Sort of stumped as to what I can do.. came here in hope :)

---

### Post by HazeUK on 2008-06-14
Still unable to get it to work - and the next day post is back to page 8.. :(

---

### Post by nickdbliss on 2008-06-14
I am experimenting with mine so if anything good comes out of it i ll let you know buddy.

---

### Post by nickdbliss on 2008-06-14
i would like you to give me the output of the following commands
code:
#sudo lshw -C network
# sudo iwlist wlan0 scan

---

### Post by HazeUK on 2008-06-14
*-network:0
description: Wireless interface
      
 product: RT2561/RT61 802.11g PCI
      
 vendor: RaLink
       physical id: 2
   
 bus info: pci@0000:02:02.0
   
 logical name: wmaster0   
 version: 00
     
 serial: 00:17:3f:29:3c:1c
   
 width: 32 bits
     
 clock: 33MHz
     
 capabilities: pm bus_master cap_list logical ethernet physical wireless
    
 configuration: broadcast=yes driver=rt61pci ip=192.168.1.4 latency=32 module=rt61pci multicast=yes wireless=IEEE 802.11g
  *-network:1
    
 description: Ethernet interface
  
 product: RTL-8139/8139C/8139C+
   
 vendor: Realtek Semiconductor Co., Ltd.
   
 physical id: b
     
 bus info: pci@0000:02:0b.0
  
 logical name: eth0
     
 version: 10
   
 serial: 00:0f:ea:13:da:f6
   
 size: 10MB/s
  
 capacity: 100MB/s
   
 width: 32 bits
      
 clock: 33MHz
     
 capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
  
 configuration: autonegotiation=on broadcast=yes driver=8139too driverversion=0.9.28 duplex=half latency=32 link=no maxlatency=64 mingnt=32 module=8139too multicast=yes port=MII speed=10MB/s

-------------------------------------------------------------------------


wlan0     interface does not support scanning: network is down.

-------------------------------------------------------------------------


(this is with it set to dhcp, with it set to roaming mode it can do the second command)

---

### Post by HazeUK on 2008-06-14
Still unable to get this working - having to use laptop while I **** about with linux :(

When set to dhcp, on network setings it shows up as no wireless connection, only has a greyed out wired connection but no wireless, and on left click there's no enable wireless.

---

### Post by nickdbliss on 2008-06-14
ok give me the second command output with roaming enabled. I am hoping it is network manager problem. if it is i have a solution.thanks

---

### Post by HazeUK on 2008-06-14
wlan0     Scan completed :
          Cell 01 - Address: 00:0F:3D:B4:56:C4
                    ESSID:"G604T_WIRELESS"
                    Mode:Master
                    Channel:6
                    Frequency:2.437 GHz
                    Signal level=-64 dBm  
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 22 Mb/s
                              6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Extra:tsf=00000011a93e94c8

Ty :)

---

### Post by nickdbliss on 2008-06-14
> **HazeUK said:**
> wlan0     Scan completed :
          Cell 01 - Address: 00:0F:3D:B4:56:C4
                    ESSID:"G604T_WIRELESS"
                    Mode:Master
                    Channel:6
                    Frequency:2.437 GHz
                    Signal level=-64 dBm  
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 22 Mb/s
                              6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Extra:tsf=00000011a93e94c8

Ty :)

Are you having encryption key on? like WEP or WPA?

---

### Post by HazeUK on 2008-06-14
Yes, my router has a WEP.

---

### Post by nickdbliss on 2008-06-14
Hope it will work couse it did with me.I will like you to install wicd over network manager. For installing it:
Go to system>Administration>Software Sources - Third party software
Click to add the following one by one

deb [http://apt.wicd.net](http://apt.wicd.net) hardy extras
deb [http://apt.wicd.net](http://apt.wicd.net) hardy all

(i forgot to ask u which version do u have? hardy or gutsy anyways replace hardy with gutsy if u have gutsy.)

Close it and let it reload. After that open synaptic package manager
system>administration>synaptic package manager.

Search for wicd and install it.Once it is done open it from applications>internet>Wicd

Hit refresh and u will see your wireless network. Go to preference and tick to enable Always show wired connection. Hope that will work. If it doesnt or mess up revert back to network manager. For that in synaptic package manager uninstall wicd and install network-manager and network-manager-gnome

Good luck!

---

### Post by HazeUK on 2008-06-14
I don't have internet on the PC, I'm using a laptop atm - and setting stuff up/transfering stuff over with my USB pen drive. How can i do it without internet?

---

### Post by nickdbliss on 2008-06-14
> **HazeUK said:**
> I don't have internet on the PC, I'm using a laptop atm - and setting stuff up/transfering stuff over with my USB pen drive. How can i do it without internet?

type the following from the terminal: sudo dpkg -i /path_to_the_package/name_of_the_package_to_install.deb

(Wicd file attached)

---

### Post by HazeUK on 2008-06-14
Conflicts with network manager, how do I disable that?

---

### Post by nickdbliss on 2008-06-14
go to synaptic package manager and remove the files named:
network manager and network-manager-gnome

---

### Post by HazeUK on 2008-06-14
How do I change it to dhcp? I think it's stil doing the roaming thing.. as I connect to router, it assigns me to 192.168.1.4 but I can't connect to any sites.

Ty

---

### Post by nickdbliss on 2008-06-14
> **HazeUK said:**
> How do I change it to dhcp? I think it's stil doing the roaming thing.. as I connect to router, it assigns me to 192.168.1.4 but I can't connect to any sites.

Ty

By default it is DHCP. When i connect to my wireless it obtains the ip automatically. When i used static in advanced settings it worked equally well. :) 
What does this shows? #ping [www.google.com](www.google.com) -c 5
#ping 192.168.1.1 -c 5
and sudo iwlist wlan0 scan

---

### Post by HazeUK on 2008-06-14
haze@Haze-Gamer:~$ ping [www.google.com](www.google.com) -c 5
PING [www.l.google.com](www.l.google.com) (66.249.93.99) 56(84) bytes of data.
64 bytes from [www.google.com](www.google.com) (66.249.93.99): icmp_seq=1 ttl=245 time=32.1 ms
64 bytes from [www.google.com](www.google.com) (66.249.93.99): icmp_seq=2 ttl=245 time=44.4 ms
64 bytes from [www.google.com](www.google.com) (66.249.93.99): icmp_seq=3 ttl=245 time=43.7 ms
64 bytes from [www.google.com](www.google.com) (66.249.93.99): icmp_seq=4 ttl=245 time=50.4 ms
64 bytes from [www.google.com](www.google.com) (66.249.93.99): icmp_seq=5 ttl=245 time=28.9 ms

--- [www.l.google.com](www.l.google.com) ping statistics ---
5 packets transmitted, 5 received, 0% packet loss, time 3999ms
rtt min/avg/max/mdev = 28.980/39.958/50.407/8.065 ms
haze@Haze-Gamer:~$ sudo iwlist wlan0 scan
[sudo] password for haze:
wlan0     Scan completed :
          Cell 01 - Address: 00:0F:3D:B4:56:C4
                    ESSID:"G604T_WIRELESS"
                    Mode:Master
                    Channel:6
                    Frequency:2.437 GHz
                    Signal level=-60 dBm  
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 22 Mb/s
                              6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Extra:tsf=00000013befa3030

haze@Haze-Gamer:~$

---

### Post by nickdbliss on 2008-06-14
> **HazeUK said:**
> haze@Haze-Gamer:~$ ping [www.google.com](www.google.com) -c 5
PING [www.l.google.com](www.l.google.com) (66.249.93.99) 56(84) bytes of data.
64 bytes from [www.google.com](www.google.com) (66.249.93.99): icmp_seq=1 ttl=245 time=32.1 ms
64 bytes from [www.google.com](www.google.com) (66.249.93.99): icmp_seq=2 ttl=245 time=44.4 ms
64 bytes from [www.google.com](www.google.com) (66.249.93.99): icmp_seq=3 ttl=245 time=43.7 ms
64 bytes from [www.google.com](www.google.com) (66.249.93.99): icmp_seq=4 ttl=245 time=50.4 ms
64 bytes from [www.google.com](www.google.com) (66.249.93.99): icmp_seq=5 ttl=245 time=28.9 ms

--- [www.l.google.com](www.l.google.com) ping statistics ---
5 packets transmitted, 5 received, 0% packet loss, time 3999ms
rtt min/avg/max/mdev = 28.980/39.958/50.407/8.065 ms



Are you kidding me? it is pinging google. so it should be able to open website buddy if not all then [www.google.com](www.google.com) for sure.

---

### Post by HazeUK on 2008-06-14
No sites work for me, I'm using firefox. I could try and install opera and test that but I doubt it's different. Pidgin isn't signing in either.

---

### Post by Blackneto on 2008-06-14
I don't know if it's relevant but i've been battling with network manager on my laptop with this new release.
No problems with networking on the server I just upgraded to HH, but then again I don't use Network Manager on it.

Anyway. My wireless connection (broadcom) drops at random and it takes a while for it to come back.
Funny thing is it still has an IP (static for home) and my router sees it but theres no connectivity.
I got to poking around and noticed that the default gw disappears.

when it's working it looks like this:
[PHP]Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.38.0    0.0.0.0         255.255.255.0   U     0      0        0 vmnet8
172.16.135.0    0.0.0.0         255.255.255.0   U     0      0        0 vmnet1
172.16.1.0      0.0.0.0         255.255.255.0   U     0      0        0 wlan0
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 wlan0
0.0.0.0         172.16.1.1      0.0.0.0         UG    100    0        0 wlan0[/PHP]

but when it's borked it looks like this:
[PHP]Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.38.0    0.0.0.0         255.255.255.0   U     0      0        0 vmnet8
172.16.135.0    0.0.0.0         255.255.255.0   U     0      0        0 vmnet1
172.16.1.0      0.0.0.0         255.255.255.0   U     0      0        0 wlan0[/PHP]

I try to add the default gateway but it keeps failing.

Really aggravating.
I don't know if this info would help the OP but from what i'm reading lots of people are having this issue.
I think I will try that third party app wicd and see if it works better.

---

### Post by nickdbliss on 2008-06-14
> **HazeUK said:**
> No sites work for me, I'm using firefox. I could try and install opera and test that but I doubt it's different. Pidgin isn't signing in either.

This completely surprised me lol. Is there any firewall installed by you? I am not sure now what is causing this problem. Pinging google reflects that data is travelling from ur pc to google server and coming back. Short of ideas here my friend.


Hi black i hope it works for you.

---

### Post by HazeUK on 2008-06-14
Does anyone else have an idea what this could be? It could be so obvious we're missing it. Any suggestions welcome.

---

### Post by HazeUK on 2008-06-15
Any ideas guys? Really want to get this sorted.

Thanks for all replies :)

---

### Post by nickdbliss on 2008-06-15
Give me the output of this file
#sudo gedit /etc/network/interfaces

And also try disabling ipv6, it might be causing the problem.Open file
#sudo gedit /etc/modprobe.d/aliases

find the line:

alias net-pf-10 ipv6

and replace with:

alias net-pf-10 off #ipv6

Since you are able to resolve [www.google.com](www.google.com) during pinging, i believe it is ipv6 problem. Disabling it should solve your problem 99%. Cheers

Waiting for your reply....

---

### Post by HazeUK on 2008-06-15
Ok, internet works now, I can connect to stuff and load sites - I'm posting from linux now - though sometimes my internet goes REALLY  slow, everything loads crap and my d/l speed is low.

But saying that.. sometimes it's as fast as xp.


My install/remove program from menu also can't seem to get stuff from the internet... it just refreshes all the time without trying to apply anything.

I also don't quite understand the synaptic manager :)

But many many thanks for helping me get internet connecting!!

---

### Post by nickdbliss on 2008-06-15
> **HazeUK said:**
> Ok, internet works now, I can connect to stuff and load sites - I'm posting from linux now - though sometimes my internet goes REALLY  slow, everything loads crap and my d/l speed is low.

But saying that.. sometimes it's as fast as xp.


My install/remove program from menu also can't seem to get stuff from the internet... it just refreshes all the time without trying to apply anything.

I also don't quite understand the synaptic manager :)

But many many thanks for helping me get internet connecting!!


I am glad that you are able to connect to the internet now. Its my pleasure buddy. 
And add/remove program and synaptic package manager are very easy to use my friend. It displays the programs that are kept on the website of ubuntu packages. When u click to install it collects them from the site n downloads n install. In the previous post i posted the method to install wicd. remember? i gave u something to add to software sources. Whatever source like some website etc u add there, synaptic shows u the programs that are on that source. U will find people often telling u that way to install something. It can be done via terminal as well so dont be confused. Installation can be done manually like u did with wicd,but why use it when ubuntu can itself take care of things.;) 

P.S Connection slow or fast problem is basically related to the driver you are using. 

Have fun!! And yeah mark this post as solved!! Cheers

---

### Post by Blackneto on 2008-06-29
it took 2 weeks but i finally got rid of network-manager
i installed wicd but will just use it for roaming.
I manually configured my connections at home and not a drop in the past 24 hrs.
I wonder what changed with the way network-manager works. I never had an issue with it prior to hardy.

thanks to all for the info in this post.

---

### Post by nickdbliss on 2008-06-30
> **Blackneto said:**
> it took 2 weeks but i finally got rid of network-manager
i installed wicd but will just use it for roaming.
I manually configured my connections at home and not a drop in the past 24 hrs.
I wonder what changed with the way network-manager works. I never had an issue with it prior to hardy.

thanks to all for the info in this post.

ALways welcomed buddy.

---

