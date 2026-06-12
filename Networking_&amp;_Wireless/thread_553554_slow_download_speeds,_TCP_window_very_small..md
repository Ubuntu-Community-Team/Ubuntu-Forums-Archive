---
title: "slow download speeds, TCP window very small."
date: 2007-09-17
forum: Networking &amp; Wireless
---

### Post by adamc6 on 2007-09-17
Title says it......I have very slow download speeds and my TCP window is very small.   I have edited my rc.local with echo values and I have changed my sysctl.conf to include the temporary changes but still my TCP window size is still very small and bandwidth test show very slow download speed.  I need help, step by step newbie linux instructions to solve this problem.  Thank you.

TCP options string = 020405b40101040201030305
MTU = 1500
MTU is fully optimized for broadband.
MSS = 1460
Maximum useful data in each packet = 1460, which equals MSS.
Default TCP Receive Window (RWIN) = 5856
RWIN Scaling (RFC1323) = 5 bits (scale factor of 10)
Unscaled TCP Receive Window = 183

RWIN seems to be set to a very small number. If you're on a broadband connection, consider using a larger value.
For optimum performance, consider changing RWIN to a multiple of MSS.
Other RWIN values that might work well with your current MTU/MSS:
513920 (MSS x 44 * scale factor of 8)
256960 (MSS x 44 * scale factor of 4)
128480 (MSS x 44 * scale factor of 2)
 64240 (MSS x 44)
bandwidth * delay product (Note this is not a speed test):

Your TCP Window limits you to: 234 kbps (29 KBytes/s) @ 200ms
Your TCP Window limits you to: 94 kbps (12 KBytes/s) @ 500ms
Consider increasing your RWIN value to optimize TCP/IP for broadband.
MTU Discovery (RFC1191) = ON
Time to live left = 48 hops
TTL value is ok.
Timestamps (RFC1323) = OFF
Selective Acknowledgements (RFC2018) = ON
IP type of service field (RFC1349) = 00000000 (0)

---

### Post by nixfedex on 2007-09-17
What are you trying to download? what is the speed you are getting? Can you run mtr [www.ubuntuforums.org](www.ubuntuforums.org) for sometime and show the log file here, it might be helpful in debuging... The problem may not be on your side... Anyways in the mean time you can also read:
[http://www.psc.edu/networking/projects/tcptune/](http://www.psc.edu/networking/projects/tcptune/)

---

### Post by adamc6 on 2007-09-18
Normal download speeds vary from 600-1000 kB/s yes Bytes and now I average 95kB/s  speedtest.net shows download bandwidth 1500 kbps not the usual 8000 to 9000 I get. 




            My traceroute  [v0.71]
adam-laptop (0.0.0.0)                                  Mon Sep 17 22:59:03 2007
Keys:  Help   Display mode   Restart statistics   Order of fields   quit
                                       Packets               Pings
 Host                                Loss%   Snt   Last   Avg  Best  Wrst StDev
 1. 192.168.1.1                       0.0%    30    1.4   1.8   1.3  10.7   1.7
 2. 10.7.125.1                        0.0%    30   68.2  14.0   8.0  68.2  11.2
 3. 12-215-8-65.client.mchsi.com      0.0%    30   25.5  13.1   8.6  25.5   3.7
 4. 12-215-0-42.client.mchsi.com      0.0%    30   47.2  22.6  18.6  47.2   5.4
 5. tbr1.sl9mo.ip.att.net             0.0%    30   49.5  42.4  36.9  63.3   6.4
 6. tbr2.dlstx.ip.att.net             0.0%    29   37.1  40.1  33.2  78.2  10.1
 7. 12.122.86.209                     0.0%    29   38.7  50.4  35.0 193.1  35.6
 8. br2-a340s5.wswdc.ip.att.net       0.0%    29   38.3  39.5  35.8  52.7   4.1
 9. ae-2-56.bbr2.Dallas1.Level3.net   0.0%    29   73.0  39.4  32.9  91.9  12.8
10. as-0-0.bbr1.London2.Level3.net    0.0%    29  152.9 126.2 121.4 152.9   6.7
    ae-1-0.bbr2.London2.Level3.net
11. ae-25-52.car1.London2.Level3.net  0.0%    29  129.3 127.9 123.0 159.8   7.4
    ae-15-51.car1.London2.Level3.net
    ae-15-55.car1.London2.Level3.net
    ae-25-56.car1.London2.Level3.net
    ae-15-53.car1.London2.Level3.net
    ae-25-54.car1.London2.Level3.net
12. tge9-3-146.core-r-1.lon2.adaptpl  0.0%    29  124.0 133.1 121.9 312.0  34.9
13. 85.133.32.134                     0.0%    29  154.0 126.4 121.7 154.0   5.9

---

### Post by nixfedex on 2007-09-18
Looks like big delays in each hop. mtr is better because you can get the statistics over a period of time. 
Sometimes manually changing the tcp settings disables the tcp autotuning. Make sure its enabled and test again.

---

### Post by adamc6 on 2007-09-20
I am getting the same numbers as before.  Download speeds start slow speed up a little but are still significantly lower than normal.  Is there a way to reset the autotuning perhaps reinstall drivers?

---

### Post by adamc6 on 2007-10-23
I have had the problem fixed then I messed up my update to 7.10 and now I have a fresh install.  I am encountering the problem once again and I forget how to fix it.  I do remember that I changed the values but I don't know which ones.

Does anyone know the solution?  Honestly this is ubuntu.

---

