---
title: "Wifi issues only when on battery"
date: 2014-11-27
forum: Networking &amp; Wireless
---

### Post by ariskk on 2014-11-27
Hi, on my laptop with ubuntu 14.04 the wifi is working fine when the laptop's power is plugged in. But when on battery, the wifi can't connect to my wifi router ( a sky hub, I am living in London, UK ). It doesn't tell much on the log files but I get this when I unplug the power:

Nov 27 15:33:29 ariskk-laptop kernel: [ 3269.233626] init: anacron main process (5136) killed by TERM signal
Nov 27 15:33:37 ariskk-laptop wpa_supplicant[860]: wlan0: CTRL-EVENT-SCAN-STARTED 
Nov 27 15:33:38 ariskk-laptop wpa_supplicant[860]: nl80211: send_and_recv->nl_recvmsgs failed: -33

When I plug the power back it doesn't say anything relevant to the wifi:

Nov 27 15:34:21 ariskk-laptop anacron[5859]: Anacron 2.3 started on 2014-11-27
Nov 27 15:34:21 ariskk-laptop anacron[5859]: Will run job `cron.daily' in 5 min.
Nov 27 15:34:21 ariskk-laptop anacron[5859]: Jobs will be executed sequentially


Any ideas what might be causing this?

Thanks

P.S. Some details that might help:

lspci
00:00.0 Host bridge: Intel Corporation 2nd Generation Core Processor Family DRAM Controller (rev 09)
00:01.0 PCI bridge: Intel Corporation Xeon E3-1200/2nd Generation Core Processor Family PCI Express Root Port (rev 09)
00:01.1 PCI bridge: Intel Corporation Xeon E3-1200/2nd Generation Core Processor Family PCI Express Root Port (rev 09)
00:02.0 VGA compatible controller: Intel Corporation 2nd Generation Core Processor Family Integrated Graphics Controller (rev 09)
00:16.0 Communication controller: Intel Corporation 6 Series/C200 Series Chipset Family MEI Controller #1 (rev 04)
00:1a.0 USB controller: Intel Corporation 6 Series/C200 Series Chipset Family USB Enhanced Host Controller #2 (rev 05)
00:1b.0 Audio device: Intel Corporation 6 Series/C200 Series Chipset Family High Definition Audio Controller (rev 05)
00:1c.0 PCI bridge: Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port 1 (rev b5)
00:1c.1 PCI bridge: Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port 2 (rev b5)
00:1c.2 PCI bridge: Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port 3 (rev b5)
00:1c.3 PCI bridge: Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port 4 (rev b5)
00:1c.4 PCI bridge: Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port 5 (rev b5)
00:1d.0 USB controller: Intel Corporation 6 Series/C200 Series Chipset Family USB Enhanced Host Controller #1 (rev 05)
00:1f.0 ISA bridge: Intel Corporation HM67 Express Chipset Family LPC Controller (rev 05)
00:1f.2 RAID bus controller: Intel Corporation 82801 Mobile SATA Controller [RAID mode] (rev 05)
00:1f.3 SMBus: Intel Corporation 6 Series/C200 Series Chipset Family SMBus Controller (rev 05)
01:00.0 VGA compatible controller: Advanced Micro Devices, Inc. [AMD/ATI] Seymour [Radeon HD 6400M/7400M Series] (rev ff)
09:00.0 Network controller: Intel Corporation Centrino Wireless-N 1030 [Rainbow Peak] (rev 34)
0a:00.0 Unassigned class [ff00]: Realtek Semiconductor Co., Ltd. RTS5209 PCI Express Card Reader (rev 01)
0b:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller (rev 06)
0c:00.0 USB controller: NEC Corporation uPD720200 USB 3.0 Host Controller (rev 04)

---

### Post by ajgreeny on 2014-11-27
This could be related to the wireless power-management, so do a quick search on that or try the answer I have found with a search.
See if there is a difference in the output of **iwconfig** when using the battery as opposed to when plugged into mains electricity, and if the power-management is on when on battery try turning power-management off by editing **/etc/network/interfaces** and adding the third line shown below:

auto wlan0
iface wlan0 inet dhcp
wireless-power off

---

### Post by ariskk on 2014-11-27
Thanks, I gave it a try but unfortunatelly no luck. My /etc/network/interfaces looks like:

# interfaces(5) file used by ifup(8) and ifdown(8)
auto lo
iface lo inet loopback

wireless-power off



Does the above look ok?

---

### Post by ajgreeny on 2014-11-27
Yes, it looks fine to me, so I think that is not the problem, though you could back up what you have now and replace it with my new version just as a trial.  If it is not any help just undo the change and put back what you had before.

I wish I could help more but I think I am now out of my depth.  Sorry.

---

### Post by ariskk on 2014-11-28
np, thank you.

---

### Post by ajgreeny on 2014-11-28
> **ariskk said:**
> np, thank you.
So, is this solved?

Does "np" mean "no problem" or "problem over"?

If everything now works OK please mark as Solved from **Thread Tools** at the top of thread.

---

### Post by ariskk on 2014-11-29
Hi, no problem not resolved.

On windows the wifi works ok with or without the battery. Seems like a driver issue.

---

### Post by gian on 2015-04-24
same issue here...

Lenovo Yoga 2, when I plug in the power, wifi stops working.

Only trace on logs is anacron starting...

As soon as I unplug power chord, wifi resumes.

---

### Post by ariskk on 2015-04-24
[B]I managed to make mine work but it has been some time now, I think it is related to power management which should be off, try:

iwconfig wlan0 power off[/B]

---

### Post by gian on 2015-04-24
Ariskk,

thanks for your kind reply.

Iwconfig reports that power management is OFF already...

I will try Ubuntu 15.04 this week-end...

-Gian

---

### Post by jeremy31 on 2015-04-24
gian, maybe you should try turning power management on.

---

