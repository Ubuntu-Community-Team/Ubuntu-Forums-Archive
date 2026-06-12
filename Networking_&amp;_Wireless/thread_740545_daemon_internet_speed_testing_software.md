---
title: "daemon internet speed testing software"
date: 2008-03-30
forum: Networking &amp; Wireless
---

### Post by net4home on 2008-03-30
I have been looking for a program that will test and graph my internet download / upload speeds but all I can find are programs for clients and nothing for servers / firewalls.  I did find the myspeed software but for the price for the server software is to steep for a home network.

I have Charter 10MB Cable Internet, but my connection will bounce between 95k to over 10MB.  My upload speed is pretty constant right around 900Kb or better so I can't complain about that.  I have had several technicians out and they keep telling me every thing is fine, but they can't tell me why my speed bounces so much.  I'm sick of paying for something I'm not getting and want to monitor and graph it so I can show them idiots what's going on.

I'm currently monitoring my internet with smokeping and that is giving me the latency, but I would like to be able to graph the upload and download speeds I'm getting.  Has anyone out there come across any software like this?

Thanks
Kevin

---

### Post by sonofusion82 on 2008-03-30
perhaps you can try iperf: [http://dast.nlanr.net/Projects/Iperf/](http://dast.nlanr.net/Projects/Iperf/)

---

### Post by net4home on 2008-03-31
Thanks, I tried that last night.  Looks like it would work, but I need to have either a client or a public server on the Internet to do the testing with.  I've been reading the limited documentation on iperf but I have not yet found a way to use it with any thing on the Internet.  

Can you tell me am I missing something?  

Thanks
Kevin

---

### Post by net4home on 2008-04-07
So far the only reply I've had for a daemon has been to use Iperf.  One problem with that is you need to control both ends, unless I'm just not reading it right to figure it out.  But I have found a tool that works wonders.  It's not a daemon but you can run it when you need to.  It is called "Bing".  It works when you only are able to control one side of the test.  Thought I'd update this post for those who are searching for the same thing as I was.

This is what the output looks like from my Charter.net 10MB Internet line

~$ sudo bing -z -d -P -i 8 -p ff 10.200.100.1 [www.charter.net](www.charter.net)
BING    10.200.100.1 (10.200.100.1) and [www.charter.net](www.charter.net) (64.192.190.12)
        44 and 108 data bytes (1024 bits)
[www.charter.net:](www.charter.net:) minimum delay difference is zero, can't estimate link throughput
[www.charter.net:](www.charter.net:) minimum delay difference is zero, can't estimate link throughput
[www.charter.net:](www.charter.net:) minimum delay difference is zero, can't estimate link throughput
[www.charter.net:](www.charter.net:)  4.571Mbps 0.224ms 0.218750us/bit
[www.charter.net:](www.charter.net:)  5.306Mbps 0.193ms 0.188477us/bit
[www.charter.net:](www.charter.net:)  5.565Mbps 0.184ms 0.179687us/bit
[www.charter.net:](www.charter.net:)  1.943Mbps 0.527ms 0.514648us/bit
[www.charter.net:](www.charter.net:)  1.943Mbps 0.527ms 0.514648us/bit
[www.charter.net:](www.charter.net:)  1.943Mbps 0.527ms 0.514648us/bit
[www.charter.net:](www.charter.net:)  1.872Mbps 0.547ms 0.534180us/bit
[www.charter.net:](www.charter.net:)  1.320Mbps 0.776ms 0.757812us/bit
[www.charter.net:](www.charter.net:)  1.320Mbps 0.776ms 0.757812us/bit
[www.charter.net:](www.charter.net:)  1.320Mbps 0.776ms 0.757812us/bit
[www.charter.net:](www.charter.net:)  1.320Mbps 0.776ms 0.757812us/bit
[www.charter.net:](www.charter.net:)  1.320Mbps 0.776ms 0.757812us/bit
[www.charter.net:](www.charter.net:)  1.320Mbps 0.776ms 0.757812us/bit
[www.charter.net:](www.charter.net:)  1.316Mbps 0.778ms 0.759766us/bit
[www.charter.net:](www.charter.net:)  1.316Mbps 0.778ms 0.759766us/bit
[www.charter.net:](www.charter.net:)  1.316Mbps 0.778ms 0.759766us/bit
[www.charter.net:](www.charter.net:)  1.316Mbps 0.778ms 0.759766us/bit
[www.charter.net:](www.charter.net:)  1.316Mbps 0.778ms 0.759766us/bit
[www.charter.net:](www.charter.net:)  1.316Mbps 0.778ms 0.759766us/bit
[www.charter.net:](www.charter.net:)  1.316Mbps 0.778ms 0.759766us/bit
[www.charter.net:](www.charter.net:)  1.316Mbps 0.778ms 0.759766us/bit
[www.charter.net:](www.charter.net:)  1.316Mbps 0.778ms 0.759766us/bit
[www.charter.net:](www.charter.net:)  1.316Mbps 0.778ms 0.759766us/bit
[www.charter.net:](www.charter.net:)  1.316Mbps 0.778ms 0.759766us/bit
[www.charter.net:](www.charter.net:)  1.316Mbps 0.778ms 0.759766us/bit
[www.charter.net:](www.charter.net:)  1.316Mbps 0.778ms 0.759766us/bit
[www.charter.net:](www.charter.net:)  1.316Mbps 0.778ms 0.759766us/bit
[www.charter.net:](www.charter.net:)  1.316Mbps 0.778ms 0.759766us/bit
[www.charter.net:](www.charter.net:)  1.316Mbps 0.778ms 0.759766us/bit
[www.charter.net:](www.charter.net:)  1.316Mbps 0.778ms 0.759766us/bit
[www.charter.net:](www.charter.net:)  1.316Mbps 0.778ms 0.759766us/bit
[www.charter.net:](www.charter.net:)  1.316Mbps 0.778ms 0.759766us/bit
[www.charter.net:](www.charter.net:)  1.316Mbps 0.778ms 0.759766us/bit
[www.charter.net:](www.charter.net:)  1.316Mbps 0.778ms 0.759766us/bit
[www.charter.net:](www.charter.net:)  1.316Mbps 0.778ms 0.759766us/bit
[www.charter.net:](www.charter.net:)  1.316Mbps 0.778ms 0.759766us/bit
[www.charter.net:](www.charter.net:)  1.316Mbps 0.778ms 0.759766us/bit
[www.charter.net:](www.charter.net:)  1.316Mbps 0.778ms 0.759766us/bit
[www.charter.net:](www.charter.net:)  1.316Mbps 0.778ms 0.759766us/bit
[www.charter.net:](www.charter.net:)  1.316Mbps 0.778ms 0.759766us/bit
[www.charter.net:](www.charter.net:)  1.316Mbps 0.778ms 0.759766us/bit
[www.charter.net:](www.charter.net:)  1.316Mbps 0.778ms 0.759766us/bit

--- 10.200.100.1 statistics ---
bytes   out    in   dup  loss   rtt (ms): min       avg       max   std dev
   44    50    50          0%           0.214     0.269     0.808     0.090
  108    50    50          0%           0.145     0.160     0.352     0.032

--- [www.charter.net](www.charter.net) statistics ---
bytes   out    in   dup  loss   rtt (ms): min       avg       max   std dev
   44    49    49          0%          50.698    52.134    62.240     2.348
  108    49    49          0%          51.407    52.347    55.583     0.860

--- estimated link characteristics ---
host                              bandwidth       ms
warning: rtt big 10.200.100.1 0.145ms < rtt small 10.200.100.1 0.214ms (ignored)
[www.charter.net](www.charter.net)                      1.316Mbps      50.483

I know great service...:mad:

Kevin

---

### Post by MrChilly0 on 2008-05-18
OK...I'll get flamed for saying this...  I'll tell you what you need to do and I'll try and describe what's happening. 

First of all, call back in, set up another trouble call. I know it's PITA but I'll get you the info you'll need to get this taken care of.  When calling in, do the normal ranting and raving, but also mention that your internet is intermittant and tell the tech to put you on the intermittant list. If he tells you it doesn't exist, tell him this word for word: "Add my modem to the eqa watch list". Tell the tech also that it's on and off, and that the phone rep said something about noise in the area. That should get you escalated to the line tech's who will find where the prob is in the area.

Now to the reason.  You have internet and for argument's sake, video also. You're a paying customer who busts his butt to pay for your services. The cable company did all the wiring and you're on the up and up. The slacker down the street, he thinks he's smooth and is just going to hook himself up. This usually entails busting parts off of the cable line and jamming in a bared store bought cable line. What happens is, he's basically created a ghetto antenna that radiates bad signals into the cable main line, thus interfering with paying customers service.  

There could be other reasons you're having the prob, it may be a quick fix or it may not, but regardless, they tell you you're guaranteed that speed, and it may just be that you got an inexperienced tech.

Good luck... I had this happen to me after 8 years of great internet, it sucked, but in the end, it ended up being the lazy guy down the street screwing it up for everyone.

---

### Post by MrChilly0 on 2008-05-18
one more thing that may help narrow it down...ping charter.com or net a few thousand times and see what your packet loss looks like. Anything below 99% let the tech know

---

