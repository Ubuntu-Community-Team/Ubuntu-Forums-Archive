---
title: "Ethernet on my Thinkpad is slower than expected"
date: 2014-03-16
forum: Networking &amp; Wireless
---

### Post by Alex D on 2014-03-16
Hi all,

I wonder whether anybody is able to provide me some advice on the issue below, I already asked for some help four weeks ago on the Mint forum but nobody reacted.
Since a 3 months I am running Linux Mint 13 Mate on my Thinkpad T40 with a Pentium M processor 1.5 GHz, 2GB RAM.
Ethernet controller		: Qualcomm Atheros AR5212 802.11abg NIC (rev 01)
Ethernet controller		: Intel Corporation 82801DB PRO/100 VE (MOB) Ethernet Controller (rev 81)

Everything is running smoothly, however I am not satisfied about my browsing experience.
I use FF, two main issues:

1)  Launching FF takes 20 secs. to show up. (I have already taken all  suggested steps to speed up FF as advised by the tutorial on the Mint  website, including the Preload package).
2) When wheel scrolling the  pages, it is not fluid, I mean, it takes some time to load the images, I  have to wait in order to continue scrolling.

When I look at my  wireless connection, speed is 54 Mb/s in the connection info panel and  the signal strength bars are usually 2/4 bars (it was 4/5 when the same  PC was on Windows 7), router is close to the PC.
When I hook it to the Ethernet wire, speed in the connection info panel goes to 100 Mb/s
I use OpenDNS servers.

Now, I ran a speed test** **on my ThinkPad and below the results:

**Wired:**
Download Speed: 34903 kbps (4362.9 KB/sec transfer rate)
Upload Speed: 28531 kbps (3566.4 KB/sec transfer rate)
Latency: 7 ms
Jitter: 3 ms
Packet Loss: -1%

**Wireless:**
Download Speed: 20145 kbps (2518.1 KB/sec transfer rate)
Upload Speed: 9908 kbps (1238.5 KB/sec transfer rate)
Latency: 8 ms
Jitter: 16 ms
Packet Loss: -1%

If I run the same test on my W7 Core i5 I get exactly what I pay for: 50/30 Mbps.

**Wired**
Download Speed: 50290 kbps (6286.3 KB/sec transfer rate)
Upload Speed: 31556 kbps (3944.5 KB/sec transfer rate)
Latency: 4 ms
Jitter: 5 ms
Packet Loss: -1%

**Wireless**
Download Speed: 43776 kbps (5472 KB/sec transfer rate)
Upload Speed: 31441 kbps (3930.1 KB/sec transfer rate)
Latency: 4 ms
Jitter: 2 ms
Packet Loss: -1%

My router is an Actiontec R1000H.

The negative packet loss, seems to be due to a software issue with the ISP provider, obviously not relevant being negative.


In you opinion, what is affecting the wired speed so much?
What can I do to improve my browsing experience?
Are the two issues related?

Hopefully, I provided all the necessary information for you to help, but if you need more, I'll be happy to provide it [IMG]http://forums.linuxmint.com/images/smilies/icon_smile.gif[/IMG]

Thank you!
Alex

---

### Post by tgalati4 on 2014-03-16
T40 is an old machine.  They are business machines and are built relatively tough, with conservative designs and thus are not very fast.  Comparing a Pentium M to an i5 means you should compare the cost as well ($200 versus $1500 in today's US dollars).  

Your T40 has an Ethernet 100 Mbit connection.  I'm pretty sure your i5 has a Gigabit connection.  I have a T43p and I replaced the old disk drive with a new (at the time) 320 GB drive.  I don't have a problem with Firefox.  I used to run firefox in a RAMdisk to speed it up, now I don't have to.

There are a lot of tools to monitor network performance.  Try installing *iperf* on your T40 and on another linux machine on the same, wired network and measure speed that way.

What is the basic speed of your current disk drive?

```
sudo hdparm -tT /dev/sda
```

Try measuring speed of Windows7 on your T40.

---

### Post by Alex D on 2014-03-16
Hi,

thank you for your quick reply.

I ran 
sudo hdparm -tT /dev/sda on my terminal, here is what I got:

 Timing cached reads:   650 MB in  2.00 seconds = 324.32 MB/sec
 Timing buffered disk reads: 170 MB in  3.01 seconds =  56.43 MB/sec

My HDD is a WD 250GB 5400RPM PATA - WD2500BEVE
I only have this machine with Linux (T40) on my home network, all the rest is on W7.

I am not familiar with the *iperf* tool, but I have now installed it on both my Corei5 and Linux machines.

Would you help me with the commands to run to get the speed of W7 on my T40?
W7 as a server and the T40 as a client?

Thanks
Alex

---

### Post by tgalati4 on 2014-03-16
Your RAM speeds and disk speeds are kind of low:

2006 Acer Extensa:  

tgalati4@Mint14-Extensa ~ $ sudo hdparm -tT /dev/sda
[sudo] password for tgalati4: 

/dev/sda:
 Timing cached reads:   1660 MB in  2.00 seconds = 830.60 MB/sec
 Timing buffered disk reads: 144 MB in  3.03 seconds =  47.49 MB/sec

The first number is the RAM read speed.  the second number is the raw disk read speed.  Multiply by 8 to get Megabits/sec.  So your disk speed would be 451 Megabits/second.  Your disk is probably not the bottleneck for firefox performance.

Run *free* in a terminal and see how much RAM is used during a firefox session.


Some *iperf* examples in this thread:  [http://ubuntuforums.org/showthread.php?t=2143393&highlight=iperf](http://ubuntuforums.org/showthread.php?t=2143393&highlight=iperf)

---

### Post by Alex D on 2014-03-19
Hi there,

no idea why they are so slow, attached the results of *free* in the terminal with FF on.

Thanks
Alex

---

### Post by tgalati4 on 2014-03-20
Your RAM looks OK.  Since no swap is being used, your slowdowns are not caused by excessive swapping to disk.  Run the *iperf* tests to see if there are network bottlenecks.

---

### Post by Alex D on 2014-03-20
Hi,

the two screenshots attached show the Iperf results using Linux both as a server and client with my W7.

Alex

---

### Post by tgalati4 on 2014-03-20
You might have a lot of traffic on your router or you have some policies set up on the router such as Quality of Service (QoS).  Go into your router webpage and check your settings.

Try changing cables and ports on computer and run the tests again.  Your results should be 80 to 90 megabits/sec with no other traffic and 40 to 45 megabits/sec with one additional computer.  Each additional computer cuts the bandwidth approximately in half.

Wireless is slower, a 54G (54 megabit/sec maximum throughput) is actual only 48 megabit/sec in the US and that means 24 megabits/sec up and 24 megabits/sec down.  Add a second wireless device and you cut that in half (12 up and down).  If you have any wireless B devices (like an older, wireless printer) that will slow the speeds down to 1 megabits/sec for everybody on that same wireless G network.

So, you need to find the bottleneck using a wired connection, fix that, then perform your tests with wireless.

What version of Firefox?

---

### Post by Alex D on 2014-03-22
Hi,

Here the results of the test, only two machines wired: 1 Linux + 1W7
The results are as you described.

To  be honest with you, I do not think there is anything wrong with my  network, even when I browse with the Linux PC only connected and all the  rest is off, I get the same speed test results and the same slow  response from FF.
I will try another browser to see if I get the same (Chromium ?), but I think the issue is my T40 hardware somewhere.
I mean, shouldn't I get the same connection speed of my W7 when I run the speedtest (50/30 M/bps)?

Alex

---

### Post by tgalati4 on 2014-03-22
If it is only Firefox that is slow, then disable all of your plugins, clear your cache, clear your cookies.  If that doesn't work, then delete your firefox profile and start fresh.  

What version of Firefox?

---

### Post by Alex D on 2014-03-22
Firefox 28

---

### Post by tgalati4 on 2014-03-22
So you are running the latest Firefox.  I don't have any other ideas at this point.  Your disk throughput is OK, your RAM is OK, your network card is working to capacity.  The only other thing contributing to browser slowness is March Madness.

---

### Post by Alex D on 2014-03-22
As I said, I'll compare with another browser and see what happens, I'll post back the results. :)  Alex

---

