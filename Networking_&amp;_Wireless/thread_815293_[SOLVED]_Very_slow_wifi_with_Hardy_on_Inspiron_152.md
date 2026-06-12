---
title: "[SOLVED] Very slow wifi with Hardy on Inspiron 1525"
date: 2008-06-01
forum: Networking &amp; Wireless
---

### Post by SpecialFred on 2008-06-01
I'm running a fresh install of Hardy 64bit on a Dell Inspiron 1525. Wireless wasn't working out of the box, but I got it running with ndiswrapper by following the instructions here: 

[https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff#head-d8ce0e35a4ccdbeddd6cf36f9cb23a11d8e0e9dc]("https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff#head-d8ce0e35a4ccdbeddd6cf36f9cb23a11d8e0e9dc"). 

Though wireless now works, it is really slow, around 1/Mbps. The wireless card is a Broadcom 4310. iwconfig outputs this:

ru@toaster:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11b  ESSID:"linksys"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: 00:06:25:7B:51:6B   
          Bit Rate=11 Mb/s   Tx-Power:32 dBm   
          RTS thr:2347 B   Fragment thr:2346 B   
          Power Management:off
          Link Quality:68/100  Signal level:-52 dBm  Noise level:-96 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:724  Invalid misc:220278   Missed beacon:0

I'm curious about the huge number of invalid miscs. The other computers I have running here have few to no invalid miscs or excessive retries. Additionally, Vista on the same computer is really slow with wireless. I haven't bothered looking for a fix for Vista, but if wifi is slow under both, could it be possible that I have a hardware issue with the card?

I've looked high and low for a fix, but I keep coming up dry. Any help would be greatly appreciated.

---

### Post by SpecialFred on 2008-06-02
For anyone who is interested or has a similar problem, I traced the issue to the driver. Apparently, the driver used by the instructions in the link in the original post, as well as Vista, doesn't play nicely with Wireless-B networks. Once I replaced the router with one capable of Wireless-G, everything worked fine.

---

