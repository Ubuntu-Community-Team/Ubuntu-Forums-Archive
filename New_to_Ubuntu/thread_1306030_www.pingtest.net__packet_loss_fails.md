---
title: "www.pingtest.net  packet loss fails"
date: 2009-10-30
forum: New to Ubuntu
---

### Post by ubername on 2009-10-30
HI

I have been struggling to get my internet speed on Ubuntu as good as it is on windows and have using these forums I have identified (I think) it is to do with DNS. As part of testing this I have used the site pingtest.net, and consistently (always) cannot complete the packet loss test, whereas in Windows (7) I had to allow the java app through the firewall. AFAIK I am not using a firewall in Ubuntu. Amy clues?

(and if anyone has a silver bullet for internet speed I would be grateful! I have tried manually configuring Network settings, disabling IPv6 as a command line option in GRUB, and messing with my nsswitch.conf hosts setting)

Here are some example pingtest results:

ubuntu (as good as I can get it
[[IMG]http://www.pingtest.net/result/2033676.png[/IMG]](http://www.pingtest.net)

I am using Karmic (upgraded since alpha1) on x64 Dell with wired Intel network card.
Windows (first and subsequent tries)
[[IMG]http://www.pingtest.net/result/1991635.png[/IMG]](http://www.pingtest.net)

---

### Post by phillw on 2009-10-30
Running FF, 9.10, Wireless - I get ...

Ping 54ms
Download 4.89 Mb/s
Upload 0.74 Mb/s

I'm happy with that.

There is some stuff to fine tune FF over at  [http://ubuntuforums.org/showthread.php?t=1193567](http://ubuntuforums.org/showthread.php?t=1193567)

Regards,

Phill.

---

### Post by tarps87 on 2009-10-30
Have you tried using other tools, such as the built in ping funtionality?

---

### Post by ubername on 2009-10-30
> **phillw said:**
> Running FF, 9.10, Wireless - I get ...

Ping 54ms
Download 4.89 Mb/s
Upload 0.74 Mb/s

I'm happy with that.

There is some stuff to fine tune FF over at  [http://ubuntuforums.org/showthread.php?t=1193567](http://ubuntuforums.org/showthread.php?t=1193567)

Regards,

Phill.
I think that's speedtest.net you're using, and I am on chrome, but thanks anyway!

---

### Post by ubername on 2009-10-30
> **tarps87 said:**
> Have you tried using other tools, such as the built in ping funtionality?Bytes	Source	Seq	Time	Units
64	69.17.117.207	1	539	ms
64	69.17.117.207	2	745	ms
64	69.17.117.207	3	820	ms
64	69.17.117.207	4	763	ms
64	69.17.117.207	5	1247	ms
Time minimum:	539.00 ms
Time average:	775.50 ms
Time maximum:	1247.00 ms
Packets transmitted:	5
Packets received:	5
Successful packets:	100%

This shows another of my problems - massive variance in ping results (the above is for speedtest.net, I got about 18ms for google.com)

My real question is about the difference between ubuntu and windows hoiwever. Here is a latest  pingtest.net result. 
[[IMG]http://www.pingtest.net/result/2038103.png[/IMG]](http://www.pingtest.net)

---

### Post by phillw on 2009-10-30
> **ubername said:**
> I think that's speedtest.net you're using, and I am on chrome, but thanks anyway!

pingtest.net has now crashed my browser twice (I have 8 tabs open ..... thank heavens for FF being able to recover)

So, soz, I won't be popping my results on !!!

the latency / packet loss of pings depends a lot on the number of Hops and latency of the servers along the way. Also upon how responsive the servers are. Google should be good, the ubuntu servers for the iso images would have been horrendous y/day, as everyone and their dog was downloading 9.10 ;-)   Hence the request to use torrents !!

Phill.

---

### Post by markbuntu on 2009-10-30
Have you tried another testing tool?
It seems to me that some of these tools do not work so well when you are not using windoze. Speedtest always has ubuntu faster at upload/download than windoze but pingtest cannot test packet loss on any linux system I have tested with it so it probably is depending on something specific in the windoze IP stack that linux does not use. 

Anyway, I got this with my hardy heron:

[IMG]http:///www.pingtest.net/result/2072657.png[/IMG]

Speedtest

[IMG]http://www.speedtest.net/result/607615820.png[/IMG]

---

### Post by ubername on 2009-10-31
Markbuntu - Thanks for the info re pingtest on linux systems, it would be good to know what the problem is. 

FWIW My Speedtest on Ubuntu:

[[IMG]http://www.speedtest.net/result/607927559.png[/IMG]](http://www.speedtest.net)

---

### Post by tarps87 on 2009-10-31
Have you tried using the same tools on the windows machine, when you use the ping command try it will google rather than the ping test server
It will be interesting to see if they differ too.
It is possible that the site is windows specific which would explain why it can work out the packet loss

---

### Post by ubername on 2009-11-01
Hmm... Odd

Result from karmic on my hard drive:
[[IMG]http://www.pingtest.net/result/2245571.png[/IMG]](http://www.pingtest.net) 

Result from karmic on my USB drive
[[IMG]http://www.pingtest.net/result/2245931.png[/IMG]](http://www.pingtest.net) 

So it looks like it is not a windows / Linux thing./ Must do some more digging!

---

### Post by ubername on 2009-11-20
I think it is something to do with the way java / browser interacts, after dropping a note to pingtest..


The following from a lucid box:
Firefox
[[IMG]http://www.pingtest.net/result/3907711.png[/IMG]](http://www.pingtest.net)

Chrome
[[IMG]http://www.pingtest.net/result/3934260.png[/IMG]](http://www.pingtest.net)

Opera
[[IMG]http://www.pingtest.net/result/3934395.png[/IMG]](http://www.pingtest.net)

---

### Post by Cigaras on 2009-11-23
Is it because you're using Wifi internet? When I switched to cable - everything is ok.

[[IMG]http://www.pingtest.net/result/4201873.png[/IMG]](http://www.pingtest.net)

---

### Post by ubername on 2009-11-29
> **Cigaras said:**
> Is it because you're using Wifi internet? When I switched to cable - everything is ok.

[[IMG]http://www.pingtest.net/result/4201873.png[/IMG]](http://www.pingtest.net)

Nope, all tests from wired connection. As I say, it appears to be the way the browser and java work together.

---

### Post by vol7ron on 2010-08-16
ubername is right.

I `apt-get install sun-java6-plugin` to use Java for pingtest.net

I tried this with Chrome.  The "Packets Sent/Received" lines were just blank.

I tried this with Firefox.  The "Packets Sent" went up to 250 and Packets Received stalled out at 0, but at least Java was able to capture some of the information, whereas it consistently failed with Chrome.

Something to note: Firefox brought up a security warning, asking for permission for pingtest.net to establish a connection with ubuntu.  Chrome never asked for any sort of permission until opening it after Firefox.  Then Chrome was able to send 250 packets and stall out at 0 received.

In a way, I liked it better before it stalled out because I was at least able to

---

