---
title: "Streaming media over powerline"
date: 2016-03-27
forum: Networking &amp; Wireless
---

### Post by fieldingadam12 on 2016-03-27
I have a raspberry Pi B+, connected to an 8-bay HDD enclosure. I recently bought and ODROID C2, with the intention of setting it up on another TV, and stream my movies and TV shows to it from the Pi.

Everything is set up and connected, but when I try to play anything, it opens in VLC, the timer bar moves, but I get no picture. If I pick out a random time, it will display 1 frame, like a screenshot, but nothing more, and the timer keeps moving.

The setup as it is now goes: Pi, directly connected to the 8 bay enclosure->Powerline adapter->Router->Powerline adapter at the router->Powerline adapter at the ODROID. The drives are 2x4TB seagate ST4000DM000. 
I've tried removing the Powerline at the router, to see if it made a difference, but nothing changed. 

Is it too many steps to be able to playback? Are the drives too slow? Is it a USB limitation? 
Any help would be appreciated

---

### Post by TheFu on 2016-03-28
Curious - is this an ubuntu question?

Media servers need sufficient throughput. A Raspberry Pi usually doesn't provide sufficient throughput to be a server.  Plus, powerline throughput varies hugely depending on the distance, hops, and other unknowns in the house wiring.

I did some powerline testing in my house. The results were surprising/bad: [http://blog.jdpfu.com/2015/08/27/powerline-ethernet-adapters](http://blog.jdpfu.com/2015/08/27/powerline-ethernet-adapters)

If you have _some_ budget, I will share my media setup - a $55 CPU is at the center - with a GigE NIC.  The Raspberry Pi is a remote system connected by DLNA (Plex) and NFS. It is wired; no wifi, no powerline.  I only have 7 disks connected to the server (no Seagates).

---

### Post by papibe on 2016-03-28
Hi fieldingadam12.

I have a raspberry Pi B too. It can fairly pull/download very close to 100Mbps, however it can't push/upload not even close to that.

I also have a 300Mbps powerline set. In my apartment, which I imagine has 'shared' electric wires, it just a bit better than Wireless-G speeds. That's not enough for streaming 1080p content.

If you want to be very thorough, use iperf (example [here]("http://askubuntu.com/questions/7976/how-do-you-test-the-network-speed-betwen-two-boxes")) to measure maximum network speeds between the machines.

If that is enough, you should also test disk read speed in order to discard/confirm the drives are not the ones slowing you (examples of dd on the same link)

Hope it helps. Let us know how it goes.
Regards.

---

### Post by fieldingadam12 on 2016-03-28
> **TheFu said:**
> Curious - is this an ubuntu question?

I wasn't really syre which forum to post it under

> powerline throughput varies hugely depending on the distance, hops, and other unknowns in the house wiring.

That's what I was afraid of. Ive yet to do any speed/performance tests

> If you have _some_ budget, I will share my media setup - a $55 CPU is at the center - with a GigE NIC.  The Raspberry Pi is a remote system connected by DLNA (Plex) and NFS. It is wired; no wifi, no powerline.  I only have 7 disks connected to the server (no Seagates).
Would any dual-core do? Also, because of how far apart the devices are (opposite ends of the house), I don't really have a way to not use powerline, other than just wireless, because of a lack of Ethernet ports

---

### Post by fieldingadam12 on 2016-03-28
So I just ran iperf, and got bandwidth of 21Mbp/s, and a transfer of 26.2Mbytes over 10.2 seconds. Shouldn't 21Mbp/s be more than adequate? maybe not big 1080p, but ive also tried some 480p shows, and surely they don't need a huge amount of bandwidth

---

### Post by TheFu on 2016-03-28
Raspberry Pi throughput isn't designed to be a server.

Any core 2 duo?  Can't say. I know that motherboard support for networking and USB vary wildly - that is putting it nice.  If a single USB2 port is used for that storage, that basically limits the storage access to 20Mbps, tops.  Real-world USB2 performance sucks.  Sometimes USB3 real-world performance sucks too.  I have a very fast Core i5 system with a USB3 add-on card, but it performs only 2x faster than USB2 storage, when it should provide 130Mbps-200Mbps throughput.  How do I know?  That $55 CPU, on a new motherboard, has onboard USB3 which works very well.   Older systems aren't designed for USB the same way newer systems are.

Network Options:
* Run CAT5e through the attic/basement/crawlspace to connect both sides of the house.
* Use a quality wifi AP (not the stupid "Home routers" sold for $20 -$200) - something from Ubiquiti (about $80) would be a good bet - but have a wired ethernet connection from the router to the AP run across the house.
* Wireline measured performance doesn't show all the ups/downs of that performance.  WiFi has this too, unless it is line-of-sight..

If you are out of ports, buy a $20 GigE 8-port unmanaged switch.  Now you have 7 more ports. Connect 1 end to the router and all the others to any other wired systems.

Raspberry Pi systems are clients, not servers, for stuff like this.  Sure, you can run 10 websites on a R-Pi too, but that doesn't push nearly as much data as video streaming does.  Video needs solid, dependable, network performance. That sort of performance is easiest to get over a wired ethernet cable. That is just the way it is.  People will claim to get solid networking working over wifi to a server, but they are doing human-being stuff, not computer-sensitive stuff.  Surfing and email and twitter and facebook aren't anything like streaming video.

---

### Post by fieldingadam12 on 2016-03-28
Thanks for the in-depth reply. I don't have the option to run Ethernet through the house (I don't own it). As for quality WiFi APs, at this point I don't want to spend that sort of money ($AU180) to solve the problem.

Would you recommend swapping over to a mITX build, or a NUC? If I did, would powerline become a similar bottleneck?

---

### Post by papibe on 2016-03-28
> **fieldingadam12 said:**
> 21Mbp/s be more than adequate?
It should be OK for SD content, may be even 720p (with minimum stutter on action scenes).

I would test a raw movie/file transfer as detail on the link. On the server:
```
nc -vvlnp 12345 >/dev/null
```
on the player:
```
dd if=/path/to/media/file bs=1M count=1K | nc -vvn 192.168.1.1 12345
```
where 192.168.1.1 is the IP of the server.

Another thought: PIs can decode 1080p video using its internal GPU. Are you sure the ODROID-C2 can decode and play video using hardware acceleration? You should be able to test this by playing local media on the ODROID-C2. Sometimes VLC is not the player which takes advantage of the acceleration on little those devices. You may need mplayer, or mpv.

Regards.

---

### Post by TheFu on 2016-03-28
IMHO, NUCs are 2x the price for what you get.
The only way to know if powerline or the r-pi is the bottleneck is to test without the r-pi and see how that works.  Is that possible?  Is the storage USB2 or USB3 or does it have other connections like eSATA (which would be the best by far!)?

mITX or microATX - I lean towards microATX because if you have any ATX case laying around, then the micro/mini/normal ATX motherboards will fit.  I'm not suggesting you change the rendering device - just the server part.  The server shouldn't be in the same room with the TV/projector due to noise considerations.  That is what networking helps with too.

Ubiquiti Stuff .... 
[http://www.amazon.com/Ubiquiti-Networks-Enterprise-AP-Unifi/dp/B00HXT8R2O/](http://www.amazon.com/Ubiquiti-Networks-Enterprise-AP-Unifi/dp/B00HXT8R2O/) is what I'm suggesting. That should be about AU$80 according to XE. I didn't see that option on Amazon.com.au - hum....   I know Ubiquiti sells in Asia - did a 4 node deployment in Nepal 5 yrs ago.
[http://www.streakwave.com.au/store/ubiquiti-networks/ubiquiti-unifi](http://www.streakwave.com.au/store/ubiquiti-networks/ubiquiti-unifi) - AU$121 
[http://www.ubiquitishop.com.au/3_unifi_access_points_wifi.products](http://www.ubiquitishop.com.au/3_unifi_access_points_wifi.products) - AU$130
Not really good options for those prices.  Sadly, the other cheap, consumer wifi stuff sucks in comparison.

Just because you don't own the house, that doesn't mean that the owner wouldn't let you connect 2 ends of the house with an ethernet cable through the attic. It is actually really, really, easy sometimes.  Even easier with a basement to run the cables.  Maybe $20 total in parts and cable for a nice wall-mount on each end.  Plus the minimum speed you would see is 100Mbps SOLID. If you have GigE stuff, you can get 900+ Mbps for about the same price.  GigE networking has about a $5 premium over 10/100 networking these days.

So, I have a Pentium G3258 which acts as a network storage, Plex Server, Calibre Server, transcoding server, language translation server, and a few other things.  The CPU + MB was $99 total.  I had RAM, disk, case, PSU laying around, so $99 was the total cost to me for this new system.  The USB3 performance is excellent.  It comes with a GigE port that is supported out-of-the-box by Ubuntu 14.04.  It has onboard intel GPU, but I don't have it connected to a monitor.  Uses about 30W most of the time, except when doing video transcoding - then it sucks 53W.  The CPU supports VT-x and VT-d so you can run virtual machines on it easily if you like.  It is a relatively cheap, solid, system for a low-end desktop too.  If you like to overclock the CPU, the stock cooler supports over 1GHz above the rated CPU clock speed easily.  I don't overclock anymore - haven't in over 15 yrs.  There are slightly cheaper solutions that use a little less power, but they won't have the same CPU bang-for-the-buck that the G3258 has.  Every once in a while, the pricing for a CPU is just great.

Oh -I'm using a $50 gigabyte motherboard with that CPU.

But definitely find out where the bottleneck is before buying anything else.

For media playback - I'd use Kodi, not vlc, mpv, mplayer.  Kodi is designed for the r-pi. Get the OSMC distro for it.  For that other device - you are on your own.  Out of the box, Kodi/OSMC on r-pi supports 1080p video using h.264 video codecs.  If you want hidef mpeg2 video (720+), then you'll need to buy the commercial mpeg license from the r-pi store.  I transcode everything into h.264, so no commercial codecs are needed. CPU use runs about 7% on the pi, since all the video decoding happens in hardware.

---

### Post by kurt18947 on 2016-03-28
Do you have decent coax? We have Verizon FiOS which uses MoCA for ethernet over coax for certain purposes such as VOD. I believe other cable/fiber operators use MoCA as well. If you're interested, you might spend some time on DSLreports.com/broadbandreports.com researching wired networking options. There's a pretty informative thread on the Verizon FiOS forum about various router configurations even if you don't have Verizon FiOS. One thing that could complicate things for you would be splitters on coax. Not all splitters are created equal, some will work with higher frequencies than others. MoCA requires splitters capable of 1 ghz+ I believe. MoCA is certainly not going to touch CAT5/CAT6 gigabit cable throughput but I prefer it to wireless.

I know of only one situation where you can't use coax for both TV and ethernet -- satellite TV. Satellite uses high frequencies like MoCA so the two signals can't coexist like cable TV (low frequency) and MoCA (high frequency). I'm no expert on this stuff but that's how I understand it. People buy used Actiontec Verizon FiOS routers and repurpose them as MoCA-Ethernet bridges. Actiontec/Verizon routers also have wifi so can be used as wireless access points using MoCA over coax. The wifi systems in Verizon's Actiontec routers are fairly uninspired though.

---

