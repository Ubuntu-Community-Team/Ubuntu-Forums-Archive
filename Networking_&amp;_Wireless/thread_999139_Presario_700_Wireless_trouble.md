---
title: "Presario 700 Wireless trouble"
date: 2008-12-01
forum: Networking &amp; Wireless
---

### Post by horadrim.sage on 2008-12-01
I used Ubuntu on my laptop a while back but with Gutsy the wireless was broken, and with school I didn't have time to try and wait for a fix as the school's IT dptmnt was unable to resolve my issues.  Since then I went back to XP and then used Fluxbuntu but found it lacking, so upgraded to Xubuntu 8.10 and now my wireless isn't working and cannot find a fix.  This will be a tedious process as my laptop has no internet (ethernet hasn't worked in years) and will need to shuttle the data to desktop to post.

Any help would be greatly appreciated.

I cannot ping the router and scanning turns up no wireless networks.  They're both on the same channel and no encryption. (I live the boonies)
Here is what I've logged. I'm sure you'll need more info than this, but it's a start.  I look forward to being wireless once more.

drew@drew-laptop:~$ sudo iwconfig
[sudo] password for drew: 
lo        no wireless extensions.

eth0      no wireless extensions.

wifi0     IEEE 802.11b  Nickname:""
          Mode:Managed  Frequency:2.422 GHz  Access Point: 00:50:8B:46:87:A8   
          Bit Rate:1 Mb/s   Sensitivity=1/3  
          Retry short limit:8   RTS thr:off   Fragment thr:off
          Encryption key:off
          Power Management:off
          
wlan0     IEEE 802.11b  Nickname:""
          Mode:Managed  Frequency:2.422 GHz  Access Point: 00:50:8B:46:87:A8   
          Bit Rate:1 Mb/s   Sensitivity=1/3  
          Retry short limit:8   RTS thr:off   Fragment thr:off
          Encryption key:off
          Power Management:off
          Link Quality=0/92  Signal level=-90 dBm  Noise level=-90 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:4799   Missed beacon:0

pan0      no wireless extensions.


drew@drew-laptop:~$ sudo lshw -C network
  *-network               
       description: WL100_11Mbps_Wireless_PC_Card
       product: Version 01.00
       vendor: Compaq
       physical id: 0
       slot: Socket 0
       resources: irq:3
  *-network
       description: Ethernet interface
       product: RTL-8139/8139C/8139C+
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: b
       bus info: pci@0000:00:0b.0
       logical name: eth0
       version: 10
       serial: 00:08:02:2e:f0:a9
       size: 10MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=8139too driverversion=0.9.28 duplex=half latency=64 link=no maxlatency=64 mingnt=32 module=8139too multicast=yes port=MII speed=10MB/s
  *-network:0
       description: Wireless interface
       physical id: 1
       logical name: wlan0
       serial: 00:50:8b:46:87:a8
       capabilities: ethernet physical wireless
       configuration: broadcast=yes driver=hostap firmware=0.6.2 multicast=yes wireless=IEEE 802.11b
  *-network:1 DISABLED
       description: Ethernet interface
       physical id: 2
       logical name: pan0
       serial: 5a:f5:99:31:73:c3
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes

---

