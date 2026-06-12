---
title: "Either no Internet or extremely slow, ping works fine"
date: 2008-09-07
forum: Networking &amp; Wireless
---

### Post by JoshHendo on 2008-09-07
Hi everyone,

I have had a look around, and it appears that heaps of other people have been having similar problems to mine, but I can't seem to find an one solution that works.

Basically, today websites stopped working in Firefox, Pidging stopped working etc. Ping still worked though, and internet works fine in WinXP with a VirtualBox. I find this rather strange.

It all seemed to start happening when I tried to access my router via the url "dsldevice.lan". I don't know why, but it seemed to. From what I have read, it also seemes to have something to do with ipv6 or something like that (I use 4).

Sometimes though I am able to get internet access, but it is extremely slow. It isn't slow as in the page slowly loads over time, it is slow where it takes forever to start loading (a few minutes), and then it finally loads all in one go. I did a traceroute of google.com and it came back the following:

```

josh@Scruffy:~$ traceroute google.com
traceroute to google.com (64.233.167.99), 30 hops max, 40 byte packets
 1  192.168.0.1 (192.168.0.1)  0.350 ms  0.410 ms  0.519 ms
 2  speedtouch.lan (192.168.1.254)  97.894 ms  97.557 ms  96.989 ms
 3  lo0.core-r1.nsw01.dataco.com.au (202.63.35.1)  18.720 ms  23.529 ms  28.758 ms
 4  core0.syd.dft.com.au (202.76.170.242)  34.080 ms  39.555 ms  54.082 ms
 5  59.154.21.221 (59.154.21.221)  59.007 ms  64.206 ms  69.089 ms
 6  203.208.169.58 (203.208.169.58)  224.120 ms  166.928 ms  167.615 ms
 7  216.239.46.180 (216.239.46.180)  173.212 ms 216.239.46.182 (216.239.46.182)  178.642 ms 216.239.46.180 (216.239.46.180)  183.018 ms
 8  209.85.253.178 (209.85.253.178)  198.480 ms 216.239.43.144 (216.239.43.144)  204.634 ms 209.85.253.178 (209.85.253.178)  209.000 ms
 9  209.85.243.123 (209.85.243.123)  212.057 ms  217.845 ms  222.989 ms
10  209.85.242.210 (209.85.242.210)  257.474 ms  282.451 ms  283.799 ms
11  209.85.243.116 (209.85.243.116)  280.797 ms  285.673 ms  288.933 ms
12  209.85.241.20 (209.85.241.20)  235.785 ms  217.270 ms  215.641 ms
13  209.85.241.23 (209.85.241.23)  228.801 ms  235.092 ms  240.296 ms
14  66.249.94.132 (66.249.94.132)  246.689 ms 66.249.94.134 (66.249.94.134)  253.312 ms 66.249.94.132 (66.249.94.132)  256.680 ms
15  64.233.175.42 (64.233.175.42)  261.613 ms 64.233.175.26 (64.233.175.26)  275.657 ms 64.233.175.42 (64.233.175.42)  276.575 ms
16  py-in-f99.google.com (64.233.167.99)  274.626 ms  283.776 ms  284.547 ms

```

This in itself took a few minutes to do. Again, ping works fine, and Internet in a VirtualBox works GREAT.

I know heaps of other people have had this problem, so sorry for posting again, but I couldn't seem to find a fix going through all the threads.

Thanks, Josh.

---

### Post by superprash2003 on 2008-09-07
changing your DNS servers to opendns servers may help.Their ips are 208.67.222.222 and 208.67.220.220

---

