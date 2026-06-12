---
title: "Able to ping but no internet connection (8.04)"
date: 2008-06-09
forum: Networking &amp; Wireless
---

### Post by Squ1shy on 2008-06-09
I just installed a fresh copy of ubuntu 8.04 and I'm having issues with the internet. I am able to ping websites but am not able to access them using apt-get update or the update manager or even firefox. I know it has something to do with my DNS servers because I can access the internal network ok EXCEPT my main router (192.168.0.1). For some reason I can ping it but I can't access the webpage. I am NOT trying to access it via a proxy. I am able to access my wireless router (192.168.0.98) and I was able to access the google search engine directly via an ip address. This issue occurs for both the wired and wireless connection. I have also disabled IPv6.

**ifconfig**
eth0      Link encap:Ethernet  HWaddr 00:1d:72:8a:e0:49  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Base address:0x1840 Memory:f8200000-f8220000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:50 errors:0 dropped:0 overruns:0 frame:0
          TX packets:50 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:3516 (3.4 KB)  TX bytes:3516 (3.4 KB)

wlan0     Link encap:Ethernet  HWaddr 00:1f:3b:6c:9a:1f  
          inet addr:192.168.0.104  Bcast:192.168.0.255  Mask:255.255.255.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:2379 errors:0 dropped:0 overruns:0 frame:0
          TX packets:921 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:325744 (318.1 KB)  TX bytes:201854 (197.1 KB)

wmaster0  Link encap:UNSPEC  HWaddr 00-1F-3B-6C-9A-1F-00-00-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

**route -n**
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.0.0     0.0.0.0         255.255.255.0   U     0      0        0 wlan0
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 wlan0
0.0.0.0         192.168.0.1     0.0.0.0         UG    0      0        0 wlan0

I have tried...
sudo ufw disable && sudo ufw status
But no luck

**host google.com**
google.com has address 72.14.207.99
google.com has address 64.233.167.99
google.com has address 64.233.187.99
google.com mail is handled by 10 smtp1.google.com.
google.com mail is handled by 10 smtp2.google.com.
google.com mail is handled by 10 smtp3.google.com.
google.com mail is handled by 10 smtp4.google.com.

**ping google.com**
PING google.com (72.14.207.99) 56(84) bytes of data.
64 bytes from eh-in-f99.google.com (72.14.207.99): icmp_seq=1 ttl=243 time=237 ms
64 bytes from eh-in-f99.google.com (72.14.207.99): icmp_seq=2 ttl=243 time=237 ms
64 bytes from eh-in-f99.google.com (72.14.207.99): icmp_seq=3 ttl=243 time=235 ms

--- google.com ping statistics ---
3 packets transmitted, 3 received, 0% packet loss, time 1998ms
rtt min/avg/max/mdev = 235.659/236.653/237.292/0.815 ms

**cat /etc/resolv.conf**
### BEGIN INFO
#
# Modified_by:  NetworkManager
# Process:      /usr/bin/NetworkManager
# Process_id:   5003
#
### END INFO



nameserver 203.2.75.132
nameserver 198.142.0.51
nameserver 192.168.0.1


**/etc/dhcp3/dhclient.conf**
prepend domain-name-servers 203.2.75.132, 198.142.0.51;

**nslookup google.com** 
Server:		203.2.75.132
Address:	203.2.75.132#53

Non-authoritative answer:
Name:	google.com
Address: 64.233.167.99
Name:	google.com 
Address: 64.233.187.99
Name:	google.com
Address: 72.14.207.99

When I try running the following...
sudo apt-get update
0% [Waiting for headers] [Waiting for headers] 

It just freezes on the waiting for headers message and doesn't go any further.

When I run...
wget google.com
--00:11:02--  [http://google.com/](http://google.com/)
           => `index.html'
Resolving google.com... 64.233.187.99, 72.14.207.99, 64.233.167.99
Connecting to google.com|64.233.187.99|:80... connected.
HTTP request sent, awaiting response... 

It just freezes on the Http request sent, awaiting response... and doesn't go any further.

---

### Post by superprash2003 on 2008-06-09
you could try changing your current dns servers to opendns - 208.67.222.222 and 208.67.220.220

---

### Post by wdaniels on 2008-06-09
It doesn't seem to be a DNS problem - looks like port 80 (used for HTTP) is blocked somehow. Check that it's not blocked (or being forwarded elsewhere) on the router first.

---

### Post by wdaniels on 2008-06-09
> **Squ1shy said:**
> I was able to access the google search engine directly via an ip address.

Oh, missed that on first reading - maybe it does have something to do with DNS then :confused:

---

### Post by wdaniels on 2008-06-09
Maybe something like:

```
netstat -tnap
```

...will give you some idea what's going on.

---

### Post by Squ1shy on 2008-06-09
Forgot to mention that I did try the opendns servers but with no luck. All my other machines I have are able to access the internet without a problem but they are running XP/2000/Vista. My other computer running ubuntu 6.06 works fine.

---

### Post by superprash2003 on 2008-06-09
are you able to access [http://72.14.207.99](http://72.14.207.99) in firefox?

---

### Post by Squ1shy on 2008-06-11
I am not able to access google from [http://72.14.207.99](http://72.14.207.99) 
Anything else I can do?

netstat -tnap
Active Internet connections (servers and established)
Proto Recv-Q Send-Q Local Address           Foreign Address         State       PID/Program name
tcp        0      0 127.0.0.1:631           0.0.0.0:*               LISTEN      5101/cupsd      
tcp        0      0 192.168.0.110:33704     74.125.19.103:80        ESTABLISHED 6087/firefox    
tcp        0      0 192.168.0.110:37865     91.189.88.46:80         ESTABLISHED 6421/wget       

This is a traceroute to google.com

Hop	Hostname	IP	Time 1	Time 2
1	squishy-laptop.local	192.168.0.110	0.229ms	\UffffffffE\Uffffffff\u0601G\Uffffffff
1	no	reply	*	\Uffffffff\Uffffffff\Uffffffff
2	10.59.0.1	10.59.0.1	20.609ms	\UffffffffE\Uffffffff\u0601G\Uffffffff
3	bla2-ge1-1.gw.optusnet.com.au	198.142.160.161	11.877ms	\Uffffffff\Uffffffff\UffffffffF
4	sbr3-ge14-0-0-821.gw.optusnet.com.au	211.29.156.12	23.246ms	\UffffffffE\Uffffffff\u0601G\Uffffffff
5	203.208.148.225	203.208.148.225	206.343ms	\UffffffffE\Uffffffff\u0601G\Uffffffff
6	ge-4-0-0-0.plapx-dr2.ix.singtel.com	203.208.149.6	171.617ms	\UffffffffE\Uffffffff\u0601G\Uffffffff
7	no	reply	*	\Uffffffff\Uffffffff\Uffffffff

---

### Post by Nathariel on 2008-06-11
Could you please post a short dump log of your connection attempts
using tcpdump. Just start it and after that try to connect to some website. 
The first 50 packets should be enough.

Btw: Speaking blindly , you could also try to disable the firewall of the linux(flushing the current chains, setting the default chain policies to "Accept". **Don't forget to save them before that and restore them if it doesn't work**)  and try it this way.

---

### Post by nandelbosc on 2008-10-01
Same problem here!

I have a clean install of ubuntu 8.04 (10 minutes ago) and I haven't internet.

From console:
Ping to 213.97.3x.xx (My work IP Address)  work's fine
Ping to [www.google.com](www.google.com) works fine (it's not a DNS problem)

But if I try to surf with firefox I haven't internet (I tried [http://www.google.com](http://www.google.com) and [http://213.97.3x.xx](http://213.97.3x.xx))

If I try to connect to my work's sshd server I can't.

I tried to disable UFW...

/etc/init.d/ufw stop

but no luck.

Can anybody help me?!

Thank's!

---

### Post by Squ1shy on 2008-11-27
This is bugging me like crazy =P I have tested my laptop at work and that appears to work fine on their connection. So I can establish that it is my network and not the computer. 

I have tried replacing the wireless router but that doesn't seem to be the problem because I can still access my internal file server perfectly fine using the wireless router. So now I believe it is my router/voip device which is causing all the problems... 

I have the following network diagram...

Optus Cable -> Cable modem -> voip router (192.168.0.1) -> wireless router (192.168.0.9).

All my computers are connected to the wireless router. I have a mac/xp machines and vista. They all don't seem to have any problems with the hardware.

Help? 

I have tried to remove the default network manager and replaced it with Wicd manager but it still hasn't resolved the issue.

I am able to access [http://192.168.0.9](http://192.168.0.9) via firefox but cannot access [http://192.168.0.1](http://192.168.0.1). Is this to do with some routing rules which I need to setup?

---

### Post by nandelbosc on 2008-11-27
I'm sorry, but I can't help you.

My problem was solved changing the DSL router... after this all works fine!

---

### Post by moore.bryan on 2008-11-27
do i understand correctly you're trying to connect through a wireless connection or is are you trying through a hard-line connected to your router?

---

### Post by Squ1shy on 2008-11-27
I'm trying to connect using a wireless connection... but I have also plugged a cable straight into my wireless router to make sure that it wasn't my wireless that was stuffing up.

I'm 100% certain that if I replace the voip router that my cable modem is connected to I will be able to resolve this issue but I don't want to buy another voip router =S Besides if Vista/XP and Mac OS all work I don't see why linux can't.

I dunno if this is relevant but the voip router is also the DHCP server.

Optus Cable -> Cable modem (external ip address) -> voip router (192.168.0.1) -> wireless router (192.168.0.9).

All other computers connect using ip range 192.168.0.0 and subnet 255.255.255.0.

---

### Post by moore.bryan on 2008-11-27
long shot, but ubuntu might be getting confused if both your voip and wireless routers are dhcp; do you know if that's the case or not?

---

### Post by Squ1shy on 2008-11-27
I only have one of them acting as a DHCP server... and that is the voip router. Somehow once you connect to the wireless router, the client is able to query the voip router to obtain a valid ip address. 

The DHCP server gives out addresses in the 100 to 150 range.

---

### Post by moore.bryan on 2008-11-27
okay... sorry if these are questions already covered, but just so i can get my head wrapped around everything:

[LIST]
[*]you have a cable modem with your isp giving you an ip address for the modem.
[*]you have a voip router connected to the cable modem acting as dhcp server.
[*]you have a wireless router connected to the voip router for your various computer connections.
[*]with windows, osx, and dapper you can connect to the internet, but not with hardy.
[/LIST]
have you tried just pulling the voip router out of the equation and seeing if it works?

---

### Post by Squ1shy on 2008-11-27
Re: Able to ping but no internet connection (8.04)
okay... sorry if these are questions already covered, but just so i can get my head wrapped around everything:

* you have a cable modem with your isp giving you an ip address for the modem.
Yes

* you have a voip router connected to the cable modem acting   as dhcp server.
Yes

* you have a wireless router connected to the voip router for your various computer connections.
Yes
    
* with windows, osx, and dapper you can connect to the internet, but not with hardy.
I have tried other Linux distros on this computer and I think 6.X worked... but 7 onwards has not worked.

have you tried just pulling the voip router out of the equation and seeing if it works? 
No... but that's probably a good idea. I'll try it now...

Okay confirmed... it is the voip router. So besides throwing it away how can I fix this? =P XP/Vista and the Mac are smart enough to work around it... surely Linux can too?

---

### Post by moore.bryan on 2008-11-27
> **Squ1shy said:**
> Okay confirmed... it is the voip router. So besides throwing it away how can I fix this? =P XP/Vista and the Mac are smart enough to work around it... surely Linux can too?
well, that's good news and bad news; we know something--e.g., some setting, some checkbox--on the voip router is screwy and we know it's not the entire router because your other os's seem to be able to handle it. what are your settings on the voip router; can you backup them up into a txt file and post it?

---

### Post by Squ1shy on 2008-11-27
It's a Netcomm V300

WAN MODE :   	DHCP mode
WAN IP Address :   	122.107.X.X
Subnet Mask :   	255.255.240.0
Default Gateway :   	122.107.96.1
Current State :   	Active
Primary DNS Server :   	203.2.75.132
Secondry DNS Server :   	198.142.0.51

It really doesn't have much more you can modify...
Lan setup = lan ip, netmask.

DHCP Server Configuration
Status:Enable
Starting/ending ip address.
Lease Time (in Days) :7

Then there is the Voip section of the setup.
SIP
VoIP QOS

Then there is an advanced section which contains...
NAT Port Forwarding
DMZ -> currently disabled
Access Control -> reset my password
Remote Access -> currently disabled
APS -> automatically updated firmware I believe
SNTP -> time server

As I have previously mentioned lookup's work fine from the terminal in Linux... I think it is just a setting I need to tweak in Linux to do with netstat maybe? But I'm not sure.

---

### Post by j21a2t89 on 2008-11-27
Have you tried changing the mtu of the connection. Setting it to below 1492 might help.

---

### Post by moore.bryan on 2008-11-27
hmmm... not a whole lot in that info. and everything works fine without the voip router, correct?

what happens when you set the wireless router as your dhcp server and not the voip router?

---

