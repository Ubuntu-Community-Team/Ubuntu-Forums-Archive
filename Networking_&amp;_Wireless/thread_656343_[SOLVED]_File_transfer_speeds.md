---
title: "[SOLVED] File transfer speeds"
date: 2008-01-02
forum: Networking &amp; Wireless
---

### Post by troutbum13 on 2008-01-02
I have a gigbit  home network, cat 6 cables, netgear pro 16 dumb switch (gigabit), Server is WHS (i know, i know) my workstation is  gutsy. I am getting incredibly slow (for gigabit) file transfer speeds. this is occuring both up and down I am getting ~5MB/s These are very large files ~8GB

I don't believe this to be a network layer issue, 
```

alec@Lebowski:~$ iperf -c donnie -i 3 -t 15 -l 64k -r -f M
------------------------------------------------------------
Server listening on TCP port 5001
TCP window size: 0.08 MByte (default)
------------------------------------------------------------
------------------------------------------------------------
Client connecting to donnie, TCP port 5001
TCP window size: 0.02 MByte (default)
------------------------------------------------------------
[  5] local 192.168.0.17 port 40884 connected with 192.168.0.15 port 5001
[  5]  0.0- 3.0 sec    214 MBytes  71.4 MBytes/sec
[  5]  3.0- 6.0 sec    216 MBytes  71.9 MBytes/sec
[  5]  6.0- 9.0 sec    216 MBytes  72.0 MBytes/sec
[  5]  9.0-12.0 sec    212 MBytes  70.8 MBytes/sec
[  5] 12.0-15.0 sec    213 MBytes  70.9 MBytes/sec
[  5]  0.0-15.0 sec  1071 MBytes  71.4 MBytes/sec
[  4] local 192.168.0.17 port 5001 connected with 192.168.0.15 port 1041
[  4]  0.0- 3.0 sec    152 MBytes  50.6 MBytes/sec
[  4]  3.0- 6.0 sec    160 MBytes  53.2 MBytes/sec
[  4]  6.0- 9.0 sec    159 MBytes  53.1 MBytes/sec
[  4]  9.0-12.0 sec    160 MBytes  53.3 MBytes/sec
[  4] 12.0-15.0 sec    159 MBytes  53.1 MBytes/sec
[  4]  0.0-15.0 sec    791 MBytes  52.7 MBytes/sec

```

Not sure why my download speeds are so much slower than up, but they are both far superior to my file transfer speeds

```

alec@Lebowski:~$ sudo ethtool eth0
Settings for eth0:
        Supported ports: [ MII ]
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
        Port: MII
        PHYAD: 1
        Transceiver: external
        Auto-negotiation: on
        Supports Wake-on: g
        Wake-on: d
        Link detected: yes

```

Any guesses on what could be clogging file transfer speeds?

---

### Post by ARhere on 2008-01-02
This may not be it, but I have noticed with Linksys, Netgear, and other consumer based switches that they do not follow the standard as far as cable length goes (*less power for the Tx and Rx hardware ports == less development cost*.  When using a Linsys switch you have a max of 32 feet, after that the signal degrades so much that the switch resets for 10Mb or even 1Mb automatically to lessen the CRC errors.  And that **is** with Cat5e!

Just a thought.  -AR

EDIT: The hardware can reset to a slower speed for a single instance and you will not notice because the default stays at the level you set; which in your case it 1000Mb, 100Mb, or 10Mb.  Also, check  you cable.  I noticed a lot of Software developers like to throw around the same cable they have used for 10 years!  Kinks = bad signal!  :-P

---

### Post by troutbum13 on 2008-01-02
Thanks, but it doesn't seem to be network layer issue... I can get sustained transfers through iperf filling ~70% of the pipe < 600Mb/s. I wouldn't expect to get much better that 700Mb/s through the switch...so the network layer could be tweaked some, but doesn't seem like it would be responsible for ~40Mb/s

I am getting 450+ Mb/s reads from the HDDs, So I think it must be driver or software based issue

Maybe my logic is flawed, but Iperf is testing RAM-->RAM, and hdparm HDD-->ram.

I think I need a test box to determine if it is the server or the workstation that is throttling the file transfers...

I kind of suspect it is a WHS issue, maybe I can run a live CD or boot to a flash drive of unraid or ubuntu, anyone know if I will be able to access the WHS JBOD shares???

---

### Post by ARhere on 2008-01-02
> **troutbum13 said:**
> Thanks, but it doesn't seem to be network layer issue... I can get sustained transfers through iperf filling ~70% of the pipe < 600Mb/s. I wouldn't expect to get much better that 700Mb/s through the switch...so the network layer could be tweaked some, but doesn't seem like it would be responsible for ~40Mb/s

I am getting 450+ Mb/s reads from the HDDs, So I think it must be driver or software based issue

Maybe my logic is flawed, but Iperf is testing RAM-->RAM, and hdparm HDD-->ram.

I think I need a test box to determine if it is the server or the workstation that is throttling the file transfers...

I kind of suspect it is a WHS issue, maybe I can run a live CD or boot to a flash drive of unraid or ubuntu, anyone know if I will be able to access the WHS JBOD shares???

You really have me confused.  You are complaining about network transfer speeds being slow, but now you are talking about speeds between your RAM and HDD. (*Which is all in the same box*).

Am I misunderstanding your problem?  Is your server and client listed above on the same machine?

P.S.:  What I was talking about is part of the hardware layer, not the network layer.

---

### Post by troutbum13 on 2008-01-02
the network consists of a WHS server, a Ubuntu workstation, separate boxes. I have gigabit switch, new cat6 cabling. There are 6 other machines and a WAP along with a print server, but they should be irrelevant for this.

I am not a network guy so bear with me,

Ipref is testing network throughput, without writing anything to the server or client HDDs. This tells me network throughput. The results from iperf look reasonable for a gigabit network, I am getting ~600Mbs up and slightly less down. ( if there were a network problem (cabling or the switch) I assume I would see problems here, but maybe not??)
I am seeing very low file transfer rates.. 40Mbs

It doesn't matter how fast I can put data through the pipe if it is throttled at an endpoint. So it could be the HDDs can't read/write fast enough. This is certainly the case, I think most HDDs can get swamped by fast ethernet. But hdparm and hdtach on the WHS machine tell me that the HDDs are running at better than 400Mbs. 

I am no expert, but it seems to me that if I can get data on and off the drives at 400Mbs and I can send it across the network at 600Mbs but I am only getting 40Mbs in a file transfer there is something else going on?? 

am I missing something?

Anyone know if a run a live CD on the server will I be able to read the WHS JBOD or even individual disks?

---

### Post by ARhere on 2008-01-02
Gotcha.  Sorry for the confusion but I am a EE, not a developer so I appreciate the education on "iperf".

I do know that even though you have a gigabit switch and network, and everything tests at 600Mbps with iperf, when you actually try to use the system to transfer files the real speed is MUCH slower due to everything that goes on in-between.

I am running a network scan now while transferring 20gigs of random data and I am getting 10.7MB per sec (85.6Mbps) data throughput and I know we use a good gigabit switch here with a RAID 5 on the server side.

I think the problem might simply be having too high of expectations, but others might disagree.  40Mbps is a tad slower then I would expect, but there is a lot of possibilities that can be your bottleneck.

Everything aside I know for a _fact_ you will never see 600Mbps data transfer speed on a standard gigabit switch without major tweaking!

-AR

---

### Post by troutbum13 on 2008-01-02
agreed, There is going to be overhead, but I don't think it is unrealistic to think that I should be able to pull at least 250-300Mps...does anyone else think I am expecting too much?

---

### Post by ARhere on 2008-01-03
<..<

>..>

<shrug> :-k

Sorry I could not help you more.  I did some more searching and I am seeing the same results; 40Mbps~120Mbps, but nothing like you are expecting.

Is it causing lag in some application?  Or are you just curious?

-AR

---

### Post by troutbum13 on 2008-01-03
Thanks for your help, mostly annoying, I am getting good enough read rates to stream all my media, but when I try to put media up to the server it takes for ever...

I discovered it is the WHS software that is causing the slowdown...there are several threads over at MS.com. Seems the way WHS "balances" the server is to write all network transfers to the primary disk, then when it gets to a certain threshold it starts copying from the primary disk to the storage disks (JBOD array). So when you are transferring files of any size it is  simultaneously trying to read and write to the priamry disk. :rolleyes: 

I am going to replace the WHS with something a little better suited to my needs. Problem is I have over a TB of media files on that machine, not sure if I have to trnasfer the files before I move the HDDs to ubuntu server or if I can just mount and share the NTFS drives as is from Samba?

---

