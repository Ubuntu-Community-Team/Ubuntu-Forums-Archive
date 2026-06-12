---
title: "Multiple concurrent connections"
date: 2021-06-02
forum: Networking &amp; Wireless
---

### Post by keith-goodwin on 2021-06-02
I am trying to get to overcome an apparent limitation in the ability of Ubuntu 20.04 to use multiple network interfaces in parallel.

I have a fairly extensive setup, but have pared it all down to the basics and not managed to sort this out.
Simply put, I am trying to make multiple servers, a Dell R900 and several Dell R620's that all have quad gigabit network cards, transfer files faster than just the speed of a single Ethernet interface.
I had everything networked correctly, using LACP in my switches and tried both team and bond with LACP (also round robin and active backup etc). I know that LACP will only give a speed increase when there are multiple connections from different sources. The speed does not increase with multiple distinct client transfers, and I would be happy to achieve even just that.

Early on I ruled out the disk speed bottleneck and run all tmpfs mounts which are ridiculously fast for file transfer, in the region 1.5GB/sec.

I stepped back further and further from a full setup and now have two, fresh Ubuntu 20.04 install, servers connected directly to each other, port 1 to port 1, port 2 to port 2... Each Ethernet interface has a unique static ipv4 address. I have removed all bonding and teaming setups and just have the simple Ethernet profiles for each port.

On the R900 i have got 4 terminals open. Each has a netcat listen to file, specifying the ip and port of an individual Ethernet interface.
On the R620 I have also got 4 terminals open. Each with a netcat send file from source ip and port to the R900 corresponding ip and ports so : -
R620 eno1 192.168.8.131 5001 with tmpfs mount and 10G file > R900 eno1 192.168.8.111 5001 with empty tmpfs mount
R620 eno2 192.168.8.132 5002 with tmpfs mount and 10G file > R900 eno2 192.168.8.112 5002 with empty tmpfs mount
R620 eno2 192.168.8.133 5003 with tmpfs mount and 10G file > R900 eno2 192.168.8.113 5003 with empty tmpfs mount
R620 eno2 192.168.8.134 5004 with tmpfs mount and 10G file > R900 eno2 192.168.8.114 5004 with empty tmpfs mount

Each netcat transfer works at full speed and completes successfully when run individually.

Running two at the same time, the speed per transfer is halved. three and the speed is likewise a third and four gives a quarter of the speed per transfer. Never going faster than the speed of a single gigabit link.

I'm either doing something wrong or have an erroneous assumption about the way quad port gigabit network cards work in ubuntu.

Does anybody have any thoughts or suggestions, please?

---

### Post by TheFu on 2021-06-02
Quad port gigabit network cards are limited by the bus speeds for the system. 

In general, transfers for files will be per interface, so 1 Gbps is the limitation per stream, as you posted. Transferring 4 separate files over a bonded connection should see each get about 940Mbps. The bonding provides 4x1Gbps streams on a single IP.

For testing network performance, perhaps using iperf3 would make sense?

My router uses Intel i210 NICs, but each AMD GX CPU is of limited capacity.  The way to get more total throughput is to have more streams.

So, here's some tests with 8, 4, and 2 separate connections from a fast server to the router, using iperf3.
On the router, I just ran:  **iperf3 -s**  nothing more.
On the client, I ran these commands and got these outputs:
```
$ iperf3 -c rt1 -t3  -P 8 | egrep SUM
[SUM]   0.00-1.00   sec   102 MBytes   855 Mbits/sec    6             
[SUM]   1.00-2.00   sec  97.7 MBytes   819 Mbits/sec    6             
[SUM]   2.00-3.00   sec  96.8 MBytes   812 Mbits/sec    5             
[SUM]   0.00-3.00   sec   296 MBytes   829 Mbits/sec   17             sender
[SUM]   0.00-3.00   sec   293 MBytes   820 Mbits/sec                  receiver
$ iperf3 -c rt1 -t3  -P 4 | egrep SUM
[SUM]   0.00-1.00   sec  90.4 MBytes   758 Mbits/sec    0             
[SUM]   1.00-2.00   sec  86.0 MBytes   722 Mbits/sec    0             
[SUM]   2.00-3.00   sec  83.9 MBytes   704 Mbits/sec    0             
[SUM]   0.00-3.00   sec   260 MBytes   728 Mbits/sec    0             sender
[SUM]   0.00-3.00   sec   259 MBytes   723 Mbits/sec                  receiver
$ iperf3 -c rt1 -t3  -P 2 | egrep SUM
[SUM]   0.00-1.00   sec  66.8 MBytes   560 Mbits/sec    0             
[SUM]   1.00-2.00   sec  65.8 MBytes   552 Mbits/sec    0             
[SUM]   2.00-3.00   sec  65.4 MBytes   549 Mbits/sec    0             
[SUM]   0.00-3.00   sec   198 MBytes   554 Mbits/sec    0             sender
[SUM]   0.00-3.00   sec   197 MBytes   551 Mbits/sec                  receiver

```
So, 2 connections got around 550 Mbps.  4 connections got 710Mbps and 8 connections got 820 Mbps. Gee - adding connections achieved higher throughput.  Hummmm,
```
$ iperf3 -c rt1 -t3  -P 12 | egrep SUM
[SUM]   0.00-1.00   sec   104 MBytes   870 Mbits/sec    9             
[SUM]   1.00-2.00   sec   100 MBytes   843 Mbits/sec    6             
[SUM]   2.00-3.00   sec  99.0 MBytes   831 Mbits/sec    9             
[SUM]   0.00-3.00   sec   303 MBytes   848 Mbits/sec   24             sender
[SUM]   0.00-3.00   sec   299 MBytes   835 Mbits/sec                  receiver
```

Well, it doesn't keep working. 20 connections reduces the throughput. Around 16 seems to be the sweet spot for the quad-core AMD CPU.

Found this, which might be helpful:
[https://unix.stackexchange.com/questions/469346/link-aggregation-bonding-for-bandwidth-does-not-work-when-link-aggregation-gro](https://unix.stackexchange.com/questions/469346/link-aggregation-bonding-for-bandwidth-does-not-work-when-link-aggregation-gro)

---

### Post by keith-goodwin on 2021-06-03
Thanks for replying to this.

The R900 is an older machine and does have a slower bus speed, being PCIe v2.0. The single quad port card has access to the PCIe x8 lanes from one of the four CPUs with a theoretical max of 4GBps. Taking that into account, I added two single 1Gbps NICs to the PCI lanes from two other CPUs and then ran just three connections, instead of four. The PCIe lanes of each card now being controlled by a six core CPU of it's own, with 2GBps bus speed for the single cards as they are PCIe x4. This made absolutely no difference to the results.
The R620s are PCIe3 and considerably quicker, with 10Gb card offered as an optional from Dell directly, so they can definitely cope with a quad port card.

I'm not sure what your setup is, but the iperf3 results you show are very slow for a single 1Gbps connection, yet alone supposed multiple bonded. Below are the results of a single connection: -

```
$** iperf3 -c 192.168.8.111 -t3**
Connecting to host 192.168.8.111, port 5201
[  5] local 192.168.8.131 port 46050 connected to 192.168.8.111 port 5201
[ ID] Interval           Transfer     Bitrate         Retr  Cwnd
[  5]   0.00-1.00   sec   114 MBytes   953 Mbits/sec    0    372 KBytes       
[  5]   1.00-2.00   sec   113 MBytes   946 Mbits/sec    0    436 KBytes       
[  5]   2.00-3.00   sec   113 MBytes   946 Mbits/sec    0    543 KBytes       
- - - - - - - - - - - - - - - - - - - - - - - - -
[ ID] Interval           Transfer     Bitrate         Retr
[  5]   0.00-3.00   sec   339 MBytes   948 Mbits/sec    0             sender
[  5]   0.00-3.00   sec   337 MBytes   **941 Mbits/sec**                  receiver

$ **iperf3 -c 192.168.8.111 -t3 -P2 | egrep SUM**
[SUM]   0.00-1.00   sec   115 MBytes   965 Mbits/sec    0             
[SUM]   1.00-2.00   sec   113 MBytes   948 Mbits/sec    0             
[SUM]   2.00-3.00   sec   112 MBytes   939 Mbits/sec    0             
[SUM]   0.00-3.00   sec   340 MBytes   951 Mbits/sec    0             sender
[SUM]   0.00-3.00   sec   337 MBytes   **941 Mbits/sec**                  receiver



```

When I add additional physical connections, the speed goes up very slightly. Not enough to warrant showing a separate set of results.

Thanks for the link. That is one of the many that searching has brought to my attention. The author of that also failed to make it work.

I did get some success by using round robin between two machines directly connected with a max of 3.2Gbps for four connections, but when trying to do a file transfer from two separate clients through a switch to the server with round robin still configured, everything slowed way down. I'm guessing because of TCP having to correct packet arrival order. Would have almost been quicker to do transfers in series over 100Mb, lol.

No other configuration has produced anything other than ~944Mbps divided by the number of transfers.

---

### Post by TheFu on 2021-06-03
None of my systems are bonded. We don't do that here.

I specifically picked the router, which is a $140 SBC designed for BSD compatibility. The BSD i210 drivers are single threaded, so limited to what that CPU specifically using different cores, can accomplish.  The router is doing lots of filtering, logging, and monitoring, which takes a hit in the throughput. My small business WAN connection isn't even 50/50 Mbps, so for the use here, logging, filtering, etc are much more important that pure WAN bandwidth.

The reason I picked that specific device was to show more about using multiple connections than raw performance.  My intention was not to confuse, just to provide a possible explanation.

Guess I failed. Sorry.

---

### Post by keith-goodwin on 2021-06-03
Ah, OK, thanks for clarifying.
Not a failure. I was able to follow a different line of thought and rule out some other possible bottlenecks, so still, thank you.

---

### Post by keith-goodwin on 2021-06-08
For anyone else that comes across this, using xargs for parallel execution of multiple rsync streams worked for me.
I found the information at [https://stackoverflow.com/questions/24058544/speed-up-rsync-with-simultaneous-concurrent-file-transfers](https://stackoverflow.com/questions/24058544/speed-up-rsync-with-simultaneous-concurrent-file-transfers)
I was able to push the speeds up to ~3Gbps from ramdisk to ramdisk. That speed is obviously different between other forms of storage.

---

### Post by TheFu on 2021-06-08
Be very, very, very, careful using **ls** as an input for file names as shown in that answer.  Best to use the built-in bash glob() capabilities.
In the end, you had to get multiple streams started - each is limited to what 1 card can provide, yes?

---

### Post by TheFu on 2021-06-08
As another alternative, not better, just alternative, using a task queue system that will run multiple jobs, limited to 3 or 6 or 20 or 99 concurrently might make sense.  I use a tool called "Task Spooler" for batch queue management to keep systems busy, but not overloaded.  Tasks get submitted and only 1 is allowed to run at a time - it is usually multi-threaded tasks, so they peg all the cores already. I submit the tasks with a lower priority so interactive workloads aren't impacted, but the system stays busy.  A job is running now on a 6-core desktop:
```
$ uptime 
 09:01:02 up 2 days, 23:41,  5 users,  **load average: 10.70, 10.80, 8.48**

```
It is pretty busy now.

---

