---
title: "slow BCM4306 wireless"
date: 2008-10-17
forum: Networking &amp; Wireless
---

### Post by Ken53 on 2008-10-17
With some difficulty, I installed Ubuntu 8.04 on my Dell Latitude D600 laptop and even got wireless working, but it's extremely slow. In Windows XP (I have a dual-boot setup) a recent test at [http://www.dslreports.com/speedtest?flash=1](http://www.dslreports.com/speedtest?flash=1) showed 2262 Kb/s download, 1049 Kb/s upload. Minutes later, running Ubuntu (same location), the wireless rate was 254 Kb/s download, 442 Kb/s upload. It hurts to say this, but as a percentage of Windows speed that's 11% download, 42% upload. I realize that rate depends on many factors, but I've been trying this several days and those results are pretty representative.

In Terminal, lspci gives the following on the card
```

02:03.0 Network controller: Broadcom Corporation BCM4306 802.11b/g Wireless LAN Controller (rev 02)
	Subsystem: Dell TrueMobile 1300 WLAN Mini-PCI Card
	Flags: bus master, fast devsel, latency 32, IRQ 5
	Memory at fafee000 (32-bit, non-prefetchable) [size=8K]
	Capabilities: <access denied>

```
and iwconfig wlan0 gives
```

wlan0     IEEE 802.11g  ESSID:"OSU_Access"  
          Mode:Managed  Frequency:2.412 GHz  Access Point: 00:0B:86:E7:E1:02   
          Bit Rate=1 Mb/s   Tx-Power=27 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2346 B   
          Link Quality=56/100  Signal level=-65 dBm  Noise level=-69 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

```
I tried using iwconfig to change the Bit Rate to everything from 2 Mb/s to 54 Mb/s. None helped. In many tries (even with rates iwconfig accepted), it took several tries to actually change the rate parameter. In some cases, performance even deteriorated.

I did not use ndiswrapper to install the wireless driver. Installation from the 8.04 CD apparently provided the driver, sans firmware, which I got using b43-fwcutter (see [http://linuxwireless.org/en/users/Drivers/b43#devicefirmware](http://linuxwireless.org/en/users/Drivers/b43#devicefirmware)).

As you can probably tell from my post, I'm new to Linux and not current on system admin and find this all pretty confusing. I would appreciate help with this problem.

---

### Post by timfairbank on 2008-11-22
Hi Ken,

I just wanted to let you know that I'm having the exact same problem.

The machine is a HP Pavilion ze4560us, running Ubuntu 8.10.

lspci reports that the chip is a BCM4306

---

### Post by Joe2Shoe on 2008-11-22
see my post here: [http://ubuntuforums.org/showthread.php?t=990216](http://ubuntuforums.org/showthread.php?t=990216)
I'm on 8.10 and pulling 2Mb/s using the BCM4306 rev. 02 wifi card.

---

