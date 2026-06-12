---
title: "replacement wifi card suggestions please"
date: 2020-04-08
forum: Networking &amp; Wireless
---

### Post by kim3 on 2020-04-08
Hi folks, I had mega problems with my
 [FONT=system-ui]

[/FONT][COLOR=#000000]Ultimate N WiFi Link 5300[/COLOR][COLOR=#FFFFFF][FONT=system-ui]
[/FONT][/COLOR]on ubuntu a few years back, same issues on mint, tried all the fixes  but no joy.

Now I have updated my ubuntu, albeit very slowly, as the realtek routine remains very slow indeed. 1mb/s when my macbook 2014 model next to it gets 30mb/s!

Happy to replace now and wondering if anyone could recommend some options for me common enough to find one in a local computer parts store here in Melbourne?

Any ideas?

Cheers!

---

### Post by SeijiSensei on 2020-04-08
The little USB dongles work pretty well if you're only interested in N speeds.  (Linux support for AC hardware is more of a hit-or-miss in my experience.) I've used one of these: [https://www.amazon.com/Edimax-EW-7811Un-150Mbps-Raspberry-Supports/dp/B003MTTJOY](https://www.amazon.com/Edimax-EW-7811Un-150Mbps-Raspberry-Supports/dp/B003MTTJOY)

In general, I try to stay far away from Broadcom hardware which always seems to have problems in Linux. This Edimax device uses the Atheros chipset and is well-supported out-of-the-box.

---

### Post by chili555 on 2020-04-08
Your prior thread is here: [https://ubuntuforums.org/showthread.php?t=2389618&p=13760970#post13760970](https://ubuntuforums.org/showthread.php?t=2389618&p=13760970#post13760970) In post #2, you link to your similar thread in Mint: [https://forums.linuxmint.com/viewtopic.php?f=53&t=259452](https://forums.linuxmint.com/viewtopic.php?f=53&t=259452) In the Mint thread, you said:> 
 the antennae is never fully screwed on the current one. 
Isn't this a hardware problem that no operating system can solve? Perhaps Loctite or superglue can solve it.

I have and use an Intel wireless card with the driver iwlwifi and it's fast and rock solid.

```
chili@T440p:~$ ./speedtest-cli 
Retrieving speedtest.net configuration...
Retrieving speedtest.net server list...
Testing from AT&T U-verse (xxxx.129.95)...
Selecting best server based on latency...
Hosted by AT&T (xxxx, NC) [36.57 km]: 16.777 ms
Testing download speed........................................
Download: 230.91 Mbit/s
Testing upload speed..................................................
Upload: 69.38 Mbit/s

```

---

### Post by kim3 on 2020-04-14
> **SeijiSensei said:**
> The little USB dongles work pretty well if you're only interested in N speeds.  (Linux support for AC hardware is more of a hit-or-miss in my experience.) I've used one of these: [https://www.amazon.com/Edimax-EW-7811Un-150Mbps-Raspberry-Supports/dp/B003MTTJOY](https://www.amazon.com/Edimax-EW-7811Un-150Mbps-Raspberry-Supports/dp/B003MTTJOY)

In general, I try to stay far away from Broadcom hardware which always seems to have problems in Linux. This Edimax device uses the Atheros chipset and is well-supported out-of-the-box.

I have that USB nano wifi. Plugged it in and the blue light came on. Took some fiddling to choose it from top right icon on the desktop. Then I managed to get 6mb/s which was much better but still very poor compared to the macbook measuring the same router directly next to it. And swiftly the speed went down to 0.2mb/s or 0.2 as the PCI wireless came back into action (after I had turn it off).

How do you configure the uSB??

Not sure how common an issue but this is the worst experience with linux over the years. enough to probably just reinstall windows 10. I dont like it as much bit basic issues like wifi are very very easy!

---

### Post by MoebusNet on 2020-04-17
> **kim3 said:**
> Not sure how common an issue but this is the worst experience with linux over the years. enough to probably just reinstall windows 10. I dont like it as much bit basic issues like wifi are very very easy!

You don't give us much information (hardware, Ubuntu version, etc.) to be able to assist, but having just replaced my pcie wireless card with the Intel Dual Band Wireless-AC 7260 wireless card, I can say that it works perfectly for me on Ubuntu 18.04 out-of-the-box without having to do any configuration. Just select your desired access point in Network Manager, sign in (if required) and you are connected. No searching for Windows drivers or anything.

Intel WiFi seems to be the consensus.

---

