---
title: "Gigabit Lan 33MB/s acceptable?"
date: 2007-12-17
forum: Networking &amp; Wireless
---

### Post by narsaw on 2007-12-17
I can transfer a 1GB file from my samba server (ubuntu 7.10) to my XP box in 30 seconds. Which works out to approximately 33MB/s (33 * 30 = 970MB, so it's approximate). 

Is this good? I would expect a transfer rate of about 100MB/s on gigabit lan if configured properly. Is this too much to ask?

---

### Post by Paulmd on 2007-12-17
Many IDE hard disks can only write in the 30MB/sec range (typically in the 20gb capacity range). The fastest consumer-grade sata drives can write in the 80MB/sec range. You are likely running into disk speed limits.

If I know the make/model of your hard disks on both ends I can tell you for sure.

---

### Post by narsaw on 2007-12-17
Thanks for the fast reply..

some hdparm info:

sudo hdparm -Tt /dev/hdb1

/dev/hdb1:
 Timing cached reads:   578 MB in  2.01 seconds          = 288.05 MB/sec
 Timing buffered disk reads:  174 MB in  3.02 seconds =  57.53 MB/sec

Info on drive:
ATA device, with non-removable media
        Model Number:       Maxtor 6Y250P0
        Serial Number:      Y63J91JE
        Firmware Revision:  YAR41BW0

It's a Maxror 250GB drive, fairly new. Same drive on both ends.

---

### Post by netztier on 2007-12-17
> **narsaw said:**
> I can transfer a 1GB file from my samba server (ubuntu 7.10) to my XP box in 30 seconds. Which works out to approximately 33MB/s (33 * 30 = 970MB, so it's approximate). 

Is this good? I would expect a transfer rate of about 100MB/s on gigabit lan if configured properly. Is this too much to ask?

For samba, this is acceptable. Try taking a file that is not too large so that fits into the server's disk cache completely, and then transfer it multiple times sequentially. Like this, you can transfer it from cache instead of disk - can give you a noticeable boost in throughput.

If your Samba client is running Gnome, check the "Resources" tab in Gnome's System Monitor - it can give you a good estimate of network-I/O in a graph (lower the polling frequency to 1 or 2 seconds to make the Graph more responsive).

If you really want to see what your network is capable of, use **iPerf** from the universe repositories to measure raw throughput. If you play around with the -P <no of threads> parameter, you can get close to the 100Mbytes/s barrier.

Actually getting 100MBytes/s from an application is definitely non-trivial and most often requires disk arrays (mirrored or striped) and a decently configured PCI bus and chipset arrangement by the maker of your motherboard. Where I work, it took us a while of optimizing a well-equipped Sun V480's TCP stack until it could keep it's Gigabit pipe full at a constant rate of >115MBytes/s (with Veritas NetBackup). Not something you'd expect from your common PC hardware.

And finally, you could experiment with Jumbo Frames (check that your gigabit switch supports it), that will boost throughput even more. Be careful though - running systems mixed with MTU 1500 and MTU 9000 on the same subnet can be tricky if not impossible. 

As long as all applications in use are running over TCP, it will work, since the 3-way TCP handshake also includes information about the Maximum Segment Size (MSS); so the MTU 1500 systems can inform the MTU 9000 systems not to send large packets. But UDP does not have this feature - and (standard) NFS-over-UDP will in this case fail between mixed MTU systems. That's why running mixed MTU on the same broadcast domain is generally discouraged.


regards

Marc

---

### Post by mellowd on 2007-12-17
Also remember that 100% of a packet isn't data. You have all kinds of overhead in each packet, as well as regular network traffic.

Jumbo frames would be a good idea if possible.

---

### Post by Lostincyberspace on 2007-12-17
You also might not have hardware that responds well enough a 100mbps card is can only really go to a bout 90mbps or so and is slowed down on both sides if they are both the same rating.

---

### Post by mellowd on 2007-12-17
Also, I'm assuming you've checked that it's running in full duplex?

---

### Post by narsaw on 2007-12-17
> **mellowd said:**
> Also, I'm assuming you've checked that it's running in full duplex?

I did. Here is some info:

```
ethtool eth0
Settings for eth0:
        Supported ports: [ TP ]
        Supported link modes:   10baseT/Half 10baseT/Full
                                100baseT/Half 100baseT/Full
                                1000baseT/Full
        Supports auto-negotiation: Yes
        Advertised link modes:  10baseT/Half 10baseT/Full
                                100baseT/Half 100baseT/Full
                                1000baseT/Full
        Advertised auto-negotiation: Yes
        Speed: 1000Mb/s
        Duplex: Full
        Port: Twisted Pair
        PHYAD: 0
        Transceiver: internal
        Auto-negotiation: on
        Supports Wake-on: pumbg
        Wake-on: g
        Current message level: 0x00000033 (51)
        Link detected: yes

```

Mellowd:
I realize that 100% of packet is not data, that’s why I said I would expect 100 MB/s. The theoretical speed for gigabit Ethernet is around 125MB/s.

33MB/s isn’t terrible. I would like to see closer to the 50-70MB/s range. JUMBO frames I have not explored yet. I’ll need to check my hardware to  see if this is possible.

It would be useful if readers of this thread with gigabit Ethernet Lan comment on the MB/s transfer rate when using Samba.

---

### Post by Lostincyberspace on 2007-12-17
I get about 30-40 megabitpersecond from my samba. Are you getting 33MBytes or 33Mbits. There is a big difference, I thought you had the later transfer rate initially but now I am confused a little.

---

### Post by psusi on 2007-12-17
Is it typical?  I believe so.  Is it acceptable?  Not to me.  I have not yet had the chance to play with gigabit setups, but years ago I wrote an ftp server and I did not rest until it was transferring 11,820 KB/s over 100 Mbps ethernet.

---

### Post by narsaw on 2007-12-17
> **Lostincyberspace said:**
> I get about 30-40 megabitpersecond from my samba. Are you getting 33MBytes or 33Mbits. There is a big difference, I thought you had the later transfer rate initially but now I am confused a little.

If you are getting 30-40 Mb/s (note small "b", for Mega bits"), then you are NOT getting fast transfers at all.

I am getting 33MB/s (Megabytes, big "B") per second. I would like to see 50-70MB+/s with my current hardware.

The card I am using is the following has the following chipset info:

Brand:
```

ENCORE ENLGA-1320 10/ 100/ 1000Mbps PCI Ethernet Card 1 x RJ45
http://www.newegg.com/Product/Product.asp?Item=N82E16833180026

```

Chipset: I've read that people are having issues with Realtek chipsets with Ubuntu
```

01:08.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8169 Gigabit Ethernet (rev 10)

```

I am thinking about buying this card. 

```

Intel PWLA8391GT 10/ 100/ 1000Mbps PCI PRO/1000 GT Desktop Adapter 1 x RJ45
http://www.newegg.com/Product/Product.aspx?Item=N82E16833106121

```

That Intel card uses the e1000 kernel module. I read people getting "nearly" theoretical gigabit speeds with this card. Any experiences with this Intel card?

---

### Post by netztier on 2007-12-17
> **narsaw said:**
> It would be useful if readers of this thread with gigabit Ethernet Lan comment on the MB/s transfer rate when using Samba.

My prehistoric P-III 500MHz server (512MB RAM) with it's RAID-1 of two 120Gig Disks (classical ATA disks) can get around 25MBytes/s (buffered) and 136MBytes/s (cached) from it's /dev/md0 with hdparm.

With Samba, it does 13-15 MBytes/s on first reads, and can peak out just a tad over 20MBytes/s when serving from cache. Writes tend to be around 15-16MBytes/sec.

NFS(over-TCP) is considerably faster and does 20-22MBytes/s on first reads and dashes over 40MBytes/s when serving from cache. I'd rather not talk about the NFS writes... I have no clue whatsoever why these peak out at > 20Mbytes at first, then collapse to zero for a few seconds and crawl the rest of the job at less than 8MBytes/s, or peaks out over 20MBytes/s again for a few seconds and collapes back to zero for another 8-10 seconds. It's not TCP-vs-UDP related; NFS-over-UDP just has more peaks, but collapses after a peak just like NFS-over-TCP.

With Jumbo frames enabled,  NFS gets a considerable boost: serving from cache comes in at 50-60MBytes/s - and writes still aren't any faster. I can't remember the jumbo frame figures for samba, but I think I remember that the increase wasn't as dramatic as with NFS.


regards 

Marc

---

### Post by tgalati4 on 2007-12-17
A typical PCI bus will only handle ~33 MB/sec, so it sounds like you are hitting an internal limit between the disk, memory, and CPU.  With handshaking between both machines, the transfer will only go as fast as the slowest link in the chain.  Also realize that most Southbridge or Northbridge chipsets use the same physical chip to handle ethernet request and disk I/O.  So you could be experiencing a chipset bottleneck caused by a shared interrupt between disk I/O and the ethernet "card".

Do a little digging on your motherboard chipset and you may find an answer.

---

### Post by narsaw on 2007-12-17
> **tgalati4 said:**
> A typical PCI bus will only handle ~33 MB/sec, so it sounds like you are hitting an internal limit between the disk, memory, and CPU.  With handshaking between both machines, the transfer will only go as fast as the slowest link in the chain.  Also realize that most Southbridge or Northbridge chipsets use the same physical chip to handle ethernet request and disk I/O.  So you could be experiencing a chipset bottleneck caused by a shared interrupt between disk I/O and the ethernet "card".

Do a little digging on your motherboard chipset and you may find an answer.

I belive you are wrong here on your transfer speed comment. 

At 33MHz, with a 32-bit data bus, the theoretical maximum data transfer rate of the PCI bus is 132MB/sec. At 66MHz, with a 64-bit data path, the top speed would be 528MB/sec. 

You comments about the north/south bridge maybe be correct but thats beyond my pay grade.

---

### Post by mellowd on 2007-12-17
> **narsaw said:**
> 
Mellowd:
I realize that 100% of packet is not data, that’s why I said I would expect 100 MB/s. The theoretical speed for gigabit Ethernet is around 125MB/s.

33MB/s isn’t terrible. I would like to see closer to the 50-70MB/s range. JUMBO frames I have not explored yet. I’ll need to check my hardware to  see if this is possible.

It would be useful if readers of this thread with gigabit Ethernet Lan comment on the MB/s transfer rate when using Samba.

Remember megabit and megabyte are difference. 100Mb network will be able to sustain a maximum of 12.5 Megabytes per second with no overhead.

---

### Post by narsaw on 2007-12-17
> **mellowd said:**
> Remember megabit and megabyte are difference. 100Mb network will be able to sustain a maximum of 12.5 Megabytes per second with no overhead.

The issue of megaBITS and megaBYTES have been addressed already. I am always referring to megaBYTES, I use the nomenclature, "MB" for megaBYTES and "mb" for megaBITS. So when I say I am getting 33MB/s, I mean 33 megaBYTES / second.

---

### Post by Lostincyberspace on 2007-12-17
@mellowd:I think you have your conversion backwards.

---

### Post by mellowd on 2007-12-17
> **Lostincyberspace said:**
> @mellowd:I think you have your conversion backwards.

No, 8 bits = 1 byte

---

### Post by mellowd on 2007-12-17
> **narsaw said:**
> The issue of megaBITS and megaBYTES have been addressed already. I am always referring to megaBYTES, I use the nomenclature, "MB" for megaBYTES and "mb" for megaBITS. So when I say I am getting 33MB/s, I mean 33 megaBYTES / second.

alright, relax. just trying to help out here

---

### Post by tgalati4 on 2007-12-17
You are correct.  It is the typical IDE bus that is 33 MB/sec.  Are you running your SATA dries in IDE mode?  If so, then you will only get IDE transfer speeds.

---

### Post by narsaw on 2007-12-17
> **tgalati4 said:**
> You are correct.  It is the typical IDE bus that is 33 MB/sec.  Are you running your SATA dries in IDE mode?  If so, then you will only get IDE transfer speeds.

Not true:

At 33MHz, with a 32-bit data bus, the theoretical maximum data transfer rate of the PCI bus is 132MB/sec. At 66MHz, with a 64-bit data path, the top speed would be 528MB/sec.

    * 33.33 MHz clock with synchronous transfers
    * Peak transfer rate of 133 MB per second for 32-bit bus width (33.33 MHz × 32 bits ÷ 8 bits/byte = 133 MB/s)
    * 32-bit bus width
    * 32-bit address space (4 gigabytes)
    * 32-bit port space (now deprecated)
    * 256-byte configuration space
    * 3.3- or 5-volt signaling
    * Reflected-wave switching

---

### Post by jinx099 on 2007-12-17
I'm getting comparable transfers with my gigabit network.  I experienced little difference using jumbo frames.  I'll be looking into this problem more now that I see this thread.

I'm using 2x 320GB Seagate Perp. Recording drives in RAID-1 so I should be getting decent reads over NFS I would think.

---

### Post by Lostincyberspace on 2007-12-17
It is probably samba's limitation.

---

### Post by williammanda on 2007-12-17
Can anyone point me to instructions for setting NFS over TCP? Right now I setup with NFS over UDP. I used this link to originally set it up:
[http://ubuntuforums.org/showthread.php?t=249889](http://ubuntuforums.org/showthread.php?t=249889)
Thanks

---

### Post by narsaw on 2007-12-17
> **Lostincyberspace said:**
> It is probably samba's limitation.

Don't think so. I seen reports where users are getting 50-70MB/s using Samba on a Gigabit Ethernet setup.

---

### Post by netztier on 2007-12-18
> **williammanda said:**
> Can anyone point me to instructions for setting NFS over TCP? Right now I setup with NFS over UDP. I used this link to originally set it up:
[http://ubuntuforums.org/showthread.php?t=249889](http://ubuntuforums.org/showthread.php?t=249889)
Thanks

What you find in there is perfectly right. All you need to add is "proto=tcp" to the mount options on the *client*. Provided TCP support is there, the server will adapt accordingly. All NFS servers I've come across on Ubuntu support it.

Sample line from fstab:

```
server:/path/to/share /path/to/mountpoint rw,[COLOR="Red"]proto=tcp[/COLOR],rsize=...
```

If I remember correctly,  NFS-over-TCP always uses 32768 for rsize and wsize by default, so setting them might be unnecessary.

regards

Marc

---

### Post by psusi on 2007-12-18
> **mellowd said:**
> Remember megabit and megabyte are difference. 100Mb network will be able to sustain a maximum of 12.5 Megabytes per second with no overhead.

It is actually 11.92 Megabytes per second.  100,000,000 / 8 / 1024 / 1024.

---

### Post by tgalati4 on 2007-12-18
Regardless of theoretical calculations, I read that sustained IDE transfer (normal 33 MHz mode) is ~ 33 MB/sec.  My own testing with older hardware (PIII, 500 MHz) seems to agree.

Burst speeds are much faster, but not helpful for large file transfers.  I tried fiddling with hdparm settings but could not break the 33 MB/s barrier.

---

### Post by Paulmd on 2007-12-18
> **narsaw said:**
> Thanks for the fast reply..

some hdparm info:

sudo hdparm -Tt /dev/hdb1

/dev/hdb1:
 Timing cached reads:   578 MB in  2.01 seconds          = 288.05 MB/sec
 Timing buffered disk reads:  174 MB in  3.02 seconds =  57.53 MB/sec

Info on drive:
ATA device, with non-removable media
        Model Number:       Maxtor 6Y250P0
        Serial Number:      Y63J91JE
        Firmware Revision:  YAR41BW0

It's a Maxror 250GB drive, fairly new. Same drive on both ends.

PG 43 lists the max sustained transfer rate.

In your case, it's 37MB/s.

[http://www.seagate.com/staticfiles/maxtor/en_us/documentation/data_sheets/diamondmax_plus_9_data_sheet.pdf](http://www.seagate.com/staticfiles/maxtor/en_us/documentation/data_sheets/diamondmax_plus_9_data_sheet.pdf)

One way to test this independently is to make a copy of your 1GB file, on your local machines, and time how long it takes.

PS: that same model is available in both PATA and SATA, which interface do you have?

---

### Post by narsaw on 2007-12-18
> **Paulmd said:**
> PG 43 lists the max sustained transfer rate.

In your case, it's 37MB/s.

[http://www.seagate.com/staticfiles/maxtor/en_us/documentation/data_sheets/diamondmax_plus_9_data_sheet.pdf](http://www.seagate.com/staticfiles/maxtor/en_us/documentation/data_sheets/diamondmax_plus_9_data_sheet.pdf)

One way to test this independently is to make a copy of your 1GB file, on your local machines, and time how long it takes.

PS: that same model is available in both PATA and SATA, which interface do you have?

I clicked on that PDF link and saw no information about **Sustained Trasnfer Rate**. The PDF was two pages long. Was there  another link?

I have the IDE interface. I also have a SATA II drive on this server. I will test my transfer rate with that one and post.

Testing:

Copy 1GB file from Drive A to Drive B:
```
time cp 1GB.FILE /media/netdisk500/1GB.FILE.2
0.032u 11.308s 0:17.56 64.5%    0+0k 0+0io 0pf+0w
```
As you can see it took about 17.5 seconds to copy that file. This works out to about 56.9MB/s. As hdparm previously predicted.

Copy 1GB file from Drive A to Drive A:
```

time cp 1GB.FILE 1GB.FILE.2
0.076u 10.152s 0:39.49 25.8%    0+0k 0+0io 0pf+0w

```
This took about 40 seconds. This works out to about 25.3MB/s. I would expect this to be slower since we are reading and writing to the same drive.

---

### Post by jinx099 on 2007-12-18
> **narsaw said:**
> I clicked on that PDF link and saw no information about **Sustained Trasnfer Rate**. The PDF was two pages long. Was there  another link?

I have the IDE interface. I also have a SATA II drive on this server. I will test my transfer rate with that one and post.

Testing:

Copy 1GB file from Drive A to Drive B:
```
time cp 1GB.FILE /media/netdisk500/1GB.FILE.2
0.032u 11.308s 0:17.56 64.5%    0+0k 0+0io 0pf+0w
```
As you can see it took about 17.5 seconds to copy that file. This works out to about 56.9MB/s. As hdparm previously predicted.

Copy 1GB file from Drive A to Drive A:
```

time cp 1GB.FILE 1GB.FILE.2
0.076u 10.152s 0:39.49 25.8%    0+0k 0+0io 0pf+0w

```
This took about 40 seconds. This works out to about 25.3MB/s. I would expect this to be slower since we are reading and writing to the same drive.

That's good data, I'll do that on my server too later for comparison.  My server has an 80 GB single drive, 2x 80GB drives in RAID-0, and 2x 320GB drives in RAID-1 so it'll be a good mix of configs.  What happens when you copy the file over NFS?

---

### Post by narsaw on 2007-12-18
> **jinx099 said:**
> That's good data, I'll do that on my server too later for comparison.  My server has an 80 GB single drive, 2x 80GB drives in RAID-0, and 2x 320GB drives in RAID-1 so it'll be a good mix of configs.  What happens when you copy the file over NFS?

I don't have NFS setup on my server. So I can't perform this test for you.
When you benchmark you server, please post results for us to see. If you can do a disk to disk test and a Samba test that would be great.

---

### Post by Paulmd on 2007-12-18
> **narsaw said:**
> I clicked on that PDF link and saw no information about **Sustained Trasnfer Rate**. The PDF was two pages long. Was there  another link?

I have the IDE interface. I also have a SATA II drive on this server. I will test my transfer rate with that one and post.

Testing:

Copy 1GB file from Drive A to Drive B:
```
time cp 1GB.FILE /media/netdisk500/1GB.FILE.2
0.032u 11.308s 0:17.56 64.5%    0+0k 0+0io 0pf+0w
```
As you can see it took about 17.5 seconds to copy that file. This works out to about 56.9MB/s. As hdparm previously predicted.

Copy 1GB file from Drive A to Drive A:
```

time cp 1GB.FILE 1GB.FILE.2
0.076u 10.152s 0:39.49 25.8%    0+0k 0+0io 0pf+0w

```
This took about 40 seconds. This works out to about 25.3MB/s. I would expect this to be slower since we are reading and writing to the same drive.


Yes, sorry about that, I gave you the wring link:
[http://www.seagate.com/staticfiles/maxtor/en_us/documentation/manuals/diamondmax_plus_9_manual.pdf](http://www.seagate.com/staticfiles/maxtor/en_us/documentation/manuals/diamondmax_plus_9_manual.pdf)

---

### Post by narsaw on 2007-12-18
> **Paulmd said:**
> Yes, sorry about that, I gave you the wring link:
[http://www.seagate.com/staticfiles/maxtor/en_us/documentation/manuals/diamondmax_plus_9_manual.pdf](http://www.seagate.com/staticfiles/maxtor/en_us/documentation/manuals/diamondmax_plus_9_manual.pdf)

Don't believe this applies to my particular drive. These specification are for drives up to 200GB. It is true that smaller capacity drives generally have lower throughput. For example a 20GB drive will generally have lower read/writes speeds. I say generally becaues there are always exceptions.

Great info in that PDF. Thanks

---

### Post by jinx099 on 2007-12-19
Single 80GB to RAID-0 80GBs  ~36MB/s
```
time cp 1GB.FILE /bt/

real    0m28.011s
user    0m0.066s
sys     0m5.875s
```

From RAID-0 to RAID-1  ~40MB/s
```
time cp 1GB.FILE /pbd/

real    0m25.592s
user    0m0.044s
sys     0m4.415s
```

From RAID-1 to RAID-0  ~36MB/s
```
time cp 1GB.FILE /bt/1GB.FILE-2

real    0m28.412s
user    0m0.045s
sys     0m6.536s

```

From RAID-1 to desktop over NFS  ~20MB/s
```
time cp 1GB.FILE ~

real    0m51.038s
user    0m0.030s
sys     0m3.652s
```

From RAID-0 to desktop over NFS  ~23MB/s
```

time cp 1GB.FILE-2 ~

real    0m45.088s
user    0m0.026s
sys     0m3.387s
```

Hmmm, this sucks.  This is slower than last time I calculated my speeds.  Looking into more...

---

### Post by narsaw on 2007-12-19
> **jinx099 said:**
> Single 80GB to RAID-0 80GBs  ~36MB/s
```
time cp 1GB.FILE /bt/

real    0m28.011s
user    0m0.066s
sys     0m5.875s
```

From RAID-0 to RAID-1  ~40MB/s
```
time cp 1GB.FILE /pbd/

real    0m25.592s
user    0m0.044s
sys     0m4.415s
```

From RAID-1 to RAID-0  ~36MB/s
```
time cp 1GB.FILE /bt/1GB.FILE-2

real    0m28.412s
user    0m0.045s
sys     0m6.536s

```

From RAID-1 to desktop over NFS  ~20MB/s
```
time cp 1GB.FILE ~

real    0m51.038s
user    0m0.030s
sys     0m3.652s
```

From RAID-0 to desktop over NFS  ~23MB/s
```

time cp 1GB.FILE-2 ~

real    0m45.088s
user    0m0.026s
sys     0m3.387s
```

Hmmm, this sucks.  This is slower than last time I calculated my speeds.  Looking into more...

Your speeds does seem a bit slow. What does hdparm -tT report for your speeds. I would expect you to get much better performance from your setup.

---

### Post by Paulmd on 2007-12-19
> **narsaw said:**
> Your speeds does seem a bit slow. What does hdparm -tT report for your speeds. I would expect you to get much better performance from your setup.

To add to that: is it hardware or software raid? And how is it configured?

For example: an IDE raid system using master/slave on the same channel may be bottlenecked by the controller.

With software raid, there is some overhead.

Another consideration you may not be aware of is the physical addresses of the data sometimes matter. Typically the lower numbered addresses are faster than the higher numbered addresses. By exactly how much is variable, but I've seen it as high as 10MB/s difference.

A file that is heavily fragmented may be slower because of seek times. 

Other processes your system may be running may affect transfer rates.

---

### Post by jinx099 on 2007-12-19
My RAID-1 LD, Linux software RAID, SATA drives are attached to the motherboard
```
[root@localhost ~]# hdparm -Tt /dev/md0

/dev/md0:
 Timing cached reads:   1652 MB in  2.00 seconds = 827.18 MB/sec
 Timing buffered disk reads:  224 MB in  3.02 seconds =  74.14 MB/sec

```

My RAID-0 LD, using a PCI Promise RAID card that Fedora maps to
```

[root@localhost ~]# hdparm -Tt /dev/mapper/pdc_eahafaifgip1

/dev/mapper/pdc_eahafaifgip1:
 Timing cached reads:   1642 MB in  2.00 seconds = 822.19 MB/sec
 Timing buffered disk reads:  314 MB in  3.00 seconds = 104.64 MB/sec

```

Single 80GB SATA drive on motherboard
```
[root@localhost ~]# hdparm -Tt /dev/sda

/dev/sda:
 Timing cached reads:   1654 MB in  2.00 seconds = 828.23 MB/sec
 Timing buffered disk reads:  170 MB in  3.01 seconds =  56.46 MB/sec

```

These results seem about right.  I should also note that my gigabit card is a standard PCI card which shares the PCI bus with the Promise card.

---

### Post by psusi on 2007-12-19
> **jinx099 said:**
> These results seem about right.  I should also note that my gigabit card is a standard PCI card which shares the PCI bus with the Promise card.

Ahhh, there's your problem... conventional pci bus is limited to around 100 MB/s so that cuts you down to at most 50 reading from the disk, and 50 to the nic.

---

### Post by jinx099 on 2007-12-19
> **psusi said:**
> Ahhh, there's your problem... conventional pci bus is limited to around 100 MB/s so that cuts you down to at most 50 reading from the disk, and 50 to the nic.

Yeah I'm aware of that, but what about transferring between drives, and what about transferring from my RAID-1 LD over the network?

---

### Post by Paulmd on 2007-12-19
> **psusi said:**
> Ahhh, there's your problem... conventional pci bus is limited to around 100 MB/s so that cuts you down to at most 50 reading from the disk, and 50 to the nic.

Close....

Conventional PCI is 133MB/sec.

[http://www.dell.com/content/topics/global.aspx/vectors/en/2004_pciexpress?c=us&l=en&s=corp](http://www.dell.com/content/topics/global.aspx/vectors/en/2004_pciexpress?c=us&l=en&s=corp)

---

### Post by Paulmd on 2007-12-19
> **jinx099 said:**
> Yeah I'm aware of that, but what about transferring between drives, and what about transferring from my RAID-1 LD over the network?

Between drives that are connected to the motherboard, the PCI bus need not be involved. 

Between drives that are attached to your Raid card, the pci bus will not be involved. 

Transferring from the drives on the raid card, to ones on the motherboard will involve the PCI bus.  Do will transferring over the network. 

Transferring from the promise card, over the network, will likely max out the PCI bus.

The following article has good diagrams, so you can see how everything interconnects.

[http://www.dell.com/content/topics/global.aspx/vectors/en/2004_pciexpress?c=us&l=en&s=corp](http://www.dell.com/content/topics/global.aspx/vectors/en/2004_pciexpress?c=us&l=en&s=corp)

---

### Post by Paulmd on 2007-12-19
> **narsaw said:**
> Don't believe this applies to my particular drive. These specification are for drives up to 200GB. It is true that smaller capacity drives generally have lower throughput. For example a 20GB drive will generally have lower read/writes speeds. I say generally becaues there are always exceptions.

Great info in that PDF. Thanks

The reason that there's a relationship between capacity and throughput is basic physics. Higher capacity drives have more bits squeezed onto the same area. Thus, all other things being equal, the higher capacity drives will transfer faster.

---

### Post by jinx099 on 2007-12-20
Earlier I moved my PCI-e gigE NIC to my server and am using the onboard gigE NIC on my desktop.  Using the PCI-e NIC did improve the performance a bit over NFS.

RAID-0 over NFS  ~38 MB/s
```
$ time cp 1GB.FILE ~

real    0m26.612s
user    0m0.007s
sys     0m2.587s
```

RAID-1 over NFS  ~24 MB/s
```
$ time cp 1GB.FILE ~

real    0m42.596s
user    0m0.008s
sys     0m2.556s
```

Disk to disk on the server times did not change much.  My disk performance in general still seems a bit slow.

---

### Post by psusi on 2007-12-20
> **Paulmd said:**
> Close....

Conventional PCI is 133MB/sec.

[http://www.dell.com/content/topics/global.aspx/vectors/en/2004_pciexpress?c=us&l=en&s=corp](http://www.dell.com/content/topics/global.aspx/vectors/en/2004_pciexpress?c=us&l=en&s=corp)

No.  A MegaByte is not 1 million bytes.  It is 1024 KB, which is 1024 Bytes.  That gives 125 MB/s maximum theoretical speed, not counting any overhead.  After counting overhead, it is closer to 100.

---

### Post by Paulmd on 2007-12-20
> **psusi said:**
> No.  A MegaByte is not 1 million bytes.  It is 1024 KB, which is 1024 Bytes.  That gives 125 MB/s maximum theoretical speed, not counting any overhead.  After counting overhead, it is closer to 100.

Where EXACTLY did I, or that article say that it was, for Chrissakes?

I actually sourced multiple articles to CHECK that number. I only provided the link to this one because it was the best.

Here's more:

[http://en.wikipedia.org/wiki/Peripheral_Component_Interconnect](http://en.wikipedia.org/wiki/Peripheral_Component_Interconnect)

[http://www.viaarena.com/default.aspx?PageID=5&ArticleID=86](http://www.viaarena.com/default.aspx?PageID=5&ArticleID=86)

You find me an article that states the throughput for standard PCI as anything other than 133MB/sec, and I'll consider it. It won't be that easy. Somehow, I do not think that every last article I've come across is making the same gaffe. I think, that you're making a correction, when you shouldn't be.

Overhead is more difficult to calculate, as it will depend on the devices attached to it. Lopping off a nice round number isn't exactly a reasonable approach, though.

You're not really that far off on principle, but you have got to do the required reading from time to time. 

You may have come across an article stating that giababit ethernet, at 125MB/sec effectively saturates the PCI bus.  Which is a true statement, but it does not imply that the PCI bus is 125MB/sec.

---

### Post by psusi on 2007-12-20
The articles are wrong then.  I will log in to wikipedia today and try to correct it.  

33,000,000 ( 33 Mhz clock speed ) x 32 bits bus width = 132,000,000 bytes per second.  Divide that by 1024^2 and you get 125.885.

Likewise, gigabit ethernet is also 125,000,000 bytes per second ( 1 billion / 8 ), which is 119.2 MB/s.

Actually I think the clock speed of pci may have been 33 and one third Mhz, so that would give:

33,333,333 x 4 bytes = 133,333,332 bytes per second, which is 127.156 MB/s.  I'll have to find my copy of the PCI spec and double check that, but I bet that's what it was which is where the 133 MB/s number comes from, which as I said before, uses 1 million for MB, which is incorrect.

---

### Post by Paulmd on 2007-12-21
> **psusi said:**
> The articles are wrong then.  I will log in to wikipedia today and try to correct it.  

33,000,000 ( 33 Mhz clock speed ) x 32 bits bus width = 132,000,000 bytes per second.  Divide that by 1024^2 and you get 125.885.

Likewise, gigabit ethernet is also 125,000,000 bytes per second ( 1 billion / 8 ), which is 119.2 MB/s.

Actually I think the clock speed of pci may have been 33 and one third Mhz, so that would give:

33,333,333 x 4 bytes = 133,333,332 bytes per second, which is 127.156 MB/s.  I'll have to find my copy of the PCI spec and double check that, but I bet that's what it was which is where the 133 MB/s number comes from, which as I said before, uses 1 million for MB, which is incorrect.


I know a gauntlet when I see one. :)

[http://www.pcisig.com/specifications/conventional/](http://www.pcisig.com/specifications/conventional/)

You've got to be a member to download: (or you can do a Google search on the filename.)

Page 18 of "Conventional PCI 3.0"

"
1.5.         PCI Local Bus Features and Benefits
The PCI Local Bus was specified to establish a high performance local bus standard for
several generations of products. The PCI specification provides a selection of features that
can achieve multiple price-performance points and can enable functions that allow
differentiation at the system and component level. Features are categorized by benefit as
follows:
High Performance             Transparent upgrade from 32-bit data path at 33 MHz
                             (132 MB/s peak) to 64-bit data path at 33 MHz
                             (264 MB/s peak), from 32-bit data path at 66 MHz (264 MB/s
                             peak) to 64-bit data path at 66 MHz (532 MB/s peak), and from
                             32-bit data path at 133 MHz (532 MB/s peak) to 64-bit data path
                             at 133 MHz (1064 MB/s peak).
                             Variable length linear and cacheline wrap mode bursting for both
                             read and writes improves write dependent graphics performance.

".

I've skimmed this thing, I'm not seeing offhand where it's giving Megabytes as a Million Bytes. But if you wanna, I'll be happy to email you the spec,

I also found the Specs for PCI 2.3, the portion where it mentions the bandwidth is a identical to the 3.0 spec.


If you're sufficiently determined, you can call the authors, and ask if they meant a megabyte is a million bytes or not. 

PCI-SIG
5440 SW Westgate Drive
Suite 217
Portland, Oregon 97221
Phone: 503-291-2569
Fax: 503-297-1090
e-mail [email]administration@pcisig.com[/email]
[http://www.pcisig.com](http://www.pcisig.com)

---

