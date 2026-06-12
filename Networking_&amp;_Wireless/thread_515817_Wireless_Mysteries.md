---
title: "Wireless Mysteries?"
date: 2007-08-02
forum: Networking &amp; Wireless
---

### Post by pjj on 2007-08-02
Hi everyone. I am new to this forum and still learning a lot about Ubuntu/Kubuntu.

Here is something that puzzles me:

Using Dapper Drake I have a very reliable, strong wireless connection to a public access point.
The same connection becomes much weaker (as represented by the signal meter) and is at times very difficult to access. It is even worse with Gutsy Gibbon.
Connections are most difficult to get.

I am using Atheros 5212 (Airlink 101) on a 2.6 Ghz CPU for all three OS incarnations.

Can anyone explain this to me, please?

---

### Post by noob12 on 2007-08-02
If you post more info, I may be able to see something, but I'm just guessing.

You should figure out which drivers specifically you are using (**lshw -C network** should show this in the configuration line) and use **modinfo** to get further info and check sites/lists specific to those drivers.

One wild guess is that power management or transmission power regulation features may be getting implemented in newer drivers and this may be causing problems in your situation.  New bugs of course are another possibility as this stuff matures.  

Try using **iwconfig** while bound to this AP and see what signal strengths you're getting.  
You might try using **iwconfig** tweaks (**man iwconfig**) to set your txpower and disable power management features.

---

### Post by pjj on 2007-08-04
Thanks for the reply. Output for first request lshw -C network is:



       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ath_pci driverversion=0.9.6.0 (EXPERIMENTAL) ip=192.168.9.14 multicast=yes wireless=IEEE 802.11g
       resources: iomemory:e2000000-e200ffff irq:10
  *-network:1
       description: Ethernet interface
       product: VT6102 [Rhine-II]
       vendor: VIA Technologies, Inc.
       physical id: 12
       bus info: pci@00:12.0
       logical name: eth0
       version: 74
       serial: 00:0d:87:af:44:a9
       size: 10MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegociation
       configuration: autonegociation=on broadcast=yes driver=via-rhine driverversion=1.2.0-2.6 duplex=half link=no multicast=yes port=MII speed=10MB/s
       resources: ioport:e000-e0ff iomemory:e2012000-e20120ff irq:11



Could not get modinfo to give me anything.

iwconfig yields:

ath0      IEEE 802.11g  ESSID:"eleventh"
          Mode:Managed  Frequency:2.462 GHz  Access Point: 00:80:C8:05:98:40
          Bit Rate:11 Mb/s   Tx-Power:18 dBm   Sensitivity=0/3
          Retry:off   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=10/94  Signal level=-85 dBm  Noise level=-95 dBm
          Rx invalid nwid:38005  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:6  Invalid misc:6   Missed beacon:2788


Hope this gives you a better idea.

Thanks again for your time and efforts.

Peter

---

### Post by pjj on 2007-08-17
Answering my own question:

Found a link to Wicd Manager somewhere in the Ubuntu Forums.
Downloaded application, removed KNetworkmanager from computer. Then I installed Wicd.
Now I have reliable wireless  connections in all versions of Kubuntu/Ubuntu including the most up-to-date.

---

