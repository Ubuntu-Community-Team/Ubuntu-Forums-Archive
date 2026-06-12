---
title: "Wireless Feisty Can't Get It To Work Help!"
date: 2007-04-28
forum: Networking &amp; Wireless
---

### Post by acwspoon on 2007-04-28
I really hope someone can help me, so I've been sitting in my computer chair for the past 2 hours trying to figure out how to get my wireless to work on feisty, well needless to say nothing say worked, I previously had Edgy and I had it running and since the installation is similar I assumed that it would be no problem, I WAS WRONG!

My wireless card isn't even detected!

```
 lspci | grep Broadcom\ Corporation
02:00.0 Ethernet controller: Broadcom Corporation NetXtreme BCM5751M Gigabit Ethernet PCI Express (rev 11)

```

Here's this
```
 lspci
00:00.0 Host bridge: Intel Corporation Mobile 915GM/PM/GMS/910GML Express Processor to DRAM Controller (rev 03)
00:01.0 PCI bridge: Intel Corporation Mobile 915GM/PM Express PCI Express Root Port (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 1 (rev 03)
00:1c.2 PCI bridge: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 3 (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #3 (rev 03)
00:1d.3 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #4 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB2 EHCI Controller (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev d3)
00:1e.2 Multimedia audio controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) AC'97 Audio Controller (rev 03)
00:1e.3 Modem: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) AC'97 Modem Controller (rev 03)
00:1f.0 ISA bridge: Intel Corporation 82801FBM (ICH6M) LPC Interface Bridge (rev 03)
00:1f.2 IDE interface: Intel Corporation 82801FBM (ICH6M) SATA Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) SMBus Controller (rev 03)
01:00.0 VGA compatible controller: ATI Technologies Inc M22 [Radeon Mobility M300]
02:00.0 Ethernet controller: Broadcom Corporation NetXtreme BCM5751M Gigabit Ethernet PCI Express (rev 11)
04:00.0 CardBus bridge: Ricoh Co Ltd RL5c476 II (rev 8d)
04:02.0 Ethernet controller: Atheros Communications, Inc. AR5212 802.11abg NIC (rev 01)

```


Here's my ifconfig

```
eth0      Link encap:Ethernet  HWaddr 00:11:25:16:5B:E9  
          inet addr:192.168.0.100  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::211:25ff:fe16:5be9/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:15047 errors:0 dropped:0 overruns:0 frame:0
          TX packets:9538 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:20435985 (19.4 MiB)  TX bytes:943371 (921.2 KiB)
          Interrupt:16 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:42 errors:0 dropped:0 overruns:0 frame:0
          TX packets:42 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:2100 (2.0 KiB)  TX bytes:2100 (2.0 KiB)

```

I've just installing the firmware for the BCM43xx using these links
[COLOR="DarkOrange"][http://ubuntuforums.org/showthread.php?t=197102]("http://ubuntuforums.org/showthread.php?t=197102")[/COLOR]
[COLOR="DarkOrange"][http://ubuntuforums.org/showthread.php?t=285809&highlight=bcmwl5]("http://ubuntuforums.org/showthread.php?t=285809&highlight=bcmwl5")[/COLOR]
that didn't work.... then I tried the ndiswrapper instructions, didn't work

I tried to use the ndiswrapper-1.42 from the website and completely stumped......
It was so easy on Edgy, and I feel I know what I'm doing but apparently I shouldn't because I can not figure this out.


Thanks in advance for any help!

---

### Post by chili555 on 2007-04-28
I'm confused. The interface you highlighted:> Ethernet controller: Broadcom Corporation NetXtreme BCM5751M Gigabit Ethernet PCI Express (rev 11)is a wired ethernet adapter. According to this:> eth0      Link encap:Ethernet  HWaddr 00:11:25:16:5B:E9  
          inet addr:192.168.0.100  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::211:25ff:fe16:5be9/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:15047 errors:0 dropped:0 overruns:0 frame:0
          TX packets:9538
etc.your ethernet interface is connected and transmitting and receiving data.

However, your wireless interface is, I believe, this:> Atheros Communications, Inc. AR5212 802.11abg NIC (rev 01)Installing Broadcom firmware, etc. won't help your Atheros adapter at all. This link may help: [http://ubuntuforums.org/showthread.php?t=420627](http://ubuntuforums.org/showthread.php?t=420627)

---

### Post by acwspoon on 2007-04-28
Ok I guess I was making the mistake before that the ethernet card was my wireless card but that's so weird that I got it to work with ndiswrapper...

Well IT WORKS! thanks a lot, I'm still new at this and I apparently I know even less that I had thought.

One thing thought, after I installed it said something like restricted drivers in the notification area and said i couldn't use them and when I clicked on it it wouldn't open and it said I needed linux-restricted-modules-2.6.15 instead of what i have which is 2.6.17.  I don't know if that is a serious problem thought because my wireless is working fine.

Thanks

---

