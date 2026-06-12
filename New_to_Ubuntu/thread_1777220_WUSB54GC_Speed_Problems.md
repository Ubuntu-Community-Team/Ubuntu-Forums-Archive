---
title: "WUSB54GC Speed Problems"
date: 2011-06-07
forum: New to Ubuntu
---

### Post by Rivkah on 2011-06-07
I set-up my slightly older desktop right next to my current one and put Ubuntu 10.04 on it last night. I went to use Firefox on it, but it didn't seem to be working. So, this morning I go to get back on it, and I realize it is running EXTREMELY slow (Taking 30+ seconds to load just Google). Although, there is nothing wrong with my internet, while running multiple downloads and Online Games from multiple computers on my network my speed is: [LEFT][IMG]http://www.speedtest.net/result/1288909802.png[/IMG][/LEFT]. I downloaded Chromium (Which I was planning to use Chrome anyways, but the download isn't working or is just too slow) and it also performs at these extremely slow speeds. I did search around for this question but they all refer to using the ndiswrapper or RALink's drivers. The wireless card seemed to install fine right at install tho because, after it booted for the first time I only had to select my network! Thank you for any help before hand ;)
[Will check the thread frequently, although E3 is starting now..So will be on teh TV for a bit]

---

### Post by LowSky on 2011-06-07
Hi welcome to the forums.

If I go by just what I'm seeing from  speedtest.net rating your ping is pretty high but if your using wifi or doing a lot of streaming or downloading while running that test than its normal. Your internet speed is pretty fast, mine isn't half that for download and nearly 8 times slower for uploading. For example here is mine:

[IMG]http://www.speedtest.net/result/1330777181.png[/IMG]

However you could try a simple ping test
open terminal and use this command, and paste the results here

```
ping -c 5 www.google.com
```

for example again here are my results, you should see similar or better
```
ohn@mediacenter:~$ ping -c 5 www.google.com
PING www.l.google.com (74.125.93.99) 56(84) bytes of data.
64 bytes from qw-in-f99.1e100.net (74.125.93.99): icmp_req=1 ttl=53 time=25.6 ms
64 bytes from qw-in-f99.1e100.net (74.125.93.99): icmp_req=2 ttl=53 time=26.5 ms
64 bytes from qw-in-f99.1e100.net (74.125.93.99): icmp_req=3 ttl=53 time=25.6 ms
64 bytes from qw-in-f99.1e100.net (74.125.93.99): icmp_req=4 ttl=53 time=26.1 ms
64 bytes from qw-in-f99.1e100.net (74.125.93.99): icmp_req=5 ttl=53 time=25.7 ms

--- www.l.google.com ping statistics ---
5 packets transmitted, 5 received, 0% packet loss, time 4006ms
rtt min/avg/max/mdev = 25.617/25.959/26.594/0.424 ms

```

---

### Post by Rivkah on 2011-06-07
Well, that is from my main computer and yes it runs off of Wifi, it has a Linksys WMP54G v1 PCI-Card running off of vista. Here is the results of my secondary desktop (The one I loaded Ubuntu onto and is having major speed issues) with the ping command: [Typing it out, so excuse any typos]
```
code@code-destop:~$ ping -c 5 www.google.com
PING www.l.google.com (74.125.45.106) 56(84) bytes of data.
64 bytes from yx-in-f106.1e100.net (74.125.45.106): icmp_seq=1 ttl=52 time=110 ms
64 bytes from yx-in-f106.1e100.net (74.125.45.106): icmp_seq=2 ttl=52 time=403 ms
64 bytes from yx-in-f106.1e100.net (74.125.45.106): icmp_seq=3 ttl=52 time=624 ms
64 bytes from yx-in-f106.1e100.net (74.125.45.106): icmp_seq=4 ttl=52 time=93.2 ms
64 bytes from yx-in-f106.1e100.net (74.125.45.106): icmp_seq=5 ttl=52 time=16.6 ms

--- www.l.google.com ping statistics ---
5 packets transmitted, 5 received, 0% packet loss, time 10352ms
rtt min/avg/max/mdev = 16.665/249.725/624.928/229.218 ms

```
[Will upload what speedtest said from that computer once I finally can get to it, this is rediculous
EDIT: Looks like I won't get that speedtest anytime soon, Flash isn't on the Ubuntu desktop yet. Took 10 minutes just to load half the page and find that out!]

Ping results on my vista computer that also runs off Wifi and is what the first post's speedtest is from:
```
Pinging www.l.google.com [74.125.45.147] with 32 bytes of data:
Reply from 74.125.45.147: bytes=32 time=6ms TTL=52
Reply from 74.125.45.147: bytes=32 time=6ms TTL=52
Reply from 74.125.45.147: bytes=32 time=6ms TTL=52
Reply from 74.125.45.147: bytes=32 time=5ms TTL=52
Reply from 74.125.45.147: bytes=32 time=6ms TTL=52

Ping statistics for 74.125.45.147:
    Packets: Sent = 5, Received = 5, Lost = 0 (0% loss),
Approximate round trip times in milli-seconds:
    Minimum = 5ms, Maximum = 6ms, Average = 5ms
```

---

### Post by Rivkah on 2011-06-07
Ok, well I started looking around on Ubuntu finally and went to the Update Manager, then obviously pressed "Check". Well, it is currently downloading "Package Information" and is at 32/34. Figured I might say here that at first it was constantly failed, then continually said "hit" then failed a few times inbetween. Now, I have gotten an error message of: "Could not download all repository indexes".
```
Failed to fetch http://security.ubuntu.com/ubuntu/dists/lucid-security/universe/i18n/Translation-en_US.bz2 Connection failed [IP:91.189.92.167 80]

Some index files failed to download, they have been ignored, or old ones used instead.
```
Although the non "boxed" error states it could because network problems.

UPDATE: Ok, apparently the network speed is headed back north...The computer that was having speed issues is currently at:
[IMG]http://www.speedtest.net/result/1331198907.png[/IMG]
Don't know what the problem is, but going to mark this as resolved. Hopefully I don't have to come back to this thread!

---

