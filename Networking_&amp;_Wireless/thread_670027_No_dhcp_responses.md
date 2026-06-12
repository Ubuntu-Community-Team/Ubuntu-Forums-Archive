---
title: "No dhcp responses"
date: 2008-01-17
forum: Networking &amp; Wireless
---

### Post by dreamer.redeemer on 2008-01-17
Hello, I'm new to this and i'm trying to get gutsy server edition to connect to the internet, but can't get a dhcp response. So far i've tried eth0 and eth1, both onboard, both static and dynamic addressing. Nothing has been working. I've read that maybe i need to stop or remove the network manager, but i'm hesitant to do that until i get more information. Any help would be appreciated!

---

### Post by kripkenstein on 2008-01-17
NetworkManager might be the issue, but first lets see some other things. Can you post the output of ```
ifconfig
``` and also the error messages you get when trying the things you mention?

---

### Post by zipperback on 2008-01-17
Please provide the output of the following:

```


lspci

ifconfig

iwconfig


```

Thank you

- zipperback
:popcorn:

---

### Post by dreamer.redeemer on 2008-01-17
ifconfig

eth0

link encap:ethernet HWaddr 00:1d:60:B7:66:59
inet addre:71.199.49.91 Bcast 71.199.51.255 Mask 255.255.252.0
UP BORADCAST MULTICAST MUT:1500 METRIC:1
RX PACKETS:0 ERRORS:0 DROPPED:0 OVERRUNS:0 FRAME:0
TX ""
COLLISIONS:0 TXQUEUELEN:1000
RX BYTES:0....
Interrupt 20: Base address:0x200

lo

inet addr:127.0.0.1 Mask:255.0.0.0
(if you need more let me know, typing this all)

lspci 

00:08.0 Bridge: nvidia MCP55 ethernet rev a3
00:09.0 ""

No wireless.


Also, hah, can you tell me how to stop the ping command?
The only reason I thought it might be the dhcp was because during the installation network auto-config the dhcp setup always failed, no matter what I tried, so i just skipped it without setup (yes, this is a fresh install, besides what i've tried to setup in /etc/network/interfaces). I suppose there could be other things I need to setup since i skipped that installation feature?

---

### Post by kripkenstein on 2008-01-17
What is the actual error you get?

To see if DHCP is an issue, try to run DHCP manually, do
```

sudo ifdown eth0
sudo ifup eth0
sudo dhclient eth0

```

---

### Post by dreamer.redeemer on 2008-01-17
For the sudo dhclient eth0 i get the no DHCPOFFERS recieved error.
However, i'm looking at the /etc/init.d/networking restart and it says "There is already pid file /var/run/dhclient.eth0.pid with pid 0"
that sounds like a problem, is it?

---

### Post by kripkenstein on 2008-01-17
> **dreamer.redeemer said:**
> For the sudo dhclient eth0 i get the no DHCPOFFERS recieved error.
However, i'm looking at the /etc/init.d/networking restart and it says "There is already pid file /var/run/dhclient.eth0.pid with pid 0"
that sounds like a problem, is it?
Actually no, I don't think it is. The "no DHCPOFFERS" sounds more relevant. Perhaps you can supply the entire output of dhclient...?

---

### Post by dreamer.redeemer on 2008-01-17
ok.

Listening on lpf/eth0/00:1D:60:b7:66:59
sending on ""
sending on socket/fallback
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 7
""
""
""
No DHCPOFFERS received.
no working leases in persistent databse - sleeping.

Thanks for the help, and for being so quick!

---

### Post by kripkenstein on 2008-01-17
Ok, now please show me the complete output of ```
/etc/init.d/networking restart
```

---

### Post by dreamer.redeemer on 2008-01-17
already pid, killed old, removed pid

already a pid file with pid 0


Listening on lpf/eth0/00:1D:60:b7:66:59
sending on ""
sending on socket/fallback
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 7
""
""
""
No DHCPOFFERS received.
no working leases in persistent databse - sleeping.

would you mind letting me know a bit of what you're thinking so i can try and follow along, to try and know why you want these bits of info?

---

### Post by kripkenstein on 2008-01-17
Well, it seems that the network interface is functioning normally, and the issue is that it doesn't receive a DHCP offer. So, the question is why.

What kind of network are you on? Do you have a DHCP server that should be responding to your requests? (If so, is the physical connection to it ok?) Or should this computer normally use a static IP and not DHCP?

---

### Post by dreamer.redeemer on 2008-01-17
Well i've tried running it straight to the cable modem and didn't get it to work, but right now it's hooked up to the second port on my xp box. The connection is properly bridged, as i can use my xp laptop to connect to the net just fine. using the bridge in ubuntu i've tried dhcp and static ip on both sides in all possible combinations with no luck. And i've been keeping track of ifconfig and rebooting as necessary.

There is some reasonable possibility that i screwed up on the way, i have been up all night, ha.

and i tried sudo apt-get remove network-manager 
it says E: file not found i think. Something like that.

---

### Post by kripkenstein on 2008-01-17
Hmm, I am not familiar with how XP handles network sharing. It could be via DHCP, or not. You can see what your laptop is doing that works.

NetworkManager might be the issue. To check, you can stop it from running and then try networking. To stop it, do
```

killall NetworkManager
killall NetworkManagerDispatcher
killall nm-applet

```

---

### Post by dreamer.redeemer on 2008-01-17
On my laptop the ip was dynamically assigned. Thus i got the ip anyway and tried on the ubuntu box both dhcp and static, with the ip that my laptop spit out. Didn't work.

For those kill commands for network manager, all returned "no process killed"  :confused:

---

### Post by kripkenstein on 2008-01-17
Well, this is pretty strange...

Perhaps take a look at your log files (system->administration->system log). In particular, see what messages are added when you restart networking.

---

### Post by dreamer.redeemer on 2008-01-17
The only new information is:

ntpdate[4584]: can't find host ntp.ubuntu.com
ntpdate[4584]: no servers can be used, exiting

really, thanks for your help, all the other threads i found on this were abandoned.

For some other command, i'm not sure which, i got 

kernel: eth0: no link during initialization
kernel: ADDRCONF(NETDEV_UP): eth0: link is not ready

please don't tell me that means i have the rj45 in the wrong port. ha

---

### Post by kripkenstein on 2008-01-17
> **dreamer.redeemer said:**
> The only new information is:

ntpdate[4584]: can't find host ntp.ubuntu.com
ntpdate[4584]: no servers can be used, exiting

This can be ignored.
> 
For some other command, i'm not sure which, i got 

kernel: eth0: no link during initialization
kernel: ADDRCONF(NETDEV_UP): eth0: link is not ready

please don't tell me that means i have the rj45 in the wrong port. ha
This seems critical. Are you sure the network hardware in this computer is functioning correctly? Does it run ok when booting into a different OS?

Otherwise, perhaps there is a driver issue here.

---

### Post by dreamer.redeemer on 2008-01-17
I will download knoppix and see if i can get the connection running there.

---

### Post by dreamer.redeemer on 2008-01-18
So far i'm unable to get the network to work in knoppix. I can't even get it to show eth0 in ifconfig. While it could be that the nic is faulty, i'm thinking it has something to do with the nvidia mcp55. I've read around something about forcedeth...? I'm really at a loss.

---

### Post by kripkenstein on 2008-01-18
Is this a new computer? Or have you seen the NIC work in some other OS previously?

---

### Post by dreamer.redeemer on 2008-01-18
Yeah, it's a new computer. I've been avoiding it, but i'll try to install windoz and see if i can get it to work there, just to rule out a faulty motherboard. I suppose i might be able to find a cheap pci nic...

---

### Post by kripkenstein on 2008-01-18
Well, I hope it isn't a hardware issue. Good luck.

At this point my only guesses would be hardware or a driver issue. The driver issue might be relevant because its a new computer, perhaps the NIC isn't well-supported by the kernel yet. You can do a search for other people using the same NIC to see if there are other reports of problems and possible solutions.

---

### Post by dreamer.redeemer on 2008-01-22
Well i got the new nic here. I made sure to buy one that wasn't cutting edge so it should have driver support. Anyway, it's in, i made sure it was assigned eth2, changed the interface to eth2, and attempted dhclient eth2 with **no luck.**

---

### Post by kripkenstein on 2008-01-22
> **dreamer.redeemer said:**
> Well i got the new nic here. I made sure to buy one that wasn't cutting edge so it should have driver support. Anyway, it's in, i made sure it was assigned eth2, changed the interface to eth2, and attempted dhclient eth2 with **no luck.**
Sorry to hear that...

My only suggestions at this point would be to try other distros (maybe even Dapper, that was a pretty stable release), or *shudder* Windows. I really don't know what else to do at this point.

---

### Post by dreamer.redeemer on 2008-01-22
Does it have to be the distro though? I'm thinking this because it's not working in knoppix either. I heard a story somewhere that comcast was for some reason blocking macs that weren't the ones that had always been used. as i'm currently unable to get a connection in windows on my laptop while connected straight to the router, i'm thinking my problem might be with comcast. I really wish i had better options than comcast :(

---

### Post by kripkenstein on 2008-01-22
> **dreamer.redeemer said:**
> Does it have to be the distro though? I'm thinking this because it's not working in knoppix either. I heard a story somewhere that comcast was for some reason blocking macs that weren't the ones that had always been used. as i'm currently unable to get a connection in windows on my laptop while connected straight to the router, i'm thinking my problem might be with comcast. I really wish i had better options than comcast :(
Hmm, well maybe you can call some technical support (waste their time :) ) for the laptop? If that is sorted out, maybe it'll help with the rest.

---

### Post by dreamer.redeemer on 2008-01-23
Problem has been solved, it was a problem with the modem. For comcast users, motorola surfboard users, ubuntu gutsy gibbon users: If you are unable to get any DHCPOFFERS, do this: unplug the modem's power. plug in your linux box's ethernet. plug power back in. 

YES it really is that simple. I had seen this solution before but thought to myself *'oh but that's way too simple'*

---

### Post by kripkenstein on 2008-01-24
> **dreamer.redeemer said:**
> Problem has been solved, it was a problem with the modem. For comcast users, motorola surfboard users, ubuntu gutsy gibbon users: If you are unable to get any DHCPOFFERS, do this: unplug the modem's power. plug in your linux box's ethernet. plug power back in. 

YES it really is that simple. I had seen this solution before but thought to myself *'oh but that's way too simple'*
lol

Glad you worked it out.

---

