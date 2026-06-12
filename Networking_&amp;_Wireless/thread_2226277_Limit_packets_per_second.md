---
title: "Limit packets per second"
date: 2014-05-26
forum: Networking &amp; Wireless
---

### Post by chris137 on 2014-05-26
Hi,
I'm using a vServer to download stuff.
I already got warned because my traffic is way too high.
They provide 1Gbps but apparently the packet-limit is 150kpps.
Since I do not want to get banned I'd like to install something which limits the packets to maybe 100kpps.

I tried google but could not find anything helpful.
iptables seems to be only able to limit up to 10kpps which is way to low.
Other solutions are pretty complicated so I hope you could help me.

---

### Post by tgalati4 on 2014-05-26
One way to approach this problem is to set the physical connection speed on your ethernet card.  If you are running a 1 Gigabit/sec network card, then switch it to 100 Mbit/sec or even 10 Mbit/sec.  If this is a wireless connection, you can degrade the wireless bandwidth from 54 Mb/sec to 12 Mb/sec.

Use *modinfo* and *ethtool* to see what the switches are for your network card.


tgalati4@tpad-Gloria7 ~ $ sudo ethtool eth0
[sudo] password for tgalati4: 
Settings for eth0:
	Supported ports: [ TP ]
	Supported link modes:   10baseT/Half 10baseT/Full 
	                        100baseT/Half 100baseT/Full 
	                        1000baseT/Half 1000baseT/Full 
	Supports auto-negotiation: Yes
	Advertised link modes:  Not reported
	Advertised auto-negotiation: No
	Speed: 100Mb/s
	Duplex: Half
	Port: Twisted Pair
	PHYAD: 1
	Transceiver: internal
	Auto-negotiation: off
	Supports Wake-on: g
	Wake-on: d
	Current message level: 0x000000ff (255)
	Link detected: no

---

### Post by chris137 on 2014-05-26
Since it's a vServer I don't even think I have full access to these settings but this is not the way I want to go anyway.
Most of the time there is no problem with 30MB/s and up but sometimes the packets are so weird that I could reach this limit with 15MB/s.
So I'd need a way to specifically limit the packets.

---

### Post by tgalati4 on 2014-05-26
Get friendly with *tc*.  

```
man tc
```

Normally you would use Quality of Service (QoS) to limit bandwidth to a particular port, but I don't know of a way to limit it by packet speed.  That occurs at a level in the Networking Stack that is not normally accessible.  

Your search continues:

[http://lartc.org/howto/lartc.ratelimit.single.html](http://lartc.org/howto/lartc.ratelimit.single.html)

[http://askubuntu.com/questions/388390/shape-throttle-an-ip-on-the-network-qos](http://askubuntu.com/questions/388390/shape-throttle-an-ip-on-the-network-qos)

Finally, I would ask "they" to put a QoS filter on your connection, since they are the ones complaining.

---

### Post by chris137 on 2014-05-26
So I read your links but again could not find any pps-solution
Maybe there is one but I just did not get it.
Until now I always found a solution for my problems but this one is really hard.
I tried iptables again because I could not believe that this would be limited.
But with anything above 10000/s I get this: "Rate too fast"

Any idea why?

---

### Post by tgalati4 on 2014-05-26
What is the exact syntax that you are using for your iptables filter?

---

### Post by chris137 on 2014-05-26
iptables -D INPUT -p tcp -m limit --limit 10000/s -j ACCEPT
works, while
iptables -D INPUT -p tcp -m limit --limit 10001/s -j ACCEPT
does not:
iptables v1.4.12: Rate too fast "10001/s"

---

### Post by tgalati4 on 2014-05-26
It must be a hard-coded limit.  You can do a couple of things:

1.  Look through the source code for iptables and see if you can find the limit and change it and recompile.
2.  Look for another method to limit bandwidth.

Remember, if you have multiple threads or connections downloading files then you will probably exceed your packet rate.  So check your processes to see how many threads are created and perhaps control the thread count if you have multiple downloads occurring.

---

### Post by chris137 on 2014-05-27
I would'nt even know where to start with #1
#2 is what I was doing the past few days.

I only download via rtorrent so there is only one thread.

Edit: Just now I had an idea:
I'm using vnstat to monitor my traffic on that server.
Wouldn't it be possible to somehow automatically monitor the pps (which vnstat can read) and - if a certain limit is reached - kill rtorrent?
Since it is only this one process this could actually work.
I just do not know how to monitor vnstat's output.

This would not be the ideal solution but would do the job.

---

### Post by tgalati4 on 2014-05-27
You could take any network monitor tool and if you exceed a certain parameter, you could *ionice* rtorrent instead of killing it.  I still think you need to work with your service provider, they are the ones that should implement bandwidth throttling, not you.

---

### Post by chris137 on 2014-05-27
Never used ionice, will read to it further tomorrow.
Will use pkill in my example below.
I like my idea :D
Sadly I've never done something like this before.
The script should be pretty easy.
Could look like this:
```
for a=0
no idea, see below
pps=whatever
if $pps > 100000
a=1
pkill rtorrent
```
So the hard part is getting $pps

vnstat seems to only deliver pps with vnstat -l
It looks like this:
```
$ vnstat -l
Monitoring eth0...    (press CTRL-C to stop)     
rx:     384.00 KB/s   293 p/s          tx:      23.50 KB/s   181 p/s
```
$pps obviously had to be the first one plus the second one.
I think I did something far related before but I can't figure it out.
vnstat -l >> file
seems not ideal because something like this would be the output:
```
Monitoring eth0...    (press CTRL-C to stop)

   getting traffic...^H ^H^H ^H^H ^H^H ^H^H ^H^H ^H^H ^H^H ^H^H ^H^H ^H^H ^H^H ^H^H ^H^H ^H^H ^H^H ^H^H ^H^H ^H^H ^H^H ^H^H ^H   rx:       2.00 KB/s    23 p/s          tx:       2.00 KB/s    18 p/s^H ^H^H ^H^H ^H^H ^H^H ^H^H ^H^H ^H^H ^H^H ^H^H ^H^H ^H^H ^H^H ^H^H ^H^H ^H^H ^H^H ^H^H ^H^H ^H^H ^H^H ^H^H ^H^H ^H^H ^H^H ^H^H ^H^H ^H^H ^H^H ^H^H ^H^H ^H^H ^H^H ^H^H ^H^H ^H^H ^H^H ^H^H ^H^H ^H^H ^H^H ^H^H ^H^H ^H^H ^H^H ^H^H ^H^H ^H^H ^H^H ^H^H ^H^H ^H^H ^H^H ^H^H ^H^H ^H^H ^H^H ^H^H ^H^H ^H^H ^H^H ^H^H ^H^H ^H^H ^H^H ^H^H ^H^H ^H^H ^H^H ^H^H ^H^H ^H   rx:       2.50 KB/s    18 p/s          tx:       3.00 KB/s    18 p/s
```
No idea how to get the right number out of this mess.

Any ideas?
Maybe vnstat is just not the right tool for it?

---

### Post by tgalati4 on 2014-05-27
Normally you would use sed, awk, gawk, mawk, or perl to get a specific field from a command's output and then use that in a script to control something.

[http://www.faqforge.com/linux/reduce-load-of-backup-scripts-with-nice-and-ionice/](http://www.faqforge.com/linux/reduce-load-of-backup-scripts-with-nice-and-ionice/)

[http://friedcpu.wordpress.com/2007/07/17/why-arent-you-using-ionice-yet/](http://friedcpu.wordpress.com/2007/07/17/why-arent-you-using-ionice-yet/)

---

### Post by slooksterpsv on 2014-05-27
What about trickled?

sudo trickle -d 20 -u 20 "apt-get install xyz"

or:

sudo trickle -d 150 -u 10 transmission-gtk

You can also do a daemon with:

sudo trickled -d 150 -u 10

---

### Post by chris137 on 2014-05-28
**@**tgalati4:
Currently I have no time to look into those you named.
So if there is no one providing me with further info I would probably have to reschedule next week.

I read into ionice and think I got it.
But since there isn't really running anything else (beside those standard-linux-things and an apache) I am not sure how this could have any effect.
Tried it and it actually did not work.
$ ionice -c 3 -p 12376
while 12376 is the pid of rtorrent
Had no effect on it at all.


@slooksterpsv:
trickled would actually be pretty cool if there was a way to do this with packets per second ;)

---

### Post by chris137 on 2014-05-31
Okay, I just had a liitle time and tried something.
Of course I knew gawk, just did not recognize it without context. Was exactly what I was looking for.
So this is what I got and I think it should work:
```
#!/bin/bash
for ((i=0;i<4))
do
        traffic=$(sar -n DEV 1 1 | grep eth0 | tail -n 1 | gawk '{print $3+$4}')
        if [ $traffic -gt 140000 ]; then
                pkill rtorrent
                sleep 30
                rtorrent
                i++
        fi
done
```

```
sar -n DEV 1 1 | grep eth0 | tail -n 1 | gawk '{print $3+$4}')
```
Gets me my packets per second using 'sysstat', adds up-&download and saves it as $traffic.

If the traffic is over 140kpps rtorrent gets killed and restartet after 30 seconds.
If the limit is exceeded more than 3 times it won't start again.

So this is what should happen.
However I think that this is not quite accomplished.
As far as I understand my own script this is what actually happens:
If rtorrent is killed three times it gets started again but the script won't run at all and therefor not monitor the traffic.
Where would I put this 'for' so that it does what I want?

Hope this script is right at all.


Edit:
Okay so as I found out that is not even how for works.
I edited and as far as I see it does work.
```
#!/bin/bash
i=0
while :
do
        traffic=$(sar -n DEV 1 1 | grep eth0 | tail -n 1 | gawk '{print $3+$4}')
        if [ $traffic -gt 120000 ]; then
                pkill rtorrent
                echo `date +"%d.%m.%y  %T killed with "$traffic" p/s"` >> trafficlog
                sleep 30
                if [ $i -eq 4 ]; then
                        exit
                else
                        rtorrent
                        echo `date +"%d.%m.%y  %T started"` >> trafficlog
                        i=$[$i+1]
                fi
        fi
done
```

Should do the job

---

