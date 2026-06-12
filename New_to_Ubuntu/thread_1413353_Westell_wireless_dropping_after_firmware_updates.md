---
title: "Westell wireless dropping after firmware updates"
date: 2010-02-22
forum: New to Ubuntu
---

### Post by summersource on 2010-02-22
We have 3 more computers that are not dropping signal only mine. When I boot up my wireless will stay up for less than 5 mins before it drops and prompts me for my WEP Key sometime's it will connect for a second and sometimes not at all. What could be the problem?

---

### Post by summersource on 2010-02-22
got on long enough to ifconfig/ispci

kerrie@kerrie:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:26:2d:7c:65:b0  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:16 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:4 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:240 (240.0 B)  TX bytes:240 (240.0 B)

wlan0     Link encap:Ethernet  HWaddr 00:17:c4:dc:9d:85  
          inet addr:192.168.1.90  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::217:c4ff:fedc:9d85/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:11 errors:0 dropped:0 overruns:0 frame:0
          TX packets:31 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1287 (1.2 KB)  TX bytes:5129 (5.1 KB)

wmaster0  Link encap:UNSPEC  HWaddr 00-17-C4-DC-9D-85-64-63-00-00-00-00-00-00-00-00  
          UP RUNNING  MTU:0  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0

-----------------------------------
kerrie@kerrie:~$ lspci
00:00.0 Host bridge: Advanced Micro Devices [AMD] RS780 Host Bridge Alternate
00:01.0 PCI bridge: Acer Incorporated [ALI] Device 9602
00:04.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (PCIE port 0)
00:06.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (PCIE port 2)
00:11.0 SATA controller: ATI Technologies Inc SB700/SB800 SATA Controller [AHCI mode]
00:12.0 USB Controller: ATI Technologies Inc SB700/SB800 USB OHCI0 Controller
00:12.1 USB Controller: ATI Technologies Inc SB700 USB OHCI1 Controller
00:12.2 USB Controller: ATI Technologies Inc SB700/SB800 USB EHCI Controller
00:13.0 USB Controller: ATI Technologies Inc SB700/SB800 USB OHCI0 Controller
00:13.1 USB Controller: ATI Technologies Inc SB700 USB OHCI1 Controller
00:13.2 USB Controller: ATI Technologies Inc SB700/SB800 USB EHCI Controller
00:14.0 SMBus: ATI Technologies Inc SBx00 SMBus Controller (rev 3c)
00:14.2 Audio device: ATI Technologies Inc SBx00 Azalia (Intel HDA)
00:14.3 ISA bridge: ATI Technologies Inc SB700/SB800 LPC host controller
00:14.4 PCI bridge: ATI Technologies Inc SBx00 PCI to PCI Bridge
00:18.0 Host bridge: Advanced Micro Devices [AMD] K10 [Opteron, Athlon64, Sempron] HyperTransport Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K10 [Opteron, Athlon64, Sempron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K10 [Opteron, Athlon64, Sempron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K10 [Opteron, Athlon64, Sempron] Miscellaneous Control
00:18.4 Host bridge: Advanced Micro Devices [AMD] K10 [Opteron, Athlon64, Sempron] Link Control
01:05.0 VGA compatible controller: ATI Technologies Inc Device 9712
01:05.1 Audio device: ATI Technologies Inc Device 970f
03:00.0 Ethernet controller: Broadcom Corporation NetLink BCM5784M Gigabit Ethernet PCIe (rev 10)
09:00.0 Network controller: Atheros Communications Inc. AR928X Wireless Network Adapter (PCI-Express) (rev 01)
kerrie@kerrie:~$ 

          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

---

### Post by summersource on 2010-02-22
I made this post this morning but it looks as if it was deleted. I posted the lspci/ifconfig info, not sure that is allowed? I dunno anyway.   
I am having a problem with my DSL wireless I am using a Westell router Model 327W it has been dropping since we did firmware updates a few days ago. This is only happening on my system we have other computers running Ubuntu that are not having a problem. Does anyone have any suggests?

---

### Post by TurnOfTide on 2010-02-22
Westell makes very poor modems. I have one and .... it's just really bad all around. They put no money in the design phase of that piece of crap.

---

### Post by summersource on 2010-02-22
I agree we lose signal on all systems from time to time and thought that after updating the firmware it would solve the issue. However after that update mine is the only one which will not stay connected.

---

### Post by mörgæs on 2010-02-22
[https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide](https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide)

---

### Post by overdrank on 2010-02-22
> **summersource said:**
> I made this post this morning but it looks as if it was deleted. I posted the lspci/ifconfig info, not sure that is allowed? I dunno anyway.   


Hi and I found your other thread on the issue so I have merged them. Good luck. :)

---

### Post by summersource on 2010-02-22
Thx Over
 Morgaes I followed that link and have spent the last few hours trying working on it but I must admit I have no idea what I am doing.  I have tried nearly all of the commands with no results. I stay connected for 5-15 mins and then I lose connection and have to reboot to get it back and then it last for another 5-15 mins [U]
[/U]

---

### Post by mörgæs on 2010-02-23
Googling with this string in the search field

```
 Westell 327 site:[http://ubuntuforums.org/](http://ubuntuforums.org/)
```gives some good links, though many are a little old. The internal search engine on Ubuntuforums is more or less useless.

---

### Post by TBABill on 2010-02-23
I used to troubleshoot DSL problems for a phone company and my suggestion is to call and report a trouble with the modem. I assume it's the combo DSL modem and wireless router in one unit. They will probably want to send you one to connect yourself before wasting the money on a technician and most techs do not carry replacement modems in very large quantities. I'd call tech support and ask that they send you one because the firmware update did not help. Most likely the modem or router is unable to handle some portion of its job and dumps one of the ports (wireless) as a symptom of the problem, not cause of the problem.  
 
Are you experiencing the drops during heavy bandwidth times or is it dropping even when idle? Those Westells are used because they're cheap and their performance is awful. Since you most likely do not own the modem you are not responsible when they fail or perform sub-par. And the squeaky wheel gets the grease with phone companies.
 
If the company is Verizon you may end up having to call several times because they want to spend no money to provide customer service. Just push and demand a new unit be sent because they'll walk you through wasteful troubleshooting that has nothing to do with your issue before you actually get to the part that is helpful. You sound like you know what you are doing so use that to push them in the right direction....just advice from someone who has been there. Good luck!

---

### Post by summersource on 2010-02-23
You guys are awesome here thanks for the helpful tips!  I have tried everything even tried changing the channels around and found than none was better than the other. 

AT&T is my ISP and it is a modem/router combo, & it's drops even when idle. 

Since their routers are known for poor preformance what would you recommed as a replacement, and would I still need to use the Westell as the Modem?

---

### Post by TBABill on 2010-02-25
From a technical standpoint I'd stick with theirs. That way when something goes wrong with it they are on the hook for providing a replacement. Only they can provide the DSL modem (normally Telco's own the modem), but you are free to use any router if you are willing to do so. I won't make a recommendation on that end because I have had success with several brands and everyone seems to have their favorite and least favorite.

---

### Post by summersource on 2010-02-26
I just wanted to say thank you, your recommendations seems to be working ;)

---

### Post by TBABill on 2010-02-27
Just curious what the final outcome was...new modem, new router, combo westel unit, etc? Glad to help.

---

### Post by summersource on 2010-03-03
Well was working great we got a netgear but I am kinda back at square one after trying to run a  different distro side by side, it totally screwed up my ubuntu and I ended up having to format last night now I'm on the great driver hunt, once again. Thanks for checking in and thanks for the help.

---

