---
title: "Transmission kills my network"
date: 2011-02-03
forum: New to Ubuntu
---

### Post by darthspringbok on 2011-02-03
When I run lubuntu normally it is ok. When I run transmission and download torrents my wireless connection dies and cannot reconnect. Also it seems to kill the network so that other PCs in the house cannot access the internet.

Tested by downloading ubuntu iso in chromium and the connection stay up. I have throttled transmission so that it does not hog all the bandwidth but it just kills the network completely.

I have to reboot the router to get internet in the house again.

---

### Post by b0b138 on 2011-02-03
I've had the same thing problem. Maybe not affecting other computers, but my net would die, even if the torrent was getting 5k.

Now I use deluge

---

### Post by Hedgehog1 on 2011-02-03
[SIZE=2]I also had this issue (but it was with a wired connection to my router).[/SIZE]
[SIZE=2][/SIZE] 
[SIZE=2]I changed out my old 'Cisco-Linksys WRT54G Wireless-G Broadband Router' for a  'Cisco-Linksys WRT54GL Wireless-G Broadband Router (Compatible with Linux)' and loaded 'tomato' on the router.  'Tomato' is a Linux frimware that runs the Router much better than the stock firmware.[/SIZE]
[SIZE=2][/SIZE] 
[SIZE=2]My older WRT54G didn't have enough ram for 'tomato', hence the newer gear.[/SIZE]
[SIZE=2][/SIZE] 
[SIZE=2]Now transmission can run at full speed, and the upgraded WRT54GL keeps up without crashing the router.[/SIZE]
[SIZE=2][/SIZE] 
[SIZE=2]So now you have two options - differert bit-torrent software, or different router & router software.[/SIZE]
[SIZE=2][/SIZE] 
[SIZE=2]Or both...  :KS[/SIZE]

---

### Post by b0b138 on 2011-02-03
hmmm... I've had

2 differnet d-link routers
1 linksys wrt54gl running dd-wrt firmware
2 modems with 2 different isps (also checked straight to modem to rule out router)
2 different computers
2 or 3 ubuntu releases (lucid now, karmic, jaunty)

The only common thing left was using ubuntu, and.... me :)

---

### Post by Hedgehog1 on 2011-02-03
Wow! That is a serious round of testing and attempts!
 
Were you using wireless for all these variations? Or were any of them wired?  Were you only using transmission?
 
I have never tried any bit torrent cleint over my wireless connection (only on the wired server).
 
I love a good challenge like this...
 
:p

---

### Post by b0b138 on 2011-02-03
All wired. It drove me crazy forever till I gave up and just used different software lol!

But as soon as transmission started downloading something (not sure if I checked just starting the program with no dl going) my net connection came to snails pace. Now transmissions speed was fine, would d/l as fast as it could.

I should check to see if it still does it :))

---

### Post by srs5694 on 2011-02-03
FWIW, I've had sporadic problems with Transmission causing my network connection to temporarily fail, then come back. (I'm using Gentoo on this system, though, so it may handle errors differently than Ubuntu.) In any event, the effect can show up in ifconfig output:

```
$ ifconfig eth0
eth0      Link encap:Ethernet  HWaddr 00:03:47:b1:ee:b8  
          inet addr:192.168.1.2  Bcast:192.168.1.255  Mask:255.255.255.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:229333 errors:4 dropped:0 overruns:0 frame:4
          TX packets:161140 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:237148965 (226.1 MiB)  TX bytes:27829268 (26.5 MiB)

```

Note the "errors" value on the "RX packets" line; that's normally "0." More often the errors appear on the "TX packets" line. It's a rare enough problem that I still haven't figured it out. Since the connection just drops out for a few seconds to a couple of minutes, it's not all *that* big of a hassle for me, but if the network didn't come back it'd be a big problem.

When I did some Googling about it a while ago, I got some hits that suggested it might be because of bugs in the network drivers. I've got an Intel card using the e100 drivers on the relevant port, and I've got other cards, so I may swap it out to see if that improves matters.

---

### Post by Boondoklife on 2011-02-03
I have never had this issue and I have 1-3 linux boxes running torrents at any given time (2 Ubuntu 1 Linux NAS). I use a linksysN130 w/ DD-WRT, setup transmission to be at the bottom of the QoS and my network is snappy as well as the browsing on the 2 computers.

Maybe check to see if your number of connections is set high enough on the router, if you can not do that then try to limit them on the computers and you should be fine.

My NAS is wired, but the other two boxes are wireless and the network is just fine regardless.

---

### Post by bhaverkamp on 2011-02-03
Have you checked your logs? Is this a newly built system? Torrent may be creating more load for your network. Try running a network bandwidth test that should create similar loads.

---

### Post by Hedgehog1 on 2011-02-03
> **b0b138 said:**
> All wired. It drove me crazy forever till I gave up and just used different software lol!

But as soon as transmission started downloading something (not sure if I checked just starting the program with no dl going) my net connection came to snails pace. Now transmissions speed was fine, would d/l as fast as it could.

I should check to see if it still does it :))

Before I swapped in the WRT54GL with tomato, Transmission did drop the network on it's head (for everything but itself) - BUT - when I booted to Windows 7 and ran micro-torrent, the network stayed up fine.  So that was a case of different network drivers and BT client.

Do you still have one of the routers that can be loaded with tomato?  Of course, if you are happy with deluge this is all academic...

I can surf the web and run transmission without issue now with tomato.

---

### Post by Hedgehog1 on 2011-02-03
> **darthspringbok said:**
> When I run lubuntu normally it is ok. When I run transmission and download torrents my wireless connection dies and cannot reconnect. Also it seems to kill the network so that other PCs in the house cannot access the internet.

Tested by downloading ubuntu iso in chromium and the connection stay up. I have throttled transmission so that it does not hog all the bandwidth but it just kills the network completely.

I have to reboot the router to get internet in the house again.

darthspringbok,

Please give deluge a try and let us know if that gets you working.  I am afraid we have hi-jacked your thread with all this.

Still - look at everything we are learning in the process :p

---

### Post by darthspringbok on 2011-02-04
> **Hedgehog1 said:**
> darthspringbok,
 
Please give deluge a try and let us know if that gets you working. I am afraid we have hi-jacked your thread with all this.
 
Still - look at everything we are learning in the process :p
 
Thanks, I'll give that a try.
Strangely this is on a lubuntu install yet so far on a Ubuntu install on another PC also on wireless with transmission it seems ok, though I have not done enough testing.
 
If i install deluge is it possible to move half downloaded torrents from transmission?

---

### Post by mastablasta on 2011-02-04
it can take the bandwidth if allow too many connection to your file that you are sharring. they see it and everyone wants to ride on it (automaticly) because you give them permission to do it. same thing happen with every torrent porgramme if you allow it to automate the setting when you star doing it.
 
note that kilobits and megabits are not the same as kilobytes and megabytes. so take that into account when you set up torrent programmes. i have it set for small upload and small number of leeches. the download is not as fast as the connection allows it. i have 20mbit connection yet torrents donwload like i had 1mbit :-) no issue whatsoever, can surf normally and all.

---

### Post by mcduck on 2011-02-04
Also keep in mind that such problems can be caused by other things than just the actual download transfer speed. Too many simultaneous connections, or upload speed, can easily result in network problems, especially if your wireless router isn't up to the task.

That would also easily explain why some torrent programs work and others don't, being different programs they have different default limits for this kind of things. Check your settings, limit the upload speed to a bit less than your Internet connections uplink speed would be, and set a fairly low limit for the amount of simultaneous connections. You can then increase both gradually until you reach the point where you start getting problems.

---

### Post by Funnnny on 2011-02-04
I can say that its not problem with number of peer connect, upload or download speed.
I can use deluge with no problem, even I have a long list of seeding file and have a high number of allowed connection. But when I use Transmission, even if I have only one file downloading, it just kill the net completely, other machine have no problem, and even transmission have no problem, just my net.

---

### Post by Alethenorio on 2011-11-06
Has this problem been solved? I am having the same problem on 11.10

I open transmission and even if there is no download/upload going on it kills my internet (Except for Transmission, it works just fine) and no webiste works anymore.

Have you guys found a solution for this?

Regards
Alethenorio

---

### Post by computerandu on 2011-11-06
So is there any solution to it? I too am facing the same with Ubuntu 11.10

---

### Post by Rodney9 on 2011-11-06
I find [Deluge]("http://deluge-torrent.org/") works much better, it is in Synaptic or the Lubuntu Software Center.

Rodney

---

### Post by Alethenorio on 2011-11-08
Thanks for the tip, Deluge is indeed very nice but that still doesn't fix the fact that transmission is broken.

Someone should note the developer in case it hasn't been done yet.

---

### Post by Juliano Paz on 2011-11-20
Same problem here on lubuntu 11.10.  On deluge i have no problem with 200 connections limit but with transmission in 50 connections limited crash my network when full speed force me to restart.
Using deluge until solve problem with transmission.
I prefer transmission.

---

