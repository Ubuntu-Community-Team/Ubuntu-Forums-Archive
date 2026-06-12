---
title: "Internet Connection Sharing XP -&gt; 10.04"
date: 2010-06-12
forum: New to Ubuntu
---

### Post by zer010 on 2010-06-12
Firstly, I have tried to find how to set this up, and have tried a couple of things, but with no success. I have a [COLOR=Blue]XP Home box with 2 NICs(Box1)[/COLOR]. [COLOR=DarkOrange]Box2 is Ubuntu 10.04[/COLOR] with one NIC.  [COLOR=Blue]Box1[/COLOR] has eth0 connected to cable modem. eth1 is connected to [COLOR=DarkOrange]Box2[/COLOR] via crossover. 
Internet sharing is enabled on [COLOR=Blue]Box1[/COLOR]. What are the proper configurations to access internet on [COLOR=DarkOrange]Box2[/COLOR]?
[I]I don't have a router and do not plan to have one for a while.
[/I] 
Any help is greatly appreciated! Thanks in advance.

---

### Post by SRST Technologies on 2010-06-12
Ubuntu should be default set to pick up the DHCP from wherever it can.  If Box1 is not giving Box2 the IP address automatically, you're sharing the wrong ethernet device, some NIC somewhere is bad, or your cable is bad.

---

### Post by sydbat on 2010-06-12
Personally, I would do it the other way around...Linux box as router and XP box on network...mostly because I never got the set up you are trying to work. 

When I had Windows, I could network Windows boxes easily, but as soon as I introduced Linux into the mix, the Linux boxes couldn't find the network. Never sure why. So I swapped out the extra nic from the XP to the Linux and it worked.

Also, your Ubuntu box will have the better firewall, will not slow down when you are sharing your Internet connection.

---

### Post by zer010 on 2010-06-12
The cables are fine, the NICs are fine. I'm sharing the right NIC on Box1. I set eth0 on Box2 to Automatic (DHCP). nothing. 
I've tried to use Box2 as the gateway without success, so before I try that again, I'd like to get this connection running.

---

### Post by cariboo on 2010-06-12
IF you are only sharing the connection between two systems, you would be better off setting static ip addresses on eth1 on the Windows system and on the Ubuntu system. They have to be in a different subnet than eth0 on the Windows system. For example if the ip address of eth0 on the Windows system is 192.168.0.1, then the ip addresses of the other two should be something like 192.168.1.1 and 192.168.1.2.

It's been a while since I did connection sharing with Windows, but I believe that Windows doesn't install a DHCP server by default, you need add-on software. I'm not sure about Win 7, but it looks like there is no dhcp server by default either.

---

### Post by coolbrook on 2010-06-12
Get a dirt cheap router.  You might even find one for free on Craigslist.

---

### Post by zer010 on 2010-06-12
I figured I'd try to do as Sydbat suggested and have followed the community documentation [https://help.ubuntu.com/community/Internet/ConnectionSharing](https://help.ubuntu.com/community/Internet/ConnectionSharing) as far as setting up a gateway. Both computers show connection, but the XP box can't access the internet. Maybe this will help:
Thanks!

ipconfig
Local Area Connection
Connection-specific DNS Suffix:
IP Address:192.168.0.100
Subnet Mask: 255.255.255.0.1
Default Gateway: 192.168.0.1

~$ ifconfig
 
eth0      Link encap:Ethernet  HWaddr 00:0a:e6:5a:1d:c3  
          inet add Mask:255.255.255.0
          inet6 addr:  Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:14186 errors:0 dropped:0 overruns:0 frame:0
          TX packets:3318 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:3343197 (3.3 MB)  TX bytes:566154 (566.1 KB)
          Interrupt:12 Base address:0xd400 

eth3      Link encap:Ethernet  HWaddr 00:50:ba:85:1d:e0  
          inet addr:192.168.0.1  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::250:baff:fe85:1de0/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:63 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:11826 (11.8 KB)
          Interrupt:12 Base address:0xd000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:2149 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2149 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:284605 (284.6 KB)  TX bytes:284605 (284.6 KB)

---

### Post by Don1500 on 2010-06-12
> **coolbrook said:**
> get a dirt cheap router.  You might even find one for free on craigslist.

+1 - I'd send you one of mine but it's not worth the postage. (You can buy one cheaper than the postage to send it to you)

---

### Post by zer010 on 2010-06-13
^  Well, I appreciate it, but it's not feesible right now. I've tried just about everything else but to no avail. ](*,)

---

### Post by Don1500 on 2010-06-13
> **zer010 said:**
> ^  Well, I appreciate it, but it's not feesible right now. I've tried just about everything else but to no avail. ](*,)

less than $25 isn't feasible?
[[COLOR="Red"]Link to cheap Routers at Best Buy[/COLOR]]("http://www.ask.com/bar?q=best+buy+cheap+wired+router&page=1&qsrc=121&dm=all&ab=0&u=http%3A%2F%2Fwww.bestbuy.com%2Fsite%2FWired-Networking%2FWired-Routers%2Fabcat0503009.c%3Fid%3Dabcat0503009&sg=7yEDo%2BVg6owc6kje5F0XFQawbx9547UA05V2wYHYLoQ%3D&tsp=1276453385227")

---

### Post by sydbat on 2010-06-13
> **zer010 said:**
> ^  Well, I appreciate it, but it's not feesible right now. I've tried just about everything else but to no avail. ](*,)I honestly do not know what else to suggest, other than save your money and get a cheap router. Or see if one of your friends has an old one they are not using anymore. Or go to your local computer/electronics store and see if they have a recycle bin where people drop off old tech and ask if you can rifle through it to find what you need.

Sorry my suggestion did not work.

---

### Post by anewguy on 2010-06-13
I don't know how to solve your problem, but I understand the not feasable portion of what you say.  Some people may have overlooked the idea that it's possible you don't have wireless adapters in computer1 and/or computer 2 and that they may be physically separated enough that hard wiring them both to a router is not feasable.  As far as $25 being too much, I don't know your situation, but I know for me, being on disability, $25 is a lot of money to me, better placed towards other things in life.

I'm going to try to do some research to see if I can come up with any threads on the net that might be of help.

Dave ;)

---

### Post by anewguy on 2010-06-13
Found a few things you may have already seen:

[This]("http://achinghead.com/archive/57/sharing-windows-internet-connection-linux/") one is talking about dial-up, but I would think the same principles apply.  Don't worry about the 1 paragraph - it's the rest of the post you should read through.

[This]("http://www.howtoforge.com/internet-connection-sharing-masquerading-on-linux") one talks about changes to the Linux fireall tables in order to allow sharing a Linux connection with another box.

I found this in a post in Linux Forums, and it mentions some things about setting some address, including the gateway address:

> drspin 
Linux Newbie
 

Join Date: Jun 2003
Posts: 160  here's how I do it 

--------------------------------------------------------------------------------

I have my network on eth0 masqeraded through ppp0 for the internet -> each of the systems on the network... I have mac os X, os 9, Linux, m$ 98 and XP... must be configured properly - they must be assigned an ip address (unless you are running dhcp on your box). this ip must be on the same network and subnet that the eth0 port is configured on for simplicities sake. You must also specify the default gateway to the ip address of your box and each system must have a nameserver specified(this is readily available from any tech support person for your isp).

this is vague as I don't have much time but if you need more help, let me know.

Cole 

And this:

>  08-27-2003    #9 (permalink)  
drspin 
Linux Newbie
 

Join Date: Jun 2003
Posts: 160  XP 

--------------------------------------------------------------------------------

/me is going to be fkamed because there's a CHEAPER way!

In XP go to the network Connections in the control panel =-= follow the wizard and set up a bridged connection between your internal network and your internet connection - all you have to do now is tell your linux connxion to authenticate with DHCP and vioala - restart the interface 

ifconfig eth0 down 
ifconfig eth0 up

*** replace eth0 with the correct interface

you've got the internet  

cheers - Cole 

That's a few of what I've seen, but I have what may be a dumb question as well:

Are you running a firewall on the Windows box, and if so, have you configured it to allow traffice to/from the Linux box?

Dave ;)

---

### Post by zer010 on 2010-06-13
Thanks to everyone for their help. After all my study and changes I finally got ICS! Turns out that a 3rd attempt with Firestarter did the trick. :confused:  I about slapped myself when I finally got it working so easily!:lolflag:   Once again thanks for the support!

---

### Post by PatrickMahoney on 2011-02-03
I also would likt to use uBuntu 10.04LTS server for a Internet Gateway/Router/Firewall.

My reasons are because I want more control that IPTABLES provide and a faster nic that what the cheap routers provide. I have Comcast as my internet provider and they provide band width above 10 meg and I have a small budget with 3 sites to do. I want to VPN Point To Point my sites.

---

