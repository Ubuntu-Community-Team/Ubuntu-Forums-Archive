---
title: "does Ubuntu support 160 MHz WiFi channels?"
date: 2020-07-21
forum: Networking &amp; Wireless
---

### Post by anoviciate on 2020-07-21
I ask because my Intel Wireless-AC 9560 PCIe (in a Lenovo T490) only reports **866 Mbps** @ 5 GHz and 144 Mbps @ 2.4 GHz; yet, the Intel 9560 specs say that it can support 2x the WiFi legacy -AC (**1.73 Gbps**) ***"when using 160 MHz channels"***.

My router specs specify the transmission rate as: 1900Mbps(5GHz: Up to 1300Mbps, 2.4GHz: Up to 600Mbps).

Apparently, using 160 MHz channels, in addition to 80 MHz channels, is how the new WiFi 6 speeds are implemented/accomplished.

Thanks in advance for whatever insights ...

---

### Post by TheFu on 2020-07-21
160 MHz is probably the channel width.  To control the channel width, it would be the driver that matters, not the OS.
[https://www.duckware.com/tech/wifi-in-the-us.html](https://www.duckware.com/tech/wifi-in-the-us.html) So, which driver is being used specifically and does it support the 160 Mhz channel width is the real question.

The little popup that says "Connection X Mbps" ... isn't reality.  Wifi throughput is constantly fluctuating up and down.  It is like being in a landminded field using a buggy going in and out of the holes.

But usually people should feel lucky to get 30-50% of the claimed performance from any wifi device.  That's the real-world.  Lots of local issues come up for all wifi connections.  Best to use a wired ethernet whenever possible because then you should be over 90% of the specified bandwidth pretty easily.  Wired ethernet is like being on a super-interstate with smooth pavement, going straight for hundreds and hundreds of miles.

---

### Post by anoviciate on 2020-07-21
> **TheFu said:**
> lucky to get 30-50% of the claimed performance from any wifi device. 

... interesting answer, TheFu.  At 866 Mbps (50% of the claimed 1.73 Gbps), I should feel **VERY** *lucky*?  :)

I, too, have always preferred a solid Ethernet cable, when available/convenient.  Reading about new '*mesh*' WiFi routers left me wondering what's the difference between a '*mesh*' and a good ol' *Repeater* or *Access Point*?  `sounds like marketing hype, to me.   :P

Thanks for the guidance.

---

### Post by TheFu on 2020-07-21
> **anoviciate said:**
> ... interesting answer, TheFu.  At 866 Mbps (50% of the claimed 1.73 Gbps), I should feel **VERY** *lucky*?  :) 

No - the "claimed" bandwidth is 866Mbps for your setup.  50% of that is what you should feel lucky to get.  The only way to measure throughput is to push 100 files of varying sizes through the connection, keep track of the time and the file sizes.  THEN we can talk about what the bandwidth actually is. Any reported connection speed is a lie.

> **anoviciate said:**
> I, too, have always preferred a solid Ethernet cable, when available/convenient.  Reading about new '*mesh*' WiFi routers left me wondering what's the difference between a '*mesh*' and a good ol' *Repeater* or *Access Point*?  `sounds like marketing hype, to me.   :P

Mesh is about providing access, not performance. The mesh devices are able to tune their output to prevent overlapping coverage by more than 1 node at a time for most of the area being covered.  This requires a central management system and for each AP to see the other APs nearby and dynamically adjust power.  It isn't marketing in professional installations.  Poorly placed "mesh" APs in a house can be really great or really bad.  Unless less you have multiple "wings" in your estate, it is likely 2 APs, placed on opposite ends of the building and on different floors will perform nicely. This assumes each is using wired ethernet to a GigE or better wiring closet and that connection has a solid connection to the switches/routers for the network.  For my 4 brd house, an AP placed in the ceiling of the upper flood, center of the structure provides great access to almost the entire house and garage. Because it is an open floor plan, the den and kitchen have almost line of sight access on the 1st floor.  In the garden tub of the master bath, the signal drops, but relaxing there is usually about reading a book.

Location, location, location.

BTW, I don't trust any wifi security.  Mine gets connected to the WAN router outside my internal network. All wifi is untrusted unless a VPN connection is made.  Wifi-6 is too new to be trusted and all prior version have proven to be untrustworthy.  Yes, I know "everybody" trusts their WPA2 connections, but they shouldn't.

---

### Post by chili555 on 2020-07-21
Please check:

```
sudo iw reg get
```As well as: ```
 iwlist chan
```My machine reports:

```
wlp3s0    32 channels in total; available frequencies :
          Channel 01 : 2.412 GHz
          Channel 02 : 2.417 GHz
          Channel 03 : 2.422 GHz
          Channel 04 : 2.427 GHz
          Channel 05 : 2.432 GHz
          Channel 06 : 2.437 GHz
          Channel 07 : 2.442 GHz
          Channel 08 : 2.447 GHz
          Channel 09 : 2.452 GHz
          Channel 10 : 2.457 GHz
          Channel 11 : 2.462 GHz
          Channel 36 : 5.18 GHz
          Channel 40 : 5.2 GHz
          Channel 44 : 5.22 GHz
          Channel 48 : 5.24 GHz
          Channel 52 : 5.26 GHz
          Channel 56 : 5.28 GHz
          Channel 60 : 5.3 GHz
          Channel 64 : 5.32 GHz
          Channel 100 : 5.5 GHz
          Channel 104 : 5.52 GHz
          Channel 108 : 5.54 GHz
          Channel 112 : 5.56 GHz
          Channel 116 : 5.58 GHz
          Channel 120 : 5.6 GHz
          Channel 124 : 5.62 GHz
          Channel 128 : 5.64 GHz
          Channel 132 : 5.66 GHz
          Channel 136 : 5.68 GHz
          Channel 140 : 5.7 GHz
          Channel 144 : 5.72 GHz
          Channel 149 : 5.745 GHz
          Current Frequency:5.745 GHz (Channel 149)

```

```
global
country US: DFS-FCC
	(2402 - 2472 @ 40), (N/A, 30), (N/A)
	(5170 - 5250 @ 80), (N/A, 23), (N/A), AUTO-BW
	(5250 - 5330 @ 80), (N/A, 23), (0 ms), DFS, AUTO-BW
	([COLOR="#FF0000"]5490 - 5730 @ 160[/COLOR]), (N/A, 23), (0 ms), DFS
	(5735 - 5835 @ 80), (N/A, 30), (N/A)
	(57240 - 63720 @ 2160), (N/A, 40), (N/A)
```So I can get 160 mHz bandwidth on channels 100 through 140. When I check my router, I can set it to any fixed channel of 36, 40, 44, 48, 149, 153, 157, 161 or 165. Sadly, channels 100 through 140 aren't available. In my case, it is the router, not the wireless device in my laptop, that is deficient.

My iwconfig also reports 866.7 Mb/s. About 7 meters from the router, I get about 230 Mb/s down.

---

### Post by anoviciate on 2020-07-21
> **chili555 said:**
> Please check:

```
sudo iw reg get
```As well as: ```
 iwlist chan
```My machine reports: 

ok; mine reports/returns (about 6 feet from the router):

global
country 00: DFS-UNSET
    (2402 - 2472 @ 40), (N/A, 20), (N/A)
    (2457 - 2482 @ 20), (N/A, 20), (N/A), AUTO-BW, PASSIVE-SCAN
    (2474 - 2494 @ 20), (N/A, 20), (N/A), NO-OFDM, PASSIVE-SCAN
    (5170 - 5250 @ 80), (N/A, 20), (N/A), AUTO-BW, PASSIVE-SCAN
    (5250 - 5330 @ 80), (N/A, 20), (0 ms), DFS, AUTO-BW, PASSIVE-SCAN
    **(5490 - 5730 @ 160), (N/A, 20), (0 ms), DFS, PASSIVE-SCAN**
    (5735 - 5835 @ 80), (N/A, 20), (N/A), PASSIVE-SCAN
    (57240 - 63720 @ 2160), (N/A, 0), (N/A)

phy#0 (self-managed)
country US: DFS-UNSET
    (2402 - 2437 @ 40), (6, 22), (N/A), AUTO-BW, NO-HT40MINUS, NO-80MHZ, NO-160MHZ
    (2422 - 2462 @ 40), (6, 22), (N/A), AUTO-BW, NO-80MHZ, NO-160MHZ
    (2447 - 2482 @ 40), (6, 22), (N/A), AUTO-BW, NO-HT40PLUS, NO-80MHZ, NO-160MHZ
   [B] (5170 - 5190 @ 160), (6, 22), (N/A), AUTO-BW, NO-HT40MINUS
    (5190 - 5210 @ 160), (6, 22), (N/A), AUTO-BW, NO-HT40PLUS
    (5210 - 5230 @ 160), (6, 22), (N/A), AUTO-BW, NO-HT40MINUS
    (5230 - 5250 @ 160), (6, 22), (N/A), AUTO-BW, NO-HT40PLUS
    (5250 - 5270 @ 160), (6, 22), (0 ms), DFS, AUTO-BW, NO-HT40MINUS, PASSIVE-SCAN
    (5270 - 5290 @ 160), (6, 22), (0 ms), DFS, AUTO-BW, NO-HT40PLUS, PASSIVE-SCAN
    (5290 - 5310 @ 160), (6, 22), (0 ms), DFS, AUTO-BW, NO-HT40MINUS, PASSIVE-SCAN[/B]
    **(5310 - 5330 @ 160), (6, 22), (0 ms), DFS, AUTO-BW, NO-HT40PLUS, PASSIVE-SCAN**
    (5490 - 5510 @ 240), (6, 22), (0 ms), DFS, AUTO-BW, NO-HT40MINUS, PASSIVE-SCAN
    (5510 - 5530 @ 240), (6, 22), (0 ms), DFS, AUTO-BW, NO-HT40PLUS, PASSIVE-SCAN
    (5530 - 5550 @ 240), (6, 22), (0 ms), DFS, AUTO-BW, NO-HT40MINUS, PASSIVE-SCAN
    (5550 - 5570 @ 240), (6, 22), (0 ms), DFS, AUTO-BW, NO-HT40PLUS, PASSIVE-SCAN
    (5570 - 5590 @ 240), (6, 22), (0 ms), DFS, AUTO-BW, NO-HT40MINUS, PASSIVE-SCAN
    (5590 - 5610 @ 240), (6, 22), (0 ms), DFS, AUTO-BW, NO-HT40PLUS, PASSIVE-SCAN
    (5610 - 5630 @ 240), (6, 22), (0 ms), DFS, AUTO-BW, NO-HT40MINUS, PASSIVE-SCAN
    (5630 - 5650 @ 240), (6, 22), (0 ms), DFS, AUTO-BW, NO-HT40PLUS, PASSIVE-SCAN
    (5650 - 5670 @ 80), (6, 22), (0 ms), DFS, AUTO-BW, NO-HT40MINUS, NO-160MHZ, PASSIVE-SCAN
    (5670 - 5690 @ 80), (6, 22), (0 ms), DFS, AUTO-BW, NO-HT40PLUS, NO-160MHZ, PASSIVE-SCAN
    (5690 - 5710 @ 80), (6, 22), (0 ms), DFS, AUTO-BW, NO-HT40MINUS, NO-160MHZ, PASSIVE-SCAN
    (5710 - 5730 @ 80), (6, 22), (0 ms), DFS, AUTO-BW, NO-HT40PLUS, NO-160MHZ, PASSIVE-SCAN
    (5735 - 5755 @ 80), (6, 22), (N/A), AUTO-BW, NO-HT40MINUS, NO-160MHZ
    (5755 - 5775 @ 80), (6, 22), (N/A), AUTO-BW, NO-HT40PLUS, NO-160MHZ
    (5775 - 5795 @ 80), (6, 22), (N/A), AUTO-BW, NO-HT40MINUS, NO-160MHZ
    (5795 - 5815 @ 80), (6, 22), (N/A), AUTO-BW, NO-HT40PLUS, NO-160MHZ
    (5815 - 5835 @ 20), (6, 22), (N/A), AUTO-BW, NO-HT40MINUS, NO-HT40PLUS, NO-80MHZ, NO-160MHZ

This is foreign to me; I don't know how to interpret it.  For example, I have no idea what:

[B]5170 - 5190 @ 160

[/B]or any of it means, as I see no *units* specified.

Running *'speed tests'*, under optimal conditions I typically get maybe **113 Mbps down** and 11 Mbps up (Charter-Spectrum limits **up**loading speed, apparently to preclude running home servers ... without paying them 'business' rates).  I've compared the same 'speed test' with **both** Ethernet and WiFi (same router) and get ***similar*** results.

As Intel (maker of the T490 PCIe WiFi chipset) is usually pretty/reasonably reputable in their product specification claims, I wondered why I was only seeing 1,006 Mbps (866 @ 5 MHz + 140 @ 2.4 MHz) reported by Ubuntu WiFi network settings and the 'speed tests' (113 Mbps down).  Was my shortfall (from 1.73 Mbps) due to the WiFi router, Intel wireless AC 9560, Ubuntu hardware support or Charter-Spectrum bandwidth limitations?

Thanks, again, to all for whatever insights ...

---

### Post by TheFu on 2020-07-22
> I've compared the same 'speed test' with both Ethernet and WiFi (same router) and get similar results.
If you aren't transferring files between local systems, then the WAN connection will be the limiting factor. Nothing you do on the wifi will matter.

Be happy you aren't on a 1Mbps/128Kbps connection like many people.  What exactly is the bandwidth you pay for from the ISP?

All those commands are client-side - on the computer. As chili555 pointed out above, the router capabilities and WAN connection will limit what any wifi client can do.

There's nothing to be done here.  Please remember to mark this thread a "SOLVED" using the thread tools button.

---

### Post by chili555 on 2020-07-22
> 5170 - 5190 @ 160

As we see above:

```
Channel 36 : 5.18 GHz
```

Please try setting your router to a fixed, not autoselect, channel 36. Is there any improvement?

---

### Post by anoviciate on 2020-07-22
> **TheFu said:**
>  What exactly is the bandwidth you pay for from the ISP? 

I don't recall Charter-Spectrum (my ISP) making specific speed claims.  As you know, many ISP's use undefined adjectives, like "*High-speed Internet*" ... which, to them, means anything faster than a dial-up modem.  ;)

But, since I've never seen Charter-Spectrum speeds faster than 120 Mbps (at two locations, btw), I wondered about the Ethernet speed limits.  For example, if 1,000 Mega**BITS** per second ***approximates*** 1/10 that in bytes per second i.e. about 100 MegaBYTES per second, maybe (?) the 110 - 115 Mbps *speed-test* reported numbers, I've seen, reflect Gigabyte **Ethernet limits**, rather than ISP (WAN) limits?

---

### Post by TheFu on 2020-07-22
1 MBps = 8 Mbps

Looks like Charter offers 3 speeds - 200, 400, and 1000 Mbps. Of course, the physical address would determine what is available or not.  Appears they use "Ultra" in their branding for 1000 Mbps service.
[https://www.spectrum.com/internet](https://www.spectrum.com/internet)

---

### Post by kurt18947 on 2020-07-22
> **TheFu said:**
> 1 MBps = 8 Mbps

Looks like Charter offers 3 speeds - 200, 400, and 1000 Mbps. Of course, the physical address would determine what is available or not.  Appears they use "Ultra" in their branding for 1000 Mbps service.
[https://www.spectrum.com/internet](https://www.spectrum.com/internet)

I don't know about Charter, we've had Verizon FiOS for years. We have a speed that is no longer offered to new customers. We have 50/50 upgraded from 15/15 to 25/25 then to 50/50. If we got new service today, the slowest we could get is 200/200. The point being someone who has had uninterrupted internet service may have speeds lower than the lowest offered to new subscribers. Lately  speedtest.net has been pretty accurate for us, it hadn't been previously. Using one of speed test sites would give anoviciate a good estimate of what he/she is getting. Of course what anoviciate needs from his/her LAN may have little to do with internet speeds. And yeah, wired ethernet >>>>>> any wifi I've used.

Going OT a little, I recently learned about ethernet cable that's plenum rated. Apparently that means one could use HVAC ducting to route ethernet cabling. If I were to consider it, I'd use the return ducting on forced air HVAC systems. As it is we're using MoCA 2.0 which is working quite well for us. WiFi for portable devices only and I'll plug laptops into a cable if I'm doing anything beyond web browsing.

---

### Post by anoviciate on 2020-07-22
[COLOR=#ff0000]Please try setting your router to a fixed, not autoselect, channel 36. Is there any improvement?[/COLOR]

no noticeable change (compared to 'Auto"), trying several 5 GHz channels.  Results were in the 110 Mbps range, say +/- 5 ... same as via Ethernet, btw.

---

### Post by anoviciate on 2020-07-22
> **kurt18947 said:**
>  Lately  speedtest.net has been pretty accurate for us, it hadn't been previously. Using one of speed test sites would give anoviciate a good estimate of what he/she is getting. 

From Spectrum's SpeedTest.net, I'm getting the same/similar results - about 110 Mbps down and 11 Mbps up, regardless of Ethernet or WiFi.  As 110 Mbps is roughly 1/10th of Gigabit Ethernet limits, I'm suspecting that Charter-Spectrum is simply throttling the Internet service ... which is fiber (new, as of a couple of years ago) out at the street, btw.

---

### Post by TheFu on 2020-07-23
> **anoviciate said:**
> From Spectrum's SpeedTest.net, I'm getting the same/similar results - about 110 Mbps down and 11 Mbps up, regardless of Ethernet or WiFi.  As 110 Mbps is roughly 1/10th of Gigabit Ethernet limits, I'm suspecting that Charter-Spectrum is simply throttling the Internet service ... which is fiber (new, as of a couple of years ago) out at the street, btw.

If the ethernet connection isn't any faster, then the problem is either with the service - getting what you pay for - or the router hardware capabilities are maxed out.

Both of those are NOT the same topic as wifi and nobody here can make them faster by tweaking any settings.

---

