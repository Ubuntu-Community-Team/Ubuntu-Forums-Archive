---
title: "100 MB/s to 10 MB/s"
date: 2008-12-02
forum: Networking &amp; Wireless
---

### Post by ewercr on 2008-12-02
So, my university has activated some bandwidth shaping tools.  One of the major effects of this change is that loading Gmail or GCal takes forever (system monitor shows that while loading Gmail, my network speed never goes above 10 kb/s).  Now, the network admins have instituted an across the board bandwidth cap of 120 kb/s, and when I load other pages, my network speed can go this high.  I emailed one of the admins and explained my situation, asking why Google services are unable to use the available bandwidth.  It is also important to note that this anomaly only occurs when I am connected via ethernet.  The admins response was that since the wiring in my residence has a max. speed of 10 mb/s, and my ethernet adapter is probably trying to connect at 100 mb/s, I should connect at 10 mb/s.  So, my questions are 

a) How would I go about changing my ethernet connection speed from 100mb/s to 10mb/s?

b) Is there another explanation for why Gmail and Gcal load so slowly, compared to other websites?

---

### Post by costre on 2008-12-31
I'm interested in this, too. 

I was thinking of taking an old 10Mbit switch and plug in between the computer and the 100Mbit switch I normally use, effectively capping the speed to 10 Mbit.
Of course, if there's a way to solve it without extra hardware, I'm all for that.

---

### Post by ewercr on 2008-12-31
Since posting my initial question, I found the following command line tools which allow you to manually change the link speed: mii-tool and ethtool.

Both can be downloaded through APT and both must be run as root.

---

### Post by crazy ivan on 2009-11-12
Hey, I have to downgrade network speed due to broken cable (very long, so I don't want to redo it).. 

So far I found two possibilities to do it ad hoc
```

sudo ethtool -s eth0 autoneg off
sudo ethtool -s eth0 speed 10
sudo ethtool -s eth0 duplex full 

```

or 

```

sudo rmmod 8139too
sudo modprobe 8139too media=10

```

I have tried it everything to make this change permanent but...
So far what does not work is

[LIST]
[*]adding 
```

8139too media=10

```
to /etc/modprobe.d/options
[*]adding
```

8139too media=10

```
to /etc/modules
[*]changing the /etc/rc.local script from
```

...
exit 0

```
to 
```

...
cat /etc/rc.local|grep -v ^exit  >> /tmp/rc.local
echo ethtool -s eth0 autoneg off >> /tmp/rc.local
echo ethtool -s eth0 speed 100   >> /tmp/rc.local
echo ethtool -s eth0 duplex full >> /tmp/rc.local
echo exit 0 >> /tmp/rc.local
sudo cp /etc/rc.local /etc/rc.local.orig
sudo cp /tmp/rc.local /etc/rc.local
exit 0

```
following the suggestions in another thread [http://ubuntuforums.org/showthread.php?t=1164164]("http://ubuntuforums.org/showthread.php?t=1164164").
[/LIST]

I should mention that this machine is running ubuntu 8.10... 9.10 is able to cope with the interrupted connection automatically (resulting in a connection way below 10Mbit)..

May some expert enlighten my limited horizon [-o<

---

### Post by crazy ivan on 2010-01-08
“Enlightenment is man’s emergence from his self-incurred immaturity.” 18 century

"Enlightenment is knowing how to use the search engine.." today..

[URL="http://www.ubuntu-unleashed.com/2007/09/i-personally-like-gui-tools-but-i-also.html"]
http://www.ubuntu-unleashed.com/2007/09/i-personally-like-gui-tools-but-i-also.html[/URL]

---

