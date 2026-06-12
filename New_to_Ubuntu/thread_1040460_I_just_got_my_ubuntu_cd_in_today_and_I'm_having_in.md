---
title: "I just got my ubuntu cd in today and I'm having internet troubles"
date: 2009-01-15
forum: New to Ubuntu
---

### Post by Monark on 2009-01-15
I got the CD and promptly installed in on my laptop (I'm on my desktop currently). 

Previously, the laptop had windows vista, and installed Ubuntu over it. Version 8.10 I believe.

Before the install I had 0 internet problems. However, after the install my laptop doesn't even acknowledge my connection.

I've looked all over Google for the right answer to this problem, and I've found people with similar issues, but not the one I have exactly. Any help would be awesome.

If it matters it is an Ethernet connection. The modem is a Motorola SBV5222 SURFboard Digital Voice Modem. My ISP is my cable provider.

---

### Post by mikewhatever on 2009-01-15
What do you mean by 'before the install', with Vista or running from Ubuntu cd? Can you post the outputs of the following commands from Applications->Accessories->Terminal.
ifconfig
sudo lshw -C network

---

### Post by Monark on 2009-01-15
> **mikewhatever said:**
> What do you mean by 'before the install', with Vista or running from Ubuntu cd? Can you post the outputs of the following commands from Applications->Accessories->Terminal.
ifconfig
sudo lshw -C network

Ok, I'm working on it. Its kind of hard to type up everything that's on another comp screen on to this one. But I'll get on it. It does say network DISABLED I have no idea if that's important or not. Yes the internet was fine with Vista.

---

### Post by Monark on 2009-01-15
eth0     Link encap:Ethernet  HWaddr 00:1e:68:4e:40:b4
         inet6 addr: fe80::21e:68ff:fe4e:40b4/64 Scope:Link
         UP BROADCAST RUNNING MULTICAST   MTU:1500  Metric:1
         RX packets:11518 errors:0 dropped:0 overruns:0 frame:0
         TX packets:19 errors:0 dropped:0 overruns:0 carrier:0
         collisions:0 txqueuelen:1000
         RX bytes:691080 (691.0 KB)   TX bytes:4914 (4.9 KB)

lo       Link encap:Local Loopback
         inet addr:127.0.0.1  Mask:255.0.0.0
         inet6 addr:  ::1/128 Scope:Host
         UP LOOPBACK RUNNING  MTU:16436  Metric:1
         RX packets: 258 errors:0 dropped:0 overruns:0 frame:0
         TX packets: 258 errors:0 dropped:0 overruns:0 carrier:0
         collisions:0 txequeuelen:0
         RX bytes:16440 (16.4 KB)   TX bytes:16440 (16.4 KB)

Ok, thats from typing in "ifconfig" I'll get to work on copying over the other stuff next.

---

### Post by mapltux on 2009-01-15
System -> Administration -> Hardware Drivers

Install the hardware driver, if you can connect through the ethernet cable from your router that might work out..

cheers!

---

### Post by Monark on 2009-01-15
It says that No proprietary drivers are in use on this system.

---

### Post by mikewhatever on 2009-01-15
> **Monark said:**
> Ok, I'm working on it. Its kind of hard to type up everything that's on another comp screen on to this one. But I'll get on it. It does say network DISABLED I have no idea if that's important or not. Yes the internet was fine with Vista.

If it helps, I usually use a pen and a piece of paper.
Network drivers are usually installed by default, even if proprietary.

---

### Post by albinootje on 2009-01-15
> **Monark said:**
> Ok, I'm working on it. Its kind of hard to type up everything that's on another comp screen on to this one. But I'll get on it. It does say network DISABLED I have no idea if that's important or not. Yes the internet was fine with Vista.

Please copy&paste the output to a text file and save that on an usb stick or usb disk, and then copy&paste it here.

```

sudo lshw -C network
lspci
lsmod
ifconfig -a
route -n
cat /etc/resolv.conf

```

---

### Post by Monark on 2009-01-15
*-network DISABLED
description: Wireless interface
product: PRO/Wireless 3945ABG [Golan] Network Connection
vendor: Intel Corporation
physical id: 0
bus info: pci@0000:02:00.0
logical name: wmaster0
version: 02
serial: 00:1b:77:9d:61:11
width: 32 bits
clock: 33MHz
capabilities: pm msi pciexpress cap_list logical ethernet physical wireless

configuration: broadcast=yes driver=iwl3945 latency=0 module=iwl3945 multicast=yes wireless=IEEE 802.11abg

*-network
description: Ethernet interface
product: PRO/100 VE Network Connection
vendor: Intel Corporation
physical id: 8
bus info: pci@0000:05:08.0
logical name: eth0
version: 02
serial: 00:1e:68:4e:40:b4
size: 100MB/s
width: 32 bits
clock: 33MHz
capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation

configuration: autonegotiation=on broadcast=yes driver=e100 driverversion=3.5.23-k4-NAPI duplex=full firmware=N/A latency=64 link=yes maxlatency=56 mingnt=8 module=e100 multicast=yes port=MII speed=100MB/s
*-network DISABLED
description: Ethernet interface
physical id: 1
logical name: pan0
serial: 12:84:5f:6e:fb:44
capabilities: ethernet physical
configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast= yes

---

### Post by albinootje on 2009-01-15
> **Monark said:**
> 
*-network
description: Ethernet interface
product: PRO/100 VE Network Connection
vendor: Intel Corporation
physical id: 8
bus info: pci@0000:05:08.0
logical name: eth0
version: 02
serial: 00:1e:68:4e:40:b4
size: 100MB/s
width: 32 bits
clock: 33MHz
capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation

configuration: autonegotiation=on broadcast=yes driver=e100 driverversion=3.5.23-k4-NAPI duplex=full firmware=N/A latency=64 link=yes maxlatency=56 mingnt=8 module=e100 multicast=yes port=MII speed=100MB/s


Okay, thanks, what happens when you run the following :
```

sudo dhclient
ping -c4 62.108.1.65

```

---

### Post by Monark on 2009-01-15
> **albinootje said:**
> Please copy&paste the output to a text file and save that on an usb stick or usb disk, and then copy&paste it here.

```

sudo lshw -C network
lspci
lsmod
ifconfig -a
route -n
cat /etc/resolv.conf

```

I don't know if its a bad sign or not, but for the last one you asked for it was saying something close to it not existing. I'm working on transferring the text file now.

---

### Post by albinootje on 2009-01-15
> **Monark said:**
> I don't know if its a bad sign or not, but for the last one you asked for it was saying something close to it not existing. I'm working on transferring the text file now.

That /etc/resolv.conf doesn't exist, is not good, but we can easily fix that.
More important is the result *and* output of :
```

sudo dhclient

```

---

### Post by Monark on 2009-01-15
I'm having trouble with the info transfer from before, but heres the most recent data you asked for. Also now its reading wireless connections in the area, but no luck with the Ethernet. I should add there was a tiny blip of reaction from the computer acknowledging an internet connection during a part of the sudo dhclient.

sudo dhclient

Internet Systems Consortium DHCP Client V3.1.1
Copyright 2004-2008 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www/isc.org/sw/dhcp](http://www/isc.org/sw/dhcp)

wmaster0: unknown hardware address type 801
wmaster0: unknown hardware address type 801
Listening on LPF/pan0/12:24:5f:6e:fb:44
Sending on LPF/pan0/12:24:5f:6e:fb:44
Listening on LPF/wlan0/00:1b:77:9d:61:11
Sending on LPF/wlan0/00:1b:77:9d:61:11
Listening on LPF/wmaster0
Sending on LPF/wmaster0
Listening on LPF/eth0/00:1e:68:4e:40:b4
Sending on LPF/eth0/00:1e:68:4e:40:b4
Sending on Socket/fallback
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 4
DHCPDISVOCER on wmaster to 255.255.255.255 port 67 interval 4
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 4
DHCPDISCOVER on pan0 to 255.255.255.255 port 67 interval 7
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 6
DHCPDISCOVER on wmaster0 to 255.255.255.255 port 67 interval 5
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 10
DHCPDISCOVER on pan0 to 255.255.255.255 port 67 interval 10
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 12
DHCPDISCOVER on wmaster0 to 255.255.255.255 port 67 interval 5
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 17
DHCPDISCOVER on wmaster0 to 255.255.255.255 port 67 interval 8
DHCPDISCOVER on pan0 to 255.255.255.255 port 67 interval 8
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 16
DHCPDISCOVER on wmaster0 to 255.255.255.255 port 67 interval 8
DHCPDISCOVER on pan0 to 255.255.255.255 port 67 interval 18
DHCPDISCOVER on wmaster0 to 255.255.255.255 port 67 interval 15
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 20
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 12
DHCPDISCOVER on pan0 to 255.255.255.255 port 67 interval 18
DHCPDISCOVER on wmaster0 to 255.255.255.255 port 67 interval 16
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 11
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 10
No DHCPOFFERS received
No working leases in persistent database - sleeping.

ping -c4 62.108.1.65
PING 62.108.1.65 (62.108.1.65) 56(84) bytes of data
From 169.254.4.186 icmp_seq=2 Destinantion Host Unreachable
From 169.254.4.186 icmp_seq=3 Destinantion Host Unreachable
From 169.254.4.186 icmp_seq=4 Destinantion Host Unreachable

--- 62.108.1.65 ping statistics ---
4 packets transmitted, 0 received, +3 errors, 100% packet loss, time 2999ms, pipe 3

---

### Post by albinootje on 2009-01-15
Thanks for the output of "sudo dhclient".

Although your network card is an Intel card, and not a Realtek network card, perhaps this is interesting to read, and to try (if possible) :

[http://wiki.archlinux.org/index.php/Configuring_network#Realtek_No_Link_.2F_WOL_issue](http://wiki.archlinux.org/index.php/Configuring_network#Realtek_No_Link_.2F_WOL_issue)

---

### Post by Monark on 2009-01-15
> **albinootje said:**
> Thanks for the output of "sudo dhclient".

Although your network card is an Intel card, and not a Realtek network card, perhaps this is interesting to read, and to try (if possible) :

[http://wiki.archlinux.org/index.php/Configuring_network#Realtek_No_Link_.2F_WOL_issue](http://wiki.archlinux.org/index.php/Configuring_network#Realtek_No_Link_.2F_WOL_issue)

No luck. I think I might just pony up for a wireless modem,  if all else fails since its reading wireless connections perfectly.

Scratch that. It just looked like it was.

On some of the help instructions provided with Ubuntu, it says to go to system then to administration and then to network. But I don't even have a network as an option under administration. You think that has something to do with anything?

---

### Post by albinootje on 2009-01-15
> **Monark said:**
>  On some of the help instructions provided with Ubuntu, it says to go to system then to administration and then to network. But I don't even have a network as an option under administration. You think that has something to do with anything?

In my opinion it makes much more sense to make your network card working, or even have another network card in your computer, rather than buying a wireless modem.

Can you provide the output of :
```

ipconfig /all

```
from your MS-Windows machine (screenshot) ?
Then we can give Ubuntu a static ip address based on those settings.

---

### Post by Monark on 2009-01-15
> **albinootje said:**
> In my opinion it makes much more sense to make your network card working, or even have another network card in your computer, rather than buying a wireless modem.

Can you provide the output of :
```

ipconfig /all

```
from your MS-Windows machine (screenshot) ?
Then we can give Ubuntu a static ip address based on those settings.

I wish I knew exactly how to do that.

I typed it into Run. and a window popped up a and dissapeared very quickly.

---

### Post by Monark on 2009-01-15
Ok I figured it out. Ok whoa that came out kind of small. Let me try again.

OK its not much better but you might be able to see the number this time.

---

### Post by albinootje on 2009-01-15
> **Monark said:**
> Ok I figured it out. Ok whoa that came out kind of small. Let me try again.

Okay, thanks! It's readable enough to see that you're not using bridged mode on your dsl-modem/router or cable-modem, but you're using routing-mode.
You are not in a LAN, but your machine got the public ip address right away it looks like.

Did you have to install extra software in your MS-Windows installation to make your internet connection work ?

It is possible that your ISP uses authentication to make the internet connection. 
In Linux you would need pppoe or similar to make the connection then.

Can you find out whether your ISP has more information about the different possibilities to configure your DLS-modem/router or cable-modem ?

---

### Post by Monark on 2009-01-15
Its funny I just switched over to cable on Monday. And it was just plug and play. So I don't think it has any authentication process, and certainly there was no software that came with it

---

### Post by Sealbhach on 2009-01-15
> **Monark said:**
> 

On some of the help instructions provided with Ubuntu, it says to go to system then to administration and then to network. But I don't even have a network as an option under administration. You think that has something to do with anything?

In 8.10, it is in System/Preferences/Network Configuration.

Hope you get it working soon dude.

.

---

### Post by b0b138 on 2009-01-15
Try turning the modem off and back on after booting to linux.

---

### Post by Monark on 2009-01-15
> **b0b138 said:**
> Try turning the modem off and back on after booting to linux.

Did that. The link light (I think that's what its called) reacted a little. But ultimately it was a no go.

---

### Post by albinootje on 2009-01-15
> **Monark said:**
> Its funny I just switched over to cable on Monday. And it was just plug and play. So I don't think it has any authentication process, and certainly there was no software that came with it

Okay, what happens when you boot in Ubuntu, then restart the cable-modem, and then check internet connectivity.
If it still doesn't work, try again :
```

sudo dhclient

```
and report back.

---

### Post by Monark on 2009-01-15
> **albinootje said:**
> Okay, what happens when you boot in Ubuntu, then restart the cable-modem, and then check internet connectivity.
If it still doesn't work, try again :
```

sudo dhclient

```
and report back.

Hey it works now. I did exactly what you said. Do you still want me to do sudo dhclient?

I want to thank everyone here for the help. I absoultely love ubuntu, and the lack of internet access was being a problem, and having wiped Vista off the laptop it would have been a bigger problem. So thank you guys very much.

---

### Post by albinootje on 2009-01-15
> **Monark said:**
> Hey it works now. I did exactly what you said. 

Great!
> 
Do you still want me to do sudo dhclient?

No. It's fine like this.
> 
I want to thank everyone here for the help. I absoultely love ubuntu, and the lack of internet access was being a problem, and having wiped Vista off the laptop it would have been a bigger problem. So thank you guys very much.

Glad you are online with Ubuntu now.
Enjoy! :)

---

### Post by Monark on 2009-01-15
I hope this isn't a fluke with it working, lol.

---

### Post by Vantrax on 2009-01-15
> **Monark said:**
> I hope this isn't a fluke with it working, lol.

Some modems like to be on when the computer is booted up, others like it the other way. It depends on how it works. Usually if your connected to the modem when you start it up you will have no problems.

Now that you have it sorted, it should stay that way. All the commands they asked for gave information, but didn't change anything.

---

### Post by Monark on 2009-01-18
> **Vantrax said:**
> Some modems like to be on when the computer is booted up, others like it the other way. It depends on how it works. Usually if your connected to the modem when you start it up you will have no problems.

Now that you have it sorted, it should stay that way. All the commands they asked for gave information, but didn't change anything.

It actually seems like the modem is "latching on" to a computer then not letting go. Today I tried to use my desktop for the first time since the ubuntu install, and i had to reset the modem for the Internet to work on it. Just now I got home went on to the laptop, and no Internet signal. I reset the modem and now it works on the laptop but not on the desktop. I guess its the modem. Its quite a pain, especially since the modem doesn't have a reset or on/off button. I literally have to unplug it from the electrical socket to reset. Oh well, better than nothing, lol.

---

### Post by Monark on 2009-01-18
So am I stuck with this issue?

---

