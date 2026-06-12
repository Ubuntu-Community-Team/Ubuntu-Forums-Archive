---
title: "[SOLVED] Problems with gigabit network speed"
date: 2007-12-26
forum: Networking &amp; Wireless
---

### Post by Monttinen on 2007-12-26
*[COLOR="DarkOrchid"]Solved: Problem is with network adapter driver in vista. When speed was measured using ubuntu livecd in vista machine, speed was 650Mbit/s in both directions.[/COLOR]*

Hello,
I have two computers with gigabit ethernet cards connected in d-link gigabit switch. The other computer has Ubuntu and a realtek 8169 card and it is connected with cat5e cable. The other computer has Windows Vista 32bit and integrated Attansic L1 gigabit card and is connected with cat5 cable.
Here comes the actual problem:
I can transfer files from Vista computer to Ubuntu computer at 50MB/s rate, but if I'm transfering files from Ubuntu computer to Vista computer the speed is only 9MB/s. I have also tried connecting the computers directly to each other with cat5e cable and the speeds are the same.
How do I get 50MB/s when transfering files from Ubuntu to Vista?

-Monttinen

---

### Post by mips on 2007-12-26
Have you checked your duplex & speed setting for the ethernet port in ubuntu?

---

### Post by dbott67 on 2007-12-26
Can you post the output of:
```
dbott@gutsy:~$ sudo ethtool eth[COLOR=Red]1[/COLOR]
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

```

Of course, change eth1 to your appropriate interface.

-Dave

---

### Post by Monttinen on 2007-12-26
```
Settings for eth2:
        Supported ports: [ TP ]
        Supported link modes:   10baseT/Half 10baseT/Full
                                100baseT/Half 100baseT/Full
                                1000baseT/Full
        Supports auto-negotiation: Yes
        Advertised link modes:  1000baseT/Full
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
That should be ok, I think.
I tried to make the driver provided in realtek site, but it didn't work and I tried the one here: [http://gentoo-wiki.com/HARDWARE_RTL8168]("http://gentoo-wiki.com/HARDWARE_RTL8168")
That seemed to go in ok and the 1GB connection seems to work in the other way but not vice versa. That just seems weird. I tried to change the frame size from 1500 to 9000 on Vista but with no result. I have no idea what to do. :(

---

### Post by netztier on 2007-12-27
> **Monttinen said:**
> 
I can transfer files from Vista computer to Ubuntu computer at 50MB/s rate, but if I'm transfering files from Ubuntu computer to Vista computer the speed is only 9MB/s. 

Sounds like you are using Samba to copy files back and forth - wrong approach. You're most probably measuring Samba's performance instead of the network hardware.

Get iPerf from the universe repositories for the Ubuntu machine and get it from [http://dast.nlanr.net/Projects/Iperf/#download](http://dast.nlanr.net/Projects/Iperf/#download) for Windows, thean measure raw TCP performance between these two hosts. Make sure you swap "client" (sender) and "server" (receiver) roles.

With somewhat modern hardware, you should be able to reach values of 400 - 600 MBit/s. 

Samba tuning is yet another chapter...

About Speed/Duplex: Gigabit-over-Copper (aka Cat5 or better) runs Full Duplex *only* - it has no notion of half duplex. Using MTU 9000 (aka "Jumbo Frames") is only an option if your LAN switch supports it - and if all hosts connected to that subnet also support it (which rules out any WiFi-connected devices).

best regards

Marc

---

### Post by Monttinen on 2007-12-27
Results:
Ubuntu machine as server:
```
[  4] local 192.168.0.1 port 5001 connected with 192.168.0.2 port 54617
[  4]  0.0-10.0 sec    155 MBytes    130 Mbits/sec
```

Vista machine as server:
```
[  3] local 192.168.0.1 port 47323 connected with 192.168.0.2 port 5001
[  3]  0.0-10.0 sec    110 MBytes  91.9 Mbits/sec
```

That doesn't seem nice at all. I tried that first with d-link switch and then I connected machines directly to each other and the resluts were same. Something is definetly wrong with either drivers or cards.

---

### Post by mips on 2007-12-27
The above seems normal to me.

---

### Post by Monttinen on 2007-12-27
How so? They should really be well above 200 Mbits/s atleast. And if I'm able to transfer at 50MB/s rate that should get me 400 Mbits/s. I also ran iPerf again with -t 60 and the result was same.

---

### Post by trobbins on 2007-12-27
Are you using managed switches?  If so, try hard coding the speed and duplex on the switch and on the workstation and also try setting both to auto/auto.  Where I work, we've been seeing a rash of switches coded to 100full but the Windows PCs were experiencing "delayed write" errors.  Once we hard coded the workstation duplex settings to match the switch, the issues went away.  The data transfer rates were similar to what you were experiencing.  In one direction data flowed readily, but the other direction the bandwidth was poor.

---

### Post by Monttinen on 2007-12-28
I have D-Link DGS-1008D and it isn't a managed switch, besides the problem occures also if the computers are directly connected to each other so it is not about the switch.

---

### Post by mips on 2007-12-28
[http://ubuntuforums.org/showthread.php?t=650488](http://ubuntuforums.org/showthread.php?t=650488)

---

### Post by Monttinen on 2007-12-28
Well, the speeds should be about 50MB/s in both ways, I tried sending files through loopback interface and I get 50MB/s on ubuntu machine and over 60MB/s on Vista machine. So iPerf values should also be around 400MBits/s. And the thing I dont't understand is why the speed is 50MB/s the other way but only 9MB/s in other direction.

---

### Post by mips on 2007-12-28
I dunno if you have tried this yet but could I suggest turning off auto negotiate on both computers and manually setting them to 1000MB/Full-Duplex. Also disable any powersave/sleep on them.

---

### Post by netztier on 2007-12-29
> **trobbins said:**
>  If so, try hard coding the speed and duplex on the switch and on the workstation and also try setting both to auto/auto.

Again - this is pointless to do if you're running 1000baseT (gigabit over Cat5 or better) - it only knows full duplex.

> **trobbins said:**
>  Where I work, we've been seeing a rash of switches coded to 100full but the Windows PCs were experiencing "delayed write" errors..

It's either that or so called "late collisions" that are the unmistakable sign of a duplex mismatch, the ghost that haunts every switched 100Mbps Ethernet network at a given time in it's history and a very common configuration error found in these environments.

Yet, if the OP actually *had* a duplex mismatch, his throughputs would show figures below the 1Mbit/s line - he'd never be able to reach 9MBytes/s as measured by samba nor 90+ MBit/s as measured by iPerf.

best regards

Marc

---

### Post by Monttinen on 2007-12-30
> **mips said:**
> I dunno if you have tried this yet but could I suggest turning off auto negotiate on both computers and manually setting them to 1000MB/Full-Duplex. Also disable any powersave/sleep on them.

I have had my settings like that all the time.

```
monttinen@monttinen:~$ iperf -c 192.168.0.2
------------------------------------------------------------
Client connecting to 192.168.0.2, TCP port 5001
TCP window size: 16.0 KByte (default)
------------------------------------------------------------
[  3] local 192.168.0.1 port 45764 connected with 192.168.0.2 port 5001
[  3]  0.0-10.0 sec    109 MBytes  91.6 Mbits/sec
monttinen@monttinen:~$ iperf -s
------------------------------------------------------------
Server listening on TCP port 5001
TCP window size: 85.3 KByte (default)
------------------------------------------------------------
[  4] local 192.168.0.1 port 5001 connected with 192.168.0.2 port 63155
[  4]  0.0-10.0 sec    154 MBytes    129 Mbits/sec

```

EDIT: I also tested sending files through FTP and I can download files from ubuntu machine at 7,5MB/s and send files at 10,5MB/s, so all tests indicate that speed from Vista machine to Ubuntu machine is higher.

---

### Post by jcliburn on 2008-01-01
Running a development version of the atl1 driver with kernel 2.6.24-rc6, I get:

~260 Mbits/sec transmit
~200 Mbits/sec receive

This is through 3 switches and 8 segments of homebuilt cat5e.

```
[jcliburn@osprey src]$ ./iperf -c petrel
------------------------------------------------------------
Client connecting to petrel, TCP port 5001
TCP window size: 16.0 KByte (default)
------------------------------------------------------------
[  3] local 192.168.1.3 port 43889 connected with 192.168.1.6 port 5001
[  3]  0.0-10.0 sec    307 MBytes    258 Mbits/sec
[jcliburn@osprey src]$ ./iperf -s
------------------------------------------------------------
Server listening on TCP port 5001
TCP window size: 85.3 KByte (default)
------------------------------------------------------------
[  4] local 192.168.1.3 port 5001 connected with 192.168.1.6 port 53301
[  4]  0.0-10.0 sec    237 MBytes    199 Mbits/sec
[jcliburn@osprey src]$ ethtool -i eth0
driver: atl1
version: 2.1.1
firmware-version: N/A
bus-info: 0000:02:00.0

```

This version of the driver should show up in the 2.6.25 kernel.

---

### Post by troutbum13 on 2008-01-02
Those network speeds are very slow for gigE, can we see the client side output? 

iperf -c SERVERNAME -r -i 3 -t -l 64k for comparrison
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

---

### Post by charmcity on 2008-01-02
I have the same problem --> using 1 Ubuntu box and 1 XP machine.  Both have GigE NIC's and I am running through a DIR-655 Router  (DLINK)

Here's my iperf numbers (pretty poor considering nothing else going on the network):

```
@tommy:~$ iperf -c 192.168.2.199
------------------------------------------------------------
Client connecting to 192.168.2.199, TCP port 5001
TCP window size: 16.0 KByte (default)
------------------------------------------------------------
[  3] local 192.168.2.197 port 52560 connected with 192.168.2.199 port 5001
[  3]  0.0-10.0 sec    229 MBytes    192 Mbits/sec

```

```
@tommy:~$ iperf -s
------------------------------------------------------------
Server listening on TCP port 5001
TCP window size: 85.3 KByte (default)
------------------------------------------------------------
[  4] local 192.168.2.197 port 5001 connected with 192.168.2.199 port 2580
[  4]  0.0-10.0 sec    108 MBytes  90.9 Mbits/sec

```

---

### Post by dbott67 on 2008-01-02
> **charmcity said:**
> I have the same problem --> using 1 Ubuntu box and 1 XP machine.  Both have GigE NIC's and I am running through a DIR-655 Router  (DLINK)

Here's my iperf numbers (pretty poor considering nothing else going on the network):

```
@tommy:~$ iperf -c 192.168.2.199
------------------------------------------------------------
Client connecting to 192.168.2.199, TCP port 5001
TCP window size: 16.0 KByte (default)
------------------------------------------------------------
[  3] local 192.168.2.197 port 52560 connected with 192.168.2.199 port 5001
[  3]  0.0-10.0 sec    229 MBytes    192 Mbits/sec

``````
@tommy:~$ iperf -s
------------------------------------------------------------
Server listening on TCP port 5001
TCP window size: 85.3 KByte (default)
------------------------------------------------------------
[  4] local 192.168.2.197 port 5001 connected with 192.168.2.199 port 2580
[  4]  0.0-10.0 sec    108 MBytes  90.9 Mbits/sec

```

Can you try setting a static IP on each PC and then connect them directly to each other using a cross-over cable?

Report back with your results.

Check this [thread]("http://ubuntuforums.org/showpost.php?p=4026769&postcount=11") for typical results.

Thanks,
Dave

---

### Post by jcliburn on 2008-01-05
> **troutbum13 said:**
> Those network speeds are very slow for gigE, can we see the client side output? 

iperf -c SERVERNAME -r -i 3 -t -l 64k for comparrison

This is across one switch and two short cat5e cable segments.  The host named "osprey" is a Linux box using the L1 NIC with atl1 driver version 2.1.1 (a development version of the driver).  The other host is a WinXP Thinkpad T60.

The results exceed 900 megabits per second.

```

[jcliburn@osprey src]$ uname -r
2.6.24-rc6
[jcliburn@osprey src]$ ethtool -i eth0
driver: atl1
version: 2.1.1
firmware-version: N/A
bus-info: 0000:02:00.0
[jcliburn@osprey src]$ ./iperf -c 192.168.1.93 -r -i 3 -t 15 -l 64k -r -f M
------------------------------------------------------------
Server listening on TCP port 5001
TCP window size: 0.08 MByte (default)
------------------------------------------------------------
------------------------------------------------------------
Client connecting to 192.168.1.93, TCP port 5001
TCP window size: 0.02 MByte (default)
------------------------------------------------------------
[  5] local 192.168.1.3 port 45098 connected with 192.168.1.93 port 5001
[  5]  0.0- 3.0 sec    334 MBytes    111 MBytes/sec
[  5]  3.0- 6.0 sec    335 MBytes    112 MBytes/sec
[  5]  6.0- 9.0 sec    330 MBytes    110 MBytes/sec
[  5]  9.0-12.0 sec    335 MBytes    112 MBytes/sec
[  5] 12.0-15.0 sec    335 MBytes    112 MBytes/sec
[  5]  0.0-15.0 sec  1669 MBytes    111 MBytes/sec
[  4] local 192.168.1.3 port 5001 connected with 192.168.1.93 port 1026
[  4]  0.0- 3.0 sec    323 MBytes    108 MBytes/sec
[  4]  3.0- 6.0 sec    329 MBytes    110 MBytes/sec
[  4]  6.0- 9.0 sec    329 MBytes    110 MBytes/sec
[  4]  9.0-12.0 sec    328 MBytes    109 MBytes/sec
[  4] 12.0-15.0 sec    328 MBytes    109 MBytes/sec
[  4]  0.0-15.1 sec  1643 MBytes    109 MBytes/sec
[jcliburn@osprey src]$ 

```

---

### Post by HermanAB on 2008-01-05
For network speed tests, you should use netcat and very large files, since netcat has very little overhead and a large file will ensure that the startup and shutdown effects are small.

With Samba, SSH, FTP, the overhead is significant and the results will depend on the speed of the processor.  Since the protocols are asymetric, with more/less work done on the server/client, results will vary depending on the direction, as you have found.  Also, the read and write speed of disk drives are not the same, so a crummy disk drive would be able to read much faster than it can write, which will again influence things a lot.

Herman's Cosmic Constant of Laptop Data Throughput:
The sustained maximum data throughput of any laptop computer never exceeds 32MB/s.

Cheers,

Herman

---

### Post by jcliburn on 2008-01-05
> **HermanAB said:**
> For network speed tests, you should use netcat and very large files, since netcat has very little overhead and a large file will ensure that the startup and shutdown effects are small.
Or, you can use iperf or netperf (in this thread, iperf), both of which are designed explicitly for network performance measurement, each providing a variety of tunable parameters to aid in that endeavor.

---

### Post by Monttinen on 2008-01-08
Ok I just ran iPerf using ubuntu livecd in my desktop/vista machine and I got better results:
```
ubuntu@ubuntu:/tmp$ iperf -s
------------------------------------------------------------
Server listening on TCP port 5001
TCP window size: 85.3 KByte (default)
------------------------------------------------------------
[  4] local 192.168.0.2 port 5001 connected with 192.168.0.1 port 40420
[ ID] Interval       Transfer     Bandwidth
[  4]  0.0-10.0 sec   783 MBytes   656 Mbits/sec
ubuntu@ubuntu:/tmp$ iperf -c 192.168.0.1
------------------------------------------------------------
Client connecting to 192.168.0.1, TCP port 5001
TCP window size: 16.0 KByte (default)
------------------------------------------------------------
[  3] local 192.168.0.2 port 57411 connected with 192.168.0.1 port 5001
[ ID] Interval       Transfer     Bandwidth
[  3]  0.0-10.0 sec   784 MBytes   656 Mbits/sec

```
So it is either Vista or the drivers.

EDIT: I installed new drivers that were released a short time ago for my Atheros L1 in vista machine and got following iperf results:
```
monttinen@monttinen:~$ iperf -s
------------------------------------------------------------
Server listening on TCP port 5001
TCP window size: 85.3 KByte (default)
------------------------------------------------------------
[  4] local 192.168.0.1 port 5001 connected with 192.168.0.2 port 49275
[  4]  0.0-10.0 sec    380 MBytes    319 Mbits/sec
[  5] local 192.168.0.1 port 5001 connected with 192.168.0.2 port 49276
[  5]  0.0-10.0 sec    380 MBytes    318 Mbits/sec
monttinen@monttinen:~$ iperf -c 192.168.0.2
------------------------------------------------------------
Client connecting to 192.168.0.2, TCP port 5001
TCP window size: 16.0 KByte (default)
------------------------------------------------------------
[  3] local 192.168.0.1 port 51965 connected with 192.168.0.2 port 5001
[  3]  0.0-10.0 sec    836 MBytes    701 Mbits/sec
monttinen@monttinen:~$ iperf -c 192.168.0.2
------------------------------------------------------------
Client connecting to 192.168.0.2, TCP port 5001
TCP window size: 16.0 KByte (default)
------------------------------------------------------------
[  3] local 192.168.0.1 port 57728 connected with 192.168.0.2 port 5001
[  3]  0.0-10.0 sec    835 MBytes    701 Mbits/sec

```
I also tested transfering files with samba and download speed was around 12,5MB/s and 18MB/s which is better than the previous 9,0MB/s and my upload speed is also better, around 55MB/s and 67MB/s instead of the previous  50MB/s.
So the problem is about the drivers in Vista and this thread is solved, atleast on ubuntu side. Thanks for everyone.

---

### Post by moonlightcheese on 2008-03-07
a lot of people seem to be confused about the reads being faster than writes with the newer kernels.  tcp auto-tuning was built into the 26 kernel and is unchangeable.  you cannot turn it off.  this produces faster speeds when acting as the client than when acting as the server.  it seems haphazard but it isn't.

also, people are also trying to suggest disabling auto-negotiation for 1Gbps nics to increase throughput.  this is not possible because auto-negotiation cannot be disabled for 1Gbps nics, whether you tell it to or not, so specifying it as disabled for gigE is just pointless.  source: [http://www.ethermanage.com/ethernet/autoneg.html](http://www.ethermanage.com/ethernet/autoneg.html)

edit:
> The twisted-pair Auto-Negotiation system defined in Clause 28 of the standard has since been extended to include all three speeds of Ethernet supported over twisted-pair cable: 10 Mbps 10BASE-T, 100 Mbps 100BASE-TX and 1000 Mbps 1000BASE-T. The physical signaling portion of all three twisted-pair systems use the same Auto-Negotiation signaling standard. While **Auto-Negotiation can be disabled on 10BASE-T and 100BASE-TX links, it is required on 1000BASE-T systems** since Gigabit Ethernet systems use Auto-Negotiation to establish the master-slave signal timing control required to make the link operational.

---

