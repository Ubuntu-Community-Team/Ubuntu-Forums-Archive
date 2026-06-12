---
title: "ipw3945 unreliable link"
date: 2007-03-30
forum: Networking &amp; Wireless
---

### Post by betchern0t on 2007-03-30
Hi,
     I am running an 802.11b network (11mb). I have two notebooks. One has been in place for a while and has no issues - running ipw2200. Installing a brand new hp nx7400 T5500 with an ipw3945. The link is unreliable. SSH stops for a second or more when typing regularly. Ping drops packets and for some packets fails on the dns lookup. The latency on the pings ranges from 3ms to 31ms. Any ideas on resolving this?

thanks in advance

Paul

eth1      Scan completed :
          Cell 01 - Address: 00:50:FC:D4:B2:05
                    ESSID:"shilohap"
                    Protocol:IEEE 802.11b
                    Mode:Master
                    Channel:11
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s
                    Quality=94/100  Signal level=-35 dBm  Noise level=-35 dBm
                    Extra: Last beacon: 92ms ago

eth1      IEEE 802.11b  ESSID:"shilohap"  
          Mode:Managed  Frequency:2.462 GHz  Access Point: 00:50:FC:D4:B2:05   
          Bit Rate:2 Mb/s   Tx-Power:13 dBm   
          Retry limit:15   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=67/100  Signal level=-34 dBm  Noise level=-35 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:16758   Missed beacon:0

paulc@josiah:~$ uname -r
2.6.17-10-generic
paulc@josiah:~$ 

 ipw3945: Intel(R) PRO/Wireless 3945 Network Connection driver for Linux, 1.1.0mp
[17179592.120000] ipw3945: Copyright(c) 2003-2006 Intel Corporation
[17179592.120000] ACPI: PCI Interrupt 0000:10:00.0[A] -> GSI 17 (level, low) -> IRQ 177
[17179592.120000] PCI: Setting latency timer of device 0000:10:00.0 to 64
[17179592.120000] ipw3945: Detected Intel PRO/Wireless 3945ABG Network Connection

[17179594.208000] ipw3945: Detected geography ABG (13 802.11bg channels, 4 802.11a channels)

---

### Post by chili555 on 2007-03-30
Here is your iwconfig with some areas in bold for emphasis:```
eth1 IEEE 802.11b ESSID:"shilohap"
Mode:Managed Frequency:2.462 GHz Access Point: 00:50:FC:D4:B2:05
Bit Rate:**2 Mb/s** Tx-Power:13 dBm
Retry limit:15 RTS thr: off Fragment thr: off
Power Management: off
Link Quality=67/100 **Signal level=-34 dBm Noise level=-35 dBm**
Rx invalid nwid:0 Rx invalid crypt:0 Rx invalid frag:0
Tx excessive retries:0 Invalid misc:16758 Missed beacon:0
```The difference between signal and noise in your system is but 1 dBm! In my own iwconfig, the Noise level is -84 dBm. You are either far away from the router, in a very radio-frequency noisy environment, or, as I suspect, both. You have already moved the router to channel 11, which is a non-overlap channel, so the next thing to work on is troubleshooting the router's environment.

---

### Post by betchern0t on 2007-03-30
Thanks Chili555,
                          I have two notebooks trying to use this wireless network. The Dell with the ipw2200 is currently showing signal and noise of 0 while the HP is showing 34/34. They are both sitting on my dining room table and the access point is about 3 metres away. The Dell has been working perfectly for about a year and a half and the HP is replacing a Toshiba which was the first on the network three years ago.

Yes I am using channel 11. I have foreign cells on 1 and 6 that I can see.

I am thinking that either there is an issue with the driver I am using, the card itself is problematic or there is a problem with the card aerial - perhaps they didn't connect it when they built the notebook. The driver is the standard one in the standard edgy kernel.

Cheers Paul

---

### Post by betchern0t on 2007-03-30
Thanks Chili555,
                          I have two notebooks trying to use this wireless network. The Dell with the ipw2200 is currently showing signal and noise of 0 while the HP is showing 34/34. They are both sitting on my dining room table and the access point is about 3 metres away. The Dell has been working perfectly for about a year and a half and the HP is replacing a Toshiba which was the first on the network three years ago.

Yes I am using channel 11. I have foreign cells on 1 and 6 that I can see. I just noticed something else. The signal/noise on the other two cells are 0/0 for the dell and 41/41 and 76/76. 

I am thinking that either there is an issue with the driver I am using, the card itself is problematic or there is a problem with the card aerial - perhaps they didn't connect it when they built the notebook. The driver is the standard one in the standard edgy kernel.

Cheers Paul

---

### Post by betchern0t on 2007-03-31
Hi,
     I think I am running into three bugs in the ipw3945. 

Bug 1: there is a bug related to encryption and smp. This notebook is a core 2 duo. Version 1.2.15 or later of ieee80211 subsystem is fixed. 1.2.15 was merged in 2.6.18 or later and 1.2.16 in 2.6.20. [http://ieee80211.sourceforge.net/](http://ieee80211.sourceforge.net/) I don't know how to test for this especially since the other two are very clear. However Intel linked this bug in the text fo the last one.

Bug 2: there is a bug in the driver itself that incorrectly reports signal and noise. The bug report: [http://www.bughost.org/bugzilla/show_bug.cgi?id=1002](http://www.bughost.org/bugzilla/show_bug.cgi?id=1002) describes two manifestation - large changes in noise level (c.30dBm) and the tools reporting signal and noise to be approximately the same. The second seems to be what I am seeing. The bug report stresses that other methods of measuring the signal and noise suggest that the environment is clean - good signal zero noise. Intel described this as cosmetic.

Bug 3: There is a bug in the driver itself that exhibits as general poor performance. Varying speeds down to 40kb/s and iwconfig or equivalent reporting thousands of invalid misc. [http://www.bughost.org/bugzilla/show_bug.cgi?id=1124](http://www.bughost.org/bugzilla/show_bug.cgi?id=1124).

I am moving to 2.6.17.11 and compiling latest versions of the driver and the ieee80211 stack. If this doesn't help I will try the latest vanilla kernel. Finally I will try ndiswrapper. All the ndiswrapper information suggests that for this card it needs a windows userspace daemon. Would be happy is someone told me otherwise. I am not confident that using the native drivers will fix this in the short term. bug 1124, the guy tried lots of different kernels and drivers.

I will post back

Paul

---

### Post by chili555 on 2007-03-31
I also have a Core 2 Duo notebook with ipw3945, althogh I've had it less than a week. Other than: > bug in the driver itself that incorrectly reports signal and noisewhich I can confirm, my experience couldn't have been better. When I installed Edgy on this machine, it recognized the card and installed the driver out of the box. I inputted the ESSID and WEP key and connected. (Not all the dinosaurs on my network yet support WPA). My obligatory 164 updates went smoothly, often downloading at the speed limit my I$P imposes.

---

### Post by betchern0t on 2007-04-01
Hi Chili555,
                  you must be one of those who win the lottery - can you send me some of your luck:) Seriously, I was seeing the exact behaviour of the third bug. Pulling down source for the ieee80211 stack and the driver source and the kernel source produced over a 100,000 invalid miscs. Watching the downloads the speeds varied from 0 to 70kb/second when the theoretical max was 25kb - I have apt-cacher going.

Anyway after a weekend of effort I am reasonably confident that I have working wireless.

1) I tried to compile a new ieee80211 stack against the standard ubuntu kernel sources - 2.6.11. This threw up an error with all sorts of dire warnings about symbols. I later learned that this can be ignored and switched off as instructed in the error message. However I had already moved on.

2) I tried pulling down the latest kernel sources - 2.6.20.4 - from kernel.org. I compiled it twice and both hung on boot. I have compiled lots of kernels but there must have been something in the config that wasn't right.

3) I tried the ndiswrapper installed on ubuntu edgy - 1.10?. It gave an error on the modprobe step. Howto is documented many places including by this community.

4) I upgraded to 1.8_1.18 as suggested in the bug reports on launchpad.net. There is a ubuntu package for this however it is not in the repositories. This removed that error and it modprobed ok. However the windows driver when it came up crashed the notebook. This was V11.1.0.0_XP_DRIVERS.ZIP off the intel site, the current latest. behavioiur was that the terminal acted like it had a stuck enter key. Mouse still worked but no clicks worked. Somewhere around here I completely trashed the networking and so reinstalled edgy.

5) I tried the one before: WIRELESS_V10.5.3.0_WIN_Drivers.zip. With this command sequence:
iwconfig eth1 key open s:xxxxxxxxxxxxx
iwconfig eth1 essid xxxxxxx
killall dhclient
killall dhclient3
dhclient3 eth1

brought it up stable and with no problems. There are a few other things like blacklisting the old driver also.

6) This translates in the /etc/network/interfaces file as:

auto eth1
iface eth1 inet dhcp
wireless-key s:xxxxxxxxxxxx open
wireless-essid xxxxxx

One thing to note is that many of the documents talk about wlan0 for the interface. For some reason as shown in /var/log/messages, ndiswrapper for this version at least changes it to eth1.

eth1      IEEE 802.11b  ESSID:"xxxxxx"  
          Mode:Managed  Frequency:2.462 GHz  Access Point: 00:50:FC:D4:B2:05   
          Bit Rate:11 Mb/s   
          Fragment thr:110000 B   
          Encryption key:xxxxxxxxx   Security mode:open
          Power Management:off
          Link Quality:0/100  Signal level:-47 dBm  Noise level:-256 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0


So now hopefully I can begin to do some value add on the notebook.

many thanks for your help

Paul

---

### Post by betchern0t on 2007-04-01
Hi Chili555,
                  you must be one of those who win the lottery - can you send me some of your luck:) Seriously, I was seeing the exact behaviour of the third bug. Pulling down source for the ieee80211 stack and the driver source and the kernel source produced over a 100,000 invalid miscs. Watching the downloads the speeds varied from 0 to 70kb/second when the theoretical max was 25kb - I have apt-cacher going.

Anyway after a weekend of effort I am reasonably confident that I have working wireless.

1) I tried to compile a new ieee80211 stack against the standard ubuntu kernel sources - 2.6.11. This threw up an error with all sorts of dire warnings about symbols. I later learned that this can be ignored and switched off as instructed in the error message. However I had already moved on.

2) I tried pulling down the latest kernel sources - 2.6.20.4 - from kernel.org. I compiled it twice and both hung on boot. I have compiled lots of kernels but there must have been something in the config that wasn't right.

3) I tried the ndiswrapper installed on ubuntu edgy - 1.10?. It gave an error on the modprobe step. Howto is documented many places including by this community.

4) I upgraded to 1.8_1.18 as suggested in the bug reports on launchpad.net. There is a ubuntu package for this however it is not in the repositories. This removed that error and it modprobed ok. However the windows driver when it came up crashed the notebook. This was V11.1.0.0_XP_DRIVERS.ZIP off the intel site, the current latest. behavioiur was that the terminal acted like it had a stuck enter key. Mouse still worked but no clicks worked. Somewhere around here I completely trashed the networking and so reinstalled edgy.

5) I tried the one before: WIRELESS_V10.5.3.0_WIN_Drivers.zip. With this command sequence:
iwconfig eth1 key open s:xxxxxxxxxxxxx
iwconfig eth1 essid xxxxxxx
killall dhclient
killall dhclient3
dhclient3 eth1

brought it up stable and with no problems. There are a few other things like blacklisting the old driver also.

6) This translates in the /etc/network/interfaces file as:

auto eth1
iface eth1 inet dhcp
wireless-key s:xxxxxxxxxxxx open
wireless-essid xxxxxx

One thing to note is that many of the documents talk about wlan0 for the interface. For some reason as shown in /var/log/messages, ndiswrapper for this version at least changes it to eth1. BTW intel are no longer labelling the drivers by the card number. I had to read inf files to find the right one.

eth1      IEEE 802.11b  ESSID:"xxxxxx"  
          Mode:Managed  Frequency:2.462 GHz  Access Point: 00:50:FC:D4:B2:05   
          Bit Rate:11 Mb/s   
          Fragment thr:110000 B   
          Encryption key:xxxxxxxxx   Security mode:open
          Power Management:off
          Link Quality:0/100  Signal level:-47 dBm  Noise level:-256 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0


So now hopefully I can begin to do some value add on the notebook.

many thanks for your help

Paul

---

### Post by betchern0t on 2007-12-22
I fixed this in the end by doing several things:

1) upgraded to gutsy

2) changed from an 802.11b minitar accesspoint to the access point on a netcomm nb5plus4w (btw this router is crap and I don't recommend it)

3) changed to 802.11g from 802.11g

4) changed from wep to wpa

It all magically started to work.

Cheers Paul

---

