---
title: "Internet slower in ubuntu compared to win XP"
date: 2007-02-12
forum: Networking &amp; Wireless
---

### Post by keith11 on 2007-02-12
I have a dual boot with win xp pro sp2 and ubuntu edgy on my toshiba m35-s320 centrino (2004 model). I have been facing problems with the wireless internet (I haven't had a chance to check out the ehternet lan/wired connection) in ubuntu. Whenever I open a page in firefox, I see "looking for..." in the status bar of the firefox window for a few seconds, then I see "waiting for..." for a few seconds and then "transferring...", again for a few seconds. The few seconds add up and the opening of a webpage becomes very slow. Initially I thought it was the connection, but then I logged into windows and the connection was much faster than what I was experiencing in ubuntu. Many times, the downloading page will also get stuck at one of the stages: looking up, waiting or transferring. This is very disappointing as I have always gotten better speeds in linux compared to windows. 

I read on this forum and disabled ipv6. The pings seem 100% better, but I am still facing the problem. I have also disabled ipv6 through the about:config command in firefox. I recently upgraded to 2.6.17.11 i386 kernel from 2.6.17.10 i386 kernel. But the problem stays the same in both the newer and the older kernel environments. Any ideas anyone? Thank you.

---

### Post by gradedcheese on 2007-02-12
I'm pretty sure that you need to disable IPv6 and you will see an improvement.  In Firefox, this is done by going to "about:config" (as a URL) and setting **network.dns.disableIPv6** to true.  You can also disable IPv6 in Ubuntu altogether: [http://ubuntuforums.org/showthread.php?t=6841](http://ubuntuforums.org/showthread.php?t=6841)

EDIT: oops, I didn't see that you took care for Firefox already.  The link to disabling it globally still applies...

---

### Post by simonfoley on 2007-02-12
Does anyone else have any other tips at all on this?

I am also finding Ubuntu slightly slower than windows in general

S

---

### Post by keith11 on 2007-02-12
An update: I don't know if this will help someone to find out the problem I am facing but I am in my office right now and the internet seems to work fine here. Could it be possible that when I am operating from home, I might be behind some protocols on the wireless connection I use at home that might be creating the slowness?

Note: I had already disabled ipv6 globally before posting this post.

---

### Post by mips on 2007-02-12
Manually configure your ISP DNS servers in ubuntu. You could see an improvement in speed.

---

### Post by r4ik on 2007-02-12
Also try about:config in the adresbar and set the "pipe" maxrequest to 8

---

### Post by keith11 on 2007-02-12
I tried changing the number of pipes too. I couldn't figure out how to find out the dns servers for my ISP so I couldn't configure those but something seriously seems wrong. Currently, I have ipv6 disabled globaly as well as in firefox. When I opened firefox, it opened a webpage at a lightening speed, but just that first page. Everytime I try to open  a webpage in firefox now, it either gets stuck at "waiting for..." stage or it downloads some part of the page and then gets stuck at "transferring data from...". This is really of great concern to me as it has almost paralysed me on the internet from home. I don't know how to fix this. I work from home too and this is absolutely crippling. The problem is with my mozilla web browser too. So it seems it is the problem in the browsers but I am not able to make sense out of the fact that the same browsers work great in my office. So why don't they work properly at my home? Interestingly, internet explorer works fine through crossoffice. I had slow internet because of ipv6 (maybe), but it is just worse now. Even changing back to ipv6 doesn't solve the problem I have now. I would truly appreciate any help on this as this is crucial for me. Thanks.

---

### Post by 454redhawk on 2007-02-12
> **keith11 said:**
> Whenever I open a page in firefox, I see "looking for..." in the status bar of the firefox window for a few seconds,

This is a DNS problem. Try to manually configure your DNS and maybe use the open DNS address's. I am reasonably sure you will see an increase in speed and you should NOT see the "looking for" message anymore.

[http://www.opendns.com/start/](http://www.opendns.com/start/)

208.67.222.222
208.67.220.220

---

### Post by keith11 on 2007-02-13
Update: I did use the opendns servers and I also have the ipv6 globally disabled. The internet seems to work fine BUT it gets disconnected after some time and this happens regularly. I can ping a website in the console, but can't download the pages. I disconnect and reconnect the connection and then everything goes to normal. Does the opendns server disconnect you regularly? One more change I made was adding "alias net-pf-10 off" in a file called "bad_list"
 in the /etc/modprobe.d folder (found this method on [http://ubuntuforums.org/showthread.php?t=87798 )](http://ubuntuforums.org/showthread.php?t=87798 )). Any ideas why I am geting disconnected? Thanks.

Edit: I found out that whenever I got connected through vpnc to my university, my wireless connection got disconnected. I noticed the following things too when I open the network-admin window:

1. The DNS servers change (which I think should be obvious, but there are no dns servers for my wireless connection from home, so there are the dns servers of the university only).
2. The module tun0 is loaded but it shows as not configured.
3. I added the dns server addresses from opendns.com but they don't show anymore in the dns servers' list. This is when I have disconnected the vpn and when the home wireless dns servers show.

How to overcome this? Thanks.

---

### Post by 454redhawk on 2007-02-13
> **keith11 said:**
> Update: 

1. The DNS servers change (which I think should be obvious, but there are no dns servers for my wireless connection from home, so there are the dns servers of the university only).
2. The module tun0 is loaded but it shows as not configured.
3. I added the dns server addresses from opendns.com but they don't show anymore in the dns servers' list. This is when I have disconnected the vpn and when the home wireless dns servers show.

How to overcome this? Thanks.

OpenDNs will not disconnect you. Seems like some other problem

As far as the DNS changing. You should be able use Open DNS for everything. Even while connected your university network.

Do this to keep your DNS from changing.

Edit the /etc/resolv.conf file as root (sudo) and add your DNS values. Delete the others.

Then apply this
```
sudo chattr +i /etc/resolv.conf
```

That will lock down that file and prevent overwriting.

To unlock it, 

```
sudo chattr -i /etc/resolv.conf
```

---

### Post by mux2000 on 2007-02-13
I get the same behavior, connection is good for a minute or two (google pinged in 200ms), it slows down significantly afterwards (ping google.com takes 3000ms, with 25% lost packets) and stays that way for about 15-45 minutes before disconnecting. I tried adding a cron job to connect me every time it disconnects, but it's a kludge, and I still get very bad loading times. 

PS. I use pptp through a ethernet cable modem to a regular (israei - they're notorious for making trouble) ISP.

---

### Post by mux2000 on 2007-02-13
> **keith11 said:**
>  The internet seems to work fine BUT it gets disconnected after some time and this happens regularly. I can ping a website in the console, but can't download the pages. I disconnect and reconnect the connection and then everything goes to normal. 

I have this too. For about a minute after connection, everything is fine, then it gets VERY slow, and about 15-45 minutes after connection I get disconnected again. Very very annoying.

Anybody got an idea?

---

### Post by keith11 on 2007-02-13
MUX: If you read my earlier post you would have noticed that the problem of internet is solved for me (as far as speeds are concerned), but it is only that when I connect through vpnc, my wireless connections drops and goes back on only when I disconnect vpnc to my university. So you may want to check if you are using vpnc too. Once again, I have ipv6 disabled globally and even with the default dns servers (not the opendns servers) my internet seems to work fine now. So my problem right now is how to stop vpnc from disconnecting me. Hope this information will be of some help to you. Does anyone know how to solve the problem of getting disconnected becuase of vpnc (and hence the change of dns servers in the resolv.conf file)? If I lock the resolv.conf (will tvpnc work then?), will it do the trick? Thanks.

---

### Post by mips on 2007-02-14
What network address ranges does your VPN & wireless use ?

---

### Post by rebanador on 2007-02-14
Hi all,

I did *everything* mentioned here and still didn't work. I was really annoyed.
Well, something did work for me. Internet right now is at its normal speed.

The solution:  Make sure the following lines are set to 0 in /etc/sysctl.conf:

net.ipv6.conf.all.dad_transmits = 0
net.ipv6.conf.all.autoconf = 0
net.ipv6.conf.all.accept_redirects = 0
net.ipv6.conf.all.accept_ra = 0
net.ipv6.conf.all.forwarding=0
net.ipv6.conf.all.router_solicitations=0

and reboot.

Maybe it works due to a combination of other settings as well. But you can always try.

Good luck,

Francisco

---

### Post by keith11 on 2007-02-14
> **mips said:**
> What network address ranges does your VPN & wireless use ?

I am not sure if you wanted to know just the dns server names or you wanted the first 6 numbers of the ip address I have so I am pasting the following:

ip address - 128.123.xxx.xxx
bcast - 128.123.xxx.xxx
mask - 255.255.xxx.xxx

The above addresses are from when I am on wireless in the university, which I assume will be the same when I connect through vpn from my home.

I am not at home right now but I know it assigns me an ip address as 172.16.x.xx. But I remember the dns servers when I am connected at home start from 68.xxx.xxx.xxx. 

Please let me know if this information is the one you asked for or else please guide me as to how to provide the information you asked for. Thanks.

---

### Post by mips on 2007-02-14
> **keith11 said:**
> 
Please let me know if this information is the one you asked for or else please guide me as to how to provide the information you asked for. Thanks.

Yes. I was just trying to establish whether your VPN & Wireless do not perhaps use the same network address range. But from what you say it does not seem to.

Can you provide the following *before* VPN, *during* VPN and *after* VPN as i would like to see what happens during these stages of use.

ifconfig -a
route -n
cat /etc/resolv.conf

---

### Post by keith11 on 2007-02-16
I am facing a new problem now.:) Just a few days ago I wrote in this thread that my internet speed problem was solved. Well, it is kind of solved. I connect to a wireless which is provided by the landlord for the apartment complex I live in. Two nights ago, the wireless provider changed the ip addresses and since then I have been having problems. 

I have noticed that when I use ONLY the IPs from opendns.org, the ping times rise to somewhere between 1000 to 2000 ms. When I put these IPs as the first two entries in my resolv.conf and also keep the dns servers which my system detects by default I notice that the internet works fine and the speed is great too BUT that speed lasts for some time only and then all of a sudden the webpages start getting stuck at "waiting for...". What could be wrong here? When the webpages (in forefox, mozilla and opera) get stuck, I try pinging some website and the ping rates seem normal so I assume it's only the browsers which are acting weird. Are my browsers somehow losing the connection ? I have checked the resolv.conf when this happens and it always shows the name of the dns servers, so even that seems fine. So what could be the problem? All the browsers work without any problem in my university but the problem is only at home. Any ideas? Thanks.

MIPS: I will post the information you asked for as soon as my internet at home starts working fine. Thanks for you help.

---

### Post by keith11 on 2007-02-21
> **mips said:**
> Yes. I was just trying to establish whether your VPN & Wireless do not perhaps use the same network address range. But from what you say it does not seem to.

Can you provide the following *before* VPN, *during* VPN and *after* VPN as i would like to see what happens during these stages of use.

ifconfig -a
route -n
cat /etc/resolv.conf

Before VPN:

1. output of ifconfig -a 

eth0      Link encap:Ethernet  HWaddr 00:0E:7B:43:FB:18  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

eth1      Link encap:Ethernet  HWaddr 00:0E:35:0A:D1:97  
          inet addr:xxx.xxx.xxx.xxx  Bcast:130.0.255.255  Mask:255.255.0.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:7659 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4437 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:4264945 (4.0 MiB)  TX bytes:678461 (662.5 KiB)
          Interrupt:11 Base address:0xc000 Memory:c2005000-c2005fff 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:2 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:100 (100.0 b)  TX bytes:100 (100.0 b)

2. Output of route -n 

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
130.0.0.0       0.0.0.0         255.255.0.0     U     0      0        0 eth1
0.0.0.0         130.0.0.1       0.0.0.0         UG    0      0        0 eth1

3. Output of cat /etc/resolv.conf

nameserver 208.67.222.222
nameserver 208.67.220.220



During VPN:

1.

eth0      Link encap:Ethernet  HWaddr 00:0E:7B:43:FB:18  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

eth1      Link encap:Ethernet  HWaddr 00:0E:35:0A:D1:97  
          inet addr:xxx.xxx.xxx.xxx  Bcast:130.0.255.255  Mask:255.255.0.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:8604 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4675 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:4351553 (4.1 MiB)  TX bytes:726869 (709.8 KiB)
          Interrupt:11 Base address:0xc000 Memory:c2005000-c2005fff 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:2 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:100 (100.0 b)  TX bytes:100 (100.0 b)

tun0      Link encap:UNSPEC  HWaddr 00-00-00-00-00-00-00-00-00-00-00-00-00-00-00-00  
          inet addr:128.123.253.14  P-t-P:128.123.253.14  Mask:255.255.255.255
          UP POINTOPOINT RUNNING NOARP MULTICAST  MTU:1390  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:500 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

2. 

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.65.78.142   130.0.0.1       255.255.255.255 UGH   0      0        0 eth1
130.0.0.0       0.0.0.0         255.255.0.0     U     0      0        0 eth1
0.0.0.0         0.0.0.0         0.0.0.0         U     0      0        0 tun0

3. 

nameserver 208.67.222.222
nameserver 208.67.220.220


After VPN:

1.

eth0      Link encap:Ethernet  HWaddr 00:0E:7B:43:FB:18  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

eth1      Link encap:Ethernet  HWaddr 00:0E:35:0A:D1:97  
          inet addr:xxx.xxx.xxx.xxx  Bcast:130.0.255.255  Mask:255.255.0.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:9126 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4814 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:4409910 (4.2 MiB)  TX bytes:754240 (736.5 KiB)
          Interrupt:11 Base address:0xc000 Memory:c2005000-c2005fff 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:2 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:100 (100.0 b)  TX bytes:100 (100.0 b)

2.

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
130.0.0.0       0.0.0.0         255.255.0.0     U     0      0        0 eth1
0.0.0.0         130.0.0.1       0.0.0.0         UG    0      0        0 eth1

3.

nameserver 208.67.222.222
nameserver 208.67.220.220


As you will see that I am finding the internet better by using the opendns server names and by locking the resolv.conf. I am still having the same problem with vpnc and the information provided above is the one you wanted me to post for you to analyze further. Thanks.

454redhawk: I took your advice and locked my resolv.conf file with the opendns servers in it and it is working so far.:) Thanks.

---

### Post by keith11 on 2007-02-23
MIPS:

I was wondering if you had a chance to look at the information you asked for and I provided. Thanks.

---

### Post by mips on 2007-02-24
Apologies for the late response but i've been mia.

The first thing I noticed is that when you have the vpn running your Default Route goes via the tun0. This basically tells your PC that all traffic should go via the tunnel interface and this includes your Internet traffic.

Could I suggest you try the following:

1. Activate the VPN
2. Delete the default route
3. Create a new default route that goes via eth1
4. Create a static route for the network you want to reach via VPN

This wont be permanent but should test my theory out.

Let us know how it goes & if it works we can try something permanent.

---

### Post by keith11 on 2007-02-25
Thanks again for responding. I don't know how to delete the default route, but I will do some research and accomplish what you asked me to and then let you know how it goes.

EDIT: I did come accross some posts on this forum which had to do with adding new routes and I also read the man page for "route". I will have to admit that I am confused and a little bit cautious about changing my routes based just on the information I could gather. I came to know that there are classes of networks and I don't know if my network (130.x.x.x) is class A, C or any other so I don't know what combination of options I should apply while deleting as well as adding a route. I am fairly new to Linux so I am confused. If it is not a bother, could you please guide me for carrying out the steps that you asked me follow? I also wanted to add that this problem has started without my knowledge meaning it was not always the case. I was able to connect to the VPN and still remain connected to the wireless too, but suddenly things have changed since two weeks.

---

### Post by mips on 2007-02-25
I'll get back to you. Have to look up the command syntax.

---

### Post by it.henrik on 2007-02-25
Have you tried to ping the ip adress and the "name" of the site?
If the time for pinging the ip adress stays the same but pinging the name takes longer then it is probably a problem with the DNS when resolving the adress. 

I can understand if they would make it slower to use their servers after a while, cause if everyone changed to using their dns .. then they would be under a DDOS attack :) 



> **keith11 said:**
> I am facing a new problem now.:) Just a few days ago I wrote in this thread that my internet speed problem was solved. Well, it is kind of solved. I connect to a wireless which is provided by the landlord for the apartment complex I live in. Two nights ago, the wireless provider changed the ip addresses and since then I have been having problems. 

I have noticed that when I use ONLY the IPs from opendns.org, the ping times rise to somewhere between 1000 to 2000 ms. When I put these IPs as the first two entries in my resolv.conf and also keep the dns servers which my system detects by default I notice that the internet works fine and the speed is great too BUT that speed lasts for some time only and then all of a sudden the webpages start getting stuck at "waiting for...". What could be wrong here? When the webpages (in forefox, mozilla and opera) get stuck, I try pinging some website and the ping rates seem normal so I assume it's only the browsers which are acting weird. Are my browsers somehow losing the connection ? I have checked the resolv.conf when this happens and it always shows the name of the dns servers, so even that seems fine. So what could be the problem? All the browsers work without any problem in my university but the problem is only at home. Any ideas? Thanks.

MIPS: I will post the information you asked for as soon as my internet at home starts working fine. Thanks for you help.

---

### Post by mips on 2007-02-25
> **it.henrik said:**
> Have you tried to ping the ip adress and the "name" of the site?


That wont work. His default route points elsewhere than the internet.

---

### Post by keith11 on 2007-02-25
Thanks it.henrik for your suggestions.

MIPS: I know you would hate this, because I totally do, but I am facing sort of the same kind of problem again, which is that any webpage in Firefox or Mozilla just gets stuck at the "waiting for..." stage and doesn't move further. I keep on running into this problem again and again and that discourages me very much. I have not done anything to my networking except the normal system restart, which I did even earlier, but it was working fine for some days. I am thankful you offered that you will let me know about the commands to add and delete the routes. At this point in time, I am not even able to connect to wireless. I am wondering about a few things here. Whenever I disconnect myself through the wireless-radar applet and try connecting back on, almost always it just doesn;t connect me again. I don't know why it happens but then I have to restart the whole system to connect back on (network restarting doesn't work either). Second thing: I don't know why I connect fine for a few days and then all of a sudden I start getting the same error of "waiting for..." in my browsers. Third thing: I noticed that even the pings are much much higher in Ubuntu (200-500 ms) compared to that in Windows (80-100 ms). 

Just to give an update of what, if anything, I did yesterday, I just opened a port (it has not opened actually although I followed the guide on Azureus wiki for port forwarding, I don't know why) for Azureus and closed one. I don't think that can cause this problem becuase I was able to connect fine even after that. I am just clueless what is wrong. All of a sudden Ubuntu is not even recognizing my USB tablet when I try to find it through "lsusb" although it recognizes my phone. I know we are dealing with the problem of VPN here, but if you have any suggestions to overcome the above mentioned problems, please let me know. Could it be related to my firewall? Thanks.

Keith.

Edit: My connection is working fine now, but if someone read this whole thread he would know that this has been happeneing off and on. I have observed one thing; I don't know if this is the case always but most of the times when I get the "waiting for..." error I end up booting into Windows XP and stay in Windows for some hours. After that, when I boot in Linux, things seem fine. Could this be any clue?

---

### Post by keith11 on 2007-03-02
MIPS: I was wondering if you wanted me to delete and add the routes for solving the vpn problem and if you could help me with the commands. Thanks.

Keith.

---

### Post by mips on 2007-03-02
Keith,

Apologies, I have completely forgotten about you.

Yes, try deleting & adding the routes.

I'm about to leave for the weekend and will only be back on sun/mon.

In the meantime I have subscribed to this thread so i dont forget about it again.

---

### Post by keith11 on 2007-03-03
Thanks for subscribing to this thread. I guess I will get the answer when you return then because as you said you were going to help me with the commands to add and delete the routes. So, at this stage I don't have the tools in the form of those commands to do that. I will wait until you get time. Thanks.

Keith.

---

### Post by ssavelan on 2007-03-03
I... have a newbie low-hack solution....


try KDE network manager.  

Generally, I don't like KDE compared to Gnome; but, I hereby swear by the KDE network manager.


That is really strange that your internet is slower in Ubuntu than XP, that is on of my main raves about Ubuntu.... it is so fast... especially firefox on the net........

but, with wireless, I have always used KDE net man (the first and only thing that I have gotten to work.  i am on a Toshiba Satellite P4 running xubuntu and i love the wireless.  It is stronger, faster and more reliable than the same laptop on XP.

What net man are you using?

---

### Post by keith11 on 2007-03-03
I am using gtkwifi, but whether it is gtkwifi or wifiradar, AI read somewhere all net managers scan periodically for networks and that's when they can get disconnected or plainly STUCK. I will give kDE network manager a try though. Thanks for your suggestions.

Keith.

---

