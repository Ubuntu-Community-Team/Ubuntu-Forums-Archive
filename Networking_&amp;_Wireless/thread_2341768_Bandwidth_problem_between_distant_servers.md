---
title: "Bandwidth problem between distant servers"
date: 2016-10-31
forum: Networking &amp; Wireless
---

### Post by faroutliving on 2016-10-31
For a long time we have had fiber + microwave feeding a server in the Florida swamp. We could get data copied to/from our server in Boston at top speed of the microwave (approx 250mbps). Then something happened and speeds dropped off from like noon to midnight. Dropped to like 3-8 mbps! That is a big drop off! Nothing running on our servers that we know of that is time sensitive like that. AT&T in Florida checked out their fiber and swore it was working better than guaranteed rates of 250mbps, and a guy jacked into _our_ router there could see the same fast speed while the server using iPerf3 back up to Boston would see only 4-5mbps. Management said we were finally getting new fiber in to the Swamp directly and dropping the microwave (takes a lot of red tape cutting evidently) and didn't want me trying to solve the problem. Well they installed that new fiber Friday. Of course, I warned them that it could have absolutely nothing to do with that and the switch to new fiber provider may not fix a thing. Indeed, it did not. In fact, it seems that we have a not as slow connection now around 30-90mbps, but still not the 1gbps that both facilities now have and not the 250mbps we once had. Actualy scp copies from Boston to Swamp are running about 120mbps (not sure why it would be faster but still slower than it should be).

What is strange, is that iperf3 to iperf.scottlinux.com (3rd party in California with 1gbps connection?) shows 260+mbps from either location, but iperf3 -R to iperf.scottlinux.com shows 20-40mbps from the swamp and 100-120 mbps to Boston.

Now, I never checked rates to iperf.scottlinux.com before. We had our theoretical max from Swamp to Boston and everyone was happy so I can't say what problems started when but if someone could either direct me to some place that would help tune this up or give me some suggestions it would be much appreciated.

Thanks,
Deron

Just in case the iperf3 output helps here is some:

Swamp connecting to Boston server:
```
iperf3 -c 104.129.77.106
Connecting to host 104.129.77.106, port 5201
[ 4] local 170.55.19.154 port 46930 connected to 104.129.77.106 port 5201
[ ID] Interval Transfer Bandwidth Retr Cwnd
[ 4] 0.00-1.00 sec 32.0 MBytes 269 Mbits/sec 4 1.21 MBytes
[ 4] 1.00-2.00 sec 17.5 MBytes 147 Mbits/sec 3 393 KBytes
[ 4] 2.00-3.00 sec 8.75 MBytes 73.4 Mbits/sec 0 430 KBytes
[ 4] 3.00-4.00 sec 8.75 MBytes 73.4 Mbits/sec 1 331 KBytes
[ 4] 4.00-5.00 sec 7.50 MBytes 62.9 Mbits/sec 0 352 KBytes
[ 4] 5.00-6.00 sec 7.50 MBytes 62.9 Mbits/sec 1 270 KBytes
[ 4] 6.00-7.00 sec 5.00 MBytes 41.9 Mbits/sec 1 211 KBytes
[ 4] 7.00-8.00 sec 6.25 MBytes 52.4 Mbits/sec 0 226 KBytes
[ 4] 8.00-9.00 sec 5.00 MBytes 41.9 Mbits/sec 1 174 KBytes
[ 4] 9.00-10.00 sec 3.75 MBytes 31.5 Mbits/sec 0 189 KBytes
- - - - - - - - - - - - - - - - - - - - - - - - -
[ ID] Interval Transfer Bandwidth Retr
[ 4] 0.00-10.00 sec 102 MBytes 85.6 Mbits/sec 11 sender
[ 4] 0.00-10.00 sec 94.0 MBytes 78.8 Mbits/sec receiver


iperf3 -c 104.129.77.106 -R
Connecting to host 104.129.77.106, port 5201
Reverse mode, remote host 104.129.77.106 is sending
[ 4] local 170.55.19.154 port 46934 connected to 104.129.77.106 port 5201
[ ID] Interval Transfer Bandwidth
[ 4] 0.00-1.00 sec 6.32 MBytes 53.0 Mbits/sec
[ 4] 1.00-2.00 sec 8.32 MBytes 69.8 Mbits/sec
[ 4] 2.00-3.00 sec 8.43 MBytes 70.7 Mbits/sec
[ 4] 3.00-4.00 sec 9.00 MBytes 75.5 Mbits/sec
[ 4] 4.00-5.00 sec 9.29 MBytes 77.9 Mbits/sec
[ 4] 5.00-6.00 sec 9.35 MBytes 78.4 Mbits/sec
[ 4] 6.00-7.00 sec 10.2 MBytes 85.4 Mbits/sec
[ 4] 7.00-8.00 sec 10.6 MBytes 88.8 Mbits/sec
[ 4] 8.00-9.00 sec 10.7 MBytes 89.8 Mbits/sec
[ 4] 9.00-10.00 sec 11.5 MBytes 96.8 Mbits/sec
- - - - - - - - - - - - - - - - - - - - - - - - -
[ ID] Interval Transfer Bandwidth Retr
[ 4] 0.00-10.00 sec 96.6 MBytes 81.0 Mbits/sec 285 sender
[ 4] 0.00-10.00 sec 94.2 MBytes 79.0 Mbits/sec receiver

```

In Swamp connecting to 3rd Party in California:
```
iperf3 -c iperf.scottlinux.com
Connecting to host iperf.scottlinux.com, port 5201
[ 4] local 170.55.19.154 port 35618 connected to 45.33.39.39 port 5201
[ ID] Interval Transfer Bandwidth Retr Cwnd
[ 4] 0.00-1.00 sec 20.9 MBytes 175 Mbits/sec 7 6.01 MBytes
[ 4] 1.00-2.00 sec 37.5 MBytes 315 Mbits/sec 0 6.01 MBytes
[ 4] 2.00-3.00 sec 35.0 MBytes 294 Mbits/sec 2 6.01 MBytes
[ 4] 3.00-4.00 sec 36.2 MBytes 304 Mbits/sec 2 6.01 MBytes
[ 4] 4.00-5.00 sec 36.2 MBytes 304 Mbits/sec 1 6.01 MBytes
[ 4] 5.00-6.00 sec 35.0 MBytes 294 Mbits/sec 0 6.01 MBytes
[ 4] 6.00-7.00 sec 36.2 MBytes 304 Mbits/sec 0 6.01 MBytes
[ 4] 7.00-8.00 sec 37.5 MBytes 315 Mbits/sec 0 6.01 MBytes
[ 4] 8.00-9.00 sec 35.0 MBytes 294 Mbits/sec 0 6.01 MBytes
[ 4] 9.00-10.00 sec 37.5 MBytes 315 Mbits/sec 0 6.01 MBytes
- - - - - - - - - - - - - - - - - - - - - - - - -
[ ID] Interval Transfer Bandwidth Retr
[ 4] 0.00-10.00 sec 347 MBytes 291 Mbits/sec 12 sender
[ 4] 0.00-10.00 sec 339 MBytes 284 Mbits/sec receiver

iperf3 -c iperf.scottlinux.com -R
Connecting to host iperf.scottlinux.com, port 5201
Reverse mode, remote host iperf.scottlinux.com is sending
[ 4] local 170.55.19.154 port 35614 connected to 45.33.39.39 port 5201
[ ID] Interval Transfer Bandwidth
[ 4] 0.00-1.00 sec 2.32 MBytes 19.5 Mbits/sec
[ 4] 1.00-2.00 sec 2.23 MBytes 18.7 Mbits/sec
[ 4] 2.00-3.00 sec 2.39 MBytes 20.1 Mbits/sec
[ 4] 3.00-4.00 sec 2.49 MBytes 20.9 Mbits/sec
[ 4] 4.00-5.00 sec 2.51 MBytes 21.1 Mbits/sec
[ 4] 5.00-6.00 sec 2.73 MBytes 22.9 Mbits/sec
[ 4] 6.00-7.00 sec 2.62 MBytes 22.0 Mbits/sec
[ 4] 7.00-8.00 sec 2.75 MBytes 23.1 Mbits/sec
[ 4] 8.00-9.00 sec 2.84 MBytes 23.8 Mbits/sec
[ 4] 9.00-10.00 sec 3.24 MBytes 27.2 Mbits/sec
- - - - - - - - - - - - - - - - - - - - - - - - -
[ ID] Interval Transfer Bandwidth Retr
[ 4] 0.00-10.00 sec 27.0 MBytes 22.7 Mbits/sec 53 sender
[ 4] 0.00-10.00 sec 26.5 MBytes 22.2 Mbits/sec receiver

```

In Boston connecting to 3rd Party in California:
```
iperf3 -c iperf.scottlinux.com
Connecting to host iperf.scottlinux.com, port 5201
[ 4] local 104.129.77.106 port 40168 connected to 45.33.39.39 port 5201
[ ID] Interval Transfer Bandwidth Retr Cwnd
[ 4] 0.00-1.00 sec 25.2 MBytes 211 Mbits/sec 222 4.31 MBytes
[ 4] 1.00-2.00 sec 36.2 MBytes 304 Mbits/sec 0 4.31 MBytes
[ 4] 2.00-3.00 sec 41.2 MBytes 346 Mbits/sec 0 4.31 MBytes
[ 4] 3.00-4.00 sec 38.8 MBytes 325 Mbits/sec 0 4.31 MBytes
[ 4] 4.00-5.00 sec 41.2 MBytes 346 Mbits/sec 0 4.31 MBytes
[ 4] 5.00-6.00 sec 38.8 MBytes 325 Mbits/sec 0 4.31 MBytes
[ 4] 6.00-7.00 sec 42.5 MBytes 357 Mbits/sec 0 4.31 MBytes
[ 4] 7.00-8.00 sec 38.8 MBytes 325 Mbits/sec 0 4.31 MBytes
[ 4] 8.00-9.00 sec 40.0 MBytes 336 Mbits/sec 0 4.31 MBytes
[ 4] 9.00-10.00 sec 40.0 MBytes 336 Mbits/sec 0 4.31 MBytes
- - - - - - - - - - - - - - - - - - - - - - - - -
[ ID] Interval Transfer Bandwidth Retr
[ 4] 0.00-10.00 sec 383 MBytes 321 Mbits/sec 222 sender
[ 4] 0.00-10.00 sec 373 MBytes 313 Mbits/sec receiver

iperf3 -c iperf.scottlinux.com -R
Connecting to host iperf.scottlinux.com, port 5201
Reverse mode, remote host iperf.scottlinux.com is sending
[ 4] local 104.129.77.106 port 39930 connected to 45.33.39.39 port 5201
[ ID] Interval Transfer Bandwidth
[ 4] 0.00-1.00 sec 6.23 MBytes 52.3 Mbits/sec
[ 4] 1.00-2.00 sec 7.09 MBytes 59.5 Mbits/sec
[ 4] 2.00-3.00 sec 7.25 MBytes 60.8 Mbits/sec
[ 4] 3.00-4.00 sec 6.64 MBytes 55.7 Mbits/sec
[ 4] 4.00-5.00 sec 6.34 MBytes 53.1 Mbits/sec
[ 4] 5.00-6.00 sec 6.53 MBytes 54.8 Mbits/sec
[ 4] 6.00-7.00 sec 6.95 MBytes 58.3 Mbits/sec
[ 4] 7.00-8.00 sec 7.21 MBytes 60.4 Mbits/sec
[ 4] 8.00-9.00 sec 7.11 MBytes 59.7 Mbits/sec
[ 4] 9.00-10.00 sec 5.56 MBytes 46.7 Mbits/sec
- - - - - - - - - - - - - - - - - - - - - - - - -
[ ID] Interval Transfer Bandwidth Retr
[ 4] 0.00-10.00 sec 68.7 MBytes 57.6 Mbits/sec 18 sender
[ 4] 0.00-10.00 sec 67.4 MBytes 56.5 Mbits/sec receiver

```

---

### Post by TheFu on 2016-10-31
Are the microwave links still aligned and unobstructed?  
No nests or leaves in the way?  
Are the antennas clean - dirt and dust removed?  
Have the antennas been recoated with hydrophobic spay in the last year? 
Sometimes wireless devices wear out. The good news is that high speed wireless connections have never been cheaper for LOS deployments 10-150+ miles are very possible these days. 
[https://www.ubnt.com/products/](https://www.ubnt.com/products/) for $1000 - $7000, it is amazing what is possible today - that's 500Mbps to 2Gbps links.

---

### Post by faroutliving on 2016-10-31
Hello TheFu,

Guess I was not clear. This problem is with a direct fiber connection, no microwave in use now. Also, I could test across the microwave link and that was never the problem.

Thanks for trying!
Deron

---

### Post by TheFu on 2016-10-31
Ah ... I didn't read it that way.  Thought there was a fibre link to a microwave station that used a microwave link to the site.  Also thought the old fibre link had been replaced with newer fibre and the microwave was still in used. Sorry.

If you want to find the slow parts of a network, it comes down to 
a) simplify and test
b) redo "a" until the problem becomes clear.

So ... check the performance of every leg of the connection.  computer to switch, switch to router, router to the next link. all along the line between the different systems involved.  I'd use traceroute to see the slowest parts of the network links.  iperf doesn't reflect real-world transfer performance, BTW. It is useful as a comparison, but not for actual transfer speeds using real files and real protocols.

I'm completely confused by the scottlinux.com use.  Why is that being used?

So, make a list of all the links and start testing.  Start with 1 hop. Then the next hop. Then the next. Keep it simple.

Sometimes links are in parts of a network that we don't own/control.  Sometimes really odd routing is happening for unknown reasons -  [http://research.dyn.com/2013/11/mitm-internet-hijacking/](http://research.dyn.com/2013/11/mitm-internet-hijacking/)

---

### Post by faroutliving on 2016-10-31
I can see how I was not clear. Sorry about that. It made perfect sense to me :-)

The  current test from Swamp to Boston is as direct as I can go. The Swamp  is copper connected directly to a Florida Power and Light switch, and  Boston is fiber connected directly to a Lightower switch. No other  devices are connected to these service provider switches, though the servers on both ends have a switch on a  different port that everything in those facilities are connected to. Withing those facilities in the Swamp and Boston, copies from these devices on the switch happen at or near theoretical maximum. I  included the test to socttlinux.com to show that both machines can  obtain at least 3x faster speeds with someone else if if that speed is still less than a third of maximum.

Not sure how  traceroute would help either. Ping times from Swamp to scottlinux.com is  2x slower than to Boston, yet transfers is 3x faster. Is there some  mode with Traceroute that elicits more info? Or are you supposing that routing has gone crazy? Looking at it (results below) it seems like the route between Boston and Swamp is logical, and better than the route from either to California.

I have included  speeds for real world copying. I am getting about 120 mbps (roughly 1.5x  iperf3 indicates speeds) from Boston to Swamp, but both Florida Power  and Light and Lightower claim 1gbps minimum speeds.

Thanks for your help,
Deron

Traceroute from Boston to Swamp
```
traceroute --resolve-hostname 170.55.19.154
traceroute to 170.55.19.154 (170.55.19.154), 64 hops max
  1   104.129.77.105 (104.129.77.105.lightower.net)  0.290ms  2.744ms  4.167ms 
  2   64.72.64.113 (ae2-bstpmallj42.lightower.net)  0.271ms  0.274ms  0.186ms 
  3   4.53.56.181 (5-1-32.bear2.Boston1.Level3.net)  5.970ms  6.444ms  5.901ms 
  4   4.69.150.161 (ae-2-3513.edge1.Atlanta4.Level3.net)  23.590ms  23.601ms  54.599ms 
  5   4.53.236.46 (FPL-FIBERNE.edge1.Atlanta4.Level3.net)  23.368ms  23.369ms  41.593ms 
  6   208.67.164.74 (m1049-atl-10ge-lag-1.fplfn.net)  23.582ms  23.612ms  23.625ms 
  7   208.67.165.102 (m1049-jax-10ge-1-1-2.fplfn.net)  29.642ms  30.266ms  29.566ms 
  8   208.67.165.121 (m1049-orlw-10ge-1-1-5.fplfn.net)  39.354ms  39.387ms  39.537ms 
  9   208.67.167.94 (m1049-ftl2a-20ge-lag-199.fplfn.net)  39.384ms  39.434ms  39.316ms 
 10   208.67.167.85 (m1049-cse-10ge-1-1-2.fplfn.net)  40.173ms  40.047ms  40.250ms 
 11   208.67.164.37 (208.67.164.37)  40.135ms  40.073ms  40.003ms 

```

Traceroute from Swamp to Boston
```
traceroute --resolve-hostnames 104.129.77.106
traceroute to 104.129.77.106 (104.129.77.106), 64 hops max
  1   170.55.19.153 (170.55.19.153)  1.053ms  0.991ms  0.946ms 
  2   208.67.164.194 (m1049-dlls-10ge-10-1-5.fplfn.net)  3.224ms  3.228ms  3.325ms 
  3   198.32.124.176 (nota.he.net)  3.310ms  5.105ms  3.326ms 
  4   184.105.213.25 (100ge11-1.core1.atl1.he.net)  17.453ms  24.032ms  25.101ms 
  5   184.105.213.70 (100ge11-1.core1.ash1.he.net)  34.688ms  145.920ms  36.827ms 
  6   184.105.223.166 (100ge3-1.core1.nyc4.he.net)  35.025ms  34.610ms  44.862ms 
  7   184.105.213.218 (10ge4-1.core1.nyc5.he.net)  34.628ms  41.029ms  34.529ms 
  8   216.66.50.106 (lightower-fiber-networks.10gigabitethernet3-2.core1.nyc5.he.net)  34.718ms  34.682ms  34.708ms 
  9   64.72.64.110 (ae12-nycmnyzrj91.lightower.net)  35.023ms  34.723ms  34.745ms 
 10   104.207.214.100 (ae11-washdc12j41.lightower.net)  35.660ms  35.655ms  35.635ms 
 11   104.207.214.103 (ae6-prvdrinwj41.lightower.net)  40.282ms  40.669ms  40.319ms 
 12   104.207.214.80 (ae28-bstpmallj91.lightower.net)  40.310ms  40.333ms  40.340ms 

```


Traceroute from Boston to scottlinux.com (California)
```
traceroute --resolve-hostnames iperf.scottlinux.com
traceroute to iperf.scottlinux.com (45.33.39.39), 64 hops max
  1   104.129.77.105 (104.129.77.105.lightower.net)  0.244ms  0.236ms  0.219ms 
  2   64.72.64.113 (ae2-bstpmallj42.lightower.net)  0.223ms  0.207ms  0.233ms 
  3   38.140.12.73 (be4157.ccr22.bos01.atlas.cogentco.com)  0.747ms  0.798ms  0.754ms 
  4   154.54.43.14 (be2302.ccr22.alb02.atlas.cogentco.com)  4.383ms  5.799ms  4.512ms 
  5   154.54.29.173 (be2879.ccr22.cle04.atlas.cogentco.com)  15.737ms  15.413ms  15.852ms 
  6   154.54.7.129 (be2718.ccr42.ord01.atlas.cogentco.com)  23.366ms  23.535ms  23.285ms 
  7   154.54.44.169 (be2832.ccr22.mci01.atlas.cogentco.com)  36.000ms  35.929ms  36.056ms 
  8   154.54.31.89 (be3036.ccr22.den01.atlas.cogentco.com)  46.380ms  46.569ms  46.698ms 
  9   154.54.42.97 (be3038.ccr21.slc01.atlas.cogentco.com)  58.184ms  58.550ms  58.149ms 
 10   154.54.3.185 (be2086.ccr21.sfo01.atlas.cogentco.com)  72.092ms  71.933ms  71.994ms 
 11   154.54.28.34 (be2164.ccr21.sjc01.atlas.cogentco.com)  74.892ms  74.855ms  74.885ms 
 12   154.54.3.138 (be2095.rcr21.b001848-1.sjc01.atlas.cogentco.com)  74.201ms  74.281ms  74.214ms 
 13   204.68.252.106 (204.68.252.106)  76.815ms  76.765ms  76.682ms 
 14   173.230.159.1 (173.230.159.1)  76.539ms  76.559ms  76.575ms 

```

Traceroute from Swamp to scottlinux.com (California)
```
traceroute --resolve-hostnames iperf.scottlinux.com
traceroute to iperf.scottlinux.com (45.33.39.39), 64 hops max
  1   170.55.19.153 (170.55.19.153)  0.989ms  0.976ms  0.943ms 
  2   208.67.164.194 (m1049-dlls-10ge-10-1-5.fplfn.net)  3.235ms  3.242ms  3.232ms 
  3   206.41.108.23 (206.41.108.23)  3.321ms  6.584ms  3.356ms 
  4   184.105.213.25 (100ge11-1.core1.atl1.he.net)  17.527ms  17.588ms  17.522ms 
  5   184.105.81.170 (100ge12-1.core1.dal1.he.net)  95.334ms  49.288ms  73.370ms 
  6   72.52.92.153 (10ge9-1.core3.fmt2.he.net)  81.642ms  201.133ms  89.951ms 
  7   173.230.159.1 (173.230.159.1)  83.483ms  83.468ms  83.530ms 

```

---

### Post by TheFu on 2016-10-31
Do the log files have any data?
Can you try using scp to localhost? Any unexpected performance issues?  What about to other systems on the LAN?

Does increasing the scp verbosity provide any clues?  What about transfers over https or sftp?

---

