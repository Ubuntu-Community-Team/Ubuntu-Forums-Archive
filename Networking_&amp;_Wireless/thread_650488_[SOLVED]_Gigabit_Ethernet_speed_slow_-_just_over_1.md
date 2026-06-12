---
title: "[SOLVED] Gigabit Ethernet speed slow - just over 100 Mbps"
date: 2007-12-26
forum: Networking &amp; Wireless
---

### Post by dbott67 on 2007-12-26
[COLOR=Purple]*Update: The problem (if you can call it that) has been resolved.  The issue was the fact that I was relying on the throughput reported by Samba transfers, which turns out to be quite poor.  See post #11 for performance benchmarks using iPerf and FTP rather than Samba for measuring throughput.*[/COLOR]

Hi Folks,

I've recently upgraded my home network to gigabit, and like others, am seeing very poor performance (~100 Mbps, give or take).  I have read many different threads that report similar behaviour but have yet to find a solution.

I have tried with & without [COLOR=Red]jumbo frames[/COLOR], but it does not seem to make a significant difference:
```
 sudo ifconfig eth1 mtu 9000
``````
dbott@gutsy:~$ ifconfig
eth1      Link encap:Ethernet  HWaddr 00:19:5B:FC:8E:14  
          inet addr:192.168.1.100  Bcast:192.168.1.255  Mask:255.255.255.0
          UP BROADCAST RUNNING MULTICAST  [COLOR=Red]MTU:9000[/COLOR]  Metric:1
          RX packets:1496973 errors:0 dropped:0 overruns:0 frame:0
          TX packets:754971 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:2062443098 (1.9 GB)  TX bytes:383736761 (365.9 MB)
          Interrupt:17 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:1764 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1764 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:307438 (300.2 KB)  TX bytes:307438 (300.2 KB)
```Using Nautilus (or the 'cp' command) performs the copy in about 23 seconds (just over 100 Mbps).  Here are the results using a 302 MB file:
```
dbott@gutsy:~/Media/Videos$ time cp Rush_R30.m4v /home/dbott/Desktop/

real    0m22.980s
user    0m0.052s
sys     0m3.248s
```The results indicate a bandwidth of 105 Mbps. 

(302 MB / 22.98 s * 8 bits/Byte  = ~105 Mbps)

Bandwidth Monitor (bwm) seems to indicate similar results:

12322 KB/s * 8 = ~98 Mbps

```
Bandwidth Monitor 1.1.0

       Iface        RX(KB/sec)   TX(KB/sec)   Total(KB/sec)

          lo            0.000        0.000           0.000
        eth1        12322.516      326.510       12649.026

       Total        12322.516      326.510       12649.026

Hit CTRL-C to end this madness.
```_**[SIZE=3]Hardware Used[/SIZE]**_

[B]Desktop PC

CPU: Intel P4-1.8 GHz
RAM: 896 MB
Hard Drive: 160 GB WD
[/B]```
dbott@gutsy:~$ sudo hdparm -Tt /dev/sda1

/dev/sda1:
 Timing cached reads:   422 MB in  2.00 seconds = 210.78 MB/sec
 Timing buffered disk reads:  170 MB in  3.01 seconds =  56.46 MB/sec

```[B]
NIC: D-Link DGE-530T[/B]
```
dbott@gutsy:~$ sudo lshw -C network
  *-network               
       description: Ethernet interface
       product: DGE-530T Gigabit Ethernet Adapter (rev 11)
       vendor: D-Link System Inc
       physical id: b
       bus info: pci@0000:02:0b.0
       logical name: eth1
       version: 11
       serial: 00:19:5b:fc:8e:14
       size: 1GB/s
       [COLOR=Purple]capacity: 1GB/s[/COLOR]
       width: 32 bits
       clock: 66MHz
       capabilities: pm vpd bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=skge driverversion=1.11 duplex=full firmware=N/A ip=192.168.1.100 latency=32 link=yes maxlatency=31 mingnt=23 module=skge multicast=yes port=twisted pair speed=1GB/s
``````
dbott@gutsy:~$ sudo lspci -v | grep Ethernet -A 7
02:0b.0 Ethernet controller: D-Link System Inc DGE-530T Gigabit Ethernet Adapter (rev 11) (rev 11)
        Subsystem: D-Link System Inc DGE-530T Gigabit Ethernet Adapter (rev 11)
        Flags: bus master, 66MHz, medium devsel, latency 32, IRQ 17
        Memory at be000000 (32-bit, non-prefetchable) [size=16K]
        I/O ports at b000 [size=256]
        [virtual] Expansion ROM at bff00000 [disabled] [size=128K]
        Capabilities: [48] Power Management version 2
        Capabilities: [50] Vital Product Data
```[COLOR=Purple]ethtool[/COLOR] reports that the card is running at 1000 Mbps.  The [COLOR=Purple]LED[/COLOR] on the back of the card also indicates 1000 Mbps:

```
dbott@gutsy:~$ sudo ethtool eth1
[sudo] password for dbott:
Settings for eth1:
        Supported ports: [ TP ]
        Supported link modes:   10baseT/Half 10baseT/Full 
                                100baseT/Half 100baseT/Full 
                                1000baseT/Half 1000baseT/Full 
        Supports auto-negotiation: Yes
        Advertised link modes:  10baseT/Half 10baseT/Full 
                                100baseT/Half 100baseT/Full 
                                1000baseT/Half 1000baseT/Full 
        Advertised auto-negotiation: Yes
        [COLOR=Purple]Speed: 1000Mb/s
        Duplex: Full[/COLOR]
        Port: Twisted Pair
        PHYAD: 0
        Transceiver: internal
        Auto-negotiation: on
        Supports Wake-on: pg
        Wake-on: g
        Current message level: 0x00000037 (55)
        Link detected: yes
```**Switch: D-Link DGL-4500 Gigabit Wireless N Router**
Specs [here]("http://games.dlink.com/products/?pid=643&#DGL-4500").

**Cables: 2 x 3' Cat 5e Certified Patch Cables**

**Server: Netgear ReadyNAS NV+ RND-4250**
Specs [here]("http://www.netgear.com/Products/Storage/ReadyNASNVPlus/RND4250.aspx").

The NAS device also indicates that it's connected & running at 1000 Mbps (see attached screenshot).

When I swap out the Gigabit switch for a 10/100 switch, both devices report 100 Mbps so the problem does not appear to be hardware, as each system correctly determines that it is on a gigabit network.  Additionally, I can also achieve 130-150 Mbps speeds using smbget:

```
dbott@gutsy:~$ time smbget -u dbott -p mypassword smb://192.168.1.2/media/Videos/Rush_R30.m4v
Using workgroup MSHOME, user dbott
smb://192.168.1.2/media/Videos/Rush_R30.m4v                                     

[COLOR=Purple]real    0m17.728s[/COLOR]
user    0m1.384s
sys     0m5.120s
```A quick calculation reveals: 302 MB / 17.728 s x 8 = [COLOR=Purple]136 Mbps[/COLOR]

Bandwidth Monitor also confirms similar speeds:

18427 x 8 = [COLOR=Purple]147 Mbps[/COLOR]

```
Bandwidth Monitor 1.1.0

       Iface        RX(KB/sec)   TX(KB/sec)   Total(KB/sec)

          lo            0.000        0.000           0.000
        eth1        18427.367      364.898       18792.2650

       Total        18427.367      364.898       18792.2650
```I have a few other things I wish to try :

1. Crossover cable direct to NAS device.
2. Bring home work laptop (runs XP with Gb LAN interface).  Many others report that Windows works fine on same hardware/network.
3. Check through Launchpad for known issues using gigabit.

I will report back with my findings.

If anyone else has some suggestions, I'm all ears! :)

Thanks,
Dave

---

### Post by tgalati4 on 2007-12-26
A 100BaseT network usually sees peak transfers of 100 Megabits/sec but usual transfer is ~33 Mb/sec with multiple machines on the same subnet.

If you are getting sustained 100 to 135 Mb/sec then you are exceeding 100BaseT speeds.  It's not gigabit speeds, but I believe the specification is similar, peak speeds are up to 1 Gb/sec but sustained speeds are much lower.  In this case with your testing you have discovered this sustained transfer speed. (137 to 147 Mb/sec).

I have yet to see faster transfer speeds between several linux machines on the same subnet of a gigabit lan.

---

### Post by mips on 2007-12-26
What speeds are you expecting?

Lots of factors at play here like bus width/speed of NIC, HD throughput, non-blocking switch etc Theoretical throughput of a system bus does not come close to it's actual throughput due to overheads and simply running out of steam.


From what I have googled your speeds seem about normal for a desktop system. Dedicated server hardware performs much better though. Many people complain that after they upgraded to Gig Eth they don't see much benefit and this includes windows users.

** Edit:**
If you want to test the maximum throughput of your pc then connect to the loopback interface from the very same pc and do your tests. This will give you some benchmark as to the fastest speeds it is capable of

---

### Post by mips on 2007-12-26
[http://www.codinghorror.com/blog/archives/000339.html](http://www.codinghorror.com/blog/archives/000339.html)

---

### Post by dbott67 on 2007-12-26
Thanks for the posts, folks.  

@tgalati: You may be right about the level of performance to be expected. I have read other threads/posts that have achieved much higher performance, but my results just may be a limitation of my hardware.

@mips: From what I've read, I'm expecting somewhere in the 25-30 MB/s range.  I'm aware that there are many factors, but I'm only seeing between 12-19 MB/s.

The NAS device I have has benchmarks in the 20,000 - 35,000 KB/s range for reading (see figure 7) and I'm only about 12,000 - 19,000 KB/s:
[http://www.smallnetbuilder.com/content/view/29829/75/1/3/](http://www.smallnetbuilder.com/content/view/29829/75/1/3/)

So, I'm kind of at the bottom end of the scale.

[COLOR=Red]**What command would I use to perform the loopback test?**[/COLOR]

Oh, and thanks for the codinghorror.com link --- the author's note about gigabit performance being about double that of 100 Mb is what I'm experiencing.

Thanks for the feedback.

-Dave

---

### Post by psusi on 2007-12-26
It looks to me like you have a pretty slow NAS device there, plus smb is not the most efficient protocol.  Also the implementation of smbfs and smbget aren't as good as they could be.  

For the record, years ago I wrote an ftp server under windows NT and was able to sustain file transfers of 11,820 KB/s over 100Base-T.  I believe Linux can do that these days if the server is using sendfile().

---

### Post by dbott67 on 2007-12-26
> **psusi said:**
> It looks to me like you have a pretty slow NAS device there

After doing some research on NAS performance (consumer/prosumer-level NAS devices, plus a few [do-it-yourselfers]("http://www.tomsguide.com/us/cheap-fast-diy-raid-5-nas,review-779-11.html")), I've come to learn that most NAS devices in this category (Gigabit LAN w/RAID 1/5) have throughput in the 10 - 36 MBps range and aside from the 2 Thecus NAS devices, the Netgear outperforms every other NAS device in the RAID 5 category.

In fact, I even looked at benchmarks for NAS devices that did not utilize RAID just for comparison.  Although some models were able to squeeze out a little more performance (almost 40 MBps), it comes at a cost of losing redundancy.  Most were still in the 20-30 MBps range, but did not have the added overhead of RAID.

This [site]("http://www.smallnetbuilder.com/") has benchmarks for virtually every make & model NAS out there.  I've summarized the NAS devices with gigabit & RAID 5 (it's also the only category where the Netgear ReadyNAS NV+ listed):

[http://www.smallnetbuilder.com/component/option,com_nas/Itemid,190/chart,15/](http://www.smallnetbuilder.com/component/option,com_nas/Itemid,190/chart,15/)

Based on the test results, my results are a little on the low side, but still within normal range.  Here is a full write-up of the ReadyNAS NV+:

[http://www.smallnetbuilder.com/content/view/29829/75/](http://www.smallnetbuilder.com/content/view/29829/75/)

Virtually every [review]("http://reviews.cnet.com/external-hard-drives/netgear-readynas-nv-network/4505-3190_7-32464380.html") that I've read states that the NV+ offers the best features, performance and reliability of all consumer NAS devices.

So, as far as I can tell, the Netgear ReadyNAS NV+ is not slow; it is above average in performance in virtually every review I've read (*note: mine may be slow, but it may be [PEBKAC]("http://en.wikipedia.org/wiki/PEBKAC")*).

> **psusi said:**
> ...plus smb is not the most efficient protocol.  Also the implementation of smbfs and smbget aren't as good as they could be.  

For the record, years ago I wrote an ftp server under windows NT and was able to sustain file transfers of 11,820 KB/s over 100Base-T.  I believe Linux can do that these days if the server is using sendfile().

I'll have to play around with FTP and see what results I come up with.  I did come across a post of yours where you wrote about the FTP program you wrote and it got me trying a few other things.

As it stands, I don't think there is a problem to solve... maybe just a bit of refinement of some settings (jumbo frames & what-not).

Thanks for everyone's advice & input.

-Dave

---

### Post by dbott67 on 2007-12-27
Here are some benchmarks based on FreeNAS and an Ubuntu setup:
```

**Test Config     TeraStation NAS 1.0 TB         DIY RAID 5 NAS**
                                                  [COLOR=Red]Ubuntu 6.06 DT[/COLOR]     [COLOR=Blue]FreeNAS .671[/COLOR]
Avg Write
1000 Mbps         7,036                            [COLOR=Red]23,940[/COLOR]              [COLOR=Blue] 4,479[/COLOR]

Avg Read
1000 Mbps        11,900                            [COLOR=Red]27,566[/COLOR]               [COLOR=Blue]20,152[/COLOR]

Avg Write
100Mbps           4,897                             [COLOR=Red]5,059[/COLOR]               [COLOR=Blue]Not Tested[/COLOR]

Avg Read
100Mbps           8,299                             [COLOR=Red]9,136[/COLOR]               [COLOR=Blue]Not Tested[/COLOR]
```

Based on those numbers, the Netgear ReadyNAS NV+ is on par with the Ubuntu RAID 5 NAS, and outperforms the other 2 (is it me, or is the Terastation performance really low?).

---

### Post by mips on 2007-12-27
> **dbott67 said:**
> 
[COLOR=Red]**What command would I use to perform the loopback test?**[/COLOR]


You could FTP to 127.0.0.1 (will have to have a ftp server running or something along those lines) then transfer a file from your pc to your pc. Could probably also use a browser or file manager.

---

### Post by dbott67 on 2007-12-27
> **mips said:**
> You could FTP to 127.0.0.1 (will have to have a ftp server running or something along those lines) then transfer a file from your pc to your pc. Could probably also use a browser or file manager.

Thanks, mips! 

I've also picked up my laptop from work (w/ gigabit NIC) and have downloaded iPerf (as per [Netztier]("http://ubuntuforums.org/member.php?u=24875")'s suggestion) in [one of the other threads]("http://ubuntuforums.org/showthread.php?p=4023363#post4023363") on gigabit performance issues.

I'll give both a test and report back.

-Dave

---

### Post by dbott67 on 2007-12-27
Well it looks like everything is running as it should. Thanks to all who chimed in with advice & knowledge. Here are the results of iPerf between Ubuntu 7.10 and Windows XP Pro using a cross-over cable and through a D-Link DGL-4500 Router:
 
**_Cross-over Cable Connection:_ **
 
**1. Ubuntu (client) & Windows (server)**
 
```
dbott@gutsy:~$ iperf -t 30 -C -c 192.168.1.99
------------------------------------------------------------
Client connecting to 192.168.1.99, TCP port 5001
TCP window size: 16.0 KByte (default)
------------------------------------------------------------
[  3] local 192.168.1.100 port 37397 connected with 192.168.1.99 port 5001
[  3]  0.0-30.0 sec  2.04 GBytes    [COLOR=red]585 Mbits/sec[/COLOR]
``````
C:\Documents and Settings\Administrator\Desktop\iPerf>iperf -s
------------------------------------------------------------
Server listening on TCP port 5001
TCP window size: 8.00 KByte (default)
------------------------------------------------------------
[1792] local 192.168.1.99 port 5001 connected with 192.168.1.100 port 37397
[ ID] Interval       Transfer     Bandwidth
[1792]  0.0-32.1 sec  2.04 GBytes   [COLOR=red]546 Mbits/sec[/COLOR]
```**2. Windows (client) & Ubuntu (server)**
 
```
C:\Documents and Settings\Administrator\Desktop\iPerf>iperf -C -t 30 -c 192.168.1.100
------------------------------------------------------------
Client connecting to 192.168.1.100, TCP port 5001
TCP window size: 8.00 KByte (default)
------------------------------------------------------------
[1828] local 192.168.1.99 port 1392 connected with 192.168.1.100 port 5001
[ ID] Interval       Transfer     Bandwidth
[1828]  0.0-32.6 sec  1.63 GBytes   [COLOR=red]429 Mbits/sec[/COLOR]
``````
dbott@gutsy:~$ iperf -s
------------------------------------------------------------
Server listening on TCP port 5001
TCP window size: 85.3 KByte (default)
------------------------------------------------------------
[  4] local 192.168.1.100 port 5001 connected with 192.168.1.99 port 1392
[  4]  0.0-30.0 sec  1.63 GBytes    [COLOR=red]467 Mbits/sec[/COLOR]
```**_Connected via D-Link DGL-4500 Router_**
 
**3. Ubuntu (client) & Windows (server)**
 
```
dbott@gutsy:~$ iperf -t 30 -C -c 192.168.1.99
------------------------------------------------------------
Client connecting to 192.168.1.99, TCP port 5001
TCP window size: 16.0 KByte (default)
------------------------------------------------------------
[  3] local 192.168.1.100 port 53967 connected with 192.168.1.99 port 5001
[  3]  0.0-30.0 sec  2.08 GBytes    [COLOR=red]595 Mbits/sec[/COLOR]
``````
C:\Documents and Settings\Administrator\Desktop\iPerf>iperf -s
------------------------------------------------------------
Server listening on TCP port 5001
TCP window size: 8.00 KByte (default)
------------------------------------------------------------
[1792] local 192.168.1.99 port 5001 connected with 192.168.1.100 port 53967
[ ID] Interval       Transfer     Bandwidth
[1792]  0.0-32.2 sec  2.08 GBytes   [COLOR=red]555 Mbits/sec[/COLOR]
```**4. Windows (client) & Ubuntu (server)**
 
```
C:\Documents and Settings\Administrator\Desktop\iPerf>iperf -C -t 30 -c 192.168.1.100
------------------------------------------------------------
Client connecting to 192.168.1.100, TCP port 5001
TCP window size: 8.00 KByte (default)
------------------------------------------------------------
[1832] local 192.168.1.99 port 1393 connected with 192.168.1.100 port 5001
[ ID] Interval       Transfer     Bandwidth
[1832]  0.0-31.9 sec  1.55 GBytes   [COLOR=red]416 Mbits/sec[/COLOR]
``````
dbott@gutsy:~$ iperf -s
------------------------------------------------------------
Server listening on TCP port 5001
TCP window size: 85.3 KByte (default)
------------------------------------------------------------
[  5] local 192.168.1.100 port 5001 connected with 192.168.1.99 port 1393
[  5]  0.0-30.0 sec  1.55 GBytes    [COLOR=red]443 Mbits/sec[/COLOR]
```_**UPDATE**_

As per mips advice, I also performed an FTP transfer from the NAS to the local hard drive and achieved much better performance.  As noted by [psusi]("http://ubuntuforums.org/member.php?u=41311") and [Netztier]("http://ubuntuforums.org/member.php?u=24875"), Samba performance is generally quite poor.  Here is a quick test using gFTP to download a file from the NAS:

```
150 Opening BINARY mode data connection for /Archive/WinXP_SP2/WindowsXP-KB835935-SP2-ENU.exe (278927592 bytes)
226 Transfer complete.
Successfully transferred /Archive/WinXP_SP2/WindowsXP-KB835935-SP2-ENU.exe at [COLOR=Red]27416.23 KB/s[/COLOR]
Successfully changed mode of /home/dbott/Test/WindowsXP-KB835935-SP2-ENU.exe to 744
```Bandwidth Monitor also recorded peak throughput in the 33-34,000 KBps range:
```
Bandwidth Monitor 1.1.0

       Iface        RX(KB/sec)   TX(KB/sec)   Total(KB/sec)

          lo            0.000        0.000           0.000
        eth1        33642.678      796.601       34439.2790

       Total        33642.678      796.601       34439.2790

Hit CTRL-C to end this madness.
```I am a much happier camper now! :)

-Dave

---

### Post by psusi on 2007-12-28
Man, that is still rather slow... barely twice as fast as 100 Base-T.

---

### Post by dbott67 on 2007-12-28
> **psusi said:**
> Man, that is still rather slow... barely twice as fast as 100 Base-T.

What is slow?  The FTP speeds or the iPerf results?  Both?

The FTP disk reads are clocking in at almost 220 Mbps (sustained) and bursting up to 270 Mbps at times for a 275 MB file.  These results are not "performance tweaked" --- just crude tests (i.e. there are multiple machines running while I'm conducting the tests).  If you have any tips on how to increase performance, please let me know.  FTP is double that of Samba for me.

From what I've read in all of the [performance reviews]("http://www.smallnetbuilder.com/content/view/29829/75/1/3/"), that is very close to what the benchmarks were for a 256 MB file (see attached image) for ***all NAS devices***.  The Thecus N5200 is the only NAS that outperforms the NV+, and that's only on smaller file sizes.  On files > 512 MB, the NV+ outperforms all NAS devices.

So, if I'm interpreting the benchmark results properly, I shouldn't expect performance to be much greater that this, as the READ/WRITE throughput of the NAS is going to be my bottleneck (as is the READ/WRITE performance of my desktop PC).



-Dave

---

### Post by psusi on 2007-12-28
Even the iperf with the crossover was still only half of what it should be.  And your average disk drive these days can sustain a good 50+ MB/s, so 25 seems rather slow.

---

### Post by dbott67 on 2007-12-29
> **psusi said:**
> Even the iperf with the crossover was still only half of what it should be.  

Do you know of any sites that provide typical performance numbers that I should expect?  Keep in mind that the desktop PC is a P4-1.8 GHz (c.2002) with 896 MB RAM, 160 GB IDE hard drive & D-Link DGE-530T Gigabit controller.

The other machine is a Dell Latitude D830 laptop w/ T7500 Core2Duo @ 2.20 GHz, 2 GB RAM, 80 GB hard drive & Broadcom NetXtreme 57xx Gigabit NIC.

As noted above, the directly connected cross-over test results were the same as the results when connected to the switch, so I'm sure that it must be limitations of the hardware (PCI bus? CPU?) on the desktop PC.

I've checked out the iPerf documentation site, as well as a number of 'tweaking' sites, but none of the changes I made resulted in a significant performance gain.

[http://dast.nlanr.net/Projects/Iperf/iperfdocs_1.7.0.html#tuningtcp](http://dast.nlanr.net/Projects/Iperf/iperfdocs_1.7.0.html#tuningtcp)
[http://www.psc.edu/networking/projects/tcptune/#WindowsXP](http://www.psc.edu/networking/projects/tcptune/#WindowsXP)

The best result I've obtained over a sustained period (10 minutes) is just over 600 Mbps:
```
dbott@gutsy:~$ iperf -C -t 600 -c 192.168.1.100
------------------------------------------------------------
Client connecting to 192.168.1.100, TCP port 5001
TCP window size: 16.0 KByte (default)
------------------------------------------------------------
[  3] local 192.168.1.195 port 46881 connected with 192.168.1.100 port 5001
[  3]  0.0-600.0 sec  42.2 GBytes    [COLOR=Red]604 Mbits/sec[/COLOR]
```
> **psusi said:**
> And your average disk drive these days can sustain a good 50+ MB/s, so 25 seems rather slow.

It does seem slow (compared to typical hard drive throughput), but I've yet to see any read/write performance benchmarks for higher-end *consumer-level* NAS devices that performs outside of the 25-35 MB/s range.

Are you aware of any sites that reveal NAS benchmarks that show better performance for these types of consumer/pro-sumer devices?

As it stands, my thoughts on gigabit performance for *typical home systems* are:

1. Raw gigabit performance is varied depending on a number of factors, but one can expect raw throughput in the 400-600 Mbps range without substantial tweaking (i.e performance measured using iPerf).

2. Read/write performance is also impacted by a number of factors:
- RAID level (if any)
- Hard drive performance (HD cache, RPM, SCSI vs. IDE, vs. SATA)
- Protocol used (SMB, FTP, NFS, etc.)

3. Network configuration
- Number of devices
- Switch configuration (Jumbo frames, QoS, etc.)
- Cabling

Anyhow, I would greatly appreciate any sites that show performance levels above what I'm seeing.  I've done quite a bit of searching and have yet to find a site that shows performance levels (for consumer-grade, home-based systems) above what I'm experiencing here at home.

I'm going to try an NFS transfer to see how it compares to SMB & FTP and then I'll report back.

Thanks,
Dave

---

### Post by dbott67 on 2007-12-30
More gigabit performance benchmarks for reference purposes.

Using the same hardware as noted above (**Desktop PC P4 1.8 Ghz**, 896 MB RAM, 160 GB IDE HD running Ubuntu 7.10 and **Dell Latitude D830 Core 2 Duo T7500** @ 2.20 GHz, 2 GB RAM, 80 GB HD running XP Pro).  This time, rather than testing performance to the NAS, I am testing between XP Pro machine and Ubuntu using SMB and FTP protocols.

No special tweaking, just basic 'out-of-the-box' setup.  For this test, I'll be copying a bunch of video files and a large binary file for a total of 609 MB.

```
dbott@gutsy:~/Test/Test$ ls -all
total 624816
drwxr-xr-x 2 dbott dbott      4096 2007-12-30 13:23 .
drwxr-xr-x 3 dbott dbott      4096 2007-12-30 13:23 ..
-rwxr-xr-x 1 dbott dbott  27704532 2007-12-30 13:23 Sarah2002M (10th copy).mov
-rwxr-xr-x 1 dbott dbott  27704532 2007-12-30 13:23 Sarah2002M (11th copy).mov
-rwxr-xr-x 1 dbott dbott  27704532 2007-12-30 13:23 Sarah2002M (3rd copy).mov
-rwxr-xr-x 1 dbott dbott  27704532 2007-12-30 13:23 Sarah2002M (4th copy).mov
-rwxr-xr-x 1 dbott dbott  27704532 2007-12-30 13:23 Sarah2002M (5th copy).mov
-rwxr-xr-x 1 dbott dbott  27704532 2007-12-30 13:23 Sarah2002M (6th copy).mov
-rwxr-xr-x 1 dbott dbott  27704532 2007-12-30 13:23 Sarah2002M (7th copy).mov
-rwxr-xr-x 1 dbott dbott  27704532 2007-12-30 13:23 Sarah2002M (8th copy).mov
-rwxr-xr-x 1 dbott dbott  27704532 2007-12-30 13:23 Sarah2002M (9th copy).mov
-rwxr-xr-x 1 dbott dbott  27704532 2007-12-30 13:23 Sarah2002M (another copy).mov
-rwxr-xr-x 1 dbott dbott  27704532 2007-12-30 13:23 Sarah2002M (copy).mov
-rwxr-xr-x 1 dbott dbott  27704532 2007-12-30 13:23 Sarah2002M.mov
-rwxr-xr-x 1 dbott dbott  27704532 2007-12-30 13:23 Sarah.mov
-rwxr-xr-x 1 dbott dbott 278927592 2007-12-30 13:24 WindowsXP-KB835935-SP2-ENU.exe

```_**Test 1: Use SMBGET to transfer files from Dell Laptop (XP) to Ubuntu Desktop**_

```
dbott@gutsy:~/Test$ time smbget -u dbott -p xxxxxxxx smb://dell_d830/Archive/Test -R
Using workgroup MSHOME, user dbott
smb://dell_d830/Archive/Test/Test/Sarah2002M (10th copy).mov                    
smb://dell_d830/Archive/Test/Test/Sarah2002M (11th copy).mov                    
smb://dell_d830/Archive/Test/Test/Sarah2002M (3rd copy).mov                     
smb://dell_d830/Archive/Test/Test/Sarah2002M (4th copy).mov                     
smb://dell_d830/Archive/Test/Test/Sarah2002M (5th copy).mov                     
smb://dell_d830/Archive/Test/Test/Sarah2002M (6th copy).mov                     
smb://dell_d830/Archive/Test/Test/Sarah2002M (7th copy).mov                     
smb://dell_d830/Archive/Test/Test/Sarah2002M (8th copy).mov                     
smb://dell_d830/Archive/Test/Test/Sarah2002M (9th copy).mov                     
smb://dell_d830/Archive/Test/Test/Sarah2002M (another copy).mov                 
smb://dell_d830/Archive/Test/Test/Sarah2002M (copy).mov                         
smb://dell_d830/Archive/Test/Test/Sarah2002M.mov                                
smb://dell_d830/Archive/Test/Test/Sarah.mov                                         
smb://dell_d830/Archive/Test/Test/WindowsXP-KB835935-SP2-ENU.exe                

real    0m24.605s
user    0m2.232s
sys     0m11.669s
```[COLOR=Red][I]=24.751 MB/s (198 Mbps)

[/I][COLOR=Black]_**Test 2: Use 'cp' command to copy 609 MB from XP to Gutsy (equivalent of using Nautilus w/SMB to copy)**_

Time to copy: 30.317s
[COLOR=Red]*=20.108 MB/s (160.864 Mbps)*[/COLOR]

_**Test 3: Use 'cp' command to copy 609 MB from Gutsy to XP **_[/COLOR][/COLOR][COLOR=Red][COLOR=Black]_**(equivalent of using Nautilus w/SMB to copy)**_[/COLOR][/COLOR][COLOR=Red][COLOR=Black]

Time to copy: 38.701s
[COLOR=Red]*=15.736 MB/s (125.888 Mbps)*[/COLOR]
[/COLOR]
[/COLOR]_**Test 4: FTP 609 MB from Gutsy to XP using gFTP**_

Avg. transfer speed was 32,273.05 kB/s
[COLOR=Red][I]= 31.516 MB/s (252.133 Mbps)
[/I][COLOR=Black]
[COLOR=Purple]*Edit: Here are some results uploading & downloading the files from the command prompt.*[/COLOR]

**Uploading from Ubuntu to XP (best performance: 305.38 Mbps / 38.17 MB/s)**

```
Connected to 192.168.1.100.
220 Microsoft FTP Service
Name (192.168.1.100:dbott): dbott
331 Password required for dbott.
Password:
230 User dbott logged in.
Remote system type is Windows_NT.
ftp> binary
200 Type set to I.
ftp> prompt
Interactive mode off.
ftp> cd test
250 CWD command successful.
ftp> mput *.*
local: Sarah2002M (10th copy).mov remote: Sarah2002M (10th copy).mov
200 PORT command successful.
150 Opening BINARY mode data connection for Sarah2002M (10th copy).mov.
226 Transfer complete.
27704532 bytes sent in 0.60 secs (44991.3 kB/s)
local: Sarah2002M (11th copy).mov remote: Sarah2002M (11th copy).mov
200 PORT command successful.
150 Opening BINARY mode data connection for Sarah2002M (11th copy).mov.
226 Transfer complete.
27704532 bytes sent in 0.62 secs (43809.0 kB/s)
local: Sarah2002M (3rd copy).mov remote: Sarah2002M (3rd copy).mov
200 PORT command successful.
150 Opening BINARY mode data connection for Sarah2002M (3rd copy).mov.
226 Transfer complete.
27704532 bytes sent in 0.71 secs (38241.2 kB/s)
local: Sarah2002M (4th copy).mov remote: Sarah2002M (4th copy).mov
200 PORT command successful.
150 Opening BINARY mode data connection for Sarah2002M (4th copy).mov.
226 Transfer complete.
27704532 bytes sent in 0.66 secs (40894.0 kB/s)
local: Sarah2002M (5th copy).mov remote: Sarah2002M (5th copy).mov
200 PORT command successful.
150 Opening BINARY mode data connection for Sarah2002M (5th copy).mov.
226 Transfer complete.
27704532 bytes sent in 0.63 secs (43137.4 kB/s)
local: Sarah2002M (6th copy).mov remote: Sarah2002M (6th copy).mov
200 PORT command successful.
150 Opening BINARY mode data connection for Sarah2002M (6th copy).mov.
226 Transfer complete.
27704532 bytes sent in 0.62 secs (43533.2 kB/s)
local: Sarah2002M (7th copy).mov remote: Sarah2002M (7th copy).mov
200 PORT command successful.
150 Opening BINARY mode data connection for Sarah2002M (7th copy).mov.
226 Transfer complete.
27704532 bytes sent in 0.62 secs (43473.6 kB/s)
local: Sarah2002M (8th copy).mov remote: Sarah2002M (8th copy).mov
200 PORT command successful.
150 Opening BINARY mode data connection for Sarah2002M (8th copy).mov.
226 Transfer complete.
27704532 bytes sent in 1.56 secs (17299.3 kB/s)
local: Sarah2002M (9th copy).mov remote: Sarah2002M (9th copy).mov
200 PORT command successful.
150 Opening BINARY mode data connection for Sarah2002M (9th copy).mov.
226 Transfer complete.
27704532 bytes sent in 0.70 secs (38767.5 kB/s)
local: Sarah2002M (another copy).mov remote: Sarah2002M (another copy).mov
200 PORT command successful.
150 Opening BINARY mode data connection for Sarah2002M (another copy).mov.
226 Transfer complete.
27704532 bytes sent in 0.65 secs (41488.5 kB/s)
local: Sarah2002M (copy).mov remote: Sarah2002M (copy).mov
200 PORT command successful.
150 Opening BINARY mode data connection for Sarah2002M (copy).mov.
226 Transfer complete.
27704532 bytes sent in 0.79 secs (34348.8 kB/s)
local: Sarah2002M.mov remote: Sarah2002M.mov
200 PORT command successful.
150 Opening BINARY mode data connection for Sarah2002M.mov.
226 Transfer complete.
27704532 bytes sent in 0.66 secs (41287.9 kB/s)
local: WindowsXP-KB835935-SP2-ENU.exe remote: WindowsXP-KB835935-SP2-ENU.exe
200 PORT command successful.
150 Opening BINARY mode data connection for WindowsXP-KB835935-SP2-ENU.exe.
226 Transfer complete.
278927592 bytes sent in 7.38 secs (36890.4 kB/s)
```**Downloading from XP to Ubuntu**

```
ftp> mget *.*
local: Sarah2002M (10th copy).mov remote: Sarah2002M (10th copy).mov
200 PORT command successful.
150 Opening BINARY mode data connection for Sarah2002M (10th copy).mov(27704532 bytes).
226 Transfer complete.
27704532 bytes received in 0.72 secs (37440.0 kB/s)
local: Sarah2002M (11th copy).mov remote: Sarah2002M (11th copy).mov
200 PORT command successful.
150 Opening BINARY mode data connection for Sarah2002M (11th copy).mov(27704532 bytes).
226 Transfer complete.
27704532 bytes received in 0.76 secs (35668.4 kB/s)
local: Sarah2002M (3rd copy).mov remote: Sarah2002M (3rd copy).mov
200 PORT command successful.
150 Opening BINARY mode data connection for Sarah2002M (3rd copy).mov(27704532 bytes).
226 Transfer complete.
27704532 bytes received in 0.87 secs (30991.5 kB/s)
local: Sarah2002M (4th copy).mov remote: Sarah2002M (4th copy).mov
200 PORT command successful.
150 Opening BINARY mode data connection for Sarah2002M (4th copy).mov(27704532 bytes).
226 Transfer complete.
27704532 bytes received in 0.80 secs (34002.9 kB/s)
local: Sarah2002M (5th copy).mov remote: Sarah2002M (5th copy).mov
200 PORT command successful.
150 Opening BINARY mode data connection for Sarah2002M (5th copy).mov(27704532 bytes).
226 Transfer complete.
27704532 bytes received in 1.35 secs (20101.8 kB/s)
local: Sarah2002M (6th copy).mov remote: Sarah2002M (6th copy).mov
200 PORT command successful.
150 Opening BINARY mode data connection for Sarah2002M (6th copy).mov(27704532 bytes).
226 Transfer complete.
27704532 bytes received in 0.87 secs (31022.6 kB/s)
local: Sarah2002M (7th copy).mov remote: Sarah2002M (7th copy).mov
200 PORT command successful.
150 Opening BINARY mode data connection for Sarah2002M (7th copy).mov(27704532 bytes).
226 Transfer complete.
27704532 bytes received in 0.77 secs (35178.9 kB/s)
local: Sarah2002M (8th copy).mov remote: Sarah2002M (8th copy).mov
200 PORT command successful.
150 Opening BINARY mode data connection for Sarah2002M (8th copy).mov(27704532 bytes).
226 Transfer complete.
27704532 bytes received in 0.80 secs (33703.0 kB/s)
local: Sarah2002M (9th copy).mov remote: Sarah2002M (9th copy).mov
200 PORT command successful.
150 Opening BINARY mode data connection for Sarah2002M (9th copy).mov(27704532 bytes).
226 Transfer complete.
27704532 bytes received in 1.35 secs (19980.0 kB/s)
local: Sarah2002M (another copy).mov remote: Sarah2002M (another copy).mov
200 PORT command successful.
150 Opening BINARY mode data connection for Sarah2002M (another copy).mov(27704532 bytes).
226 Transfer complete.
27704532 bytes received in 0.78 secs (34500.6 kB/s)
local: Sarah2002M (copy).mov remote: Sarah2002M (copy).mov
200 PORT command successful.
150 Opening BINARY mode data connection for Sarah2002M (copy).mov(27704532 bytes).
226 Transfer complete.
27704532 bytes received in 0.82 secs (32955.3 kB/s)
local: Sarah2002M.mov remote: Sarah2002M.mov
200 PORT command successful.
150 Opening BINARY mode data connection for Sarah2002M.mov(27704532 bytes).
226 Transfer complete.
27704532 bytes received in 0.76 secs (35718.1 kB/s)
local: WindowsXP-KB835935-SP2-ENU.exe remote: WindowsXP-KB835935-SP2-ENU.exe
200 PORT command successful.
150 Opening BINARY mode data connection for WindowsXP-KB835935-SP2-ENU.exe(278927592 bytes).
226 Transfer complete.
278927592 bytes received in 9.46 secs (28784.9 kB/s)
ftp> 
```[/COLOR][COLOR=Black]_**Test 5: NFS test from Ubuntu to NAS using 1 GB of data**_

OneGigTest = 1022488 KB

```
sudo mount 192.168.1.2:/Archive /home/dbott/NFS

dbott@gutsy:~/NFS$ time cp OneGigTest/ /home/dbott/Desktop/ -R

real    1m13.409s
user    0m0.172s
sys     0m8.201s
```[COLOR=Red][I]
=13.602 MB/s (108.81 Mbps)

[/I][COLOR=Black]_**Summary**_

FTP outperforms both SMB and NFS.  In fact, FTP at the command line yielded almost 40 MB/s transfers.  NFS appears to be the slowest method, although there are a few tweaks that I didn't try, such as increasing window sizes (rsize=32768 & wsize=32768).

SMBGET offers better performance than just using Nautilus or 'cp' to copy files.

I'd be interested to see what results others are getting.

-Dave
[/COLOR][/COLOR] [/COLOR][/COLOR]

---

