---
title: "Download speed from Japan slow (many ISP's affected)"
date: 2016-10-28
forum: Networking &amp; Wireless
---

### Post by intel7tsuda99aaa on 2016-10-28
**_Update_**
The connection to Ubuntu main servers (ip starting with 91.189...) from Japan is very unreliable. My usual download speed from the main server was 5-12MiB/s, but recently it is often 20-250KiB/s. I thought that this was a problem with my isp, but it is a problem with many other ISP's (possibly a problem for all of Japan).

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
-Download speed is slow (20-250KiB/s) for about 70% of the day (decreased to about 40% of the day as of 2016.11.20). The rest of the day is normal (5-12MiB/s). When speed is fast or slow seems to be random.

---------------------------------------------------------------------------

**_Original post_**
[SIZE=1]Recently my download speed from Ubuntu servers (ip starting with 91.189...) is very slow (wired connection).

Previously (July 2016) my normal speed from the main server was 5-12MiB/s (from updates and from cdimage) but recently (from September 2016) I often only get 20KiB/s-200KiB/s. Sometimes it goes back up to my previous normal speed (5-12MiB/s) but this usually does not last long (1-10 minutes at a time). Whether my download is fast or slow seems to be completely random. This slow speed applies to any download from ubuntu including cdimage, synaptic, and update manager (they all connect to ip 91.189...).

I consistently get 9-15MiB/s from cdimage.debian.org and 50MiB/s from iso and update mirrors in Japan, so I think it is probably not a problem with my internet. I live in Tokyo Japan and have a gigabit connection. 

-disabling ipv6 does not help
-I have a skylake i5 6600 cpu. Switching motherboard (msi to gigabyte h170) did not help. Both motherboards use Intel i219v LAN adapter.
-the computer I used in July was a haswell desktop, it is broken so I cannot test it. I bought the skylake desktop in September.
-Buying a new router did not help
-this problem persists in 16.04 and 16.10
-I do not know exactly when this started because I did not use the internet between July and September 2016[/SIZE]

---

### Post by QIII on 2016-10-28
Hello!

Just use a mirror where you are getting better speed.  If the slow speed is consistent across platforms and your speed from other sites is consistently faster, then the problem is likely the size of the pipe and the amount of traffic on the main repo.

No matter the capability of the connection on your end, if there is only a trickle left at the source than a trickle is what you will get.

Cheers!

---

### Post by intel7tsuda99aaa on 2016-10-28
Thank you for the reply QIII. It is true that I could simply use a mirror, but I would really like to diagnose why I suddenly have this problem now when it was not a problem in the past.

The only remaining possibilities I can think of are faulty cpu or my isp changed routing to wherever the main server is located. 

I would completely be willing to change either of these to be able to download from cdimage at my previous normal speed

---

### Post by QIII on 2016-10-29
Hello.

It is extremely unlikely that it has anything at all with your CPU.  Your ISP does not dictate the route packets take outside of their own hardware perimeter.

Again:  The most likely source of the issue is one of traffic/capacity on the far end beyond where you can troubleshoot and affect a change.

---

### Post by intel7tsuda99aaa on 2016-11-20
This is still a problem with multiple ISPs as of 2016.11.20. The % of the day where download speed is slow has decreased (speed is slow for about 40% of the day now)

---

