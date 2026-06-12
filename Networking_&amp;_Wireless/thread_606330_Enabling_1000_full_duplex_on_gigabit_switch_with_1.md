---
title: "Enabling 1000 full duplex on gigabit switch with 100 full dulpex connected aswell"
date: 2007-11-07
forum: Networking &amp; Wireless
---

### Post by chimera007 on 2007-11-07
Hello, and thank you for reading. Lets get to the point.

Here is my case: I have a home network with a gigabit switch, 2 pc's on this network have gigabit network cards and 1 pc has 10/100 network card. Internet modem is also 10/100. 

Everything is working on full duplex, great, but the real problem is that i want my fileserver pc ( gigabit network card ) and my desktop ( gigabit network card ) be working on 1000 full duplex while the other two work at 100. 

Is this possible?

Extra Info:
-Switch is D-Link Gigabit Switch DGS-1008D

---

### Post by chimera007 on 2007-11-07
I have found out that when I right click the network icon on the gnome panel, it says the speed is 1000 Mb/s. But if i perform the command 'sudo mii-tool' it tells me 100baseTx-FD flow-control

---

### Post by netztier on 2007-11-08
> **chimera007 said:**
> I have found out that when I right click the network icon on the gnome panel, it says the speed is 1000 Mb/s. But if i perform the command 'sudo mii-tool' it tells me 100baseTx-FD flow-control

Then try **sudo ethtool ethX** instead. Sometimes either of them does not properly communicate with the kernel module or the NIC.

Another hint: sift through dmesg's output for anything that has to do with "eth": 

```
marc@blaze:~$** dmesg | grep eth**
[   42.319848] e1000: eth0: e1000_probe: Intel(R) PRO/1000 Network Connection
[   20.450000] e1000: eth0: e1000_watchdog: NIC Link is Up 1000 Mbps Full Duplex
[   33.180000] eth0: no IPv6 routers present
```

... very probably, the kernel module (here: e1000) reports what has happened during loading and initalising the card.

And yes, you can mix 10/100 devices with gigabit-devices on a gigabit switch.  Each switch port has some buffer memory that can hold just enough data before transmitting it out of a slower port until TCP's end-to-end flow control can kick in and make sure that the (gigabit) sender does not send more than the (10/100) receiver can take. 

Problems could arise if you worked with heavy broadcast and multicast traffic in the dozens-of-MBit/s range - but that's rather exotic (Norton Ghost's shipping of system images is such a case).

Ah - and don't worry about half/full duplex issues. Normal Gigabit (on fiberoptic and Cat5+ media) always does full duplex. The only half duplex implementation of Gigabit I've come across was on Cisco's Gigastack GBIC modules for the 35xxXL series switches a few years back. So there's no benefit whatsoever trying to fix speed and duplex settings on Gigabit NICs.


best regards

Marc

---

### Post by chimera007 on 2007-11-08
Hmmm... 'sudo ethtool eth0' reports it is 1000Mb/s full duplex. That is great somewhat, though the network performance is still poor or so i think. 

Here's why i say so:

I have a nfs mount on the fileserver pc, and then i mount it on my desktop. Both have gigabit connections, assuming mii-tool and ethtool are correct when they report 1000Mb/s. 

I execute 'time dd if=/dev/zero of=/media/data/testfile bs=16k count=16384' on the fileserver. On the desktop i execute 'time dd if=/mnt/data/testfile of=/dev/null bs=16k'. On an average, depending of the mount options of wsize and rsize being 8192,16384, 32768, 65535; i get lowest read speeds of 6.5 Mb/s and highest of 8.4 Mb/s.

I know I kind of deviated from the main subject, but I keep thinking it is the network card and it not being configured properly. I should at least be getting 20 Mb/s.

---

### Post by netztier on 2007-11-08
> **chimera007 said:**
>  I execute 'time dd if=/dev/zero of=/media/data/testfile bs=16k count=16384' on the fileserver. On the desktop i execute 'time dd if=/mnt/data/testfile of=/dev/null bs=16k'. On an average, depending of the mount options of wsize and rsize being 8192,16384, 32768, 65535; i get lowest read speeds of 6.5 Mb/s and highest of 8.4 Mb/s. 

That indeed is not much. My age-old P-III 500MHz does better than that via NFS and Samba.

So, here come's netztier's standard suggestion 23.2: use **iPerf ** to measure raw TCP performance. It's available in the Universe Repos. You should be getting figures at least in the 400-600Mbit/s range. Be sure to swap client (=sender) and server (=receiver) roles and experiment with larger TCP window sizes (-w parameter, go up to 256k) and parallelism (-P parameter).

This gives you a first impression what your NICs and network are capable of. 

Once the results are successful here, you can go ahead and dive into NFS optimization.

best regards

Marc

---

### Post by chimera007 on 2007-11-08
After doing some iperf tests I came up with the conclusion that something is wrong with the conections. 

PC1 = fileserver (gigabit conn)   - Pentium D 1.6Ghz dual core, 1GB Ram
PC2 = desktop (gigabit conn)     - AMD Athlon 64 X2 6000+ 3.0Ghz, 2GB Ram
PC3 = laptop (100Mbit conn)     - Pentium 4 2.4Ghz, 786MB Ram

PC2 to PC1 renders an average of 54 Mb/s on iperf
PC1 to PC2 renders an average of 70 Mb/s on iperf
PC2 to PC3 renders an average of 94 Mb/s on iperf!
PC3 to PC2 renders an average of 95 Mb/s on iperf!
PC3 to PC1 renders an average of 55 Mb/s on iperf
PC1 to PC3 renders an average of 55 Mb/s on iperf

My really stupid question is how come my desktop gets faster speeds to a 100Mbit connection? Isn't it supposed to be faster between two gigabit enabled computers?

---

### Post by chimera007 on 2007-11-08
After doing some iperf tests I came up with the conclusion that something is wrong with the conections. 
PC1 = fileserver (gigabit conn)   - Pentium D 1.6Ghz dual core, 1GB Ram
PC2 = desktop (gigabit conn)     - AMD Athlon 64 X2 6000+ 3.0Ghz, 2GB Ram
PC3 = laptop (100Mbit conn)     - Pentium 4 2.4Ghz, 786MB Ram

PC2 to PC1 renders an average of 54 Mb/s on iperf
PC1 to PC2 renders an average of 70 Mb/s on iperf
PC2 to PC3 renders an average of 94 Mb/s on iperf!
PC3 to PC2 renders an average of 95 Mb/s on iperf!
PC3 to PC1 renders an average of 55 Mb/s on iperf
PC1 to PC3 renders an average of 55 Mb/s on iperf

My really stupid question is how come my desktop gets faster speeds to a 100Mbit connection? Isn't it supposed to be faster between two gigabit enabled computers?

---

### Post by chimera007 on 2007-11-08
Eh sorry for the double post... Weird, only pressed submit post once. Anyway could the problem reside on buggy hardware? 

desktop and laptop have integrated NICs, fileserver has a PCI NEXXT gigabit card.

EDIT: The motherboard for the fileserver also has an integrated 10/100 Mbit NIC, when i preformed the test with that nic i got max speeds topping the 100 Mbit/s @ 96.8 Mb/s as an average. 

Little support for the pci card?

01:02.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8169 Gigabit Ethernet (rev 10)
        Subsystem: Realtek Semiconductor Co., Ltd. RTL-8169 Gigabit Ethernet
        Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 17
        I/O ports at e800 [size=256]
        Memory at febffc00 (32-bit, non-prefetchable) [size=256]
        Expansion ROM at 40000000 [disabled] [size=128K]
        Capabilities: <access denied>

---

### Post by netztier on 2007-11-09
> **chimera007 said:**
> 
PC2 to PC1 renders an average of 54 Mb/s on iperf
PC1 to PC2 renders an average of 70 Mb/s on iperf


Thats not good enough. However it is fast enough to say that there certainly aren't any half/full duplex issues that would need to be resolved.

> **chimera007 said:**
> 
PC2 to PC3 renders an average of 94 Mb/s on iperf!
PC3 to PC2 renders an average of 95 Mb/s on iperf!


That is a good result for FastEthernet. So PC3 and PC2 are "sane"

> **chimera007 said:**
> 
PC3 to PC1 renders an average of 55 Mb/s on iperf
PC1 to PC3 renders an average of 55 Mb/s on iperf


This nails down PC1's NIC as the "bad guy" in the game.

> **chimera007 said:**
>  My really stupid question is how come my desktop gets faster speeds to a 100Mbit connection? Isn't it supposed to be faster between two gigabit enabled computers?


Well, if one of the gigabit cards is crappy (as - alas - many Realtek cards are), or has poor driver/kernel module support, such a result can occur. 

I know that  there have been issues with the Realtek Gigabit drivers - just search the forums and you'll see. Sometimes getting the driver from Realtek seemed to help. 

You might have the luck with finding a good driver. Personally, when I read "Realtek" in a  speed problem description, I turn around and walk away, mumbling something about "get a NIC from Intel's PRO/1000 series" (even the cheap "desktop" versions will do very nicely, no need for an expensive server adapter).


regards

Marc

---

### Post by chimera007 on 2007-11-11
netztier, i have to thank you for your help. Really great full,  i will get my hands on some other brand gigabit adaptor... 

As for the ones that eventually read this thread. My gigabit adaptor was made by Nexxt. They only have one so you could find out easily about it.

---

