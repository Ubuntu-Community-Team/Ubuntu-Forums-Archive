---
title: "My Asus onboard network card won't work"
date: 2008-06-19
forum: Networking &amp; Wireless
---

### Post by matty-K on 2008-06-19
I have an Asus A8n32-SLi motherboard with an onboard ethernet card.

I just did a fresh install of Ubuntu 7.10 Gutsy and I have connected an ethernet from my router (Linksys WRT54GS) to my motherboard ethernet port. The activity light is lit up on my motherboard.

I am able to access my router's configuration from Firefox, but I cannot access any websites! Any ideas? Is there a port I need to forward in my router??

---

### Post by matty-K on 2008-06-19
Somebody must have an idea! Is there a setting I have to enable first somewhere? Or is it supposed to be plug-n-play in theory?

---

### Post by molotov00 on 2008-06-19
Wow.

"My Asus onboard network card won't work"

Then how are you accessing the admin area on the router?

Answer: your netork card works. Problem solved.

Or... are you actually saying that your modem/router is not configured properly? If this is the case, read the manual for the modem/router.

---

### Post by Lifeis on 2008-06-19
Yeah, sounds like your router isnt configured to connect to your internet line. Do you have other systems connected to the router and they can access the internet?

---

### Post by matty-K on 2008-06-19
Yeah sorry about the confusion, after some testing I found out on my own that it wasn't the card itself. I tried to edit the title of this thread but found that I couldn't. I was assuming it was the card because after Googling for answers on this card, I received an entire page of links reporting bugs with my particular card.

Yeah basically I am not sure how to configure the connection to connect to my router. Other computers on my router connect to the internet no problem.

I realized after that my motherboard's two ethernet ports actually use different chipsets. One is the Marvell tech. one that I mentioned earlier. The second one, according to lspci, is an nVidia port. This port, when connected, also is able to open my router's config page but unable to connect to any websites.

Any ideas how I can configure this properly?

---

### Post by chili555 on 2008-06-19
Let's see, from a terminal:```
ifconfig
cat /etc/resolv.conf
```Did you set static IP addresses for your interface or DHCP?

---

### Post by molotov00 on 2008-06-19
First thing I'd do is plug this computer into a port in the router that I know works for another computer.

Has this computer ever been able to access the internet? What router are you using?

Also, how are you assigning IPs?

---

### Post by Lifeis on 2008-06-19
I dont get how your pc can access the routers config, therefore is connected to the router, but cant access the internet. I cant help you there my friend, if the other systems on your network were having the same problem, then I could help you configure the router to connect to your internet line. But if its connected already but not feeding your machine then its beyond my experience buddy. Sorry I can't help you out.
- Laters

---

### Post by matty-K on 2008-06-19
Here, I'll provide more info /background knowledge...

Moltov00: I already mentioned I'm using a Linksys WRT54GS router. 

I have never used these wired connections before because I have a wireless NIC card that I use on this PC to connect to that router, the WMP54GS. In Windows, these wired ports never showed activity when connected but it didn't matter because I have the wireless NIC.

I wanted to try the Wired connection because my NIC uses the Broadcom chipset that everyone has problems with and I wanted to have a temp. fix until I solved that problem. 

In Windows, I have sort of a weird setup that seems to work. I have a static IP set, but in my router it's configured to the DHCP setting. Either way, it works. Therefore, I'm not entirely sure whether to set my connection to a DHCP or static IP. 

chili555
I'm going to log out of Windows here and into my Ubuntu boot and try that code. I'll report back right after.

---

### Post by chili555 on 2008-06-19
> In Windows, I have sort of a weird setup that seems to work. I have a static IP set, but in my router it's configured to the DHCP setting. Either way, it works. Therefore, I'm not entirely sure whether to set my connection to a DHCP or static IP.It's not a weird setup at all; I use it as well. I just need to be careful to set static addresses outside the range used by the DHCP server. I set my router to lease DHCP addresses from 192.168.1.100 to 192.168.1.109. My static addresses are set from x.115 on up. It's a common misconception that if you enable DHCP on your router, that it may *only* connect with DHCP. That's not true, as you and I can prove. Set DHCP or static as you prefer; the only difference is that, with static, it's harder to tell if you are actually connected, and, as I suspect we will learn in a few minutes, if you set static addresses, the router will not automatically populate resolv.conf, which is needed to resolve names ([www.google.com](www.google.com), for example) to IP addresses (74.125.45.104). Without /etc/resolv.conf, you can surf by number but not name. Hence, router, yes; Google, no.

---

### Post by matty-K on 2008-06-19
Haha, makes sense. Alright I'm going to go run that code quickly and report the info back.

I will report it for both ethernet ports, as they appear as two seperate wired connections in my dropdown list on the taskbar.

---

### Post by matty-K on 2008-06-19
Ok I've got the information here... Each code box corresponds to the network I had plugged in.

1)

[IMG]http://img522.imageshack.us/img522/9839/screenshotub5.png[/IMG]

```
matt@matt-desktop:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:17:31:01:D2:84  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:19 Base address:0xc000 

eth1      Link encap:Ethernet  HWaddr 00:17:31:01:C6:0B  
          inet addr:192.168.1.149  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::217:31ff:fe01:c60b/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:4 errors:0 dropped:0 overruns:0 frame:0
          TX packets:38 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:684 (684.0 b)  TX bytes:5162 (5.0 KB)
          Interrupt:21 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

matt@matt-desktop:~$ 

matt@matt-desktop:~$ cat /etc/resolv.conf
# generated by NetworkManager, do not edit!

search ed.shawcable.net


nameserver 68.151.111.24

```

2)

[IMG]http://img294.imageshack.us/img294/6744/screenshot1ta7.png[/IMG]

```
matt@matt-desktop:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:17:31:01:D2:84  
          inet addr:192.168.1.148  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::217:31ff:fe01:d284/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:9 errors:0 dropped:0 overruns:0 frame:0
          TX packets:41 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1443 (1.4 KB)  TX bytes:5627 (5.4 KB)
          Interrupt:19 Base address:0xc000 

eth1      Link encap:Ethernet  HWaddr 00:17:31:01:C6:0B  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:4 errors:0 dropped:0 overruns:0 frame:0
          TX packets:38 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:684 (684.0 b)  TX bytes:5162 (5.0 KB)
          Interrupt:21 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
matt@matt-desktop:~$ cat /etc/resolv.conf
# generated by NetworkManager, do not edit!

search ed.shawcable.net


nameserver 68.151.111.24

```

Hope that sheds some light on the subject... I guess this means eth0 is my nVidia connection and eth1 is my Marvell connection, which makes sense because those ones are labelled 1 and 2 respectively on my tower.

---

### Post by chili555 on 2008-06-19
For each connection, may we see:```
ping -c3 www.google.com
ping -c3 74.125.45.104
```If you get ping returns from the number, but not name, please *sudo gedit /etc/resolv.conf* and add a single symbol like this:```
# generated by NetworkManager, do not edit!

**#**search ed.shawcable.net


nameserver 68.151.111.24
```Proofread, save and close. Use any text editor if you don't have gedit; kwrite, kate, nano or vim will work. Then try your pings again.

On a stationary machine, you really don't need Network Manager. Let's talk about that another time.

---

### Post by matty-K on 2008-06-19
I'm from Canada and Google.com redirects to google.ca... That won't have an effect on the ping will it??

---

### Post by morpheus5 on 2008-06-19
use command
sudo dhclient
in the terminal, if it still doesnt work

use command
route
to check if your default destination goes to your gateway and check if your gateway is working.

---

### Post by chili555 on 2008-06-19
> I'm from Canada and Google.com redirects to google.ca... That won't have an effect on the ping will it??I doubt it, but try it both ways; it just takes a few extra seconds.

---

### Post by matty-K on 2008-06-19
Alright so chili555 you sort of called it... I was able to ping 74.125.45.104 no problem, but pinging [www.google.com](www.google.com) (and [www.google.ca](www.google.ca)) did not work.

I added the # sign in front of that line in the /etc/resolv.conf file and saved it but I was still not able to ping [www.google.com](www.google.com).

---

### Post by CheShA on 2008-06-19
add the following lines to /etc/resolv.conf :

```

nameserver 208.67.222.222
nameserver 208.67.220.220
```

Then just to be on the safe side, do 

```
 sudo /etc/init.d/networking restart 
```

And see if it works.

The problem is that your DNS settings are being picked up automatically. When you reboot (in fact, every so often even if you don't reboot) your /etc/resolv.conf will be rewritten again.  A better bet may be to check the DNS settings on your router.

---

### Post by matty-K on 2008-06-19
I will try that... Here's a question, do the DNS servers that show up in my "ipconfig /all" in windows have anything to do with the DNS servers in Linux? Or will they be seperate?

---

### Post by matty-K on 2008-06-19
Hey, so I tried CheShA's method and now I am able to ping [www.google.com](www.google.com) and the ip.

I am still unable to connect to any webpages in Firefox. And CheShA was right, restarting the computer removed the symbol from the resolv.conf and reverted it back to it's original state.

---

### Post by matty-K on 2008-06-20
Any other ideas to this?

---

### Post by chili555 on 2008-06-20
Please let us see:```
sudo ethtool eth0
```Substitute the interface you are actually connected to if it's not eth0.

---

### Post by matty-K on 2008-06-20
Here's the thing... I have both connections, eth0 and eth1 are the nVidia and Marvell ports... Both connect to my router but not the internet so should I just pick one? I'll go eth0 since that's Port 1 on my mobo.

EDIT

The log that came back from typing "sudo ethtool eth0"

matt@matt-desktop:~$ sudo ethtool eth0 

[sudo] password for matt: 
Settings for eth0: 
        Supported ports: [ MII ] 
        Supported link modes:   10baseT/Half 10baseT/Full  
                                100baseT/Half 100baseT/Full  
                                1000baseT/Full  
        Supports auto-negotiation: Yes 
        Advertised link modes:  10baseT/Half 10baseT/Full  
                                100baseT/Half 100baseT/Full  
                                1000baseT/Full  
        Advertised auto-negotiation: Yes 
        Speed: 100Mb/s 
        Duplex: Full 
        Port: MII 
        PHYAD: 1 
        Transceiver: external 
        Auto-negotiation: on 
        Supports Wake-on: g 
        Wake-on: d 
        Link detected: yes

---

### Post by chili555 on 2008-06-20
> Both connect to my routerWhy? What are you trying to accomplish with that? Without some serious configuration steps, you will not get two IP addresses assigned to your computer. Even if you did, what would you be trying to do?

Please disconnect ethernet port 2 and reboot. Do you now have a correctly working connection?```
ifconfig
ping -c3 www.google.com
```Thanks.

---

### Post by matty-K on 2008-06-20
Oh no, I don't mean that they are both connected simultaneously... I'm only saying if I unplug the ethernet from port one and plug it into port 2, they are both functioning properly, but use two different chipsets.

EDIT
```

matt@matt-desktop:~$ ifconfig 
eth0      Link encap:Ethernet  HWaddr 00:17:31:01:D2:84   
          inet addr:192.168.1.148  Bcast:192.168.1.255  Mask:255.255.255.0 
          inet6 addr: fe80::217:31ff:fe01:d284/64 Scope:Link 
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1 
          RX packets:2 errors:0 dropped:0 overruns:0 frame:0 
          TX packets:35 errors:0 dropped:0 overruns:0 carrier:0 
          collisions:0 txqueuelen:1000  
          RX bytes:420 (420.0 b)  TX bytes:5184 (5.0 KB) 
          Interrupt:19 Base address:0x2000  
 
eth1      Link encap:Ethernet  HWaddr 00:17:31:01:C6:0B   
          UP BROADCAST MULTICAST  MTU:1500  Metric:1 
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0 
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0 
          collisions:0 txqueuelen:1000  
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b) 
          Interrupt:18  
 
lo        Link encap:Local Loopback   
          inet addr:127.0.0.1  Mask:255.0.0.0 
          inet6 addr: ::1/128 Scope:Host 
          UP LOOPBACK RUNNING  MTU:16436  Metric:1 
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0 
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0 
          collisions:0 txqueuelen:0  
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b) 
 
matt@matt-desktop:~$ ping -c3 www.google.com 
ping: unknown host www.google.com 
```

---

### Post by chili555 on 2008-06-20
> I don't mean that they are both connected simultaneously..Excellent! I can breathe again. Something is still a bit wacky. Let's take a look at:```
cat /etc/network/interfaces
sudo ifdown eth0 && sudo ifup -v eth0
```It has to be something simple we are missing. For now, let's concentrate on port #1, which I assume is the much beloved nVidia forcedeth ("forced death"?)

---

### Post by matty-K on 2008-06-20
The results of that test seem ugly...

```

matt@matt-desktop:~$ cat /etc/network/interfaces 
auto lo 
iface lo inet loopback 
 
 
 
 
matt@matt-desktop:~$ sudo ifdown eth0 && sudo ifup -v eth0 
[sudo] password for matt: 
ifdown: interface eth0 not configured 
Ignoring unknown interface eth0=eth0. 
matt@matt-desktop:~$  

```

---

### Post by chili555 on 2008-06-20
Let's *sudo gedit /etc/network/interfaces* and make the file look like:```
auto lo 
iface lo inet loopback 


auto eth0
iface eth0 inet dhcp

#auto eth1
iface eth1 inet dhcp
```Then re-run:```
sudo ifdown eth0 && sudo ifup -v eth0
```If we need static addresses, we will fix that later, once we connect correctly.

We are taking Network Manager out of the process, so we can see if NM or forced death is the real issue.

---

### Post by matty-K on 2008-06-20
Will the file I just edited with that code revert to it's original when I go back into Linux or will it stay? The resolv.conf reset after I rebooted...

```

matt@matt-desktop:~$ sudo gedit /etc/network/interfaces
[sudo] password for matt:
matt@matt-desktop:~$ sudo ifdown eth0 && sudo ifup -v eth0
ifdown: interface eth0 not configured
Configuring interface eth0=eth0 (inet)
run-parts --verbose /etc/network/if-pre-up.d
run-parts: executing /etc/network/if-pre-up.d/wireless-tools
run-parts: executing /etc/network/if-pre-up.d/wpasupplicant

dhclient3 -e IF_METRIC=100 -pf /var/run/dhclient.eth0.pid -lf /var/lib/dhcp3/dhclient.eth0.leases eth0
There is already a pid file /var/run/dhclient.eth0.pid with pid 134519120
Internet Systems Consortium DHCP Client V3.0.5
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

Listening on LPF/eth0/00:17:31:01:d2:84
Sending on   LPF/eth0/00:17:31:01:d2:84
Sending on   Socket/fallback
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 8
DHCPOFFER from 192.168.1.1
DHCPREQUEST on eth0 to 255.255.255.255 port 67
DHCPACK from 192.168.1.1
bound to 192.168.1.148 -- renewal in 32502 seconds.
run-parts --verbose /etc/network/if-up.d
run-parts: executing /etc/network/if-up.d/avahi-autoipd
run-parts: executing /etc/network/if-up.d/avahi-daemon
run-parts: executing /etc/network/if-up.d/mountnfs
run-parts: executing /etc/network/if-up.d/ntpdate
run-parts: executing /etc/network/if-up.d/wpasupplicant

```

---

### Post by chili555 on 2008-06-20
> DHCPACK from 192.168.1.1
bound to 192.168.1.148 -- renewal in 32502 seconds.Looks like you connected. Can you surf now?```
ping -c3 www.google.ca
```Firefox?

---

