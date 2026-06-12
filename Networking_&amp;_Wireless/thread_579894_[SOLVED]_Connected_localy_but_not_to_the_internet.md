---
title: "[SOLVED] Connected localy but not to the internet"
date: 2007-10-18
forum: Networking &amp; Wireless
---

### Post by mkc on 2007-10-18
(edit 2) Problem solved - anyone who want's to see what I did, look at the bottom of the page- the issue was with my router, ipv6 and DNS numbers even though it didn't seem to be originally! (edit 2 ends)

(edit) I've just tried getting to google using one of their IP addresses (64.233.167.104) and it worked fine so I guess this is a DNS thing... I just don't know how to fix it! I put this edit up at the top cos I think it'll be usefull to know when reading the rest...(edit ends)

Well I've just installed 7.10 on a samsung Q45 and I can't connect to the internet.
I can ping the router and other local machienes. This works using a hardline or wireless so I can't see it being drivers. (log into the router being via firefox onto address 192.168.1.1)
The router has a good connection to the net for my Mac and Windows boxes.

Back on my linux box, output from #ifconfig -a;
eth0      Link encap:Ethernet  HWaddr 00:13:77:4C:31:F5  
          inet addr:192.168.1.2  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::213:77ff:fe4c:31f5/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:678 errors:0 dropped:0 overruns:0 frame:0
          TX packets:605 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:824778 (805.4 KB)  TX bytes:51104 (49.9 KB)
          Interrupt:17 

eth1      Link encap:Ethernet  HWaddr 00:1B:77:4E:92:7B  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:2055 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:16 Memory:f0300000-f0300fff 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:13 errors:0 dropped:0 overruns:0 frame:0
          TX packets:13 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:1456 (1.4 KB)  TX bytes:1456 (1.4 KB)

Where eth0 is my ethernet line and eth1 is my wireless

Output from #netstat -rn;

Kernel IP routeing table
Destination     Gateway         Genmask         Flags   MSS Window  irtt Iface
192.168.1.0     0.0.0.0         255.255.255.0   U         0 0          0 eth0
169.254.0.0     0.0.0.0         255.255.0.0     U         0 0          0 eth0
0.0.0.0         192.168.1.1     0.0.0.0         UG        0 0          0 eth0

Output from #cat /etc/resolv.conf;

nameserver 192.168.1.1

Output from #route

Kernel IP routeing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.1.0     *               255.255.255.0   U     0      0        0 eth0
link-local      *               255.255.0.0     U     1000   0        0 eth0
default         mygateway1.ar7  0.0.0.0         UG    0      0        0 eth0


As far as I can see it's all as it should be (although that's likely just because I'm ignorant!) if it weren't for my working connections on both macos and xp I'd blame the router's connection to the internet!

I've replecated this problem on Fedora7 and Debian 4. On Debian if I went in and hand edited /etc/resolv.conf to point to a specific DNS it would sometimes work for a while and then reset itself. I tried Zenwalk which seemed to allow hardline connections but I couldn't wireless stuff working at all so I gave up!

Any help would be massively appriciated.

Thanks in advance
Mark

---

### Post by AirRaven on 2007-10-18
Have you specified your DNS Servers in your Network Configuration Panel?

I've no idea if anything's changed in Gutsy yet- it's only 50% downloaded so far, but this really does sound like a DNS problem over anything else. In previous versions, it should be in System->Administration->Networking->DNS. I assume things must have been juggled around a bit, but it should be somewhere similar now.

Try setting your DNS Server as the same IP as your "Gateway" - 192.168.1.0, I'm assuming. 

If that fails, or gives you problems, you can either go into your router's control panel and get your DNS server IPs to input them manually, or you can just use [OpenDNS](http://www.opendns.com/)' free DNS service.
[quote=OpenDNS DNS Nameserver IPs]
208.67.222.222
208.67.220.220[/quote]

Hope that works. Get back to us if it fails?

---

### Post by Original Brownster on 2007-10-18
Hi, Your settings look fine to me, I cant' say I have come across this problem but I suspect it's an issue with ipv6 and your router. 
Other people sometimes have an issue with this so you could try turning this off.

---

### Post by mkc on 2007-10-18
hey. thanks for the replys.

I've tried the open DNS, but it's not working. There were already similar values in there anyway, but knowing the open dns numbers will be usefull in future so thanks!


as far as switching off ipv6 ... well how do I do that?! is there anywhere you recomend I can read up about the advantages/ disadvantages etc of ipv6 over v4?

i did a search for google incase there's a way to fix ipv6 on my router and found this post [http://ubuntuforums.org/showthread.php?t=328874](http://ubuntuforums.org/showthread.php?t=328874) where the guy says he's fixed it.... but I have no idea what he's on about in the fix.... any thoughts?

Cheers

Mark

---

### Post by Original Brownster on 2007-10-19
I don't know a hell of a lot about ipv6 apart from it will eventually replace ipv4 but is supposed to be compatible hence its used in ubuntu. 

There are a lot of people with a problem where the router always returns 1.0.0.0 as the address, see this [bug report]("https://bugs.launchpad.net/ubuntu/+bug/81057") the reason doesn't seem conclusive but disabling ipv6 as a work around may work for you.

if you open a terminal window and type
wget [www.google.com](www.google.com)
does it resolve the ip address to 1.0.0.0 ?

[This thread]("http://ubuntuforums.org/archive/index.php/t-87798.html") tells you how to disable ipv6

On using the opendns numbers, where did you put them? To get around the problem you need to edit the resolv.conf file did you do that? 
Failing that try putting them into the router itself as some people have done that with success.

The firefox fix is easy, open firefox then in the url box type ' about:config '
this gives you a page of all the settings in firefox, type 'ipv' inthe filter box and you'll see the setting for 'disable ipv6' and the value false, double click the line to change to true and thats it. I have just done this and found a noticeable speed increase in resolving the ip, I doubt this is your problem per se but it might be worth doing anyway.

---

### Post by mkc on 2007-10-19
Wayne. you're a star! I'll go and do that now. If you don't hear anything then it's all good and I've fixed it.... So thanks very much for all the help.
cheers

Mark

---

### Post by mkc on 2007-10-19
Well here goes interesting;

I disabled ipv6 in firefox to check the modprobe hacks would work and it did... so. I re-enabled ipv6 in firefox and set about the blacklist etc. as suggested in that other thread. after doing each and rebooting after each I'm certain IPv6 is not currently running on my system - lsmod | grep v6 returns nothing....

The upshot is.... Firefox runs happily. Ping now understands when I ping a name rather than a number, BUT

Synaptic can't get updates (this is not a new fault - it couldn't anyway.) and evolution can't check my mails....

So I went for the DNS idea and now it works!

To summerise for anyone with the same problems there were two issues in this case, as far as I can tell they were both to do with the router;

Issue 1
Firefox and the like use IPv6 by default, and a lot of routers don't like that at all. To switch it off look at the thread linked above or what I did;
1)sudo su
2)echo "blacklist ipv6" >> /etc/modprobe.d/blacklist-ipv6
3)reboot

Issue 2
The DNS on my router wasn't working correctly. In gnome I went to "system--> Administration --> Network" moved to the DNS Tab and added 208.67.222.222 and 208.67.220.220 to the list.

Bingo, working internet!

Mark

---

### Post by Original Brownster on 2007-10-19
Great it's sorted, I just wondered if the last issue of the dns query for synaptic and email may have been resolved by re-setting the router (power off and on) as I think the router's cache previous requests and in your case may have an incorrect entry hence the re-set.
The router might not update the cached entries for 24/48 hours....

---

### Post by mkc on 2007-10-19
Arg!!!! Well I thought It was fixed. Now when I change my connection Netwrok settings looses the DNS servers I put in - just editing /etc/resolv.conf won't work because it's mantained by network manager..... grrrr. 

:)
m

---

### Post by Original Brownster on 2007-10-19
> **mkc said:**
> Arg!!!! Well I thought It was fixed. Now when I change my connection Netwrok settings looses the DNS servers I put in - just editing /etc/resolv.conf won't work because it's mantained by network manager..... grrrr. 

:)
m

I think you can safely remove network-manager if it causes problems, that way you can manually adjust your config files without fighting it .... :)

---

### Post by mkc on 2007-10-24
Nice one Wayne. Thanks for all the help.

... now I've got Networking sorted I'm off to find the reason I can't play Videos when compiz is on! 

... 

Cheers

Mark

---

