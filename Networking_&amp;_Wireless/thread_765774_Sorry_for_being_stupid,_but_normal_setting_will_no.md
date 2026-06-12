---
title: "Sorry for being stupid, but normal setting will not load internet"
date: 2008-04-24
forum: Networking &amp; Wireless
---

### Post by wkdude18 on 2008-04-24
I was using my laptop last night and the internet loaded just fine. So this morning I turned it on and I was looking at some web pages and then I opened up the update manager. I pressed the button to install Hardy Heron LTS 8.04 (I was anticipating the release very much) and then went through the steps. It started the update process, and it said to close all programs while loading. I did, but then it got to file 3 of 1621 and just stopped. So I was bored and I started surfing again, and then I stopped. I let my laptop sit for several hours, but when I came back it still said "downloading file 3 of 1621". I thought it might have been a really big file, but I did not care, and I couldn't open the terminal setting to see what was happening. I clicked cancel, it said abort and stuff and then it said changing settings to normal. I noticed the Update Manager had updates, so I clicked to install them, but then it froze after 8 out of 49, I clicked on the details and they said failed gutsy release.ogg or something. Then I figured the problem might be the internet connection so I opened up Firefox and sure enough no pages. I looked at my settings and they were the same as normal. So I started messing around with the settings, password type, IP address, DNS server name, gateway address, static IP DNHC, etc. What really confuses me is that (I have a plugin that gives me weather.com weather) once that obviously connected because it was giving me the weather as it hadn't in previous tries. I clicked on the link for weather.com and it did not load. I've been trying to fix these problems all day, but alas, I think I've wasted my entire day. Can someone help me please? I'm so confused.:confused::confused::confused:

---

### Post by superprash2003 on 2008-04-24
have you tried rebooting.. that normally works :D .. it not please post your ifconfig results and also type ping google.com and post results here

---

### Post by wkdude18 on 2008-04-25
All firefox says is that the server will not load
Server not found
Firefox can't find the server at google.com

I typed in "iconfig" into the terminal bash:command iconfig not found

The internet would not load under normal settings, but I was screwing around with them a lot to see if something worked, like the password type, the IP addresses, etc. if I did not say that already.

I rebooted. Also did that a bunch of  times yesterday.

---

### Post by wkdude18 on 2008-04-25
Actually I believe I have the iconfig, or ipconfig, or ifconfig, or whatever.
eth0     Link encap:Ethernet HWaddr 00:09:6B:30:41:A3
UP BROADCAST MULTICAST MTU:1500 Metric:1
RX packets: 0 errors: 0 dropped: 0overruns: 0 frame:0
TX packets:0 errors:0 dropped:0overruns:0 carrier:0
collisions:0 txqueuelen:1000
Rx bytes:0 (0,0b)  TX bytes:0 (0,0 b)

eth1     Link encap:Ethernet  HWaddr 00:D0:59:C8:76:3E
inet6 addr: fe80::2d):59ff:fec8:763e/64 Scope: Link
UP BROADCAST RUNNING MULTICAST MTU:1500 Metric:1
RX packets: 368 errors: 627 dropped: 0 overruns:0 frame:627
TX packets:90 errors:6 dropped: 0 overruns: 0 carrier:0
collisions:1 txqueuelen:1000
RX bytes: 13668 (13.3 KB)  TX bytes bytes:7648 (7.4 KB)
Interrupt:11 Base address:0x8000

eth1:avah Link encap:Ethernet HWaddr 00:D0:59:C8:76:3E
inet addr:169.254.6.233 Bcast:169.254.255.255 Mask:255.255.0.0
UP BROADCAST RUNNING MULTICAST MTU:1500 Metric:1
Interrupt:11 Base Address:0x8000

lo     Link encap:Local loopback
inet addr:127.0.0.1  Mask:255.0.0.0
inet6 addr: ::1/128 Scope:Host
UP LOOKBACK RUNNING MTU:16436 MEtric:1
RX packets:43 errors:0 dropped:0 overruns:0 frame:0
TX packets:43 errors:0 dropped:0 overruns:0 carrier:0
collisons:0 txqueuelen:0
RX bytes:3611 (3.5 kb) TX bytes:3611 (3.5 kb)

wifi0  Link encap:UNSPEC HWaddr 00-D0-59-C8-76-3e-00-00-00-00-00-00-00-00-0-00(or something like that)
UP BROADCAST MULTICAST MTU:2312 Metric:1
RX packets:368 errors:627 dropped:0 overruns:0 frame:627
TX packets:90 errors:6 dropped:0 overruns:0 carrier:0
collisions:1 txqueuelen:100
RX bytes:13668 (13.3 kb) TX Bytes:7648 (7.4 kb)
Interrupt:11 Base address:0x8000

P.S. I was connected to the internet through wi-fi, with a router in my house. Is there any chance that I could receive a connection from another computer in the house?

sorry for smilies in middle :0 is supposed to be : 0 without the space no wait D0 is supposed to be D 0 without the space my bad

---

### Post by superprash2003 on 2008-04-25
go to system->administration->network choose the wifi0 card and click on properties.try entering the ip address manually.. and set the gateway address as your router's ip address. if you are not sure about that.. then turn DHCP on..after that post ifconfig again.. then in your terminal type ping google.com and post results here

---

