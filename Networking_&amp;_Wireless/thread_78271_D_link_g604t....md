---
title: "D link g604t..."
date: 2005-10-18
forum: Networking &amp; Wireless
---

### Post by michaelharg on 2005-10-18
Hi, im rather new to linux and im struggling with getting my router working. It works fine under XP, i've googled around and found that its quite trickey to get working under Ubuntu and i dont think this is helped by me not really knowing what im doing.

Ive updated to the latest firmware for the router..

Any help would be much appreciated

Thanks 

Michael Hargreaves

---

### Post by Zinckk on 2005-10-18
- looks like this is a problem for a lot of people.  I've been trying myself to sort out the same issue for days now.

DSL-G604T
Tiscali broadband
running Breezy 5.10 from DVD

booting up from hard drive (Windows XP) internet access is fine
booting up from DVD (Ubuntu) no internet BUT I can go to Network tools and ping any URL I like (eg [www.google.com](www.google.com) ) - so there is a 'link' of sorts there.

PPPoE gives the 'standard' access concentrator not responding reply.

Perhaps the title of this thread is more 'PPPoE doesn't run' ??

---

### Post by mips on 2005-10-18
michaelharg,

I'm about to reply to Zinckk's thread that is here: [http://ubuntuforums.org/showthread.php?t=78337](http://ubuntuforums.org/showthread.php?t=78337)

I'm waiting for him to supply me with certain infos, maybe you can do the same and we can try and sort this out in one thread.

Please post the following info in that thread:

1) Router Make & Model
2) Did you buy it or was it provided by the ISP
2) Connection type, Ethernet, USB or Wireless
3) Running in Bridged or Routed mode
4) Country you live in.
5) Your ISP and/or Broadband provider
6) What service are you sucribing to from them

Please provide links where possible to the above questions.

---

### Post by michaelharg on 2005-10-18
Heres the info you want...

1:my router, [http://www.dlink.com/products/?pid=372]("http://www.dlink.com/products/?pid=372")

2: I bought it.

3: I am connected to the router via ethernet

4: I think im running it in bridged mode

5: I am in the Uk

6: My broadband provider is BT

7: The service is an adsl line (512kbs)

Thanks

Michael Hargreaves

---

### Post by michaelharg on 2005-10-18
I have connected through firefox, i changed the ipv6 settings. I'm now having trouble   conecting to other services however such as synaptic and gaim.. is this a router problem or software??

Thanks

Michael Hargreaves

---

### Post by mips on 2005-10-18
Ok, the IPv6 setting is only gonna help for traffic on port 80, your basic browsing stuff. You can restore to defaults if you want.

This is a router problem, proceed to Option 2 in the other thread. 
You can restore the changes in Option one if you want later. If you dont come right with D-Link tech support then go to Option 3. I suggest you explain the problem nice to a D-Link Tech support person.

---

### Post by mips on 2005-10-18
[QUOTE=michaelharg]Heres the info you want...

1:my router, [http://www.dlink.com/products/?pid=372]("http://www.dlink.com/products/?pid=372")

2: I bought it.

3: I am connected to the router via ethernet

4: I think im running it in bridged mode

5: I am in the Uk

6: My broadband provider is BT

7: The service is an adsl line (512kbs)

Thanks

Michael Hargreaves[/QUOTE]


4. If you are running in bridged mode it means you have PPPoE configured on your PC, is this the case ???
How is your windows PC configured ?

---

### Post by michaelharg on 2005-10-18
I'm trying step 3, tech support wasnt answering..

Im struggling to find the 2 nameservers IP's, i have a single DNS server with IP 192.168.1.1 and i have ann ip adress of 192.168.1.5 but theres nothing that states DNS name server..

Man my head is starting to spin...

Thanks

---

### Post by mips on 2005-10-19
Looks like your PC is forwarding all DNS requests to your router as it is using the Default Gateway address.

Can you access your router via the browser using its IP address ? 
Somewhere in your routers setup/diagnostics you should find the DNS addresses supplied by the ISP. Maybe router status etc.

I would suggest you configure them statically on your router too.

---

### Post by Zinckk on 2005-10-19
[ Hang in there! - I'm with you in spirit: having all the same probs myself, but just following along in your trail!!!   I'm sure we'll get there eventually :???:  ]

---

### Post by michaelharg on 2005-10-20
Hi, sorry its taken me a while to respond, ive been busy with work...
There is no DNS names server anywhere in the router configuration, there is however a prefered DNS server, there is only one ip though. Should i try this one and just add 1 to the final number in the ip for the second ip i need?

Thanks very much again..

---

### Post by mips on 2005-10-20
Call your ISP and ask them for the DNS server addresses ! They will give them to you.

---

### Post by seanb on 2005-10-26
I have also been having trouble with my DSL-604T router. I disabled ipv6 in the aliases file (changed alias net-pf-10 to alias-net-pf-10 off), which has fixed web browsing. 

With apt-get, I get a failure to connect, as it seems to resolve gb.archive.ubuntu.com to 1.0.0.0. However, if I ping gb.archive.ubuntu.com and then immediately run apt-get, it works:

```
root@redbug:~# apt-get update
66% [Connecting to gb.archive.ubuntu.com (1.0.0.0)]
root@redbug:~# ping gb.archive.ubuntu.com
PING gb.archive.ubuntu.com (82.211.81.182) 56(84) bytes of data.
64 bytes from gb.archive.ubuntu.com (82.211.81.182): icmp_seq=1 ttl=46 time=14.1  ms
64 bytes from gb.archive.ubuntu.com (82.211.81.182): icmp_seq=2 ttl=46 time=14.1  ms

--- gb.archive.ubuntu.com ping statistics ---
2 packets transmitted, 2 received, 0% packet loss, time 1001ms
rtt min/avg/max/mdev = 14.122/14.151/14.180/0.029 ms
root@redbug:~# apt-get update
Get:1 http://gb.archive.ubuntu.com breezy Release.gpg [189B]
Hit http://gb.archive.ubuntu.com breezy Release
Hit http://gb.archive.ubuntu.com breezy/universe Packages
Fetched 189B in 0s (782B/s)
Reading package lists... Done
root@redbug:~#

```

This works for a short time, then apt-get seems to "forget" the address, and I'm back to square one; another ping and it starts working again (by short time, I mean no longer than the time it has taken to compose this post; maybe five minutes or so?)

My router software version is 1.00B02T02.UK.20040618. I'm reluctant to upgrade it on the grounds that it is working perfectly with my PC when booted into Windows XP and Mandrake 10.1 (using ftp, pop and smtp); so far it is only Ubuntu that has a problem (of course, the same issue might occur with other bang up to date distros).

I hope the additional info above might help someone to shed some light on the root cause of the problem.

---

### Post by seanb on 2005-10-31
Well, more info: I bit the bullet and upgraded the router to V1.00B02T02.UK.20050815, and it all works, problem solved.

Looks like it was a router problem after all, but I'm still curious as to why Windows and older Linux releases worked OK before the upgrade.

---

### Post by mips on 2005-11-01
I wish I knew but the main thing is it works !

---

### Post by teaker1s on 2005-11-01
I have dlink dsl 504t and the solution is to set your dns setting to user discover  with your isp dns ip and create a static ip address
 and on system-administation-network settings delete any locations

manually setup a static ip and dns manually
then create location
disable ipv6 on firefox and thunderbird and if possible ubuntu as my dlink and i suspect your dlink router can't handle ipv6 requests

Buggy as several reboots static ip and dns address on ubuntu randomly  disapear,but when it works synaptic etc etc work.

anyone finds a better solution i'm all ears other than a new router as current dlink firmware for my router doesn't do ipv6

---

### Post by mips on 2005-11-02
[QUOTE=teaker1s]
...anyone finds a better solution i'm all ears other than a new router as current dlink firmware for my router doesn't do ipv6[/QUOTE]

Why on earth would you require IPv6, are their actually ISP's running IPv6 on the aggregation side ???

Have a look at this thread posted above [http://ubuntuforums.org/showthread.php?t=78337](http://ubuntuforums.org/showthread.php?t=78337)

I dont know what firmaware is available for your router but try and upgrade to v2 if available.

---

### Post by teaker1s on 2005-11-02
I don't want ipv6 but the suggested ubuntu editing to turn it off completely don't work and it causes the ethernet settings to cock up regularly

---

### Post by mips on 2005-11-02
1.What firmware version are you running on the D-link ?
2.Which country are you in ?

---

### Post by michaelharg on 2005-11-02
Hey, i have managed to get it to work with the latest version of the UK firmware and going through the procedure that Mips suggested in the thread he linked to above (option 3)...its not buggy and if i can manage to do it i think any one else can, thanks Mips, its people who like you who make linux accessible to the masses.

---

### Post by Wharry on 2005-11-02
I had the self same problem and resolved it by upgrading the firmware on the G604T earlier today.

I was only able to resolve this by finding this thread, registered here to say thank you to all. :D

---

### Post by mips on 2005-11-02
It's nice when people come back, says thx and what worked for then. The feedback helps others.

No feedback and you never know if the issue was resolved or not.

---

### Post by _piglet_ on 2006-06-24
Just found this thread after many hours of hair pulling - performed the Dlink upgrade and it works! Thanks.

---

