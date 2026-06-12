---
title: "Download speed from Japan slow (many ISP's affected)"
date: 2016-10-30
forum: Networking &amp; Wireless
---

### Post by intel7tsuda99aaa on 2016-10-30
Recently the connection to Ubuntu main servers (ip starting with 91.189...) from Japan is very unreliable. My usual download speed from the main server was 5-12MiB/s, but recently it is often 20-250KiB/s. I thought that this was a problem with my isp, but it is a problem with many other ISP's (possibly a problem for all of Japan). 

Tested ISP's:
-OCN [Open Computer Network] (tested @ computer store 122.26.185.19x) [http://www.ocn.ne.jp/](http://www.ocn.ne.jp/)
-So-Net [Sony Network Communications] (tested @ internet cafe 118.238.212.x and
Dell store 59.147.202.24x) [http://www.so-net.ne.jp/](http://www.so-net.ne.jp/)
-iij (tested @ 2 computer stores and home connection) [https://www.iijmio.jp/](https://www.iijmio.jp/)
-@T-COM (tested @ internet cafe) [http://www.t-com.ne.jp/](http://www.t-com.ne.jp/)

-probably more ISP's are affected, I only listed the ones that I tested (100% of which are affected)
-I also tested download speed from cdimage.debian (always ~14MiB/s) and [http://ftp.riken.jp/](http://ftp.riken.jp/) (always ~50MiB/s). This shows that the problem is limited to the Ubuntu servers.
-all types of downloads to Ubuntu servers (apt-get, update, synaptic, cdimage etc...) are affected
-This problem started some time between July 2016 and September 2016
-Download speed is slow (20-250KiB/s) for about 70% of the day. 30% of the day is normal (5-12MiB/s). When speed is fast or slow seems to be random.
-(at times when speed is slow) sometimes canceling and restarting a download over and over again will eventually get a fast connection (5-12MiB/s). This only works occasionally. 

-Does anyone know why this is suddenly a problem?
-Who should I contact to fix this problem?

---

### Post by QIII on 2016-10-30
Duplicate of [https://ubuntuforums.org/showthread.php?t=2341420](https://ubuntuforums.org/showthread.php?t=2341420)

Closed.

---

