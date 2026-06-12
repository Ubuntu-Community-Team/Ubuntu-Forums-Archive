---
title: "Weird Wireless Behavior in Feisty"
date: 2007-04-01
forum: Networking &amp; Wireless
---

### Post by rlgoddard on 2007-04-01
Hi,

I am running Feisty on my dual boot WinXP/Feisty Fawn Ubuntu system.  I've upgraded from Edgy a week ago to Feisty, and I had a hell of a time trying to get wireless working.  Wireless worked flawlessly under Edgy, so I was perplexed as to why it didn't work in Feisty.  I finally removed network-manager and installed wicd.  At first, I had trouble getting wireless to work because it kept getting and releasing the DNS (actually the same IP address as my gateway router).  I had to re-install wicd and input my ISP's DNS addresses, and I finally got wireless working.  Yay! \\:D/

Now for the weird part.  My wireless connection seems to crest and ebb.  It would build up in speed to around 100 KB/s for about 5 seconds, then crash down to 0, and stay there for about 10 seconds before building up to around 100KB/s again, then crash down again to 0 until all data has been transferred.  The activity light on my wireless card is either constantly on or constantly blinking.  I've already disabled ipv6 in Firefox and blacklisted ipv6.

I am listing the results of iwconfig, ifconfig, and the relevant entry in my lspci outputs here:

[B]IFCONFIG

[/B]```

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:13335 errors:0 dropped:0 overruns:0 frame:0
          TX packets:13335 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:1647689 (1.5 MiB)  TX bytes:1647689 (1.5 MiB)

ra0       Link encap:Ethernet  HWaddr 00:12:17:82:2E:A9  
          inet addr:192.168.1.211  Bcast:192.168.1.255  Mask:255.255.255.0
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:83238 errors:0 dropped:0 overruns:0 frame:0
          TX packets:215240 errors:2527 dropped:2527 overruns:0 carrier:0
          collisions:2011 txqueuelen:1000 
          RX bytes:115798402 (110.4 MiB)  TX bytes:12728845 (12.1 MiB)
          Interrupt:17 Base address:0xc000
```[B]IWCONFIG

[/B]```

lo        no wireless extensions.

ra0       RT2500 Wireless  ESSID:"GoddardWAN"  
          Mode:Managed  Frequency=2.462 GHz  Access Point: 00:16:B6:17:43:8D   
          Bit Rate:54 Mb/s   Tx-Power:-3 dBm   
          RTS thr:off   Fragment thr:off
          Link Quality=86/100  Signal level=-53 dBm  Noise level:-206 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0
```[B]

SUDO LSPCI -V[/B]

```

00:08.0 Network controller: RaLink RT2500 802.11g Cardbus/mini-PCI (rev 01)
        Subsystem: Linksys WMP54G 2.0 PCI Adapter
        Flags: bus master, slow devsel, latency 32, IRQ 17
        Memory at dfffe000 (32-bit, non-prefetchable) [size=8K]
        Capabilities: [40] Power Management version 2

```Let me know if you need the output of anything else, or if you have questions.  All help is appreciated!

Take care,
Russ

---

### Post by rlgoddard on 2007-04-03
*bump*

Anyone have any ideas?

---

### Post by rlgoddard on 2007-04-05
Hi,
 
I solved the slowness issue by uninstalling WICD and using the network properties dialog to set up my wireless interface. I rebooted, and still could not get internet access, although it sees the router and uses the correct WEP key. Going to network properties again, I discovered that the DNS entries are blank for some reason. I put in the DNS's of my ISP and I got internet access without WICD! Then I tried some speed testing by using update-manager to download any updates, and the wireless connection stays on at a steady speed of around 630 KB/s without WICD, rather than cresting and ebbing with WICD. \\:D/ 
 
In the meantime, network-mangler is still not installed on my system, and I don't intend to install it anytime soon. I will just make do without a connection manager of some sort because Feisty is installed on a desktop, rather than a laptop, so it isn't important for me to automagically find wireless connections and connect to them.
 
In related news, I heard from someone on the WICD forum that network-manager is no longer a required dependency for ubuntu-desktop. I haven't tried it myself due to a lack of time on the WInXP/Ubuntu desktop I was using (work calls!), but will try it tonight. If that's true, there there is a god :) 
 
Take care,
Russ

---

