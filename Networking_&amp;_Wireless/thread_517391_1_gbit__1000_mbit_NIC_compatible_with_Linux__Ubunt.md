---
title: "1 gbit / 1000 mbit NIC compatible with Linux / Ubuntu"
date: 2007-08-04
forum: Networking &amp; Wireless
---

### Post by christian_johansson on 2007-08-04
I have googled for a definite answer to the following question with no avail: what gigabit NIC:s are there that for _sure_ works in Ubuntu?
And by 'works' I don't mean that Ubuntu will just be able to find it and use it as a 10 mbit card.
I mean it should find it and be able to use its full capacity. A windows box using the NIC:s manufacturers own drivers should not be able to outperform it.

Is there such a card?  Something tells me an Intel based card using the e1000 driver is my best bet. Can anyone confirm or deny this?

Is there anyone out there using a 1 gb NIC?   What NIC do you have?  What linux module is it using?  How does it perform?

---

### Post by jimrz on 2007-08-04
> **christian_johansson said:**
> I have googled for a definite answer to the following question with no avail: what gigabit NIC:s are there that for _sure_ works in Ubuntu?
And by 'works' I don't mean that Ubuntu will just be able to find it and use it as a 10 mbit card.
I mean it should find it and be able to use its full capacity. A windows box using the NIC:s manufacturers own drivers should not be able to outperform it.

Is there such a card?  Something tells me an Intel based card using the e1000 driver is my best bet. Can anyone confirm or deny this?

Is there anyone out there using a 1 gb NIC?   What NIC do you have?  What linux module is it using?  How does it perform?

the e1000 works as it should on my ThinkPad T42

---

### Post by macmasterxiv on 2007-08-18
I have my doubts about e1000. Even though it says it's running at 1gbps on my laptop (intel pro/1000 PL), I usually can only get 100mbit file transfer speeds out of it. Using different combinations of linux/windows between two systems, I've discovered this is not the problem with my marvell nvidia onboard nic on my desktop using the forcedeth driver, which works as it should. I'll be testing a realtek 8169 soon.

---

### Post by netztier on 2007-08-18
> **macmasterxiv said:**
> I have my doubts about e1000. Even though it says it's running at 1gbps on my laptop (intel pro/1000 PL), I usually can only get 100mbit file transfer speeds out of it. Using different combinations of linux/windows between two systems, I've discovered this is not the problem with my marvell nvidia onboard nic on my desktop using the forcedeth driver, which works as it should. I'll be testing a realtek 8169 soon.

Using filesharing to load-test a gigabit card isn't likely to give you meaningful throughput values. Too many factors come into play and throttle throughputs down - not the least the disk I/0. Delivering a sustained >100MBytes/sec is still somewhat of a challenge for a standard PC's I/0 architecture.

With NFS, I managed to get peaks of up to 60MBytes/s through a Intel e1000, from an the 128MBytes of cache on an Adaptec 2100S controller (with a RAID 10 array behind it) in an oldish P-III 500MHz. Samba would never go beyond 15-17MBytes/sec, no matter what I tried. 

Actually filling a gigabit pipe from disk I/O is not trivial at all. At my workplace, it took a considerable amount of time to tune a Sun V480's (4x UltraSparc III) IP stack until it would max-out a 1GBit/s link with multiple simultaneous TCP streams from a range of (Veritas NetBackup) clients. 10Gbit/s cards that now become available for servers will be yet another mountain to climb...

If you want to measure raw TCP (or UDP)  throughput, I suggest you use **iperf** from the universe repositories. If you google for iPerf, you'll find it's home and also a windows version, so you can measure across different platforms

With the same P-III 500 and it's e1000 card as server and an 1.8GHz Athlon 64 (Marvell Yukon Gigabit Chip with skge module) as client, I get up to ~770MBits/s to the server and ~700Mbit/s from the server. 

Server command line: 
```
iperf -s
```
Client command line (4 **P**arallel threads, 30 seconds total **t**ime, 5 sec reporting **i**nterval, **r**everse connect after first connect).
```
iperf -c <server's IP> -P 4 -t 30 -i 5 -r
```

Nota: iPerf has the notions of "server" and "client" inverted to what common sense would expect. The "server" (iperf -s) is actually the *receiver*, the "client" (iperf -c <server IP>) is the *sender*.

Overall, I consider the **e1000** a good card - it even ran instantly and hassle-free when I put it into my venerable Sun Ultra 60 or the Ultra 5 - which aren't even PCs.

Personally, I've always been suspicious about the RealTek cards. They may have matured in the last few years, along with their Linux kernel modules, but were notorious for not performing well and to generate more CPU load than throughput when under load - but that was back in the 2.2 kernel days...

best regards

Marc

---

