---
title: "Intel PRO/1000 GT speed issues"
date: 2007-06-14
forum: Networking &amp; Wireless
---

### Post by vanhoudn on 2007-06-14
Hi,

I recently purchased an Intel PRO/1000 GT so that I could take advantage of the gigabit network. The problem is that the card will burst data at 20 mbps, then go to zero, burst again at 20 mbps, go to zero, and repeat until the file is done. This makes the average transfer speed about 10 mbps, which is unacceptable. 

The pauses in between are between 0.5 and 1 second. 

I discovered this using the network monitoring utility bmon. It doesn't seem to be an artifact of bmon because the activity light on the back of the card has the same slow on off blinking pattern. 

The network pattern holds for downloading an iso from the internet with wget or transferring files with samba. The 'normal' network traffic noise also has this pattern. 

The machine is an old Dell Dimension 8100 with an onboard 100baseT NIC running Dapper Drake LTS server edition. Here is what I did:

1. Installed the gigabit NIC, noticed the on-off problem. 
2. Disabled the onboard NIC in the bios --> problem remained
3. Edited /etc/iftab so that the gigabit NIC was now eth0 --> problem remained 
4. Applied and then rolled back the networking tweaks at [here]("http://tvease.net/wiki/index.php?title=Tweak_ubuntu_for_speed") --> problem remained
5. Downloaded the most recent driver from intel, compiled it, and inserted into the kernel. Followed the directions [here]("http://ubuntuforums.org/showthread.php?p=741687").
5. Posted on this forum. 

Driver version: e1000-7.5.5
Kernel version: 2.6.15-28-server

Here is my output from lspci 
```

0000:00:00.0 Host bridge: Intel Corporation 82850 850 (Tehama) Chipset Host Bridge (MCH) (rev 02)
0000:00:01.0 PCI bridge: Intel Corporation 82850 850 (Tehama) Chipset AGP Bridge (rev 02)
0000:00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev 02)
0000:00:1f.0 ISA bridge: Intel Corporation 82801BA ISA Bridge (LPC) (rev 02)
0000:00:1f.1 IDE interface: Intel Corporation 82801BA IDE U100 (rev 02)
0000:00:1f.2 USB Controller: Intel Corporation 82801BA/BAM USB (Hub #1) (rev 02)
0000:00:1f.3 SMBus: Intel Corporation 82801BA/BAM SMBus (rev 02)
0000:00:1f.4 USB Controller: Intel Corporation 82801BA/BAM USB (Hub #2) (rev 02)
0000:01:00.0 VGA compatible controller: nVidia Corporation NV11 [GeForce2 MX/MX 400] (rev a1)
0000:02:08.0 Ethernet controller: Intel Corporation 82541PI Gigabit Ethernet Controller (rev 05)
0000:02:0a.0 Multimedia audio controller: Creative Labs SB Live! EMU10k1 (rev 0a)
0000:02:0a.1 Input device controller: Creative Labs SB Live! MIDI/Game Port (rev 0a)

```


Here is my output from ethtool 
```

Settings for eth0:
        Supported ports: [ TP ]
        Supported link modes:   10baseT/Half 10baseT/Full
                                100baseT/Half 100baseT/Full
                                1000baseT/Full
        Supports auto-negotiation: Yes
        Advertised link modes:  10baseT/Half 10baseT/Full
                                100baseT/Half 100baseT/Full
                                1000baseT/Full
        Advertised auto-negotiation: Yes
        Speed: 1000Mb/s
        Duplex: Full
        Port: Twisted Pair
        PHYAD: 0
        Transceiver: internal
        Auto-negotiation: on
        Supports Wake-on: umbg
        Wake-on: g
        Current message level: 0x00000007 (7)
        Link detected: yes

```

I don't really know a whole lot about networking tuning. Any help would be appreciated. If I should post somewhere else, let me know. Thanks.

--Nathan

---

### Post by toricred on 2007-09-10
Did you ever resolve this?  I'm having the exact same problem.

---

### Post by tech1869 on 2007-10-19
I also have the exact same problem. Please post what you find out about it.

---

### Post by toricred on 2007-10-19
I was never able to fix the issue.  I ended up just using the onboard NIC that I'm pretty convinced is inferior in terms of speed and stability.  But at least the stability is only occasional and for very short periods of time (i.e., less than a second).

---

### Post by njparton on 2007-11-06
Did you try downloading aand compiling the latest e1000 driver from Intel? it's very easy, even I could do it. Just follow the readme.

I've got an intel Pro/1000 PT card and for a 1GB transfer it peaks at just under 50MB/s and stays between 40 and 50 the whole time. That's Vista 64 to Ubuntu 7.10.

I've also set MTU = 9014 to match my windows PC jumbo frame size via the /etc/network/interfaces config file :)

---

