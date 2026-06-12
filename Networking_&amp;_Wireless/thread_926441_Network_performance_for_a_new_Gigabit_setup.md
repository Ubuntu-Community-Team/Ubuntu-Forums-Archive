---
title: "Network performance for a new Gigabit setup"
date: 2008-09-21
forum: Networking &amp; Wireless
---

### Post by LO Matt on 2008-09-21
Hello,

I've gone ahead and upgraded my home setup to Gigabit hardware:  D-link DIR-655 and cat 6 cables.  I've tried transferring files from my machine to a Powermac G5, my machine to a Terastation and the Powermac to the terastation.    I'm getting about 10Mb/s, which I'd expect better performance.  

A little background, The Terrastation is setup to use Samba and between the mac and this machine, I have netatalk setup.  Using ext3 on here and the mac has HFS.  The Terastation has XFS from what I read.  All drives are SATA.

I'm pretty confident all the hardware in my setup is Gigabit.  So are the numbers I'm seeing typical overhead or am I missing a setting?

Also, I'm transferring about 300Gb of data to the Terastation and the graph on my system monitor goes up and down in a 2 second frequency from 30Mb/s to 0. 

[IMG]http://i7.photobucket.com/albums/y285/mhpeter/Screenshot-SystemMonitor.png[/IMG] 

Is this to be expected as well or can I get a more steady networking performance?  

TIA

---

### Post by jpkotta on 2008-09-23
Could be your hard drive is the bottleneck now.  You can get a feel for maximum hard drive speeds with ```
sudo hdparm -t /dev/sdX
```  Be careful with hdparm, it is powerful.  Replace X with your hard drive letter.  

To get a better idea of maximum network throughput, use nc (netcat).

RX
```
nc -l -p 22222 > /dev/null
```

TX
```
cat /dev/zero | nc remote_hostname 22222
```

I can saturate my 100 Mbit network with this, and it gets about 90 Mbit/s.

Gigabit ethernet is not 10 times faster than 100 Mbit, as I found out recently.  It is about 2-4x faster.

---

